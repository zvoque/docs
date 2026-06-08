# GSAP Playbook — The Complete Motion Reference

Deep motion patterns for high-end bespoke websites. Everything GSAP can do, in playbook form: what it is, when to reach for it, the senior idiom, the trap.

> Part of a frontier/craft reference set — the platform features coding agents forget. Default reach for motion: a fade-in and a basic scroll listener. This is the rest of the toolkit. Mind the version/support notes; verify before prod.

> **Reduced-motion is mandatory.** Every scrub/pin/split/parallax/autoplay below needs a `prefers-reduced-motion: reduce` branch that sets the end-state and skips the motion. See §30.

---

## 0. Version & licensing (GSAP 3.13, 2025+)

- **GSAP 3.13.0 (Apr 29 2025) made the entire toolset 100% free, commercial use included.** Every former "Club GreenSock" plugin — SplitText, MorphSVG, DrawSVG, ScrollSmoother, MotionPathHelper, Physics2D/PhysicsProps, InertiaPlugin, GSDevTools, CustomBounce, CustomWiggle, Flip — now ships from the **public npm registry** in the single `gsap` package.
- **Webflow acquired GreenSock (fall 2024).** Still maintained by the original team. Webflow ships GSAP natively in-product (toggle in site settings, no CDN tag).
- **Club GreenSock is gone.** No auth tokens, no private registry, no `gsap-trial`. `pnpm add gsap`, register, ship.
- **3.13 API notes:** SplitText fully rewritten (~50% smaller, screen-reader a11y, responsive auto re-split). New: animate a property *to* a CSS variable's computed value — `gsap.to(".t", { color: "var(--brand)" })`.

```bash
pnpm add gsap          # core + every plugin, one package
pnpm add @gsap/react   # React useGSAP hook (separate package)
```

```js
import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import { SplitText } from "gsap/SplitText";
gsap.registerPlugin(ScrollTrigger, SplitText); // MANDATORY in bundlers — the call is the tree-shake guard
```

- **`registerPlugin` is not optional in a build.** Rollup/Vite/webpack shake out any plugin you don't reference; `registerPlugin` is that reference. CDN/UMD files self-register in the browser. A plugin that silently does nothing usually means it got shaken or never registered.

---

## 1. Tweens — `to / from / fromTo / set`

```js
gsap.to(targets, vars)               // current → vars
gsap.from(targets, vars)             // vars → current (immediateRender:true)
gsap.fromTo(targets, fromVars, toVars)
gsap.set(targets, vars)              // duration:0, instant write
```
`targets` = selector string · Element · Array · NodeList · or a plain JS object (animate any numeric property of anything).

### vars worth knowing

| Prop | Behavior | Trap |
|---|---|---|
| `duration` | Seconds, default `0.5`. Excludes repeats. | Function-based duration is NOT refreshed by `repeatRefresh`. |
| `ease` | Default `"power1.out"`. String or `fn(p)=>p`. | — |
| `delay` | Seconds before start. | On a timeline, use the position parameter, not `delay`. |
| `repeat` | Iterations after the first. `-1` = infinite. | `repeat:1` plays **twice**. |
| `yoyo` | Reverse alternate cycles (needs `repeat`). | Doesn't reverse the ease unless `yoyoEase:true`. |
| `yoyoEase` | `true` (invert ease on return) or a specific ease. | — |
| `repeatDelay` | Gap between cycles. | — |
| `repeatRefresh` | Re-evaluate dynamic/`"random()"`/function values each iteration. | Refreshes **values** only — never duration/delay/stagger. |
| `stagger` | Number or object (§3). | — |
| `overwrite` | `false` (default) · `true` (kill all tweens of target) · `"auto"` (kill only conflicting props, first render). | `"auto"` is the pro default for hover-in/out and interrupt-heavy UI. |
| `immediateRender` | Render at instantiation. Default `false` for `.to`, `true` for `.from`/`.fromTo`. | Stacking multiple `.from`s on the same prop flashes — set `immediateRender:false`. |
| `paused` | Start paused. | — |
| `id` | `gsap.getById(id)`, shows in GSDevTools. | — |
| `keyframes` | Multi-step (§2), `.to()` only. | — |
| `startAt` | Explicit pre-start state for `.to`/`.fromTo`. | — |
| `lazy` | Defer first write to end of tick (anti-thrash). Default `true`. | Disable if you read the value synchronously right after. |
| `inherit` | Inherit parent timeline `defaults`. Default `true`. | Set `false` to opt a child out. |

### Callbacks (each pairs with `*Params`)
`onStart` · `onUpdate` · `onComplete` · `onRepeat` · `onReverseComplete`. Inside, `this` = the tween (unless `callbackScope`). Pass the instance with `onCompleteParams: ["{self}"]`.
- `onComplete` never fires on infinite repeats. `onStart` can refire on restart.

### Instance control (chainable, returns the tween)
`play() pause() resume() reverse() restart() seek(t) kill([props],[targets]) invalidate() revert() isActive() then()`.
Getter/setters (no arg reads, arg sets): `progress() time() duration() timeScale() reversed() repeat() yoyo()` …
- `kill("opacity,x")` — surgical interruption of specific props.
- `invalidate()` — flush recorded start/end so next play re-reads live values (after a layout change).
- `revert()` — kill **and** strip inline styles back to pre-animation state.

---

## 2. Keyframes (`.to` only)

**Array** — sub-tweens run back-to-back, each with its own `duration`/`ease`/`delay` (negative delay = overlap):
```js
gsap.to(".box", {
  ease: "none", // master ease across the set
  keyframes: [
    { x: 100, duration: 1 },
    { y: 100, duration: 0.5, delay: 0.2, ease: "power2.inOut" },
    { rotation: 180, duration: 1 },
  ],
});
```
**Object / percentage** — percentages slice the tween's single `duration`:
```js
gsap.to(".box", {
  duration: 3,
  keyframes: {
    "0%":   { x: 0,   y: 0 },
    "50%":  { x: 100, y: 0, ease: "sine.out" },
    "100%": { x: 100, y: 100 },
    easeEach: "power1.inOut", // ease between EACH stop (per-stop ease overrides)
  },
});
```
- **Trap:** array derives total duration from the sum of sub-durations; object divides the outer `duration` by percentages. Don't mix the mental models.

---

## 3. Stagger

```js
stagger: 0.1                      // simple: 0.1s between starts (negative = last-first)

stagger: {
  each: 0.1,            // fixed gap per element  (total grows with count)
  amount: 1,           // OR fixed total spread   (gap shrinks as count grows)
  from: "center",      // start|center|end|edges|random | index number
  grid: [9, 15],       // [rows, cols] or "auto"
  axis: "x",           // restrict distance calc to one axis (grid)
  ease: "power2.in",   // reshapes the TIMING distribution, not the property ease
}

stagger: (i, target, list) => i * 0.1   // function: returns delay-from-start (cumulative)
```
- **`each` vs `amount` is the #1 trap.** `each` = fixed per-element gap → total duration scales with count. `amount` = fixed total → use it when you want predictable total length regardless of element count. Never set both.
- `grid:"auto"` measures via `getBoundingClientRect` and does **not** recompute on resize — wrap in `matchMedia`/refresh.
- Repeat placement: `{ repeat:-1, stagger:{} }` = whole sequence loops. `{ stagger:{ repeat:-1 } }` = each element loops independently.

---

## 4. Timelines

```js
const tl = gsap.timeline({
  defaults: { ease: "power2.out", duration: 1 }, // inherited by every child — highest-leverage feature
  paused, repeat, yoyo, repeatDelay, repeatRefresh,
  smoothChildTiming, autoRemoveChildren,
});
```

### Position parameter (3rd arg on `.to/.from/.add/.call`)
| Form | Meaning |
|---|---|
| `3` | absolute 3s from start |
| `"+=1"` / `"-=1"` | 1s after end / 1s overlap into end |
| `"<"` / `">"` | start / end of the **previous** animation |
| `"<1"`, `">-2"` | 1s after previous start / 2s before previous end |
| `"label"` / `"label+=2"` | at / after a label |
| `"+=50%"` | percentage of the **inserting** animation's own duration |

### Methods
- Content: `.to() .from() .fromTo() .set()`, `.add(child|array|fn, pos)`, `.addLabel(name, pos)`, `.call(fn, params, pos)`.
- **Nesting:** build sub-timelines in factory functions, `master.add(section(), "+=2")`. Each child keeps independent control and `timeScale` but rides the master playhead.
- **`tweenTo(pos, vars)` / `tweenFromTo(from, to, vars)`** — animate the *playhead itself* to a label/time. The idiom for "play just this segment then stop" (section hover states).

### Traps
- **`autoRemoveChildren:true`** destroys children on completion → no reverse/scrub. The root timeline uses this; never set it on a timeline you intend to scrub.
- `.progress()` excludes repeats; `.totalProgress()` includes them — pick correctly for scrub UIs.
- Referencing a non-existent label silently appends it at the current end.

---

## 5. Eases

**Built-in (no plugin):**
- `power0`…`power4` (power0 === `none`/linear; power1=quad … power4=quint), each `.in/.out/.inOut`.
- `sine` · `expo` · `circ` (each `.in/.out/.inOut`).
- `back.out(1.7)` — overshoot strength. `elastic.out(amplitude, period)` — e.g. `elastic.out(1, 0.3)`. `bounce.in/out/inOut`. `steps(n)` — discrete jumps (typewriter/sprite). `none`/`linear`.
- **EasePack** (tiny, in core): `rough({strength, points, taper, randomize})`, `slow(ratio, power)`, `expoScale(start, end)`.
- Default is `power1.out`; override globally with `gsap.defaults({ ease })`. Visualizer + bezier→CustomEase converter at gsap.com/docs/v3/Eases.

**Custom eases (free plugins, register them):**
```js
gsap.registerPlugin(CustomEase, CustomBounce, CustomWiggle);

CustomEase.create("hop", "M0,0 C0.1,0.8 0.2,1 1,1");   // SVG path
CustomEase.create("snap", ".17,.67,.83,.67");          // cubic-bezier shorthand (paste from Figma/AE)
gsap.to(el, { y: -100, ease: "hop" });

CustomBounce.create("drop", { strength: 0.6, squash: 3, squashID: "drop-squash" });
gsap.to(el, { y: 400, ease: "drop" });
gsap.to(el, { scaleX: 1.3, scaleY: 0.7, ease: "drop-squash" }); // synced squash-and-stretch = weight

CustomWiggle.create("shake", { wiggles: 8, type: "easeOut" }); // easeOut|easeInOut|anticipate|uniform|random
gsap.to(el, { rotation: 30, ease: "shake" });
```
- CustomBounce's `squashID` ease drives `scaleX/scaleY` on a *separate* tween synced to the bounce — that's what makes a drop feel heavy.
- CustomWiggle `type:"anticipate"` adds a pull-back before the wiggle.
- CustomWiggle extends CustomEase → register both. Paths must be monotonic on X (time can't reverse).

---

## 6. `gsap.utils` — the math toolbox

| Util | Signature | Idiom / trap |
|---|---|---|
| `interpolate` | `(a, b, t)` numbers/colors/arrays/objects; curried `(a,b)→fn(t)` | — |
| `mapRange` | `(inMin, inMax, outMin, outMax, value)`; omit value → `fn` | Drives scroll/pointer-linked values. Swap ranges to invert. |
| `clamp` | `(min, max, value)`; omit value → `fn` | Curried form is `pipe`-able. |
| `snap` | `(increment, v)` · `([a,b,c], v)` · `({values, radius}, v)` | `radius` only snaps within distance. |
| `wrap` | `(min, max, v)` · `([...], index)` | Infinite carousels. One-arg returns a `fn` — easy to forget to invoke. |
| `wrapYoyo` | `(min, max, v)` | Bounces at ends instead of wrapping. |
| `random` | `(min, max, [snap])` · `([arr])` · `(min,max,true)→fn` | `true` = seeded reusable fn; pairs with `repeatRefresh`. |
| `distribute` | `({base, amount, from, grid, axis, ease})` | Stagger engine, but for property *values* across targets. |
| `pipe` | `(fn1, fn2, …)→fn` left→right | `pipe(clamp(0,100), snap(5))`. Order matters. |
| `unitize` | `(fn, [unit])` | Lets numeric utils operate on `"40px"`. |
| `toArray` | `(".sel"|nodeList|el)` → real Array | Snapshots (static thereafter). |
| `selector` | `(elOrRef)` → scoped `q` fn | One per component root; scope is permanent. |
| `mapRange`/`normalize`/`getUnit`/`splitColor`/`shuffle`/`checkPrefix` | — | `shuffle` mutates in place; `getUnit("30px")→"px"` (`""` if unitless). |

---

## 7. `quickTo` / `quickSetter` — high-frequency writes

```js
const xTo = gsap.quickTo("#cursor", "x", { duration: 0.4, ease: "power3" });
const yTo = gsap.quickTo("#cursor", "y", { duration: 0.4, ease: "power3" });
addEventListener("pointermove", e => { xTo(e.clientX); yTo(e.clientY); });
```
- `quickTo(target, prop, vars)` returns a reusable `fn(value)` that **retargets one cached tween** per call — the canonical smoothed mouse-follower. Tween at `.tween`.
- `quickSetter(target, prop, [unit])` returns `fn(value)` that writes **instantly, no easing** — for per-frame writes you smooth yourself in a ticker loop. `quickSetter(el, "css")` takes an object.
- Both skip unit conversion, relative/function values, plugin parsing → **direct numeric props only** (`x`, not `left`; no `attr`). **Never** `gsap.to()` inside a mousemove/RAF loop.

---

## 8. `matchMedia` / `context` — responsive + cleanup

```js
const mm = gsap.matchMedia();
mm.add({
  isDesktop: "(min-width: 800px)",
  reduced:   "(prefers-reduced-motion: reduce)",
}, (ctx) => {
  const { isDesktop, reduced } = ctx.conditions; // booleans
  if (reduced) { gsap.set(".reveal", { opacity: 1, y: 0 }); return; } // honor a11y, set end-state
  gsap.to(".hero", { y: isDesktop ? -200 : -80 });
}, scopeEl);
mm.revert(); // tear everything down
```
- Animations created inside are **auto-reverted** when conditions stop matching — exactly what reduced-motion needs (OS setting can flip live).
- `gsap.context(fn, scope)` scopes all selector text to a root element and tracks every object for `ctx.revert()` (unmount cleanup). `matchMedia` **is** a context internally — never nest them.
- Don't call `ctx.revert()` inside the returned cleanup — it's automatic. The return is for *your* extra teardown (removing listeners).
- React: prefer `useGSAP()` (§27), which wraps this.

---

## 9. Global config, effects, ticker

```js
gsap.registerPlugin(ScrollTrigger, CustomEase);
gsap.defaults({ ease: "power2.out", duration: 1 });
gsap.config({ nullTargetWarn: false, force3D: "auto", autoSleep: 60, units: { rotation: "rad" } });
```

**`registerEffect`** — a reusable named animation (your motion vocabulary):
```js
gsap.registerEffect({
  name: "revealUp",
  extendTimeline: true,                  // also usable as tl.revealUp(...)
  defaults: { y: 40, duration: 0.6 },
  effect: (targets, cfg) => gsap.from(targets, { opacity: 0, y: cfg.y, duration: cfg.duration }),
});
gsap.effects.revealUp(".card");
tl.revealUp(".card", {}, "<");
```
Define `revealUp` / `parallax` / `pinScrub` once in a `gsap-init` module, use everywhere.

**Ticker** — GSAP's single RAF loop. Hook your render into it, never run a parallel `requestAnimationFrame`:
```js
gsap.ticker.add((time, deltaTime, frame) => renderer.render(scene, camera));
gsap.ticker.lagSmoothing(500, 33); // default: freeze big gaps so anims don't teleport after a stall
gsap.ticker.lagSmoothing(0);       // disable for scrubbed/game loops that want real delta
```

**Helpers:** `gsap.getProperty(el, "x")` · `gsap.isTweening(t)` · `gsap.killTweensOf(t[, props])` · `gsap.delayedCall(d, fn)` (cancelable, unlike setTimeout) · `gsap.parseEase("power2.out")` · `gsap.exportRoot()` (snapshot all running tweens to pause the whole page).

---

## 10. Property behaviors

**Transforms (independent, GPU-cheap — always prefer over `top`/`left`):**
- `x`/`y` (px, any unit) · `xPercent`/`yPercent` (% of element's own size — combine `x` + `xPercent:-50` to center).
- `rotation` (deg; `"1.25rad"`), `rotationX/Y/Z` · `scale`/`scaleX`/`scaleY` · `skewX`/`skewY`.
- `transformOrigin: "50% 100%"` · `transformPerspective` (element) / `perspective` (parent) · `svgOrigin` (SVG user-space).

**Other:**
- **CSS vars:** `gsap.to(el, { "--prog": 100 })` — animate custom properties; downstream CSS reacts.
- **`attr:{}`** — animate HTML/SVG attributes (not style): `attr: { x: 100, width: 200, fill: "#f00" }`. SVG `cx/cy/r`, `points`, `viewBox`.
- **`autoAlpha`** — `opacity` + auto `visibility:hidden` at 0 (drops from hit-testing/a11y tree). Standard fade-and-disable.
- **`snap` in a tween** — `{ x: 200, snap: { x: 10 } }` quantizes the animated value.
- **Function-based values** — `{ x: (i, t, all) => i * 100, rotation: () => gsap.utils.random(-30, 30) }`, per target; with `repeatRefresh` for fresh randomness each loop.
- **Relative** — `x: "+=100"`, `rotation: "-=45"`, `"*=2"`. **Color** — hex/rgb/hsl/named, `backgroundColor`/`fill`/`stroke`, gradient stops.

**Gotchas:** `x` (transform) ≠ `left` (layout reflow). Never mix a raw CSS `transform` transition on the same element GSAP animates — let GSAP own the matrix. `force3D:false` per-tween fixes blurry text during transforms. `will-change` is not auto-managed — add in CSS only for persistently-animated nodes, remove when idle.

---

## 11. Text transformations

### SplitText (3.13 rewrite — re-audit old code)
```js
const split = SplitText.create(".headline", {
  type: "words,lines",   // chars,words,lines
  mask: "lines",         // clip-wrap each line for overflow reveals
  autoSplit: true,       // re-split on font load + width change
  aria: "auto",          // a11y: aria-label on container, aria-hidden on shards
  onSplit(self) {        // runs on EVERY (re)split — put the tween here, and RETURN it
    return gsap.from(self.lines, { yPercent: 110, stagger: 0.12, ease: "expo.out", duration: 1.1 });
  },
});
// split.chars / .words / .lines / .masks  ·  split.revert() restores innerHTML
```
- **The 3.13 lockstep:** with `autoSplit`, the animation MUST live inside `onSplit` and you MUST `return` it. `onSplit` fires on initial split + every re-split; returning lets SplitText revert the prior tween so you don't stack zombies. The old `new SplitText()` + external `gsap.from(split.chars)` is now an anti-pattern when responsive.
- **Traps:** split *after* `document.fonts.ready` or lines break wrong (`autoSplit` solves it). `aria:"auto"` hides shards from SR — for a link inside the headline use `aria:"none"` + your own SR copy. Add `font-kerning: none`; avoid `text-wrap: balance`. No SVG `<text>`. Put it on a semantic element (heading/`<p>`), not a bare `<div>`. Avoid char-splitting body copy (a11y).

### Scroll-scrubbed type
```js
gsap.to(split.words, {                       // per-word dim→bright as you read (the "Apple paragraph")
  opacity: 1, color: "#fff", stagger: 0.5,
  scrollTrigger: { trigger: el, start: "top 70%", end: "bottom 60%", scrub: true },
});
```
- **Variable-font weight scrub** — animate `font-variation-settings` `wght` on scroll/velocity. Premium, rare.
- **Kinetic marquee** — infinite `xPercent` loop, speed reacts to scroll velocity (skew + speed-up).

### Char-level
- **ScrambleText** — decode effect: `scrambleText: { text: "DECODED", chars: "01", revealDelay: 0.5, speed: 0.3 }`. `text:"{original}"` scrambles in place. Mono font or you get width jitter.
- **TextPlugin** — typewriter swap: `text: { value: "New copy", delimiter: " ", type: "diff" }`. Clobbers child markup.
- Per-char magnetic repel from cursor (`quickTo` each char). 3D char flip — `rotationX`, `transformPerspective: 800`, stagger.

---

## 12. ScrollTrigger — the workhorse

Drives or toggles any tween/timeline (or fires callbacks) off scroll position. Handles pin, scrub, snap, batch, responsive teardown.

### start / end
```js
scrollTrigger: {
  trigger: ".section",
  start: "top center",     // "[trigger-edge] [scroller-edge]" — trigger's top hits viewport center
  end:   "bottom top",     // also: "+=300", "top 80%", numbers (abs px), "max", or a function
  endTrigger: ".footer",   // measure end against a different element
}
```
- Tokens: `top/center/bottom` (or `left/right`), `%`, px, relative `"+=100%"`, raw number (abs px), `"max"`, or `(self)=>...` (re-evaluated on refresh).
- **`clamp()`** — `start: "clamp(top 80%)"` keeps the resolved value in `[0, maxScroll]`, killing the above-the-fold dead-zone where an element can never reach its trigger. The senior idiom for reveal/parallax near page edges.

### scrub / pin
- `scrub: true` — progress locks 1:1 to scroll. `scrub: 1` — smoothed, the number is seconds to catch up (the weighty lag feel).
- `pin: true` (or an element). `pinSpacing: true|false|"margin"` (`false` to overlap, needed inside flex/grid). `pinType: "fixed"|"transform"` (ScrollSmoother forces `transform`). `anticipatePin: 1` kills the fast-scroll flash. `pinReparent: true` escapes a transformed ancestor (expensive, last resort).
- **Cardinal pin rule:** never animate the pinned element itself — animate its children. Create triggers top-to-bottom so pin-spacing math resolves in order.

### toggleActions / snap / markers
- `toggleActions: "play none none reverse"` — four verbs (`play pause resume reset restart complete reverse none`) for `onEnter onLeave onEnterBack onLeaveBack`. Ignored when `scrub` set.
- `once: true` — kill after first completion (cheapest one-shot). `toggleClass: "active"`.
- `snap: { snapTo: "labelsDirectional", duration: {min:.2,max:.6}, ease: "power1.inOut", directional: true }`. Shorthand: `snap: 0.2` (increments), `snap: [0,.5,1]`, `snap: "labels"`. **Trap:** snap fights `scrub: true` — pair with `scrub: <number>`.
- `markers: true` for dev — strip in prod.

### Callbacks + `self`
```js
onUpdate: self => skewSetter(clamp(self.getVelocity() / -300)), // canonical velocity-driven skew
```
`self`: `progress` · `direction` (1/-1) · `isActive` · `getVelocity()` · `.start`/`.end` (px) · `.animation` · `.scroll()`. Also `onEnter/onLeave/onEnterBack/onLeaveBack/onToggle/onRefresh/onScrubComplete`.

### Horizontal pin scroll
```js
const track = document.querySelector(".track");
const horiz = gsap.to(track, {
  x: () => -(track.scrollWidth - innerWidth), ease: "none",
  scrollTrigger: { trigger: ".track-wrap", pin: true, scrub: 1,
    end: () => "+=" + (track.scrollWidth - innerWidth), invalidateOnRefresh: true },
});
// trigger sub-animations off the horizontal motion:
ScrollTrigger.create({ trigger: ".panel-2", containerAnimation: horiz, start: "left center", onEnter: ... });
```
- **`containerAnimation` constraints:** the container tween must be `ease:"none"`; you **cannot pin or snap** inside a containerAnimation trigger; use `left/right/center` for start/end.

### batch / refresh / responsive
- `ScrollTrigger.batch(".card", { onEnter: els => gsap.to(els, {opacity:1, stagger:.1}), start: "top 85%" })` — coalesce many similar triggers into one staggered callback. Callback-driven (no scrub/toggleActions).
- `ScrollTrigger.refresh()` — recompute all start/end after DOM/layout shifts. `invalidateOnRefresh: true` — recompute function-based values on resize (**essential** for responsive scrubbed timelines). `refreshPriority: <n>` — refresh document-height-affecting pins earlier.
- **Responsive:** `ScrollTrigger.matchMedia()` is **deprecated** — use `gsap.matchMedia()` and return a cleanup that kills the trigger.
- `ScrollTrigger.clearScrollMemory()` + `getAll().forEach(t=>t.kill())` on SPA route change, or pins leak and the page jumps to a stale scroll position.
- `normalizeScroll(true)` — moves scroll onto the JS thread to fix iOS address-bar jumps / pin flicker. Experimental; turn on only if you see the jitter. `ignoreMobileResize: true` stops refresh on URL-bar show/hide.

---

## 13. ScrollSmoother

Smooth/inertial page scroll on top of ScrollTrigger, plus declarative parallax. Requires ScrollTrigger.

```html
<div id="smooth-wrapper"><div id="smooth-content"><!-- all content --></div></div>
<!-- position:fixed UI (nav, cursor) lives OUTSIDE the wrapper -->
```
```js
const smoother = ScrollSmoother.create({
  smooth: 1.2,          // seconds to catch up
  smoothTouch: 0.1,     // false by default; keep small on touch
  effects: true,        // scan data-speed / data-lag
  normalizeScroll: true,
});
```
- **Effects (markup):** `data-speed="0.5"` (parallax, `<1` slower, `>1` faster, `"auto"`, `"clamp(0.5)"`), `data-lag="0.5"` (smear/trail). Layer both for depth.
- **Imperative:** `smoother.effects(".layers", { speed: (i, el) => 1 + i*0.1, lag: 0.3 })`.
- Methods: `.paused(true)` (freeze for modal) · `.scrollTo(target, smooth, "center center")` · `.scrollTop(px)` · `.getVelocity()`.
- **Trap:** content is `transform`-translated → it's a containing block, so `position: fixed`/`sticky` *inside* content breaks. Put fixed UI outside the wrapper; use `data-speed` or ST pinning instead. ScrollSmoother auto-proxies the scroller, so your ScrollTriggers just work.

---

## 14. Observer — unified input

One normalized listener over wheel + touch + pointer + scroll. Backbone of scroll-jacked decks (no native scroll).

```js
let animating = false, i = 0;
Observer.create({
  type: "wheel,touch,pointer",
  preventDefault: true,
  tolerance: 10,                  // min px before firing — debounce micro-moves
  onDown: () => !animating && goto(i - 1),
  onUp:   () => !animating && goto(i + 1),
  onLeft, onRight, onChange, onHover, onDrag, onStop,
  lockAxis: true,                 // commit to first-moved axis
});
```
`self`: `deltaX/Y` · `velocityX/Y` · `x/y` · `isDragging` · `axis`. Static `Observer.isTouch`.
- **Trap 1:** without `tolerance` + an `animating` guard, one trackpad flick fires repeatedly → skipped slides. Gate on a flag set true on start, false in `onComplete`.
- **Trap 2:** `preventDefault: true` blocks all native scroll on the target — nested scrollables need `ignore: ".scrollable"`.
- Already using ScrollTrigger? Use `ScrollTrigger.observe({...})` instead of a separate import.

---

## 15. ScrollToPlugin

```js
gsap.to(window, { scrollTo: { y: "#section-3", offsetY: 80 }, duration: 1.2, ease: "power2.inOut" });
gsap.to(window, { scrollTo: "max" });
gsap.to(myDiv,  { scrollTo: { y: 400 } });   // div needs overflow:scroll
```
- `offsetY` subtracts sticky-header height so anchors land below the nav. `autoKill: true` cancels if the user scrolls manually (`onAutoKill` to react).
- **Trap:** conflicts with CSS `scroll-behavior: smooth` — remove the CSS, let GSAP own scroll.

---

## 16. Flip — layout/state transitions

Record layout state → mutate DOM/CSS freely → animate the visual delta. Decouples *what the layout is* from *how it transitions*.

```js
const state = Flip.getState(".box", { props: "backgroundColor,borderRadius" });
container.classList.toggle("expanded");      // reparent, reorder, display swap — anything
Flip.from(state, {
  duration: 0.7, ease: "power3.inOut",
  absolute: true,   // position:absolute during flip — fixes flex/grid reflow jank
  scale: true,      // animate scaleX/Y (GPU) instead of width/height
  nested: true,     // stop offset compounding when parent+child both flip
  onEnter: els => gsap.fromTo(els, {opacity:0}, {opacity:1}),  // appearing elements
  onLeave: els => gsap.to(els, {opacity:0}),                   // disappearing (needs absolute)
});
```
- **Killer use:** shared-element transition — grid thumb → detail view; reparenting sidebar→modal with zero coordinate math. Give the from/to elements the same `data-flip-id` + `fade:true` and Flip swaps them.
- `scale:true` is smooth but stretches inner content/borders — use for solid blocks; use `width/height` when content must not distort. `border-box` mandatory either way.
- **`Flip.batch()`** when several components flip — guarantees all `getState()` runs before any DOM mutation (else B reads a layout A already disturbed).
- **Traps:** 2D only (no `rotationX/Y/z`). React: `getState` before `setState`, run `Flip.from` in `useLayoutEffect`/`flushSync`; re-rendered components are new DOM nodes so pass an explicit `targets` selector. `absolute` coords break on mid-animation resize.

---

## 17. Draggable (+ InertiaPlugin)

```js
Draggable.create(".item", {
  type: "x,y",            // "x"|"y"|"top,left"|"rotation"|"scroll"
  bounds: container,      // element or {minX,maxX,minY,maxY}
  inertia: true,          // REQUIRES InertiaPlugin — flick momentum
  edgeResistance: 0.65,
  snap: { x: v => Math.round(v/80)*80 },  // post-release; liveSnap:true for during-drag
  lockAxis: true, autoScroll: 1, trigger: ".handle",
  onDrag(){}, onDragEnd(){}, onThrowComplete(){},
});
```
- Statics: `Draggable.hitTest(a, b, "50%")` (overlap test for drop zones), `Draggable.get(el)`. Read `.endX/.endY` = predicted inertial landing — snap to *that* cell, not the release point, for native feel.
- **#1 trap:** `inertia:true` silently no-ops without `InertiaPlugin` registered. `type:"top,left"` needs `position:relative|absolute`. Clickable children don't drag unless `dragClickables:true`.

**InertiaPlugin** standalone — velocity glide-to-stop on any property:
```js
InertiaPlugin.track(obj, "x,y");                       // continuous velocity tracking
gsap.to(obj, { inertia: { x: "auto", y: { velocity: "auto", end: [0,100,200] } } }); // throw to nearest snap
```
`velocity:"auto"` needs an active `track()` first. Duration is computed — cap with `duration:{max}`.

---

## 18. MotionPathPlugin

Animate an element along an SVG path, raw path string, or array of points.
```js
gsap.to(".rocket", {
  duration: 5,
  motionPath: {
    path: "#track",            // selector | "M9,100c..." | [{x,y},...]
    align: "#track",
    alignOrigin: [0.5, 0.5],   // which point of the element rides the path
    autoRotate: true,          // or a degree offset
    start: 0, end: 1, curviness: 1.5,
  },
});
```
- **Statics (the real power):** `convertToPath(svg)` (primitives→path), `getPositionOnPath(rawPath, p, includeAngle)` — scatter N elements along a path *without* animating, `cacheRawPathMeasurements()`, `convertCoordinates(fromEl, toEl, pt)` (bridge nested transform spaces). **MotionPathHelper** = in-browser path editor (free).
- **Trap:** `align` is computed once at start — **not responsive**. Re-create/re-measure on resize.

---

## 19. MorphSVGPlugin

Morph any path's `d` to any other, auto-equalizing point counts.
```js
gsap.to("#start", { duration: 1, morphSVG: {
  shape: "#end",
  type: "rotational",   // organic shapes — no mid-tween kink (vs default "linear")
  shapeIndex: "auto",   // point-mapping offset; hardcode an int once tuned
  origin: "50% 50%",
}});
```
- **Killer use:** logo/icon morph (hamburger↔close, play↔pause), liquid blobs. Morph a `<circle>`/`<rect>` — `MorphSVGPlugin.convertToPath()` first (or pass it directly).
- `MorphSVGPlugin.findShapeIndex()` = GUI to kill unwanted twisting; then hardcode `shapeIndex: 3` (`"auto"` recomputes each run and can pick wrong). `precompile:"log"` → paste result for hot-path morphs.
- **Trap:** `shapeIndex` only applies to closed paths. Bad `shapeIndex`/`map` causes twisting, not errors.

---

## 20. DrawSVGPlugin

Animate the visible portion of an SVG **stroke** (`stroke-dasharray`/`-dashoffset`).
```js
gsap.from("#path", { drawSVG: 0 });            // canonical draw-on
gsap.to("#path", { drawSVG: "20% 80%" });      // only middle 60% visible
gsap.to("#path", { drawSVG: "50% 50%" });      // collapse to a point
```
- Value = **end state** (`"start end"`), not a range. Works on `path/line/polyline/polygon/rect/ellipse`.
- **Killer use:** signature/handwriting draw-on, animated line illustrations, connecting-line reveals, progress strokes.
- **Traps:** stroke needs `stroke` + `stroke-width`. Firefox mis-measures — use `102%` not `100%`. iOS Safari mis-renders `<rect>` strokes — convert to `<path>`. Use `vector-effect="non-scaling-stroke"` if CSS-scaled.

---

## 21. Physics2D / PhysicsProps

```js
gsap.to(el, { duration: 2, physics2D: { velocity: 300, angle: -60, gravity: 500, friction: 0 } }); // launch arc
gsap.to(obj, { duration: 2, physicsProps: { rotation: { velocity: 100, acceleration: 200 } } });    // any prop
```
- **Physics2D** = fire at an angle under gravity (confetti, particle bursts, projectiles). **PhysicsProps** = initial velocity + friction on arbitrary props (decaying spin, friction fade).
- **Trap:** not a physics engine — no collision, no constraints, params not updatable mid-tween (one-shot trajectory). Both override easing entirely and reverse cleanly. Friction is CPU-pricey — start at `0.02`.

---

## 22. Canvas / WebGL bridges

GSAP animates plain JS objects → you push the value to the GPU each frame.

**Three.js — scrub a shader uniform:**
```js
const u = { uProgress: { value: 0 } };
gsap.to(u.uProgress, { value: 1, ease: "none",
  scrollTrigger: { trigger: ".section", end: "+=1500", scrub: true } });
gsap.ticker.add(() => renderer.render(scene, camera)); // one RAF loop
```
**R3F owns its own loop** — don't add a GSAP ticker render. Animate a ref'd value, apply in `useFrame`. Keep a monotonically increasing scroll counter so looping uniforms never snap 1→0.

**Canvas image-sequence scrub (Apple AirPods):**
```js
const seq = { frame: 0 }; // preload images[] first
gsap.to(seq, { frame: total - 1, snap: "frame", ease: "none",
  scrollTrigger: { trigger: ".pin", end: "+=3000", scrub: 0.5, pin: true },
  onUpdate: () => ctx.drawImage(images[Math.round(seq.frame)], 0, 0, w, h) });
```
Preload frames (WebP/AVIF), cap to device pixels, `ScrollTrigger.refresh()` after sizing.

**PixiPlugin** — tween Pixi DisplayObjects with GSAP ergonomics (degrees not radians, CSS colors, auto filter plumbing):
```js
PixiPlugin.registerPIXI(PIXI);   // REQUIRED or silent failure
gsap.to(sprite, { pixi: { scale: 1.5, tint: 0xff0000, blur: 8, rotation: "60_short" } });
```
**EaselPlugin** does the same for CreateJS. **Animate raw canvas-2D** by tweening a state object and redrawing in `onUpdate`.

---

## 23. Framework integration

### React / Next — `@gsap/react` + `useGSAP`
```js
import { useGSAP } from "@gsap/react";
const container = useRef(null);
const { contextSafe } = useGSAP(() => {
  gsap.to(".box", { rotation: 360 });   // selector scoped to container
}, { scope: container, dependencies: [dep], revertOnUpdate: true });

const onClick = contextSafe(() => gsap.to(".box", { x: "+=100" })); // handlers run AFTER the hook
```
- Drop-in for `useLayoutEffect`/`useEffect` — SSR-safe, and **every tween/timeline/ScrollTrigger created in the callback is auto-reverted on unmount** (it wraps `gsap.context`). No manual cleanup return.
- `scope` constrains selector text → no per-element ref proliferation. **`contextSafe`** wraps animations created in click handlers / `setTimeout` so they're scoped + cleaned up (but you still remove your own DOM listeners).
- **Trap:** default deps are `[]` → runs **once**, not every render.
- **Next App Router:** `'use client'` on every file touching gsap/refs/ScrollTrigger. Register plugins once behind the client boundary (registering on the server throws). Kill globally-created ScrollTriggers on unmount or pinned spacers leak.

### Vue / Svelte / Angular / Webflow
- **Vue/Nuxt:** register + build in `onMounted`, `ctx.revert()` in `onUnmounted`; guard SSR (`import.meta.client` / `<ClientOnly>`).
- **Svelte:** `onMount` build, return teardown (Svelte 5: `$effect` cleanup); SvelteKit guard with `browser` from `$app/environment`.
- **Angular:** `matchMedia`/`context` accept an `ElementRef` as scope; build in `ngOnInit`, revert in `ngOnDestroy`, wrap in `ngZone.runOutsideAngular` to avoid change-detection thrash.
- **Webflow:** GSAP is a native toggleable library (core + all plugins hosted). Still `registerPlugin(...)` in your custom-code embed.

---

## 24. Architecture for large animated sites

- **One `gsap-init` module** (client boundary): `registerPlugin(...)`, global `ScrollTrigger.config(...)`, `ticker`/`lagSmoothing`, all `registerEffect` definitions.
- **Master timeline + nested children** — each section in a factory returning its own timeline; `master.add(intro).add(hero, "+=0.2").add(aside, "<")`. Children keep local `timeScale`/`pause`.
- **Labels over magic numbers** — `tl.addLabel("reveal").to(".a", {x:100}, "reveal").to(".b", {y:50}, "reveal+=0.3")`; `tl.play("reveal")`.
- **Centralize `matchMedia`** (breakpoints + reduced-motion) so the reduced-motion branch is site-wide consistent.
- All teardown flows through `useGSAP`/`context` revert or `ScrollTrigger.getAll().kill()` on route change.

---

## 25. Performance rails

- **`transform`/`opacity` only.** Never animate `top/left/width/height/margin/box-shadow` in scrub — they thrash layout/paint. `x`/`y` map to `translate`. Use `xPercent`/`yPercent` for responsive offsets (no JS recompute).
- **`quickTo`/`quickSetter`** for anything called many times/sec on one prop. Never `gsap.to()` in a mousemove/RAF loop.
- **`force3D:"auto"`** (default) promotes a GPU layer during the tween and drops it after. Don't blanket `will-change` — each layer costs VRAM and can blur text.
- **One RAF loop** — hook Three/canvas into `gsap.ticker`; `lagSmoothing(0)` for scrubbed/scroll-synced, on for autonomous timelines.
- **ScrollTrigger:** `config({ limitCallbacks: true })`, `fastScrollEnd: true` (finish, don't catch up, after a fast flick), `preventOverlaps: true`, `batch()` for grids, `ignoreMobileResize: true`.
- **`ScrollTrigger.refresh()`** after async layout shifts — positions are measured at creation:
  ```js
  document.fonts.ready.then(() => ScrollTrigger.refresh());
  addEventListener("load", () => ScrollTrigger.refresh()); // images
  ```
  (SplitText `autoSplit`+`onSplit` rebuilds triggers on font load automatically.)
- **Kill on route change** — pinned triggers leave pin-spacer DOM if not reverted/killed.

---

## 26. Accessibility (mandatory)

```js
const mm = gsap.matchMedia();
mm.add("(prefers-reduced-motion: reduce)", () => {
  gsap.set(".reveal", { opacity: 1, y: 0, clearProps: "transform" }); // SET END-STATE, don't animate away
});
mm.add("(prefers-reduced-motion: no-preference)", () => {
  gsap.from(".reveal", { opacity: 0, y: 40, stagger: 0.1, scrollTrigger: { trigger: ".section", scrub: true } });
});
```
- **Build a separate reduced-motion branch** — don't just shorten durations. matchMedia auto-reverts the motion branch when the setting flips live.
- **Never animate content out and rely on motion to bring it back.** If a reveal starts at `opacity:0`, a reduced-motion user who skips the tween sees nothing — `gsap.set` to the final visible state instead.
- **Gate behind reduced-motion:** scrub, pin, parallax, autoplay loops/marquees, smooth-scroll, large translate/scale reveals. Keep: instant state changes, small opacity fades.
- **Infinite loops** get a pause affordance and pause on `visibilitychange` (hidden tab) and reduced-motion.
- **Focus:** on route/page transitions move focus to the new view's heading after `onComplete` (`el.tabIndex=-1; el.focus()`); don't leave `pointer-events:none` longer than the animation.
- **SplitText:** rely on 3.13 `aria:"auto"`, put it on a semantic element, create tweens inside `onSplit`. Avoid splitting body copy into letters.

---

## 27. Easing palette (commit these)
- Reveals: `expo.out`, `power4.out`
- Scrub: `none` (linear — scroll IS the timing)
- Morphs/Flip: `power3.inOut`
- Organic drop: `CustomBounce` + synced squash
- Banned as defaults: `bounce`, `elastic`, `back`.

---

## 28. Plugin decision matrix

| Need | Plugin |
|---|---|
| Per-line/char text reveals, responsive | **SplitText** (`autoSplit`+`onSplit`) |
| Scroll-driven anything | **ScrollTrigger** |
| Smooth page scroll + parallax | **ScrollSmoother** |
| Scroll-jacked deck / unified input | **Observer** |
| Animated anchor scroll | **ScrollToPlugin** |
| Layout/state transition, shared element | **Flip** |
| Drag / flick / knob / sortable | **Draggable** (+ **InertiaPlugin**) |
| Momentum/throw on any value | **InertiaPlugin** |
| Follow an SVG curve / scatter on path | **MotionPathPlugin** |
| Shape A → shape B | **MorphSVGPlugin** |
| Stroke draw-on/off | **DrawSVGPlugin** |
| Decode / glitch / typewriter text | **ScrambleText** / **TextPlugin** |
| Projectile / confetti / particle | **Physics2D** / **PhysicsProps** |
| Exact bezier / bounce+squash / shake | **CustomEase** / **CustomBounce** / **CustomWiggle** |
| WebGL / canvas tweening | **PixiPlugin** / **EaselPlugin** |
| Debug timeline timing (dev only) | **GSDevTools** |

All register identically and play inside `gsap.context()` / `useGSAP()` for auto-cleanup. Post-3.13 the only gate is registering the plugin — a silent no-op if you forget (`inertia` needs `InertiaPlugin`, `pixi` needs `registerPIXI`).
