# Web Shaders Playbook — GPU Craft for the Browser

The half of web shaders that doesn't make it into the Shadertoy copy-paste. Not a "what is a fragment shader" intro — this is the **technique vocabulary, the math, the integration paths, and the failure modes** that separate a shader you wrote from a shader you pasted. The compositor-killing effects, the procedural toolkit (SDFs, noise, raymarching), and the WebGL2→WebGPU reality of 2026. Companion to `css-playbook.md` (native CSS/SVG filters — §26 there is the no-GPU alternative) and `gsap-playbook.md` (JS motion).

> **Why this exists.** Shader code is where models hallucinate hardest: `texture2D` in a `#version 300 es` shader, `gl_FragColor` that no longer exists, a normal that's never normalized, colors mixed in the wrong space, a vec3 that breaks a WGSL uniform buffer. The canonical techniques (IQ's distance functions, Ashima noise, sphere tracing) are *exact* — a wrong sign or epsilon gives a black screen, not a warning. This doc is the corrective: correct, compiling, and honest about what runs where.

> **The first question is always "should this be a shader at all?"** A gradient, a blur, a frosted panel, a mask fade — CSS/SVG/Canvas2D do these cheaper, accessibly, with zero GPU risk (see `css-playbook.md` §22–26). Reach for a shader when the effect is **per-pixel procedural, genuinely 3D, real-time interactive, or GPGPU** — not because it looks impressive. A full-screen fragment shader for a two-stop gradient is a thermal bug, not a flex.

> **Verified June 2026** against MDN, caniuse, the W3C WebGPU + WGSL specs, iquilezles.org, The Book of Shaders, and Three.js docs (r184).

## Support legend

Every API/feature is tagged. **Read the tag before shipping.**

- ✅ **Baseline widely available** — safe everywhere, ship unguarded.
- 🟢 **Baseline newly available** — landed all engines recently; ship with a fallback for the straggler tail.
- 🟡 **Limited** — a major engine or platform is missing. Gate + fallback.
- 🔴 **Single-engine / experimental** — Chromium-only or flagged. Progressive enhancement only.
- ☠️ **Dead / legacy** — don't start new work on it.

## The 2026 reality nobody updated their mental model for

- **WebGPU is Baseline** (Jan 2026) — Chrome 113 (2023), Safari 26 (Sept 2025), Firefox 141 (Win) / 145 (macOS ARM). **But the tail is real:** Firefox on Linux/Android/Intel-Mac and pre-A12 iPhones still fall back. ~87% desktop, ~71% mobile. Ship WebGPU *with a WebGL2 fallback*, or just WebGL2 if you need the last 10%.
- **WebGL2 is the safe base, not legacy** — ✅ all engines since Safari 15 (2021). For 2D/full-screen fragment work it is still the correct default in 2026. WebGL**1** is the legacy one.
- **You probably shouldn't hand-write WGSL.** In Three.js, **TSL (Three Shading Language)** — stable since r184 — is a JS node graph that compiles to **both** WGSL (WebGPU) *and* GLSL (WebGL2) from one source. Hand-authored WGSL locks you out of the fallback.
- **Color management is on by default in Three (since r152).** Half of "my shader colors look washed out / too dark" is sRGB↔linear, not your math. `.encoding` is dead — it's `.colorSpace` now.
- **`fwidth()`-based anti-aliasing is the most underused craft tool** — analytic AA on SDFs, one line, no MSAA cost. Most AI-written shapes ship with hard aliased edges.
- **The expensive resource is fill rate, not instructions.** A full-screen shader runs your fragment code millions of times per frame. Resolution scaling (clamp `devicePixelRatio`) beats almost every micro-optimization.

---

# Foundations

## 1. The pipeline mental model

```
vertices → [VERTEX shader] → clip space → rasterizer → fragments → [FRAGMENT shader] → pixels
```
- **Vertex shader** runs once per vertex (cheap: a triangle = 3 invocations). Outputs clip-space position + per-vertex data to interpolate.
- **Fragment shader** runs once per *covered pixel* (expensive: a full-screen pass at 2× DPR on a 1440p display ≈ **11M invocations/frame**). This is where cost lives.
- The rasterizer **interpolates** vertex outputs across the triangle (perspective-correct) — a `varying`/inter-stage value is a *gradient*, not a constant.
- **Mental model for web effects:** most "web shaders" are a single full-screen triangle with all the work in the fragment shader. You're writing a function `pixel(uv) → color` that the GPU runs in massive parallel. Per-pixel branching that *diverges* across neighbors is what hurts (§27), not raw line count.

## 2. WebGL2 vs WebGPU vs WebGL1 — what to pick in 2026

| | Tag | Use when |
|---|---|---|
| **WebGL2** | ✅ Baseline (Safari 15+, 2021) | Default for 2D/full-screen fragment effects, post-processing, most creative work. GLSL ES 3.00. |
| **WebGPU** | 🟢 Baseline (Jan 2026) | Compute shaders (GPGPU, particles at scale), heavy scenes, modern API, less global state. WGSL. Ship a WebGL2 fallback for the mobile/Firefox-Linux tail. |
| **WebGL1** | ☠️ legacy | Never for new projects. GLSL ES 1.00, no `texture()`, no MRT, integer-poor. Only if you must support a museum browser. |

- **What WebGPU actually buys you:** real **compute shaders** (the big one — particle/physics sim without texture hacks), explicit resource binding (fewer footguns than WebGL's global state machine), storage buffers, timestamp queries for profiling, generally better multi-pass performance.
- **Migration reality:** you rarely port by hand. Use **Three.js + TSL** (§23) or a library that targets both. Hand-porting GLSL→WGSL is where the alignment/Y-flip/entry-point bugs breed.

## 3. The full-screen fragment setup (WebGL2)

The "Shadertoy on your own page" boilerplate. **No vertex buffer needed** — generate a full-screen triangle from `gl_VertexID` (the trick AI usually misses, shipping a quad + buffer instead):

```glsl
// vertex.glsl
#version 300 es
void main() {
  // 3 verts → one oversized triangle covering the screen (cheaper than a 2-tri quad)
  vec2 p = vec2(float((gl_VertexID << 1) & 2), float(gl_VertexID & 2));
  gl_Position = vec4(p * 2.0 - 1.0, 0.0, 1.0);
}
```
```glsl
// fragment.glsl
#version 300 es
precision highp float;            // REQUIRED in fragment shaders — no default float precision
uniform vec2  uResolution;
uniform float uTime;
out vec4 fragColor;               // 300 es: declare your own output. gl_FragColor is GONE.
void main() {
  vec2 uv = gl_FragCoord.xy / uResolution;     // 0..1, origin BOTTOM-LEFT (see §5)
  uv = uv * 2.0 - 1.0;                          // -1..1, centered
  uv.x *= uResolution.x / uResolution.y;        // aspect-correct (§8) — the constant botch
  fragColor = vec4(0.5 + 0.5 * cos(uTime + uv.xyx + vec3(0, 2, 4)), 1.0);
}
```
```js
// minimal WebGL2 host — compile, link, CHECK ERRORS, draw 3 verts in a RAF loop
const gl = canvas.getContext('webgl2');
const sh = (type, src) => { const s = gl.createShader(type); gl.shaderSource(s, src); gl.compileShader(s);
  if (!gl.getShaderParameter(s, gl.COMPILE_STATUS)) throw gl.getShaderInfoLog(s); return s; };   // never skip this
const p = gl.createProgram();
gl.attachShader(p, sh(gl.VERTEX_SHADER, vert)); gl.attachShader(p, sh(gl.FRAGMENT_SHADER, frag));
gl.linkProgram(p);
if (!gl.getProgramParameter(p, gl.LINK_STATUS)) throw gl.getProgramInfoLog(p);
gl.useProgram(p);
const uRes = gl.getUniformLocation(p, 'uResolution'), uTime = gl.getUniformLocation(p, 'uTime');
(function frame(t) {
  gl.uniform2f(uRes, canvas.width, canvas.height);
  gl.uniform1f(uTime, t * 0.001);
  gl.drawArrays(gl.TRIANGLES, 0, 3);
  requestAnimationFrame(frame);
})(0);
```
WebGPU does the same with ~3× the host code (adapter→device→pipeline→bind groups). For a single full-screen shader, WebGL2 is less ceremony; reach for WebGPU when you need compute. The WGSL fullscreen vertex is the same triangle trick (§21).

## 4. GLSL ES 3.00 ↔ WGSL — the cross-reference that prevents the mixups

| Concept | GLSL ES 3.00 (WebGL2) | WGSL (WebGPU) |
|---|---|---|
| Version directive | `#version 300 es` (first line, no blank above) | none |
| Float precision | `precision highp float;` (mandatory) | none — type is `f32` / `f16` |
| Vectors | `vec2 vec3 vec4` | `vec2f` / `vec2<f32>` … |
| Matrices | `mat3 mat4` | `mat3x3f` / `mat4x4f` |
| Entry point | `void main()` | `@vertex fn vs(...)` / `@fragment fn fs(...)` |
| Vertex output pos | `gl_Position` | `@builtin(position) vec4f` (return value) |
| Fragment output | `out vec4 fragColor;` | `@location(0) vec4f` (return value) |
| Vertex index | `gl_VertexID` | `@builtin(vertex_index) u32` |
| Frag coord | `gl_FragCoord` | `@builtin(position)` in the fragment fn |
| Attribute in | `in vec3 aPos;` | `@location(0) pos: vec3f` |
| Inter-stage (varying) | `out`/`in` between stages | `struct` with `@location(n)` |
| Uniform | `uniform float uT;` | `@group(0) @binding(0) var<uniform> u: U;` (a struct) |
| Texture sample | `texture(tex, uv)` | `textureSample(tex, samp, uv)` |
| Discard | `discard;` | `discard;` |
| Constructors | `vec3(1.0)` | `vec3f(1.0)` |
| `mix/fract/clamp` | same names | same names |

**Migration traps (the AI-classic bugs):**
- `texture2D()` / `textureCube()` → don't exist in 300 es; it's `texture()`. `gl_FragColor` / `varying` / `attribute` → all removed in 300 es.
- GLSL is **column-major**, multiply `M * v`. WGSL same, but watch matrix constructor order.
- WGSL needs **explicit type suffixes** and is strict: `1` is an `i32`, `1.0` is `f32`/`AbstractFloat` — no silent int→float promotion in many spots.
- WGSL entry points return their outputs; GLSL writes to globals. Forgetting `@location`/`@builtin` annotations = pipeline error, not a warning.

## 5. Coordinate spaces & the Y-flip / NDC traps

- **Clip space / NDC:** after the vertex shader, x/y ∈ [-1, 1]. **WebGL depth z ∈ [-1, 1]; WebGPU z ∈ [0, 1].** Porting depth math between them without adjusting is a silent bug.
- **UV origin differs:** `gl_FragCoord` / WebGL textures are **bottom-left origin**. Images, canvases, and **WebGPU's framebuffer are top-left**. → the **Y-flip**: sampled images appear upside-down. Fixes: `uv.y = 1.0 - uv.y` in the shader, or `gl.pixelStorei(gl.UNPACK_FLIP_Y_WEBGL, true)` at upload, or `texture.flipY` in Three. **Pick one and be consistent** — flipping twice is the bug after the fix.
- **NDC y is up; screen y is down.** A clip-space triangle and a CSS-pixel coordinate disagree on which way is up.
- `gl_FragCoord` is in **pixels** (with a half-pixel center offset: pixel centers are at `x.5`). Divide by resolution for 0..1 UV.

## 6. Precision qualifiers ✅ — and the mobile trap

```glsl
precision highp float;     // top of every fragment shader
```
- `highp` (≥ fp32-ish), `mediump` (≥ fp16), `lowp` (≥ fp10). Vertex shaders default to `highp`; **fragment shaders have no default — you must declare one.**
- **Mobile trap:** `mediump` on phones can be *actual* fp16. Large coordinates, `uTime` growing unbounded, or world positions in `mediump` → visible quantization/jitter after a few minutes. Use `highp` for positions, time, and anything accumulating; `mediump` is fine for colors/normals if you must optimize.
- **WGSL has no precision qualifiers** — everything is `f32` unless you opt into `f16` (`enable f16;`, 🟡 — not universal, check `device.features`).
- **`uTime` precision:** feed a *wrapped* or smaller time (e.g. `mod(time, 3600.0)`) so `highp` doesn't lose sub-frame resolution after long sessions. Animating off an ever-growing float is the "why did it get choppy after 10 min" bug.

## 7. Passing data in — uniforms, buffers, textures

- **GLSL:** `uniform` scalars/vectors/matrices; **UBOs** (`layout(std140) uniform Block { ... }`) for grouped data; textures as `sampler2D`. Update per frame with `gl.uniform*`.
- **WGSL:** everything is a **struct in a buffer**, bound via bind groups. This is where the **alignment trap** lives (§ "what AI gets wrong"): `vec3<f32>` aligns to **16 bytes** — a `struct { a: f32; b: vec3f; }` is not packed the way you'd guess; the GPU inserts padding and your data lands in the wrong slots. Order members large→small, or pad `vec3` to `vec4` explicitly.
- **Textures carry data, not just images** — encode positions/velocities/LUTs in float textures (`RGBA32F`/`RGBA16F`). The basis of FBO particle sims (§19) and LUT color grading (§17).
- **Cheap channel for "mouse/scroll/time":** pack interaction into a few uniforms; don't rebuild buffers per frame (§27).

---

# Fragment Craft — the 2D toolkit

## 8. UV fundamentals

```glsl
vec2 uv = gl_FragCoord.xy / uResolution;        // 0..1
vec2 p  = (gl_FragCoord.xy * 2.0 - uResolution) / uResolution.y;  // -1..1, aspect-correct, y-normalized
```
- **Aspect correction is the #1 botch** — circles become ellipses on non-square canvases. Either divide by `uResolution.y` (keeps vertical scale stable) or multiply `uv.x *= aspect`. Be deliberate about *which* axis stays unit-length.
- **Tiling:** `fract(uv * n)` repeats; `floor(uv * n)` gives the cell id (for per-cell randomness). **Mirror tiling:** `abs(fract(uv)*2.0 - 1.0)`.
- **Polar:** `float a = atan(p.y, p.x); float r = length(p);` — kaleidoscopes, radial gradients, swirls. `atan(y,x)` (two-arg) handles all quadrants; one-arg `atan` doesn't.

## 9. The math toolkit

`mix(a,b,t)` lerp · `step(edge,x)` hard 0/1 · `smoothstep(e0,e1,x)` smooth 0→1 · `clamp` · `fract` · `mod` · `sign` · `floor`/`ceil` · `abs` · `length`/`distance` · `dot`/`cross`.
- **`smoothstep` is the workhorse** — every soft edge, fade, and gradient. `smoothstep(0.4, 0.6, x)` is a soft threshold; chain two for a band: `smoothstep(a,b,x) - smoothstep(c,d,x)`.
- **`mod` sign trap:** GLSL `mod` follows the sign of the divisor (unlike C `%`). For negative inputs it may not do what you expect — `mod(-0.2, 1.0) == 0.8`.
- **`step` causes aliasing; `smoothstep` + `fwidth` fixes it** (§10).

## 10. Anti-aliasing with derivatives `fwidth` — the most under-used craft tool

The line that turns jagged SDF edges into crisp ones, at zero MSAA cost:
```glsl
float d = sdCircle(p, 0.5);              // signed distance (negative = inside)
float w = fwidth(d);                      // how fast d changes per pixel (screen-space derivative)
float mask = 1.0 - smoothstep(-w, w, d);  // 1 inside, 0 outside, ~1px smooth boundary
```
- `fwidth(x) = abs(dFdx(x)) + abs(dFdy(x))` — the per-pixel change. Using it as the smoothstep width makes the transition **exactly one pixel regardless of zoom/scale** — resolution-independent AA.
- **Crisp lines / outlines:** `float line = 1.0 - smoothstep(0.0, w, abs(d) - thickness);`.
- **Availability:** derivatives are core in GLSL ES 3.00 / WebGL2 ✅ (were an extension in WebGL1). In WGSL they're `dpdx`/`dpdy`/`fwidth`. Only valid in **fragment** shaders.
- **Trap:** `fwidth` on a value with discontinuities (e.g. across a `mod` seam or `atan` wrap) spikes → a bright/dark seam artifact. AA the continuous field, not the wrapped one.

## 11. 2D SDFs + boolean ops — the Inigo Quilez set

Signed distance: **negative inside, zero on the edge, positive outside.** Compose shapes with math, AA with §10. (Verbatim from iquilezles.org/articles/distfunctions2d.)
```glsl
float sdCircle(vec2 p, float r) { return length(p) - r; }

float sdBox(vec2 p, vec2 b) {                       // b = half-extents
  vec2 d = abs(p) - b;
  return length(max(d, 0.0)) + min(max(d.x, d.y), 0.0);
}

float sdRoundedBox(vec2 p, vec2 b, vec4 r) {        // r = per-corner radius (x=TR,y=BR,z=TL,w=BL)
  r.xy = (p.x > 0.0) ? r.xy : r.zw;
  r.x  = (p.y > 0.0) ? r.x  : r.y;
  vec2 q = abs(p) - b + r.x;
  return min(max(q.x, q.y), 0.0) + length(max(q, 0.0)) - r.x;
}

float sdSegment(vec2 p, vec2 a, vec2 b) {           // line/capsule core
  vec2 pa = p - a, ba = b - a;
  float h = clamp(dot(pa, ba) / dot(ba, ba), 0.0, 1.0);
  return length(pa - ba * h);
}
```
**Boolean ops** (combine fields):
```glsl
float opUnion(float a, float b)        { return min(a, b); }
float opSubtraction(float a, float b)  { return max(-a, b); }   // b minus a
float opIntersection(float a, float b) { return max(a, b); }
float opRound(float d, float r)        { return d - r; }        // grow/round any shape
float opOnion(float d, float r)        { return abs(d) - r; }   // annular ring/outline
```
**Smooth-minimum** (`smin`) — the organic blend that makes SDFs feel alive (metaballs, soft merges):
```glsl
float smin(float a, float b, float k) {              // polynomial smin (IQ)
  float h = clamp(0.5 + 0.5 * (b - a) / k, 0.0, 1.0);
  return mix(b, a, h) - k * h * (1.0 - h);
}
```
- **Trap:** `min`/`max` boolean ops are only *exact* distances away from the seam — `smin` and rounding bias the field slightly, so don't trust the absolute value near joins for things like outlines.
- **Stroke from any SDF:** `abs(d) - thickness` then AA. **Fill:** `mask(d)` from §10.

## 12. Hashing & noise — texture-free randomness

**Hash (pseudo-random from coords):**
```glsl
float hash(vec2 p) { return fract(sin(dot(p, vec2(127.1, 311.7))) * 43758.5453123); }
```
- **The `sin`-hash is everywhere and it's flawed** — it bands on some GPUs (precision-dependent) and isn't uniform. Fine for grain/jitter; for serious work use an integer/bit-hash (Dave Hoskins' *Hash without Sine* set) for cross-GPU stability.

**Value noise** (smooth, cheap):
```glsl
float valueNoise(vec2 p) {
  vec2 i = floor(p), f = fract(p);
  vec2 u = f * f * (3.0 - 2.0 * f);                 // smoothstep interpolation
  return mix(mix(hash(i + vec2(0,0)), hash(i + vec2(1,0)), u.x),
             mix(hash(i + vec2(0,1)), hash(i + vec2(1,1)), u.x), u.y);
}
```
**fBm** (fractal sum — the texture of clouds, terrain, smoke):
```glsl
float fbm(vec2 p) {
  float v = 0.0, a = 0.5;
  for (int i = 0; i < 6; i++) { v += a * valueNoise(p); p *= 2.0; a *= 0.5; }
  return v;
}
```
- **Gradient/Perlin & Simplex:** for higher quality use **Ashima `webgl-noise`** (`snoise`, MIT-licensed — keep the license header). Simplex scales better to 3D/4D and has fewer directional artifacts than value noise. Don't paste a "simplex" you can't attribute — half the copies online are subtly broken.
- **Worley/cellular** (the basis of Voronoi, caustics, scales): for each cell, distance to the nearest random feature point; `F2 - F1` gives crack/edge patterns.
- **Domain warping** (IQ) — feed noise into noise for organic flow: `fbm(p + fbm(p + fbm(p)))`. The single highest-impact "how is this so good" trick.

## 13. Patterns

- **Stripes:** `smoothstep` over `sin(uv.x * n)` or `fract`. **Grid:** `min(grid.x, grid.y)` of two stripe fields; AA the lines with `fwidth`.
- **Voronoi:** from cellular noise — color by cell id (`hash(cellId)`), outline by `F2 - F1`. Animated feature points = living cells.
- **Truchet tiles:** per cell, randomly pick one of two arc orientations → endless connected mazes/curves from a hash.
- **Halftone/dots:** `length(fract(uv * n) - 0.5)` thresholded by an underlying value → dot-size encodes brightness.

## 14. Color craft

**IQ cosine palette** — a whole gradient from 4 vec3s, no texture (the pro move for cohesive color):
```glsl
vec3 palette(float t, vec3 a, vec3 b, vec3 c, vec3 d) {
  return a + b * cos(6.28318 * (c * t + d));
}
// pleasing default: a=b=vec3(0.5), c=vec3(1.0), d=vec3(0.0, 0.33, 0.67)
vec3 col = palette(t, vec3(0.5), vec3(0.5), vec3(1.0), vec3(0.0, 0.10, 0.20));
```
- **sRGB ↔ linear is the source of most "wrong colors."** Lighting, blending, and `mix` are physically correct only in **linear** space; the screen wants **sRGB**. Convert in: `pow(c, vec3(2.2))`, out: `pow(c, vec3(1.0/2.2))` (approx) — or the accurate piecewise sRGB curve. In Three.js this is automatic (§26) — don't double-correct.
- **Dithering kills banding** on smooth gradients (8-bit output quantizes): add ~1/255 of noise before output.
```glsl
fragColor.rgb += (hash(gl_FragCoord.xy) - 0.5) / 255.0;   // cheap ordered/blue-noise is better
```
- **Posterize:** `floor(c * n) / n`. **HSV→RGB** (IQ): `clamp(abs(mod(h*6.+vec3(0,4,2),6.)-3.)-1.,0.,1.)` for hue rotation.
- **Mix in oklab/oklch-like space** for perceptually even ramps (mirror of `css-playbook.md` §16) — sRGB `mix` darkens through the midpoint.

---

# Advanced

## 15. Raymarching / sphere tracing

3D from a distance function — no meshes. March along the ray, step by the distance to the nearest surface:
```glsl
float map(vec3 p) {                          // the scene SDF (sphere here)
  return length(p) - 1.0;
}
vec3 calcNormal(vec3 p) {                     // gradient of the field (IQ tetrahedron — 4 taps)
  const vec2 k = vec2(1.0, -1.0);
  const float h = 0.0005;
  return normalize(k.xyy * map(p + k.xyy * h) + k.yyx * map(p + k.yyx * h) +
                   k.yxy * map(p + k.yxy * h) + k.xxx * map(p + k.xxx * h));
}
float raymarch(vec3 ro, vec3 rd) {
  float t = 0.0;
  for (int i = 0; i < 128; i++) {             // CONSTANT loop bound (GLSL needs it)
    vec3 p = ro + rd * t;
    float d = map(p);
    if (d < 0.001 || t > 50.0) break;         // hit, or escaped
    t += d;                                    // safe step = distance to surface
  }
  return t;
}
```
**Soft shadows** (IQ + Aaltonen — the banding-free version, verbatim):
```glsl
float softshadow(vec3 ro, vec3 rd, float mint, float maxt, float w) {
  float res = 1.0, ph = 1e20, t = mint;
  for (int i = 0; i < 256 && t < maxt; i++) {
    float h = map(ro + rd * t);
    if (h < 0.001) return 0.0;
    float y = h * h / (2.0 * ph);
    float d = sqrt(h * h - y * y);
    res = min(res, d / (w * max(0.0, t - y)));
    ph = h;
    t += h;
  }
  return res;
}
```
- **Lighting:** `float diff = max(dot(n, lightDir), 0.0);` (Lambert). Add ambient + a `pow(spec, shininess)` Phong highlight.
- **AO (cheap, IQ 5-tap):** sample `map()` at increasing offsets along the normal; less open space = darker.
- **Traps AI gets wrong:** (1) **never `normalize(vec3(0))`** — guard tiny epsilons; (2) the normal epsilon `h` must match scene scale — too small = noise, too large = faceting; (3) loop bound must be a **compile-time constant** in GLSL; (4) step count is your perf budget (§27) — 128 is generous for hero shots, drop to 48–64 for backgrounds; (5) thin/grazing geometry needs more steps or it leaks light.

## 16. Render-to-texture & ping-pong — the multi-pass backbone

Most real effects are **several passes**: render the scene to a texture, then run more shaders on that texture.
- **WebGL2:** render into a **Framebuffer Object (FBO)** with a texture attachment instead of the screen. **WebGPU:** render to a `GPUTexture` / render target.
- **Ping-pong:** two targets, A→B then B→A each frame. Required for any effect that reads its own previous output: separable blur, feedback trails, GPGPU sims, reaction-diffusion.
```
sceneFBO → [bright-pass] → blurA → [blur H] → blurB → [blur V] → blurA → composite to screen
```
- **Traps:** (1) you **cannot read and write the same texture in one pass** — that's why ping-pong exists; (2) match the render-target format to your needs (`RGBA16F` for HDR/bloom, `RGBA32F` for sim state — and check the float-render extension/feature); (3) reset the viewport when switching between full-res screen and lower-res buffers; (4) clear targets or last frame bleeds in (unless you *want* feedback).

## 17. Post-processing catalog

Full-screen passes over a rendered texture. Kernels you'll actually reuse:
- **Gaussian blur — separable** (the only sane way): blur horizontally then vertically (2N taps instead of N²). Weights from a Gaussian.
- **Kawase / dual-filter blur** — cheaper than Gaussian at large radii (a few taps at growing offsets); the modern default for big soft blurs and bloom.
- **Bloom:** bright-pass (`max(color - threshold, 0)`) → blur (mip chain or Kawase) → add back. Do it in **linear/HDR** space or it looks muddy.
- **Chromatic aberration:** sample R/G/B at slightly offset UVs, offset growing toward edges: `texture(t, uv + dir * vec3(-1,0,1) * amount)`.
- **Vignette:** `1.0 - dot(p, p) * amount` (or `smoothstep`) multiplied into color.
- **Film grain:** `color += (hash(uv + uTime) - 0.5) * strength;` — animate per frame.
- **CRT/scanline:** sine on `uv.y * lines`, barrel distortion on UV, RGB mask.
- **Color grading via LUT:** sample a 2D/3D lookup texture by the pixel's color → film looks. Cheap, art-directable.
- **Tone mapping** (HDR→display): **ACES** (filmic, the common choice) or Reinhard, applied **before** the sRGB encode. Required if you work in HDR/bloom.
- **FXAA:** post-AA from luma edges — cheap, slightly soft; fine for full-screen shader output where MSAA doesn't apply.
- **Order matters & space matters:** grade/bloom in linear, tonemap, *then* sRGB-encode, *then* grain/dither. Wrong order = washed or crushed output.

## 18. Vertex displacement

Move geometry on the GPU — waves, morphs, terrain, "goo".
```glsl
// vertex shader
vec3 p = position;
p.y += sin(p.x * 4.0 + uTime) * 0.2 + fbm(p.xz);   // displace
gl_Position = projectionMatrix * modelViewMatrix * vec4(p, 1.0);
```
- **THE classic bug:** displacing position but **not recomputing the normal** → lighting is flat/wrong because normals still point as if the surface were undisplaced. Fix: recompute analytically (derivative of your displacement) or via **finite differences** — displace two nearby points, cross the tangents: `normal = normalize(cross(pdx - p, pdz - p))`.
- **Keep displacement in `highp`** and in a stable space; large `uTime` in `mediump` jitters (§6).
- **Instancing:** draw thousands of copies with per-instance attributes (matrix/color) in one call — `gl_InstanceID`, `drawArraysInstanced`. The basis of GPU-cheap particle fields with real geometry.

## 19. Particles & GPGPU

Simulate millions of points on the GPU. Three approaches:
- **WebGL2 — Transform Feedback:** the vertex shader writes its outputs back into a buffer (capture position/velocity), ping-pong two buffers. No fragment stage needed. The native WebGL2 GPGPU path.
- **WebGL2 — FBO/texture sim:** store positions & velocities in **float textures**; a fragment shader integrates physics; ping-pong targets; a render pass reads the position texture as point sprites. Works everywhere WebGL2 does; the classic before compute existed.
- **WebGPU — Compute shaders** 🟢: `@compute` with storage buffers — the *right* tool. Arbitrary read/write, workgroups, no texture-as-memory hacks. Use for large-scale sims, flocking, physics. Ship a WebGL2 FBO fallback for the tail.
- **Trap:** order-dependent updates and inter-particle forces (N-body) need careful buffer separation (read old, write new) — never read the buffer you're writing.

## 20. Image effects & transitions — the web's bread and butter

- **Displacement hover/reveal:** offset texture UVs by a displacement map (noise or a designed map) driven by a `progress`/`hover` uniform → liquid image reveals, the agency-site staple.
- **Shader transitions (gl-transitions style):** a function of `(uv, progress)` mixing two textures. The portable convention:
```glsl
vec4 transition(vec2 uv) {                 // progress 0→1, getFromColor/getToColor sample the two images
  vec2 dir = uv - 0.5;
  float d = length(dir);
  float m = smoothstep(progress - 0.1, progress, d);    // expanding circle wipe
  return mix(getToColor(uv), getFromColor(uv), m);
}
```
  (The gl-transitions library is a large MIT catalog of these — reach for it before hand-rolling.)
- **Feedback buffers (trails/echoes):** blend the previous frame (slightly faded/offset) with the new one via ping-pong → motion trails, infinite-zoom tunnels, paint.
- **Reaction-diffusion (Gray-Scott):** two chemicals in a ping-pong texture, Laplacian + feed/kill rates → organic Turing patterns (spots, stripes, coral). Pure shader, mesmerizing, cheap.
- **Fluid (stable fluids / Navier-Stokes lite):** advect → diffuse → project (pressure solve) across several ping-pong passes → the interactive smoke/ink everyone wants. Heavy; use an existing implementation (PavelDoGreat's WebGL-Fluid) rather than deriving the projection step wrong.

---

# Integration

## 21. Raw WebGPU — the minimal fragment setup

When you need compute or are going WebGPU-native. The fullscreen triangle, WGSL:
```wgsl
@vertex fn vs(@builtin(vertex_index) i: u32) -> @builtin(position) vec4f {
  let p = array(vec2f(-1.0, -1.0), vec2f(3.0, -1.0), vec2f(-1.0, 3.0));   // oversized tri
  return vec4f(p[i], 0.0, 1.0);
}
@group(0) @binding(0) var<uniform> uRes: vec2f;
@fragment fn fs(@builtin(position) c: vec4f) -> @location(0) vec4f {
  let uv = c.xy / uRes;                         // top-left origin in WebGPU (§5)
  return vec4f(uv, 0.5, 1.0);
}
```
Host is heavier: `navigator.gpu.requestAdapter()` → `requestDevice()` → configure canvas context → create pipeline + bind group → encode a render pass each frame. **For one full-screen shader, this is more code than WebGL2 (§3) for no visual gain** — choose WebGPU for compute, scale, or a TSL-emitted target, not for a single effect.

## 22. Three.js — `ShaderMaterial` vs `RawShaderMaterial`

```js
const mat = new THREE.ShaderMaterial({
  uniforms: { uTime: { value: 0 }, uTex: { value: tex } },
  vertexShader, fragmentShader,
  glslVersion: THREE.GLSL3,            // opt into 300 es (and `out` fragment vars)
});
// in the loop: mat.uniforms.uTime.value = clock.getElapsedTime();
```
- **`ShaderMaterial`** injects Three's built-ins for you: `projectionMatrix`, `modelViewMatrix`, `normalMatrix`, and attributes `position`, `uv`, `normal`. Write less boilerplate. **`RawShaderMaterial`** injects *nothing* — you declare everything (and the `#version`/precision). Use Raw only when you need total control.
- **`onBeforeCompile`** — patch a *built-in* material (e.g. `MeshStandardMaterial`) by string-replacing chunks of its shader. The way to add a shader effect while keeping Three's PBR lighting/shadows. Powerful, brittle (depends on chunk names) — TSL (§23) is the supported replacement.
- **Trap:** don't re-declare uniforms Three already provides (`time` isn't one; `uv`/`position` are). Don't set `glslVersion` and then use `gl_FragColor`.

## 23. TSL — Three Shading Language (the 2026 shift) 🟢

Node-based shaders in **JavaScript** that compile to **WGSL (WebGPU) and GLSL (WebGL2) from one source** — stable since r184, the recommended path for new Three work targeting WebGPU.
```js
import { uniform, positionLocal, sin, vec3, time } from 'three/tsl';
import { MeshBasicNodeMaterial } from 'three/webgpu';
const mat = new MeshBasicNodeMaterial();
mat.colorNode = vec3(sin(time), 0.5, 0.8);        // runs on WebGPU or WebGL2, no WGSL/GLSL by hand
```
- **Why it matters:** you get the WebGPU fast path *and* the WebGL2 fallback without maintaining two shader languages — the single biggest reason not to hand-author WGSL in 2026.
- **`WebGPURenderer`** is the renderer for TSL/NodeMaterials; it falls back to WebGL2 automatically when WebGPU is absent. It's production-usable in 2026 but newer than the classic `WebGLRenderer` — test the fallback path.
- **Trade-off:** node graphs are more verbose than a terse GLSL one-liner and have a learning curve; for a quick Shadertoy port, raw `ShaderMaterial` is faster. For a maintained product wanting WebGPU, TSL wins.

## 24. React Three Fiber + drei + postprocessing

```jsx
import { shaderMaterial } from '@react-three/drei';
import { extend, useFrame } from '@react-three/fiber';
const WaveMaterial = shaderMaterial({ uTime: 0 }, vertexShader, fragmentShader);
extend({ WaveMaterial });
// <mesh><planeGeometry/><waveMaterial ref={r}/></mesh>
useFrame((_, dt) => { ref.current.uTime += dt; });   // delta-time (§28)
```
- **drei `shaderMaterial()`** generates a declarative material with typed uniform props + auto-attributes — the ergonomic R3F way; uniforms become JSX props.
- **`@react-three/postprocessing`** wraps the `postprocessing` lib's `EffectComposer` — bloom, DOF, glitch, CA, noise as `<Effect/>` components, merged into one efficient pass. Reach for it before hand-rolling a post chain.
- **Trap:** update uniforms in `useFrame`, never in render (re-creates the material). Use the `dt` argument, not a wall clock.

## 25. Other stacks + shipping shader code

- **OGL** — tiny WebGL library; when Three is too heavy but you want more than raw GL. **regl** — functional/stateless WebGL; great for one-off full-screen effects and demos. **PixiJS v8** — 2D engine, **dual WebGL/WebGPU** backend; custom filters via `Filter.from({ gl, gpu })` — the right tool for 2D image/UI effects and sprite shaders. **gl-react** — React-declarative GL for image pipelines.
- **Shipping `.glsl`/`.wgsl`:** **`vite-plugin-glsl`** (v1.6.0, maintained) imports/inlines/minifies GLSL **and WGSL** (and Slang), supports `#include` (lygia-compatible) — the de-facto loader in 2026. Plain JS template strings work for small shaders. **glslify** still exists but is legacy; new projects use `vite-plugin-glsl`'s `#include`.
- **LYGIA** — a large reusable shader `#include` library (noise, SDFs, color, filters) that works with the include resolver. Stop re-pasting `snoise`.

## 26. Color management in Three (why your colors look wrong)

- **On by default since r152.** Three works in **linear** internally and encodes to sRGB on output. `renderer.outputColorSpace = THREE.SRGBColorSpace` (default).
- **Tag your textures:** color/albedo textures are `THREE.SRGBColorSpace`; data textures (normal, roughness, displacement, LUTs, position data) are `THREE.LinearSRGBColorSpace` / `NoColorSpace`. **Mislabeling a normal map as sRGB is a classic "lighting looks off" bug.**
- **`.encoding` is dead** — it was renamed to `.colorSpace` (textures) / `outputColorSpace` (renderer). Old tutorials using `.encoding`/`sRGBEncoding` are stale.
- **In a custom `ShaderMaterial` you bypass some of this** — if you sample an sRGB texture and output directly, decode/encode yourself or set the material/texture color spaces correctly. Double-correcting (manual `pow` *and* Three's encode) is the "too dark / too bright" bug.
- **Tone mapping** (`renderer.toneMapping = THREE.ACESFilmicToneMapping`) also touches final color — turn it off to debug raw shader output.

---

# Performance, Robustness, Accessibility

## 27. Performance — fill rate is the enemy

- **Resolution scaling is the #1 win**, especially mobile: clamp DPR. `renderer.setPixelRatio(Math.min(devicePixelRatio, 2))`; for heavy full-screen shaders render at 0.5–0.75× and upscale. Halving resolution quarters fragment work.
- **Branch divergence:** GPUs run pixels in lockstep groups (warps/waves). An `if` where *neighboring pixels take different branches* makes the GPU run **both** sides. Cheap branches: uniform-driven (all pixels same way) or `mix`/`step` instead of `if`. Expensive: per-pixel data-dependent branches in tight loops.
- **Texture cost:** samples aren't free; **dependent reads** (sample at a UV you computed from another sample) defeat prefetch. Minimize taps; use mips.
- **Constant loop bounds** (GLSL): the compiler unrolls — keep iteration counts modest and `const`. Raymarching/blur step counts are your budget.
- **Minimize uniform/buffer churn:** set uniforms once if unchanged; don't rebuild geometry per frame; instance instead of looping draw calls.
- **Overdraw:** transparent/full-screen layers stack fragment work — every full-screen pass is another N-million invocations. Count your passes.

## 28. Frame loop — delta-time, not frame-count

```js
let last = performance.now();
function frame(now) {
  let dt = (now - last) / 1000; last = now;
  dt = Math.min(dt, 1/30);             // clamp: a tab regaining focus sends a huge dt → things teleport
  uTime += dt;
  requestAnimationFrame(frame);
}
```
- **Tie motion to `dt`, not "+= 0.01 per frame"** — otherwise speed depends on refresh rate (2× fast on 120Hz, slow on a janky frame). The most common amateur animation bug.
- Pause the loop when the tab/section is hidden (§29/§30) — don't burn GPU on invisible pixels.

## 29. Robustness — the production crashes

- **WebGL context loss is not optional** — GPUs reset (driver crash, tab backgrounded, too much VRAM). Without handling, your canvas goes black permanently.
```js
canvas.addEventListener('webglcontextlost', e => { e.preventDefault(); cancelAnimationFrame(raf); });
canvas.addEventListener('webglcontextrestored', () => { initGL(); /* recreate ALL gl resources */ });
```
- **WebGPU device loss:** `device.lost` is a promise — await it and re-init.
- **Always check compile/link logs** (§3) — a silent black screen is usually a shader that didn't compile. In dev, log `getShaderInfoLog`.
- **Feature/limit detection:** WebGPU — check `adapter.limits` / `adapter.features` before assuming compute/f16/storage limits. WebGL — `getExtension` for float-render, etc.
- **Fallback ladder:** WebGPU → WebGL2 → static image/CSS. Detect (`navigator.gpu`, `canvas.getContext('webgl2')`) and degrade; never assume the GPU path exists.

## 30. Accessibility

- **`prefers-reduced-motion`** — pause animation / show a static frame. A churning shader background is exactly the vestibular trigger the media query exists for (mirror of `css-playbook.md` motion-safety).
```js
if (matchMedia('(prefers-reduced-motion: reduce)').matches) { renderOneFrame(); /* don't loop */ }
```
- **Pause offscreen** — `IntersectionObserver` to stop the RAF loop when the canvas scrolls out of view. Running a shader nobody can see is pure waste (battery, heat).
- **Provide a real fallback** — `<canvas>` over a static `<img>`/CSS so no-GPU and reduced-motion users get *something*. Don't ship a blank box.
- **Flashing/contrast** — avoid strobing (seizure risk) and ensure any text over shader output stays legible against the worst-case frame.

## 31. Profiling & the black-screen checklist

- **Spector.js** — captures a WebGL frame, shows every call/state/draw. The first tool when "nothing renders."
- **WebGPU timestamp-query** — GPU-side timing per pass (where WebGL has almost no introspection). Browser GPU profilers + `chrome://gpu`.
- **Black screen debug order:** (1) shader compile/link log? (2) is anything drawn — set `fragColor = vec4(1,0,0,1)` to confirm the pass runs; (3) Y-flip / UVs out of range; (4) NaN from `normalize(0)` / `pow(neg)` / `/0`; (5) culling/depth/blend state; (6) uniforms actually set (location not -1); (7) viewport/render-target size; (8) color space (it's drawing, just black-on-black).

---

## What AI & juniors get wrong — the consolidated list

| Bug | Symptom | Fix |
|---|---|---|
| `texture2D` / `gl_FragColor` / `varying` in 300 es | won't compile | `texture()`, `out vec4`, `in`/`out` |
| Missing `#version 300 es` (must be line 1) | compile error / wrong dialect | first line, nothing above it |
| No `precision` in fragment shader | compile error | `precision highp float;` |
| **Y-flip** | sampled image upside-down | flip once (shader OR upload OR `texture.flipY`) — not twice |
| **sRGB↔linear confusion** | washed-out or too-dark, muddy blends | light/mix in linear, encode sRGB out; in Three, tag colorSpace, don't double-correct |
| Normal not normalized | broken/flat lighting | `normalize(n)` after interpolation/displacement |
| **Displaced verts, stale normals** | lit as if flat | recompute normals after displacement |
| `normalize(vec3(0.0))` | NaN → black pixels | guard with epsilon |
| Int vs float literal | `1` where `1.0` needed → compile error | always `1.0` in GLSL float context |
| NDC vs UV (−1..1 vs 0..1) | shape off-center/half-size | be explicit which space you're in |
| **WGSL `vec3` alignment** | uniform data lands in wrong fields | 16-byte align; pad vec3→vec4 or order large→small |
| WebGL z∈[−1,1] vs WebGPU z∈[0,1] | depth wrong after port | adjust depth math per API |
| `mediump` for time/position | jitter after minutes (mobile) | `highp`; wrap `uTime` |
| Frame-count animation | speed varies with refresh rate | multiply by delta-time |
| No context-loss handler | permanent black canvas in prod | handle `webglcontextlost`/`restored` |
| Premultiplied alpha mismatch | dark fringes on transparent edges | match blend func to texture's alpha mode |
| `if` per-pixel in hot loop | tanks mobile FPS | `mix`/`step`, or uniform-driven branches |

## Decision table — should it even be a shader?

| Want | Cheaper non-shader first | Shader when |
|---|---|---|
| Gradient / mesh gradient | CSS gradients (`css-playbook.md` §22) | animated/interactive procedural fields |
| Blur / frosted glass | CSS `backdrop-filter` (§24) | blur driven by sim/depth, or in a GL scene |
| Grain / duotone / distortion | SVG filters `feTurbulence`/`feDisplacementMap` (§26) | real-time, mouse/scroll-reactive, or 3D |
| Image hover/reveal | CSS mask/clip + transform | liquid displacement, fluid, per-pixel warp |
| Shape with soft edges | SVG / CSS `clip-path` | thousands of procedural shapes, SDF morphs |
| Particles (few) | DOM/Canvas2D | thousands–millions (GPGPU) |
| 3D | — | always (raster or raymarch) |

## Decision table — which stack

| Situation | Reach for |
|---|---|
| Single full-screen 2D effect, max reach | **raw WebGL2** (§3) or **regl/OGL** |
| 2D image/sprite/UI filters | **PixiJS v8** filters |
| 3D scene, classic, broad support | **Three.js** `WebGLRenderer` + `ShaderMaterial` |
| 3D scene, want WebGPU + fallback, maintained | **Three.js + TSL** + `WebGPURenderer` (§23) |
| React 3D | **R3F** + drei + `@react-three/postprocessing` |
| Compute / large GPGPU sim | **WebGPU** compute (§19), WebGL2 FBO fallback |

## The biggest wins to reach for first

`fwidth()` analytic AA on every SDF edge · IQ 2D distance functions + `smin` over hand-drawn shapes · cosine palettes for cohesive color · **work in linear, encode sRGB once** · dither to kill banding · clamp `devicePixelRatio` (the mobile lifesaver) · delta-time the loop · handle context loss · pause offscreen + honor `prefers-reduced-motion` · domain-warped fBm for "how is this so good" texture · LYGIA/gl-transitions instead of re-pasting · TSL when you want WebGPU without maintaining two shader languages · and always ask whether CSS/SVG (`css-playbook.md` §22–26) does it cheaper first.
