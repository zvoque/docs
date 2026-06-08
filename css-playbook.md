# CSS Playbook — The Frontier & Craft Reference

The CSS that gets forgotten. Not a beginner reference — this is the under-used, high-leverage, hard-to-discover half of modern CSS: the features that replace JS, the craft techniques that separate designed from default, and the 2025–26 primitives most code (and most AI) never reaches for. Companion to `gsap-playbook.md` (native motion vs JS motion cross-reference throughout).

> **Why this exists.** Models and juniors regress to the mean of training data — flexbox for everything, `rounded-2xl shadow-lg`, gray bg, one blurry shadow. The powerful stuff is rare in the corpus, needs visual iteration to tune, and is craft not snippet — exactly the three things that make it get dropped. This doc is the corrective: reach for these *first*.

> **Verified June 2026** against MDN, caniuse, web.dev, WebKit/Chrome blogs, CSSWG drafts.

## Support legend

Every feature is tagged. **Read the tag before shipping.**

- ✅ **Baseline widely available** — safe everywhere, ship unguarded.
- 🟢 **Baseline newly available** (landed all engines ≤~2.5yr ago) — ship, expect a small straggler tail.
- 🟡 **Limited** — a major engine is missing. Gate with `@supports` or keep a fallback.
- 🔴 **Single-engine / experimental** — Chromium-only or flagged. Progressive enhancement only, never load-bearing.
- ☠️ **Dead** — abandoned, don't reach for it.

## The 2026 reality nobody updated their mental model for

- **Same-document View Transitions are cross-browser Baseline** (Firefox 144, Oct 2025). Ship unguarded. Not Chrome-only anymore.
- **Scroll-driven animations ship in Safari 26 + Chrome.** Firefox is the *only* gap and it degrades clean. Production-viable as progressive enhancement *today*.
- **`color-contrast()` (list form) never shipped** — cut. The replacement `contrast-color()` (black/white only) is Baseline as of Apr 2026.
- **Native masonry is Safari-26-only** — not the `grid-template-rows: masonry` everyone assumed shipped.
- **`if()`, `sibling-index()`, customizable `<select>`, scroll-state queries, CSS carousels** are Chromium-only experimental. Real, but not portable.
- **`accent-color`, `:has()`, `@layer` ARE Baseline** — stale model priors call them experimental. They're not.

---

# Layout & Architecture

## 1. Container queries

Style on an **ancestor's** size or computed style, not the viewport. The decoupling that makes components portable.

```css
.wrap { container-type: inline-size; container-name: card; }  /* shorthand: container: card / inline-size */
@container card (width > 30rem) { .card { grid-template-columns: 12rem 1fr; } }
@container card (20rem <= width <= 40rem) { /* range syntax */ }
```
- `container-type`: `inline-size` (query inline axis, cheap — the common case) · `size` (both axes, **needs explicit block size or content collapses**) · `normal` (style queries only).
- **Length units** resolve to the *query container*: `cqi` (inline — use this), `cqb`, `cqw/cqh`, `cqmin/cqmax`. Component-relative fluid type: `font-size: clamp(1.25rem, 1rem + 2cqi, 2.5rem)`.

**Style queries** 🟡 — `@container style(--theme: dark) { ... }`. Only **custom properties** are queryable in shipping browsers (Firefox: none). Boolean form `style(--featured)` is true when the value differs from initial — a clean "flag set?" test. Killer use: **no container-type requirement, no layout cost** — pass `--variant` down and branch styling, replacing prop-to-class plumbing.

- **Traps:** an unnamed `@container` binds to the *nearest* container ancestor — a closer wrapper silently steals it; **always name + query by name**. An element **cannot query itself** (`container-type` is queryable only by descendants) — the #1 reproduced bug. `container-type` establishes a containing block → can break `position: fixed` descendants and collapse intrinsic height.
- Size queries ✅ (since 2023). Style queries 🟡.

## 2. Subgrid ✅

Nested grid adopts the parent's tracks → descendants align to the *parent's* lines. The only correct fix for "equalize title/body/CTA rows across sibling cards."
```css
.cards { display: grid; grid-template-columns: repeat(3, 1fr); gap: 1rem; }
.card  { display: grid; grid-row: span 3; grid-template-rows: subgrid; }
```
- Gaps + line names inherit from the parent across the spanned range; numbering restarts at 1 inside (position-independent). Append local names: `subgrid [a] [b]`.
- **Trap:** subgrid blocks implicit tracks in that axis — more items than spanned cells overflow into the last track. Dynamic counts: subgrid one axis, `grid-auto-rows` the other.

## 3. Grid art direction — the under-used 80% of Grid

**Cell overlap — stack on one cell, no `position: absolute`** (the single most-forgotten Grid idiom):
```css
.hero { display: grid; }
.hero > * { grid-area: 1 / 1; }   /* every child same cell → stacks via z-index, stays in flow, auto-sizes to tallest */
```
**Named areas** — re-declare in a media/container query to reflow with zero markup change:
```css
.page { display: grid; grid-template-columns: 16rem 1fr;
        grid-template-areas: "nav hero" "nav main" "nav footer"; }  /* "." = empty cell */
```
**Intrinsic tracks** (the vocabulary AI defaults away from): `minmax(min-content, 1fr)`, `fit-content(20rem)`. **auto-fill vs auto-fit:** auto-fill keeps empty phantom tracks; auto-fit collapses them so items stretch. The correct responsive line — with the overflow guard the naive version ships without:
```css
grid-template-columns: repeat(auto-fit, minmax(min(100%, 18rem), 1fr));
```
**Dense packing** `grid-auto-flow: dense` backfills holes — but reorders *visually* not in DOM → pair with `reading-flow` (§13) or avoid for focusable content.

**Masonry** 🔴 — resolved direction is CSS Grid Lanes (`grid-template-rows: masonry`); **Safari 26 shipped first (2026)**, Chrome/FF behind flags. Gate `@supports (grid-template-rows: masonry)`; not Baseline — don't claim otherwise.

## 4. Cascade layers `@layer` ✅

Explicit cascade order decoupled from specificity. Kills specificity wars structurally.
```css
@layer reset, base, theme, components, utilities;  /* order = priority, LAST wins. Declare ONCE up top */
@layer components { .btn { padding: 1rem; } }
@layer utilities  { .p-0 { padding: 0; } }         /* one class beats .btn — no !important, no hacks */
@import "lib.css" layer(vendor);                    /* wrap third-party so your code always wins */
```
- **Unlayered styles beat all layered styles** (mental model: unlayered = implicit highest layer).
- **`!important` inverts everything** (the trap): with `!important`, first-declared layer wins and unlayered `!important` becomes *weakest*. Counterintuitive — verify before relying.
- `revert-layer` drops a property to the layer beneath. Nest with `@layer a.b`.

## 5. `@scope` 🟢

Scoped styles with a lower boundary ("donut") and proximity resolution — CSS modules without a build step.
```css
@scope (.card) to (.card__slot) {   /* applies inside .card, STOPS at .card__slot subtrees */
  img { border-radius: 8px; }
  :scope { padding: 1rem; }          /* :scope = the scope root */
}
```
- Donut scope `(root) to (limit)` is unique — style a region but exclude slotted/third-party content.
- Bare selectors act like `:where(:scope)` → **zero added specificity** (great for themeable defaults).
- **Proximity (the differentiator):** when two scopes match, the one whose root is *fewer DOM hops away* wins, independent of source order — nested themes resolve to their nearest root automatically. Impossible with plain selectors. (But proximity is a *low*-priority tiebreaker — below importance/layers/specificity.)
- All engines since late 2025; gate old browsers with `@supports at-rule(@scope)`.

## 6. `:has()` — relational selector ✅

Parent, previous-sibling, quantity queries, state-driven layout. Biggest selector addition in a decade.
```css
.card:has(> img)            { grid-template-columns: 1fr 2fr; }   /* parent */
label:has(+ input:required)::after { content: " *"; }            /* prev sibling */
fieldset:has(:invalid)      { border-color: crimson; }           /* form state */
.gallery:has(> :nth-child(6)) { ... }                            /* quantity: 6+ items */
body:has(dialog[open])      { overflow: hidden; }                /* scroll-lock, no JS */
```
- Specificity = its most specific argument; itself forgiving (a bad selector inside doesn't kill the rule).
- **Perf trap:** broad anchors (`body:has(.x)`, `*:has(.y)`) re-evaluate on every matching mutation. Tighten with combinators: `.panel:has(> .open)`. (The "`:has` is slow" warning is largely outdated for 2026 — the real cost is unbounded subjects + high-frequency state.)

## 7. `:is()` / `:where()` — specificity control ✅

```css
:where(.prose) a { color: var(--link); }   /* specificity 0-0-0 — anything overrides it */
:is(h1, h2, h3) + p { margin-top: 0; }      /* takes the HIGHEST specificity of its args */
```
- **`:where()` contributes ZERO specificity** — the correct, under-used tool for design-system *defaults* and resets meant to be overridden. Prefix typography/reset rules with it so authors never fight specificity.
- Both forgiving — one unknown selector doesn't invalidate the list (ideal for cross-engine lists).

## 8. Anchor positioning 🟡

Tether one element to another's edge/size declaratively — tooltips, menus, popovers that follow their trigger with automatic overflow fallback, **no JS positioning library**.
```css
.trigger { anchor-name: --trig; }
.tooltip {
  position: fixed; position-anchor: --trig;
  top: anchor(bottom); justify-self: anchor-center;
  min-width: anchor-size(width);
  position-try-fallbacks: flip-block, flip-inline;   /* auto-reposition on overflow — replaces Floating UI */
}
@position-try --shift-up { inset: auto auto anchor(top) anchor(start); }
```
- `position-area: bottom center` is the simple 3×3-grid shorthand for common placements. `position-visibility: anchors-visible` hides the tether when the anchor scrolls off — no observer.
- **`anchor-scope`** confines an `anchor-name` to a subtree — essential in lists/repeated components, else the positioned element binds to the *first* match (real trap).
- ~81% global; all three engines but Safari 26 / Firefox 147 are recent → **progressive-enhance with a static fallback**, gate `@supports (anchor-name: --x)`.

## 9. Logical properties ✅

Flow-relative box model — adapts to writing-mode/direction for free.
```css
margin-inline: auto;          /* the idiomatic horizontal center (not margin: 0 auto) */
padding-block: 1rem; inset-inline-start: 0; border-inline-end: 1px solid;
inline-size: 40ch; block-size: auto;   /* width/height → logical */
```
Free correctness upgrade even in LTR-only: components become drop-in RTL, vertical writing modes Just Work. AI defaults to physical props out of habit.

## 10. Intrinsic sizing & `aspect-ratio` ✅

```css
width: min-content;        /* shrink to longest unbreakable content */
width: max-content;        /* expand to full unwrapped content */
width: fit-content(30ch);  /* max-content but capped — the under-used one (tags, captions, auto-width) */
inline-size: stretch;      /* fill containing block MINUS margins (fixes width:100%+margin overflow) */
.media { aspect-ratio: 16 / 9; }   /* reserve space, kill CLS; pair object-fit: cover */
```
`aspect-ratio` only fills the gap — overridden if both width and height are set. `stretch` is newer; `-webkit-fill-available` is the broad fallback.

## 11. `field-sizing: content` 🟡 — auto-growing inputs

Form controls shrinkwrap/grow to content. Auto-resizing `<textarea>` with **zero JS** (the `scrollHeight` hack, gone).
```css
textarea, input, select { field-sizing: content; min-inline-size: 8rem; max-inline-size: 40ch; max-block-size: 12rem; }
```
**Always pair with `min-*`/`max-*`** or an empty input collapses to cursor width. `rows`/`cols`/`size` are ignored under `content`. Degrades clean to fixed sizing → safe to layer on.

## 12. `reading-flow` / `reading-order` 🔴

Decouple **focus/AT order** from visual order — the a11y fix for `order`, `dense`, and reordered flex/grid (which otherwise leave tab order on DOM, not visuals).
```css
.toolbar { display: flex; reading-flow: flex-visual; }   /* tab order follows visual order */
.item { reading-order: 2; }
```
Chromium 137+ only. Enhancement only — never rely on it for baseline a11y; keep DOM order sane.

## 13. `sibling-index()` / `sibling-count()` 🔴

Per-element math from DOM position — staggers, ramps, radial menus — **without inline `--i` or JS**.
```css
li { transition-delay: calc(sibling-index() * 60ms);
     background: hsl(calc(sibling-index() / sibling-count() * 360deg) 70% 50%); }
```
Replaces the `style="--i:3"` pattern AI emits constantly. Chromium ~2026, FF in dev, Safari unshipped — experimental, needs a non-staggered fallback.

## 14. `if()` function 🔴

Inline conditional *values* — branch one property on a style/media/feature query.
```css
color: if(style(--scheme: dark): white; else: black);
background: if(supports(color: oklch(0% 0 0)): oklch(60% .2 250); else: #4477dd);
```
**Chrome 137+ only.** No space between `if` and `(`. `style()` reads custom props only. Returns invalid if nothing matches → **always put a plain fallback declaration above it.** Bleeding-edge.

## 15. `@supports` — the gate for everything above ✅

```css
@supports (anchor-name: --x) { ... }
@supports selector(:has(*)) { ... }            /* the only way to detect :has(), :state() */
@supports at-rule(@scope) { ... }
@supports font-tech(color-COLRv1) { ... }
@supports not (field-sizing: content) { textarea { /* JS-autogrow hook */ } }
```
Senior idiom: **write the baseline layout first, layer enhancements inside `@supports`** so the cascade degrades naturally.

---

# Color & Visual Effects

## 16. Perceptual color — oklch / oklab ✅

Equal numeric steps in **L** look equal to the eye (unlike HSL). *The* reason to switch: build a lightness ramp that's actually even.
```css
oklch(L C H / A)   /* L 0–1 or %, C 0–0.4 (100%=0.4), H 0–360 */
--blue-1: oklch(0.95 0.03 250);
--blue-5: oklch(0.65 0.16 250);   /* hold C & H, march L → tonal scale that reads even */
--blue-9: oklch(0.30 0.10 250);
```
- Hue numbers differ per space (red ≈ 41° oklch, ≈ 50° lch, 0° hsl) — don't port across spaces.
- `oklch` for design systems; `oklab` for mixing/interpolation (no hue-wrap surprises).
- **Trap:** chroma 100% = 0.4. High C at extreme L is out of gamut → silently clamped. Keep C modest near L extremes.

## 17. Wide gamut — display-p3 ✅

P3 = ~25% more colors; saturated reds/greens/cyans that can't exist in `#rrggbb`.
```css
.accent { background: #e6005c; }                          /* sRGB fallback FIRST */
@media (color-gamut: p3) { .accent { background: color(display-p3 0.96 0 0.4); } }
```
High-chroma `oklch()` also renders into P3 automatically where available — often the simpler route. Out-of-gamut components clamp, don't error.

## 18. Relative color syntax 🟢

Destructure any color into channels and rebuild it. One source token → entire tint/shade/alpha family, browser-computed. Kills the N-hardcoded-vars-per-color antipattern.
```css
--brand: oklch(0.62 0.18 264);
--brand-tint:  oklch(from var(--brand) calc(l + 0.12) c h);   /* move L, hold C & H */
--brand-shade: oklch(from var(--brand) calc(l - 0.12) c h);
--brand-15:    oklch(from var(--brand) l c h / 0.15);          /* alpha variant */
--complement:  oklch(from var(--brand) l c calc(h + 180));     /* rotate hue */
rgb(from var(--brand) r r r);                                  /* gray from any color (reuse a channel) */
```
- **Channels resolve to unitless numbers** — `calc(l + 20%)` is invalid; use `calc(l + 0.1)` (oklch) or `+ 20` (lch).
- **Alpha defaults to the *origin's* alpha**, not 100% (unlike absolute colors).
- ~87% (Chrome 131 / Safari 18 / FF 133). No graceful degradation — invalid syntax drops the declaration; gate with `@supports (color: rgb(from red r g b))` when the design breaks without it.

## 19. `color-mix()` ✅

Blend colors in a chosen space — the workhorse for state colors and tints.
```css
--c-tint:  color-mix(in oklab, var(--c) 75%, white);   /* even, no graying */
--c-shade: color-mix(in oklab, var(--c) 75%, black);
--c-20:    color-mix(in srgb, var(--c) 20%, transparent);   /* alpha (can only go DOWN) */
button:hover { background: color-mix(in oklab, var(--p) 88%, white); }
```
- **Default `in srgb` produces muddy/dark midpoints — prefer `in oklab`** for tints/shades, `in oklch` to keep vibrance through a hue change. Polar spaces take a hue method (`shorter`/`longer`/`increasing`/`decreasing hue`).
- color-mix = blend two colors; relative color (§18) = manipulate one color's channels.

## 20. `light-dark()` + `color-scheme` 🟢

Dark mode without a media query, per-property.
```css
:root { color-scheme: light dark; }   /* MANDATORY — without it, always resolves light */
body { color: light-dark(#1a1a1a, #eee); background: light-dark(#fafafa, #16181c); }
```
Set `color-scheme: dark` on any subtree to flip a region (and re-theme native scrollbars/controls there) — impossible cleanly with `prefers-color-scheme`. Forgetting `color-scheme` is the #1 gotcha.

## 21. `contrast-color()` 🟢

Returns black or white — whichever contrasts more with the input.
```css
color: contrast-color(var(--bg));
```
- The flexible `color-contrast()` (candidate list + target ratio) **never shipped** — cut. `contrast-color()` is minimal, Baseline Apr 2026.
- **Trap:** black/white only, ~AA. **Mid-tone backgrounds fail** (neither clears 4.5:1). Use over clearly-light or clearly-dark only; provide a fallback (it's new).

## 22. Gradients — the craft layer ✅

- **Interpolation color space** (the under-used lever): `linear-gradient(in oklch, red, green)` — kills the muddy sRGB midpoint of complementary stops.
- **Hue method:** `conic-gradient(in oklch longer hue, red, red)` — sends two stops the long way around → full rainbow from two colors.
- **Color hints:** `linear-gradient(red, 20%, blue)` — a bare position moves the 50% blend point (easing without a third stop).
- **Hard stops** (same position twice) = stripes/bands/pie, zero raster: `repeating-linear-gradient(45deg, #111 0 10px, #222 10px 20px)`.
- **Layered radials = fake gradient mesh / aurora:**
```css
background:
  radial-gradient(40% 60% at 20% 20%, oklch(.7 .2 20 / .6), transparent 70%),
  radial-gradient(50% 50% at 80% 30%, oklch(.7 .2 280 / .5), transparent 70%),
  #0b0b10;
```
- Animate gradients via `@property` (§30) — you can't transition a raw gradient, but you can transition a registered angle/percentage/color it references.
- **Trap:** a gradient is an *image* (only on `background-image`/`mask-image`/etc.) and invisible to AT — never encode meaning in one.

## 23. Blend modes ✅

`mix-blend-mode` blends with **what's behind**; `background-blend-mode` blends an element's **own background layers**. Different jobs.
- **Duotone:** grayscale image + `background-blend-mode: multiply` over a color + a `screen` layer for highlights.
- **Knockout text:** white text + `mix-blend-mode: multiply`/`difference` over a photo → punches through to reveal the backdrop.
- **Grain over color:** SVG-noise (§27) with `mix-blend-mode: overlay`/`soft-light` at low opacity.
- **`isolation: isolate`** is the discipline knob — wrap a blending group so members blend *with each other only*, not the whole page. Forgetting it is the "why is it blending with the body?" bug. Any non-`normal` blend creates a stacking context.

## 24. `backdrop-filter` 🟢 — frosted glass

```css
.glass { background: rgb(255 255 255 / .18);  /* MUST be translucent or nothing shows */
         backdrop-filter: blur(12px) saturate(1.4); -webkit-backdrop-filter: blur(12px) saturate(1.4); }
```
`saturate(1.3–1.6)` is the secret to glass that looks alive vs flat gray.
- **Scrim trap:** blur alone doesn't guarantee legible text — add a tint and often a darkening scrim; verify contrast against worst-case backdrop.
- **Backdrop-root trap:** an ancestor with `opacity<1`/`filter`/`mask`/`transform` makes the filter only see content *inside* it — the classic "glass stopped working when I faded the parent."

## 25. `mask` 🟢 — the most under-used effect tool

Any image/gradient/SVG as an alpha/luminance stencil.
```css
.scroller { mask: linear-gradient(to bottom, transparent, black 16px, black calc(100% - 16px), transparent); } /* scroll-edge fade, no overlay div */
.icon     { background: currentColor; mask: url(icon.svg) center / contain no-repeat; }                        /* recolor any icon */
```
`mask-composite: add|subtract|intersect|exclude` for cut-outs. **Still ship `-webkit-mask`** for the Safari/iOS tail. **Trap:** `mask-mode` default `match-source` — a black PNG used as an alpha mask *hides* everything; switch to `luminance` or use an alpha-shaped source.

## 26. SVG filters via `filter: url(#id)` ✅ — grain, goo, distortion

The frontier most AI skips. Reference an inline `<filter>`.

**Procedural grain (`feTurbulence`)** — no asset, infinitely scalable:
```html
<filter id="grain"><feTurbulence type="fractalNoise" baseFrequency="0.9" numOctaves="3" stitchTiles="stitch"/></filter>
```
```css
.grain::after { content:""; position:absolute; inset:0; filter:url(#grain); opacity:.06; mix-blend-mode:overlay; pointer-events:none; }
```
`fractalNoise` (grain/clouds) vs `turbulence` (marble). Low `baseFrequency` = big features. `stitchTiles="stitch"` = seamless.

**Gooey / metaballs (`feGaussianBlur` + `feColorMatrix` alpha threshold):**
```html
<filter id="goo">
  <feGaussianBlur in="SourceGraphic" stdDeviation="10" result="blur"/>
  <feColorMatrix in="blur" values="1 0 0 0 0  0 1 0 0 0  0 0 1 0 0  0 0 0 18 -7" result="goo"/>
  <feBlend in="SourceGraphic" in2="goo"/>
</filter>
```
The `18 -7` alpha row steepens + thresholds so blurry overlaps snap to a solid merged blob. Apply `filter:url(#goo)` to the *container* of moving blobs. `feDisplacementMap` (fed by `feTurbulence`) = liquid/heat-haze distortion; `feMorphology` dilate/erode = fatten/thin.
- **Trap:** filters default to linearRGB — set `color-interpolation-filters="sRGB"` when colors look off. `feTurbulence` on large animated surfaces is costly.

## 27. `box-shadow` craft + `drop-shadow` ✅

**Layered smooth shadow** — one blurry shadow looks fake; stack low-opacity layers for real penumbra falloff:
```css
box-shadow: 0 1px 1px rgb(0 0 0 / .04), 0 2px 2px rgb(0 0 0 / .04), 0 4px 4px rgb(0 0 0 / .04),
            0 8px 8px rgb(0 0 0 / .04), 0 16px 16px rgb(0 0 0 / .04);
```
**`box-shadow` vs `filter: drop-shadow()`:** box-shadow follows the border box (rectangle, respects radius, ignores content alpha). `drop-shadow()` follows the element's **actual rendered silhouette** — transparent PNG, `clip-path` shape, SVG. No `inset`, no spread.
```css
.cutout { filter: drop-shadow(0 4px 6px rgb(0 0 0 / .4)); }  /* hugs the shape, not the box */
```

## 28. `clip-path` + `shape()` ✅/🟢

```css
.reveal   { clip-path: polygon(0 0, 0 0, 0 100%, 0 100%); transition: clip-path .6s; }
.reveal.in{ clip-path: polygon(0 0, 100% 0, 100% 100%, 0 100%); }
```
- **Polygons interpolate only with matching vertex counts** — pad the simpler shape with duplicate points.
- **`shape()` 🟢** (Baseline Feb 2026) — CSS-native alternative to `path()`: uses CSS units, `%`, `calc()` (path() is fixed px / SVG syntax, doesn't scale). Commands `move/line/hline/vline/curve…with/smooth/arc/close` with `by` (relative)/`to` (absolute). Gate non-trivial uses `@supports (clip-path: shape(from 0 0, close))` with a `polygon()` fallback.

---

# Native Motion (no JS)

Replaces GSAP ScrollTrigger / IntersectionObserver reveals / FLIP libs **for the compositor-friendly subset** (transform, opacity, filter, registered custom props). GSAP still wins for pinning with reflow, scrubbed master timelines, velocity-aware interruptible springs, and JS-computed values.

## 29. `@property` — the keystone ✅

Register a custom prop with a *type* so the browser can **interpolate** it. An unregistered `--x` is a string → discrete, no animation. This is what unlocks animated gradients, sweeping conic angles, smooth color/number transitions.
```css
@property --angle { syntax: "<angle>"; inherits: false; initial-value: 0deg; }  /* initial-value REQUIRED unless syntax:"*" */
.card { background: conic-gradient(from var(--angle), #f0f, #0ff); animation: spin 6s linear infinite; }
@keyframes spin { to { --angle: 360deg; } }
```
- Types: `<angle> <color> <length> <percentage> <number> <integer> <time> <transform-function>` …; `|` unions, `+`/`#` lists.
- **Trap:** `initial-value` must be *computationally independent* — `10px`/`45deg`/`red` ok, `3em`/`100%`-relative invalid → rule silently dropped. JS `CSS.registerProperty()` wins over `@property` and throws on duplicate (try/catch).

## 30. Scroll-driven animations 🟡

Two timelines: **`scroll()`** (how far a scroller scrolled) and **`view()`** (how far the subject moved through the viewport).
```css
/* scroll progress bar */
.bar { animation: grow auto linear; animation-duration: 1ms;     /* FF needs ≥1ms; ignored otherwise */
       animation-timeline: scroll(root block); transform-origin: left; }
@keyframes grow { from { transform: scaleX(0); } to { transform: scaleX(1); } }

/* reveal-on-scroll */
.card { animation: reveal linear both; animation-timeline: view(); animation-range: entry 0% entry 100%; }
@keyframes reveal { from { opacity:0; translate:0 2rem; } to { opacity:1; translate:0 0; } }
```
- **Named + `timeline-scope`** (the under-used unlock) drives a *distant, non-descendant* element off another's scroll — the native "animate the sidebar from the main column's scroll," no JS refs:
```css
.scroller { scroll-timeline: --gallery inline; }
body      { timeline-scope: --gallery; }   /* hoist the name so any descendant can use it */
.thumb    { animation: shrink linear; animation-timeline: --gallery; }
```
- **`animation-range`** — `cover` (whole journey) · `contain` (fully inside → about to leave) · `entry`/`exit` · `entry-crossing`/`exit-crossing` (edge-cross moments) · with `%` offsets: `entry 25% cover 75%`.
- Safari 26 + Chrome ship it; **Firefox is the only gap** and the 1ms time-based fallback is imperceptible → production-viable PE today.
- **Traps:** inactive timeline (no scrollbar on that axis) = silent no-op. Animate transform/opacity/filter only — `height`/`top`/`margin` drop to main thread (jank). `both` fill holds start/end states. Reduced-motion: set final state, `animation: none`.

## 31. View Transitions ✅ (same-doc) / 🟡 (cross-doc)

**Same-document — Baseline Oct 2025, ship unguarded:**
```js
const t = document.startViewTransition(() => updateDOM());  // DOM mutation MUST be sync
await t.finished;
```
Browser snapshots old+new, cross-fades by default. Pseudo tree: `::view-transition-group(name)` → `image-pair` → `old`/`new`.
```css
.hero { view-transition-name: hero; }                                  /* old.hero ↔ new.hero auto-FLIP */
::view-transition-old(root) { animation: 240ms ease-out both fade-out; }
.card { view-transition-class: card; }  /* style a whole category */
::view-transition-group(.card) { animation-duration: 300ms; }
```
- **Types** branch by intent: `startViewTransition({ update, types:['forward'] })` + `:root:active-view-transition-type(forward) ::view-transition-old(root) { ... }`.
- **Cross-document / MPA 🟡** (Firefox gap) — pure CSS, opt in on **both** pages: `@view-transition { navigation: auto; }`. Hook `pagereveal`/`pageswap` to set names / restore scroll. FF falls back to instant nav.
- **Traps:** name the *smallest* element that morphs (each named el gets `contain` + its own snapshot → big/scrolling ones clip or oversize). `old` is a frozen image. Duplicate names abort the transition. Keep the callback a pure state swap. Guard interaction + restore focus; wrap in `prefers-reduced-motion`.

## 32. Enter/exit: `display:none` ⇄ visible ✅

The native pattern that kills the mount/unmount-animation JS dance — popover, dialog, toast.
```css
.toast {
  opacity: 0; translate: 0 1rem;
  transition: opacity .3s, translate .3s, display .3s allow-discrete, overlay .3s allow-discrete;
}
.toast.open { opacity: 1; translate: 0 0; }
@starting-style { .toast.open { opacity: 0; translate: 0 1rem; } }   /* the "from" state for entry */
```
- **`allow-discrete`** lets `display`/`overlay`/`content-visibility` participate (kept visible across the transition).
- **`@starting-style`** supplies pre-insertion values, else fresh elements snap in.
- **`overlay`** is the easy miss: top-layer els (popover/dialog) get yanked from the top layer at frame 0 of exit unless you animate `overlay` with `allow-discrete` → exit plays behind content or not at all. All Baseline 2024.

## 33. Animating to `height: auto` 🟡

```css
:root { interpolate-size: allow-keywords; }   /* opt-in; enables 0 ↔ auto/min-content/max-content/fit-content */
.panel { height: 0; overflow: clip; transition: height .3s; }
.panel.open { height: auto; }
```
Or per-value: `height: calc-size(auto, size)`. Chrome 129+ only; **Safari/FF pending**. Universal fallback — the grid hack:
```css
.wrap { display: grid; grid-template-rows: 0fr; transition: grid-template-rows .3s; }
.wrap.open { grid-template-rows: 1fr; } .wrap > * { overflow: hidden; min-height: 0; }
```

## 34. `linear()` easing ✅ — springs & bounces

```css
transition-timing-function: linear(0, 0.218 2.1%, 0.862 6.5%, 1.114, 1.05 13%, 0.98, 1.01, 0.999);
```
- `cubic-bezier()` is one curve with two control points — **can't** do multi-bounce or overshoot-then-settle. `linear()` approximates *any* curve piecewise; values may exceed 0–1 for overshoot; two `%` on a stop = a plateau.
- **Generate, don't hand-write** (Jake Archibald's linear-easing-generator converts a spring or SVG curve). It's a *baked* curve — reach for JS springs when you need velocity-aware interruption.

## 35. `offset-path` ✅ — motion paths

```css
.comet { offset-path: path("M0,200 Q200,0 400,200"); offset-rotate: auto; offset-anchor: center;
         animation: ride 4s linear infinite; }
@keyframes ride { to { offset-distance: 100%; } }
```
`offset-path`: `path()` | `ray()` | basic-shape | `url(#svgShape)`. Animate `offset-distance: 0%→100%`. `offset-rotate: auto` keeps it tangent. `path()`/`url()` solid; `ray()`/`shape()`/coord-box partial.

## 36. Individual transforms ✅

```css
.chip { translate: 0 0; rotate: 0deg; scale: 1; transition: translate .2s, rotate .2s, scale .2s; }
.chip:hover { scale: 1.1; }       /* doesn't clobber translate/rotate */
```
Under-used because AI keeps writing `transform: translate() rotate() scale()`. Killer use: animate one axis on hover, another on scroll, without a shared `transform` string overwriting. Fixed composition order: translate → rotate → scale → `transform`.

## 37. `@container scroll-state()` 🔴

Native replacement for JS scroll listeners detecting stuck/snapped. **Chrome/Edge 133+ only.**
```css
.sticky-wrap { container-type: scroll-state; }   /* on an ANCESTOR of the sticky el */
@container scroll-state(stuck: top) { .header { box-shadow: 0 2px 8px #0003; } }
@container scroll-state(snapped: x) { .slide  { outline: 2px solid hotpink; } }
```
States: `stuck`, `snapped`, `scrollable`, `scrolled`. Bleeding-edge PE.

---

# Typography & Text

## 38. Variable fonts ✅

Registered axes (lowercase): `wght wdth slnt ital opsz`. Custom (UPPERCASE): `GRAD MONO CASL` …
```css
h1 { font-weight: 760; font-stretch: 85%; font-style: oblique 12deg; font-optical-sizing: auto; }  /* PREFER high-level props */
.grade { font-variation-settings: "wght" 480, "GRAD" 88; }   /* ONLY way to custom axes */
```
- **The #1 AI botch:** `font-variation-settings` is **all-or-nothing and doesn't inherit from high-level props** — naming `"GRAD"` resets `wght` to default. Rule: use the high-level prop whenever a registered axis exists; reach for `font-variation-settings` only for custom axes, and re-declare every registered axis you care about in the same string.
- **GRAD** (grade): change weight *without changing footprint* (no reflow) — dark-mode optical compensation, hover-thicken without layout shift.
- **`opsz`:** `font-optical-sizing: auto` (default) binds to font-size; naming `"opsz"` in the settings string pins it (decouples). Animating axes interpolates but is **not GPU-composited** (layout/paint per frame) — fine for one headline, jank across a list.

## 39. Font loading — zero-CLS swap ✅

```css
@font-face { font-family: "Inter Fallback"; src: local("Arial");
  size-adjust: 107.4%; ascent-override: 90%; descent-override: 22.5%; line-gap-override: 0%; }
body { font-family: "Inter", "Inter Fallback", sans-serif; }
```
- **The under-used real fix (Baseline since 2023):** match a fallback font's box to the web font with the four overrides so `swap` doesn't shift layout. (`next/font`, `fontaine` generate the numbers.) The overrides are percentages of the *fallback's* em — eyeballing reintroduces CLS.
- `font-display`: `optional` (best CWV — no shift, no late swap) · `swap` (body, *with* the metric overrides above so FOUT is invisible) · `fallback` · `block` (avoid for content).
- **`unicode-range`** — the most under-used loading win: split into Latin / Latin-ext / Cyrillic faces; browser fetches only ranges actually rendered (self-hosters ship 4× the bytes without it).
- Preload only the critical face: `<link rel=preload as=font crossorigin>` (`crossorigin` mandatory even same-origin, else double download).

## 40. Fluid type — and the WCAG trap ✅

```css
h1 { font-size: clamp(1.5rem, 1rem + 3vw, 3rem); }   /* the rem term is LOAD-BEARING */
```
- **Raw `vw`/`cqi` fails WCAG 1.4.4** — pure-viewport text doesn't respond to zoom / text-size at a fixed viewport (200% zoom changes nothing). The `rem` component restores zoom response; it should contribute the majority at common viewports. AI consistently omits it.
- **Container-relative** (`cqi`) is the modern move for component-portable scales: `clamp(1rem, 0.8rem + 2cqi, 1.75rem)` — same rem-floor caveat. Generate steps from min/max at two viewport anchors (Utopia) rather than hand-tuning `vw`.

## 41. `text-box-trim` / leading-trim 🟡 — the 2025 type feature (still gated)

Trim the half-leading every font ships so a heading's box hugs the letterforms — labels/headings center *optically*, spacing comes from cap-height/baseline not the phantom line-box.
```css
@supports (text-box: trim-both cap alphabetic) {
  h1 { text-box: trim-both cap alphabetic; }   /* longhand: text-box-trim + text-box-edge */
}
```
`cap alphabetic` = trim to cap-height top, baseline bottom. **Chrome 133+/Safari 18.2+, no Firefox** → gate, and keep the normal-half-leading fallback looking right. Changes the box → re-tune margins; don't sprinkle on a finished layout.

## 42. `text-wrap` ✅ — balance vs pretty

```css
h1, h2, .card-title { text-wrap: balance; }   /* even line lengths — HEADINGS ONLY */
p, li               { text-wrap: pretty; }     /* kills orphan last-line — BODY */
[contenteditable]   { text-wrap: stable; }     /* typed lines don't reflow */
```
**`balance` = headings, `pretty` = body. Never balance paragraphs** — hard cap (~6 lines Chromium, ~10 FF) and it silently falls back to `auto` beyond. `pretty` is cheap (reconsiders only the last lines). AI frequently inverts this.

## 43. Line clamping 🟡

```css
.clamp { display: -webkit-box; -webkit-box-orient: vertical; -webkit-line-clamp: 3; line-clamp: 3; overflow: hidden; }
```
The legacy `-webkit-box` trio is still required (`overflow: hidden` does the clip). Standard unguarded `line-clamp` isn't Baseline yet — ship both, keep the trio for years.

## 44. OpenType — `font-variant-*` over `font-feature-settings` ✅

```css
.num, td.amount { font-variant-numeric: tabular-nums lining-nums; }   /* highest-ROI dashboard fix */
article         { font-variant-numeric: oldstyle-nums; }
.label          { font-variant-caps: all-small-caps; }                /* real small caps, not synthetic */
h1              { font-variant-ligatures: discretionary-ligatures contextual; }
.brand          { font-feature-settings: "ss01" 1, "cv11" 2; }        /* only for features with NO high-level prop */
```
- **The rule AI gets backwards:** prefer `font-variant-*` (inheritable, composable) over `font-feature-settings` (all-or-nothing, non-inheriting — naming one feature resets the rest). Drop to `font-feature-settings` only for `ss0x`/`cvxx`/`swsh`.
- **`tabular-nums`** is the most-skipped, highest-ROI feature: any column of changing numbers jitters horizontally without it. One line.
- Only `font-variant-caps: small-caps` triggers the browser's synthetic fallback when the font lacks real small caps.

## 45. `initial-letter` 🟡 — drop caps

```css
p::first-letter { -webkit-initial-letter: 3; initial-letter: 3; }   /* 3 lines tall, drop cap */
p::first-letter { initial-letter: 3 1; }                            /* tall but sinks 1 → raised cap */
```
Safari (prefixed) + Chromium; **no Firefox**. Use on `::first-letter`, not a wrapping span. Design the normal-first-letter fallback to be acceptable; never depend on the sink.

## 46. `hanging-punctuation` 🔴 (Safari-only)

```css
blockquote { hanging-punctuation: first last; }   /* optical margin alignment for quotes */
```
Genuinely **Safari-only, ~15% global** (confirmed, not stale). The detail that separates typeset quotes from default. Never load-bearing; ensure container padding so Safari users don't clip; don't `@supports`-gate (it no-ops elsewhere).

## 47. Tracking & text-decoration craft ✅

- **`letter-spacing` in `em`, never px** (tracks font-size). Tracking scales *inversely* with size: tighten display (`-0.02em` to `-0.04em`), loosen all-caps/small labels (`0.08em` on `text-transform: uppercase`). AI defaults to `0` and leaves caps cramped.
- **Designed underlines** — the under-used trio:
```css
a { text-decoration-thickness: 0.08em; text-underline-offset: 0.18em; text-decoration-skip-ink: auto; }
```
`text-underline-offset` + `text-decoration-thickness` are the biggest "designed underline" upgrade — the default crowds descenders. `from-font` respects the designer's metrics.

## 48. Vertical text & writing-mode ✅

```css
.spine { writing-mode: vertical-rl; text-orientation: mixed; }     /* CJK-correct */
.latin-spine { writing-mode: vertical-rl; text-orientation: upright; }
```
`mixed` (CJK upright, Latin rotated — correct default for Japanese), `upright` (Latin spine labels), `sideways` (all 90°). **Trap:** logical props (`-block`/`-inline`) flip meaning in vertical modes — use them throughout or layouts break.

## 49. Highlight & line pseudos ✅/🟢

```css
p::first-line { font-variant-caps: small-caps; }   /* dynamic, re-evaluates on resize */
::selection   { background: oklch(.8 .15 200 / .4); color: inherit; }   /* set BOTH bg and color */
::target-text { background: color-mix(in oklch, var(--brand) 25%, transparent); }   /* scroll-to-text-fragment arrival (Baseline 2024) */
```
- `::first-line`/`::first-letter` accept only a restricted property set (font/color/bg/decoration/spacing).
- **Custom Highlight API `::highlight()` 🟢** (Baseline 2025) — style arbitrary text ranges with **zero DOM mutation** (search hits, spellcheck, collab cursors). Register `Range`s via JS `CSS.highlights.set("name", new Highlight(range))`. Traps: ranges are static snapshots (rebuild on DOM change); only paint props work (color/background/decoration/shadow — no font-size/weight); special highlight-inheritance chain. Replaces the "wrap matches in `<mark>`" reflow hack.

---

# Advanced / Structural

## 50. Houdini reality — one survivor

- **`@property` ✅** — covered in §29; the one Houdini API that went universal (mid-2024). Reach for *this specifically*, not "Houdini."
- **Paint API `paint()` 🔴** — Chromium-only, Firefox/Safari never implemented, no intent. Procedural backgrounds/borders reacting to custom props + size; ship a static `background-image` before the `paint()` line. Don't build core visuals on it.
- **Typed OM 🟡** — `el.attributeStyleMap.set('width', CSS.px(300))`, math without string concat; Chromium full, Safari/FF partial. Only worth it in measured tight loops.
- ☠️ **Dead:** Houdini Layout API, Animation Worklet, the "extend CSS via worklets" vision.

## 51. CSS math — trig & radial layout ✅

`sin cos tan asin acos atan atan2 hypot pow sqrt exp log round mod rem abs sign` — all Baseline since ~late 2023.
```css
/* place N items on a circle — replaces a JS trig loop */
.item { --n: 12; --a: calc(sibling-index() / var(--n) * 1turn); --r: 140px;
        translate: calc(cos(var(--a)) * var(--r)) calc(sin(var(--a)) * var(--r)); }
```
- `atan2(dy, dx)` → angle; `hypot(3,4)` → distance/magnitude. `round(up, var(--h), var(--line))` snaps to a baseline grid. `pow`/`log` for modular type scales in-CSS.
- **Trap:** bare numbers in trig are **radians** — `sin(45)` ≠ `sin(45deg)`. Trig returns `<number>`; multiply by a length to use as one. (Pair with `sibling-index()` §13 🔴 for index-free; until cross-browser, set `--i` inline or via `:nth-child`.)

## 52. Generated content & counters ✅

```css
@counter-style padded { system: numeric; symbols: "0" "1" "2" "3" "4" "5" "6" "7" "8" "9"; pad: 3 "0"; }  /* 001, 002 */
ol { counter-reset: sec; } li { counter-increment: sec; }
li::before { content: counters(sec, ".") " "; }                 /* 1, 1.1, 1.1.1 nested */
.badge::before { content: "★" / "Featured"; }                   /* visual glyph + accessible name */
a[href^="http"]::after { content: " ↗ (" attr(href) ")"; }
```
- **`content: <visual> / <alt>`** — the under-used a11y move: decorative glyphs get a real accessible name (`/ ""` to hide from AT).
- `@counter-style` systems: `cyclic numeric alphabetic symbolic fixed additive extends`. `::marker` styles color/font/content only (no box — switch to `::before` for a background).
- **Trap:** *typed* `attr()` (`attr(data-w px)`) for non-`content` props is 🔴 Chromium-only; string `attr()` in `content` is the only universally safe form.

## 53. Form controls — the 2024–26 wave

- **`:user-valid` / `:user-invalid` ✅** — validate only *after* interaction (blur/submit), fixing `:invalid` lighting up empty required fields on load. Use these for live validation UX, not `:valid`/`:invalid`.
- **`accent-color` ✅** — `:root { accent-color: ... }` tints checkbox/radio/range/progress. (Baseline since ~2022 — stale priors say otherwise.)
- **`<dialog>` + `::backdrop` ✅** — `showModal()` → top layer, focus trap, ESC close. Animate in with `@starting-style` + `allow-discrete`.
- **Popover API 🟢** (2025) — `<button popovertarget="m">` + `<div id="m" popover>`. `auto` (light-dismiss, one-at-a-time) / `manual` (stackable). `popovertarget` is an implicit anchor reference — no `anchor-name` needed.
- **`<details name>` exclusive accordion 🟢** + **`::details-content` 🟡** — one-open-per-group; animate open/close with `interpolate-size: allow-keywords` + `allow-discrete` (animation is the PE layer; the accordion works everywhere).
- **Customizable `<select>` 🔴** (Chrome 135+) — `appearance: base-select` on both `select` and `::picker(select)`; style the button, popup, options (rich HTML), `::checkmark`, `::picker-icon`, `selectedcontent`. Degrades to native — design the base look as the enhancement.
- **`::file-selector-button` ✅**, **`field-sizing` 🟡** (§11).

## 54. Scroll UX

- **Baseline ✅:** `scroll-snap-type/-align/-stop`, `scroll-margin`, `scroll-padding`, `overscroll-behavior`, `scrollbar-gutter`, `scrollbar-width`, `scrollbar-color`.
```css
.rail { scroll-snap-type: x mandatory; overscroll-behavior-x: contain; scrollbar-gutter: stable; }
.rail > * { scroll-snap-align: center; scroll-snap-stop: always; }
```
`scrollbar-gutter: stable` kills the appear/disappear layout shift — zero-cost, under-used. Standard `scrollbar-color/width` now beat `::-webkit-scrollbar` for portability.
- **Snap events 🟡** (`scrollsnapchange`/`scrollsnapchanging`) — Chromium shipped, others lagging; "active dot" sync without position math, keep an IO fallback.
- **CSS Carousels 🔴** (`::scroll-button()` / `::scroll-marker` / `scroll-marker-group`, Chrome 135) — prev/next + dot indicators + tablist semantics, zero JS, `:target-current` tracks the active slide. Spec is Working Draft (unstable), single-engine — ship a plain-scroll carousel underneath, treat buttons/dots as enhancement.

## 55. Performance ✅/🟢

- **`content-visibility: auto` + `contain-intrinsic-size` 🟢** — the highest-ROI perf primitive most people never use. Browser skips layout+paint for off-screen sections; content stays in a11y tree / find-in-page / tab order.
```css
.section { content-visibility: auto; contain-intrinsic-size: auto 600px; }
```
**Always set `contain-intrinsic-size`** or the scrollbar jumps as sections render/un-render (`auto <estimate>` remembers last size). `content-visibility: hidden` *does* remove from a11y (a faster-toggle `display:none`).
- **`contain` ✅** — `contain: content` (safe default: layout+paint+style) scopes recalc; `strict`/`size` need explicit dimensions or layout collapses.
- **`will-change`** — promotes proactively but costs memory; apply just before an animation, remove after. Never blanket `will-change: transform` on many static elements (anti-optimization at scale).

## 56. Selectors & media queries ✅

- **`:nth-child(An+B of S)`** — count by arbitrary selector, not tag:
```css
tr:nth-child(even of :not([hidden])) { background: #f3f3f3; }   /* zebra that ignores hidden rows */
```
- **Range syntax:** `@media (width >= 600px) and (width < 1200px)` / `@container (400px <= width <= 800px)`.
- **`env()`** — `safe-area-inset-*` ✅ (always provide the fallback arg: `env(safe-area-inset-bottom, 0px)`); `titlebar-area-*`/`keyboard-inset-*` 🟡; `viewport-segment-*` 🔴.
- **Media features — corrected status:** `prefers-reduced-motion`/`prefers-color-scheme`/`prefers-contrast`/`forced-colors`/`scripting`/`update`/`dynamic-range` all ✅ Baseline. Genuinely gappy: `prefers-reduced-transparency` 🟡 (no FF), `inverted-colors` 🟡 (no FF), `prefers-reduced-data` 🔴 (Chromium).

---

## Motion safety (non-negotiable)

```css
@media (prefers-reduced-motion: reduce) {
  *, ::before, ::after {
    animation-duration: .01ms !important; animation-iteration-count: 1 !important;
    transition-duration: .01ms !important; scroll-behavior: auto !important;
  }
}
```
For scroll-driven animations: set the final state, `animation: none`. For View Transitions: skip or shorten. `@media (update: slow)` (e-ink/low-power) is a cheaper signal than UA sniffing.

## Native-vs-JS decision table

| Want | Native CSS | Reach for GSAP/JS when |
|---|---|---|
| Scroll progress / reveal / parallax | `scroll()`/`view()` + `animation-range` | pinning with reflow, scrubbed master timelines, JS-computed values |
| Page / route transition | View Transitions (same-doc ✅) | fine-grained interruption, FLIP across virtualized lists |
| Enter/exit of popover/dialog/toast | `allow-discrete` + `@starting-style` + `overlay` | orchestrated multi-element stagger |
| Spring / bounce easing | `linear()` (baked) | velocity-aware, interruptible springs |
| Move along a path | `offset-path` + `offset-distance` | path that morphs at runtime |
| Animate gradient / angle / custom value | `@property` + `transition` | values driven by live JS state |
| height auto reveal | `interpolate-size` over `grid 0fr→1fr` fallback | — |
| Detect stuck / snapped | `@container scroll-state()` (Chrome-only) | cross-browser today → JS/IntersectionObserver |

## The biggest fully-safe wins to reach for first

`grid-area: 1/1` cell-overlap · `:where()` zero-specificity defaults · `@layer` over specificity escalation · subgrid for card-row alignment · `@property` (unlocks animation) · `content-visibility: auto` (perf) · `:user-valid` (validation UX) · `scrollbar-gutter: stable` (no shift) · `content: x / "alt"` (a11y) · `:nth-child(of S)` zebra · `tabular-nums` on every numeric column · oklch even ramps + relative-color derivation · layered smooth shadows · `mask` scroll-edge fades · metric-override fallback fonts (zero CLS). These are Baseline, under-used, and exactly what gets forgotten.
