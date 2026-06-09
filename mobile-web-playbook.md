# Mobile Web Playbook — The Frontier & Craft Reference

Mobile is where most traffic lives and where most "responsive" sites quietly fail. This is the under-used, high-leverage, easy-to-forget half of building for phones: the viewport math nobody re-learns, the touch and keyboard behavior that desktop hides, the performance reality of a mid-tier Android on a flaky network, and the 2025–26 primitives (`dvh`, `safe-area-inset`, `interactive-widget`, `overscroll-behavior`, INP) that most code never reaches for. Companion to `css-playbook.md` (the CSS features), `gsap-playbook.md` (motion), and `app-design-taxonomy.md` (native/PWA app patterns — this doc is the *web* side).

> **Why this exists.** Models and juniors regress to the mean: "responsive" collapses to *shrink the desktop, drop in one `@media (max-width: 768px)`, ship.* The real mobile craft — viewport units that survive the address bar, hit targets sized for thumbs, inputs that don't trigger zoom, an image pipeline that doesn't blow the LCP budget — is rare in the corpus, needs a real device to tune, and is judgment not snippet. Exactly the three things that get dropped. This doc is the corrective: design for the phone *first*, not the phone *last*.

> **Verified June 2026** against MDN, web.dev, caniuse, WebKit/Chrome/Android release notes, WCAG 2.2, and the Core Web Vitals (INP) program.

## Support legend

Every support-sensitive feature is tagged. **Read the tag before shipping.**

- ✅ **Baseline widely available** — safe everywhere, ship unguarded.
- 🟢 **Baseline newly available** (landed all engines ≤~2.5yr ago) — ship, expect a small straggler tail.
- 🟡 **Limited** — a major engine (usually iOS Safari) is missing or partial. Gate with `@supports` / keep a fallback.
- 🔴 **Single-engine / experimental** — Chromium-Android-only or flagged. Progressive enhancement only, never load-bearing.
- ☠️ **Dead / harmful** — abandoned or actively an anti-pattern. Don't reach for it.

## The 2026 mobile reality nobody updated their mental model for

- **`100vh` is still wrong on mobile and `dvh`/`svh`/`lvh` are Baseline** (all engines since early 2023, Baseline *widely available* mid-2025). Stop hard-coding `100vh` for full-screen sections — it overflows under the iOS address bar. Use `100dvh` (or `svh` for the safe minimum).
- **INP replaced FID** as a Core Web Vital (March 2024). Interaction *responsiveness* — not just first-input delay — is now scored. Your tap-to-paint latency is a ranking and UX signal.
- **The 300ms tap delay is dead** on every modern mobile browser when you set the viewport meta correctly. `touch-action: manipulation` and `FastClick` shims are legacy cargo-cult.
- **`env(safe-area-inset-*)` is Baseline** — the notch/home-indicator/punch-hole are a solved problem *if* you set `viewport-fit=cover`. Most sites still don't.
- **`overscroll-behavior` is broadly supported** (Chrome/Firefox since 2018, Safari 16+ in 2022; MDN still flags it "Limited" but it's ~95% in practice) — accidental pull-to-refresh and scroll-chaining out of a modal are one line to fix, and almost nobody does.
- **The visual-viewport keyboard problem has a partial CSS answer** — `interactive-widget=resizes-content` (Chrome 108+, Firefox 132+, **not Safari**) + the `VisualViewport` API (Baseline). On iOS you still need the `VisualViewport` API; the meta key alone won't save you. Either way, beats `window.innerHeight` hacks.
- **`user-scalable=no` / `maximum-scale=1` is a WCAG failure**, not a "polish" setting. Pinch-zoom is an accessibility right. Shipping it is a bug.
- **Container queries (✅) make device breakpoints mostly obsolete** for components. Query the component's space, not the viewport — a card doesn't care what phone it's on.

---

## How to use this doc

- **Mobile-first is a method, not a slogan.** Write the small-screen layout as the unguarded base; *add* complexity at larger min-widths. `max-width` queries that subtract are the tell of a desktop design retrofitted.
- **Test on a real mid-tier Android, throttled.** The iPhone in your hand is the best-case device. The median visitor is on a 2–3-year-old Android over congested 4G. Emulators lie about CPU, touch, keyboard, and Safari quirks.
- **Capability over screen size.** `pointer: coarse`, `hover: none`, `prefers-reduced-motion`, and the `Save-Data` signal tell you what the device *can do* and what the user wants. Width tells you almost nothing now (foldables, tablets, desktop touchscreens).
- **Every entry is: what it is, when to reach for it, the senior idiom, the trap.** The trap is the part the corpus forgets.

## Table of contents

- [1. The viewport & coordinate systems](#1-the-viewport--coordinate-systems)
- [2. Touch, pointer & input](#2-touch-pointer--input)
- [3. Responsive layout architecture](#3-responsive-layout-architecture)
- [4. Typography on small screens](#4-typography-on-small-screens)
- [5. Navigation patterns](#5-navigation-patterns)
- [6. Scrolling & overscroll](#6-scrolling--overscroll)
- [7. The keyboard & forms](#7-the-keyboard--forms)
- [8. Performance — the mobile budget](#8-performance--the-mobile-budget)
- [9. Images & media](#9-images--media)
- [10. Motion on mobile](#10-motion-on-mobile)
- [11. PWA & app-like feel](#11-pwa--app-like-feel)
- [12. Capability detection & adaptation](#12-capability-detection--adaptation)
- [13. Accessibility on mobile](#13-accessibility-on-mobile)
- [14. Testing, debugging & QA](#14-testing-debugging--qa)
- [15. Graceful degradation & capability-tiered experiences](#15-graceful-degradation--capability-tiered-experiences)
- [16. The mobile anti-pattern catalog](#16-the-mobile-anti-pattern-catalog)

---

# 1. The viewport & coordinate systems

The single most misunderstood area. There is not "a viewport" — there are three, and the address bar moves one of them while you scroll.

## 1.1 The viewport meta tag

The one line without which nothing else works. The browser otherwise renders at a ~980px fake desktop width and shrinks it.

```html
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
```
- `width=device-width` — match the layout viewport to the device's CSS-pixel width. Non-negotiable.
- `initial-scale=1` — start at 1:1, no zoom-out.
- `viewport-fit=cover` — let content extend under the notch/rounded corners so you can *opt into* `safe-area-inset` padding (§1.4). Without it, you get letterboxed bars on notched devices.
- **Trap:** **never** add `user-scalable=no`, `maximum-scale=1`, or `minimum-scale=1`. Disabling pinch-zoom is a WCAG 1.4.4 / 1.4.10 failure and breaks low-vision use. The "it stops zoom on input focus" reason is wrong — the fix for that is a 16px font (§4.1), not killing zoom. ☠️

## 1.2 Layout viewport vs visual viewport

The **layout viewport** is the box your CSS lays out against (fixed for a given orientation). The **visual viewport** is what's actually on screen — it shrinks when the keyboard opens and shifts when the user pinch-zooms. `position: fixed` pins to the *layout* viewport, which is why a fixed footer hides *behind* the keyboard instead of riding above it.
- Read the visual viewport via the `VisualViewport` API: `window.visualViewport.height`, `.offsetTop`, and the `resize`/`scroll` events. This is how you keep a toolbar above the keyboard without guessing.
- **Trap:** `window.innerHeight` reports the *layout* viewport on most mobile browsers — it does **not** shrink when the keyboard appears. Code that repositions elements off `innerHeight` is reading the wrong number. Use `visualViewport.height`.

## 1.3 Dynamic viewport units — `dvh` / `svh` / `lvh` ✅

The fix for the infamous "`100vh` is too tall on mobile" bug. The mobile address bar expands and collapses on scroll, changing the usable height.
- `lvh` — **largest** viewport (address bar collapsed). `100lvh` == old `100vh`.
- `svh` — **smallest** viewport (address bar expanded). The safe "always fits" height.
- `dvh` — **dynamic**, tracks the current state live as the bar moves.
- `vh` is now defined to equal `lvh` — i.e. the *largest*, which is why `100vh` overflows when the bar is showing.

```css
.hero { min-height: 100svh; }          /* never clipped, even with the bar showing */
.fullscreen-modal { height: 100dvh; }   /* tracks live — but note the relayout caveat */
```
- **When:** full-bleed heroes, splash sections, full-screen modals/menus.
- **Trap:** `dvh` *relayouts every frame the bar animates* — for a large, expensive section that causes visible reflow jank as you scroll. Prefer `svh` for stable layout and reserve `dvh` for elements that genuinely must track. Also: `dvh` does **not** account for the keyboard (that's the visual viewport, §1.2) — a `100dvh` element still sits behind the keyboard.

## 1.4 Safe-area insets & the notch ✅

`env(safe-area-inset-top|right|bottom|left)` expose the space occupied by the notch, rounded corners, home indicator, and punch-holes. Only non-zero when `viewport-fit=cover` is set (§1.1).

```css
.app-bar    { padding-top: max(1rem, env(safe-area-inset-top)); }
.bottom-nav { padding-bottom: max(0.5rem, env(safe-area-inset-bottom)); }
.page       { padding-inline: max(1rem, env(safe-area-inset-left), env(safe-area-inset-right)); }
```
- **The `max()` idiom is the senior move:** take the larger of your normal padding and the inset, so the layout is correct on both notched and flat devices with one rule.
- `env()` takes a fallback second arg: `env(safe-area-inset-bottom, 0px)`.
- **Trap:** a `position: fixed; bottom: 0` bar without `padding-bottom: env(safe-area-inset-bottom)` sits *under* the iOS home indicator and gets its bottom row of tap targets stolen by the system swipe area. The most common notch bug after letterboxing.

## 1.5 Orientation & the foldable/dual-screen era

Handle orientation by *content*, not by locking. `@media (orientation: landscape)` adjusts; it does not assume a tablet.
- Foldables expose the `viewport-segments` / `@media (horizontal-viewport-segments: 2)` queries 🔴 (Chromium-Android experimental) and the `env(viewport-segment-*)` variables to avoid placing content across the hinge.
- **Trap:** **never** lock orientation on the web (`screen.orientation.lock()` in a non-installed context, or designing for portrait-only). It's a WCAG 1.3.4 failure — a user mounted in a car dock or with a fixed wheelchair tray may only have one orientation available. Reflow instead.

---

# 2. Touch, pointer & input

Desktop hides an entire input model from you. On touch there is no hover, no cursor, no precise pointer, and fingers are ~9mm wide.

## 2.1 Hit-target sizing — the 44/48/24 numbers

The most violated mobile rule. A tappable thing must be physically large enough for a fingertip.
- **Apple HIG: 44×44pt.** **Material: 48×48dp.** **WCAG 2.5.8 (AA): 24×24 CSS px minimum; 2.5.5 (AAA): 44×44.** Treat **44px** as the design floor, 24px as the absolute legal minimum.
- Size the *target*, not the *ink* — a 16px icon can have a 44px tap area via padding or a `::before` overlay:
```css
.icon-btn { position: relative; }
.icon-btn::before { content: ""; position: absolute; inset: -14px; } /* expands hit area, no visual change */
```
- **Spacing matters as much as size:** ≥8px between adjacent targets so a fat finger doesn't hit two. WCAG 2.5.8 lets a small target pass *if* it has enough spacing — size and spacing trade off.
- **Trap:** inline text links in body copy and tightly-stacked list rows are the usual failures. A 12px "×" close button in the corner of a modal is the single most-rage-tapped element on mobile.

## 2.2 The hover problem — `hover` & `pointer` media ✅

Touch devices can't hover. Any UI that *reveals* on hover (dropdown menus, "show on hover" actions, tooltips) is invisible or broken on touch.
```css
@media (hover: hover) and (pointer: fine) {
  .card:hover .actions { opacity: 1; }   /* mouse only */
}
@media (hover: none) {
  .actions { opacity: 1; }               /* always visible on touch, or use a tap toggle */
}
```
- `pointer: coarse` = imprecise (finger); `pointer: fine` = precise (mouse/stylus). `hover: none` = can't hover. `any-hover`/`any-pointer` test *any* connected input (a laptop with a touchscreen has both).
- **Trap:** don't gate *essential* actions behind hover and then "fix" it with a touch fallback that requires a first tap to reveal and a second to activate — that double-tap is a known frustration. On touch, just show the action.

## 2.3 `touch-action` — own the gesture ✅

Declares which gestures the browser handles vs. your JS. The correct way to kill the legacy 300ms double-tap-zoom delay and to prevent scroll-vs-drag conflicts.
```css
button, a, .tap { touch-action: manipulation; }  /* allow pan/zoom, drop double-tap delay */
.carousel-track { touch-action: pan-y; }          /* let vertical scroll pass, capture horizontal drag */
.signature-pad  { touch-action: none; }           /* fully custom gesture surface */
```
- **When:** any custom drag, swipe, pinch, or canvas surface; any element where you've wired pointer handlers and the browser's default gesture fights you.
- **Trap:** `touch-action: none` on a large area **disables scrolling through it** — users get stuck. Scope it tightly to the interactive element, and only restrict the axis you actually own (`pan-y` for a horizontal slider).

## 2.4 Pointer Events over touch/mouse events ✅

`pointerdown/move/up` unify mouse, touch, and stylus in one model with pressure, tilt, and `pointerType`. Prefer them to `touchstart`+`mousedown` pairs.
- Use `setPointerCapture()` to keep receiving events when the finger slides off the element mid-drag — the clean way to build sliders and drag handles.
- Mark scroll-region listeners `{ passive: true }` so the browser doesn't wait on your handler before scrolling (a direct INP/scroll-jank win, §8.4).
- **Trap:** calling `preventDefault()` in a *non-passive* `touchstart`/`touchmove` to stop scroll is the old way and forces the browser to block the main thread on every touch. Use `touch-action` (§2.3) declaratively instead; reserve `preventDefault` for genuinely custom surfaces.

## 2.5 Tap highlight & active feedback

Touch has no hover, so `:active` is your primary feedback channel — a tap must *feel* registered instantly.
- iOS draws a grey `-webkit-tap-highlight-color` box; restyle or remove it (`transparent`) **only if you provide your own** `:active` state. Removing it with no replacement leaves taps feeling dead.
- Provide an instant `:active { transform: scale(.97) }` or color shift — perceived responsiveness is as important as actual latency.
- **Trap:** removing the tap highlight *and* doing async work on tap with no immediate visual response makes the button feel broken; users re-tap, firing duplicate actions. Always paint an instant `:active` state, then do the work.

---

# 3. Responsive layout architecture

## 3.1 Mobile-first, `min-width`, and the cascade

Write the single-column phone layout as the base (no media query), then *add* at breakpoints with `min-width`. This ships less CSS to mobile and forces you to design the constrained case first.
```css
.grid { display: grid; gap: 1rem; }                          /* base: 1 col */
@media (min-width: 48rem) { .grid { grid-template-columns: repeat(2, 1fr); } }
@media (min-width: 72rem) { .grid { grid-template-columns: repeat(3, 1fr); } }
```
- Use `rem`/`em` in media queries, not `px` — they respect the user's browser font-size setting; `px` queries ignore zoom-by-font.
- **Trap:** a stack of `max-width` queries is the fingerprint of a desktop layout being *clawed back* for mobile — you end up overriding overrides. If you're writing `max-width`, you probably designed the wrong direction first.

## 3.2 Breakpoints follow content, not devices ✅

There is no "iPhone breakpoint." Devices are a continuum (320 → foldable → tablet → desktop touchscreen). Add a breakpoint *where your layout breaks*, found by dragging the viewport until a line wraps badly or whitespace gets absurd.
- **Container queries retire most device breakpoints.** A component should respond to *its own* space so it works in a sidebar, a grid cell, or full-bleed without knowing the device:
```css
.card-host { container-type: inline-size; }
@container (min-width: 22rem) { .card { grid-template-columns: auto 1fr; } }
```
- **Trap:** hard-coding the "popular device widths" (375, 390, 414…) bakes in this year's phones and breaks on next year's and on every width in between. Design for the *range*.

## 3.3 Fluid type & space with `clamp()` ✅

Scale type and spacing smoothly between a min and max instead of snapping at breakpoints.
```css
h1 { font-size: clamp(1.75rem, 1.2rem + 4vw, 3.5rem); }
.section { padding-block: clamp(2rem, 5vw, 6rem); }
```
- The middle term mixes a `rem` floor (accessibility — never goes below a readable size when zoomed) with a `vw` term (fluidity). Pure-`vw` is the trap.
- **Trap:** `font-size: 4vw` with no `clamp` means text that's unreadably small on a 320px phone and comically huge on a tablet, *and* it breaks zoom (a `vw` unit doesn't grow when the user zooms text). Always anchor with a `rem` term inside `clamp`.

## 3.4 The horizontal-overflow bug — the #1 mobile layout defect

A single element wider than the viewport produces a horizontal scrollbar and the "why does my page wiggle sideways" bug. Causes, in frequency order:
- A flex/grid child that won't shrink. **Fix:** `min-width: 0` on the child (flex/grid items default to `min-width: auto`, refusing to shrink below content size). The most common single fix.
- A fixed-width element (`width: 500px`) on a 360px screen. Use `max-width: 100%`.
- `100vw` on a page that has a vertical scrollbar — `vw` includes the scrollbar gutter on some setups, so `100vw` > usable width. Prefer `100%`.
- A wide image/`<pre>`/table without `max-width: 100%` / `overflow-x: auto`.
- Negative margins or `position` pushing content past the edge.
- **Debug idiom:** `* { outline: 1px solid red }` then scroll right to find the culprit, or in DevTools run `[...document.querySelectorAll('*')].filter(e=>e.scrollWidth>document.documentElement.clientWidth)`.
- **Trap:** `overflow-x: hidden` on `body` *hides the symptom* but leaves the broken element — and it silently breaks `position: sticky` on ancestors. Find and fix the actual overflowing element.

## 3.5 Intrinsic, breakpoint-free layouts ✅

The most resilient mobile layouts use almost no media queries — they flex on their own.
- `grid-template-columns: repeat(auto-fit, minmax(min(100%, 16rem), 1fr))` — wraps from N columns to 1 with zero breakpoints; the inner `min(100%, 16rem)` prevents overflow on screens narrower than the track.
- `flex-wrap: wrap` + `flex: 1 1 16rem` — items reflow naturally.
- **Trap:** `minmax(16rem, 1fr)` *without* the `min(100%, …)` wrapper overflows on screens under 16rem (≈256px — still real on small/zoomed devices). Always cap the min track at `100%`.

---

# 4. Typography on small screens

## 4.1 The 16px input rule — iOS auto-zoom

iOS Safari **zooms the page** when you focus a form field whose font-size is **under 16px**, then doesn't zoom back out — a jarring, layout-wrecking jump.
```css
input, select, textarea { font-size: max(16px, 1rem); }  /* never below 16px */
```
- This is the *real* reason people reach for `user-scalable=no` — and it's the wrong fix (§1.1). The right fix is 16px inputs.
- **Trap:** designers spec 14px inputs "to match the compact UI." On iOS that guarantees the zoom jump. Keep inputs ≥16px; shrink padding, not font, if you need compactness.

## 4.2 Body size, measure & line-height

- Body text ≥16px (many argue 17–18px on mobile held at reading distance). Smaller fails real-world legibility outdoors.
- **Measure:** 35–40 characters per line is the mobile sweet spot (vs 65–75 on desktop). A full-width paragraph on a phone is already near-ideal; don't add side padding so aggressive that lines drop to 25ch.
- Line-height ~1.5 for body on mobile (slightly looser than desktop — small screens benefit from air between lines).
- **Trap:** reusing the desktop `max-width: 65ch` measure means nothing on a 360px phone (the screen caps it first), but reusing desktop's tight `line-height: 1.3` body does hurt — it reads cramped at phone sizes and distances.

## 4.3 Respect the user's font scale

Mobile OSes have a system-wide "Larger Text" / Dynamic Type setting. Honoring it is an accessibility requirement (WCAG 1.4.4: text must scale to 200%).
- Use `rem`/`em` for type and spacing so a larger root scales the whole UI. Avoid `px` font sizes.
- Test at 200% browser zoom and with the OS large-text setting on — your layout must reflow (WCAG 1.4.10: usable at 320px-equivalent with no 2-axis scroll), not clip or overlap.
- **Trap:** fixed-`px` line-heights with `rem` font-sizes: when the user scales up, the text grows but the line box doesn't, and lines overlap. Use unitless `line-height`.

## 4.4 Wrapping, hyphenation & overflow words

- `text-wrap: balance` 🟢 on short headings (evens ragged lines — Baseline 2024, all engines). `text-wrap: pretty` 🟡 on body (kills orphans) — Chrome 117+ and Safari 26+ only, **no Firefox**, and the Safari algorithm differs; it degrades to normal wrapping, so safe as enhancement. Cheap polish, great on narrow columns.
- `hyphens: auto` ✅ (with `lang` set on `<html>`, and `-webkit-hyphens` for older iOS/Safari) — essential for long German/Finnish words and for justified narrow columns; prevents overflow from a single long word. Silently no-ops without a `lang` attribute.
- `overflow-wrap: break-word` (or `anywhere`) on user-generated content, URLs, and emails so a long unbroken string can't blow out the layout (a §3.4 overflow cause).
- **Trap:** forgetting `overflow-wrap` on anything user-supplied — one pasted URL in a comment breaks the whole column width on the narrowest screens.

---

# 5. Navigation patterns

## 5.1 The thumb zone

A held phone is operated by the thumb, which comfortably reaches the **bottom and center**; the **top corners are the hardest** to hit. This inverts desktop assumptions (where the top nav bar is prime real estate).
- Put primary, frequent actions within bottom-third reach. Bottom nav bars, bottom sheets, and FABs exist because of this.
- A top-anchored hamburger is the *least* reachable spot on a large phone — fine for occasional nav, wrong for primary actions.
- **Trap:** placing the most-used action (compose, search, cart) top-right "to match the desktop header" puts it where the thumb strains most.

## 5.2 The hamburger trade-off

Hiding all nav behind a ☰ icon is fine for deep/secondary structure and wrong for primary destinations — hidden nav measurably lowers discovery and engagement vs. visible tabs.
- **Bottom tab bar** (3–5 destinations): highest discoverability, thumb-friendly, the app-like default. Reserve for the few top-level sections.
- **Hamburger drawer:** acceptable for large/secondary IA (account, settings, long catalogs).
- **Trap:** a brand-new site with five total pages hiding all of them behind a hamburger. If they fit as visible tabs, show them. The hamburger is for *overflow*, not for tidiness.

## 5.3 Sticky headers & scroll-aware hiding

A sticky header eats vertical space that's scarce on phones. The senior pattern: **hide on scroll-down, reveal on scroll-up** (content-first while reading, nav one flick away).
- Cheapest robust implementation: an `IntersectionObserver` sentinel + a transform class, or modern `scroll-driven animations` 🟡 (Firefox gap, degrades clean).
- Keep the sticky header short (≤56–64px) — a tall sticky bar on a phone is a big chunk of the viewport gone.
- **Trap:** `position: sticky` silently dies if **any** ancestor has `overflow: hidden`/`auto`/`clip` (including the `overflow-x: hidden` someone added to "fix" §3.4). Also, a sticky header with no scroll-margin makes in-page anchor links land *behind* the header — set `scroll-padding-top` on the scroll container.

## 5.4 Drawers, bottom sheets & modals

- **Bottom sheet** (slides up from the bottom edge) is the mobile-native modal — thumb-reachable, dismissible by swipe-down. Prefer it to a center dialog for choices and forms on phones.
- The `<dialog>` element ✅ gives you focus trapping, `::backdrop`, and `Esc`/inert background for free — use it instead of a hand-rolled `div` modal.
- **Lock background scroll while open** (§6.3) or the page scrolls behind the sheet.
- **Trap:** a full-screen mobile menu that doesn't lock body scroll — the user scrolls the menu, it ends, and the *page* behind keeps scrolling. Jarring and a common bug.

## 5.5 Fixed bars + keyboard + safe area

A `position: fixed; bottom: 0` action bar (checkout CTA, message input) collides with two things: the home indicator (§1.4) and the keyboard (§1.2/§7.4).
- Pad with `env(safe-area-inset-bottom)` for the indicator, and reposition above the keyboard using `interactive-widget=resizes-content` (§7.4) or the `VisualViewport` API.
- **Trap:** the message-input bar that disappears behind the keyboard on iOS is the canonical failure — `position: fixed` pins to the layout viewport, which the keyboard doesn't shrink. You must read the visual viewport.

---

# 6. Scrolling & overscroll

## 6.1 Momentum & scroll containers

- Native scroll already has momentum on mobile; you rarely need a JS smooth-scroll library (Lenis et al.) on touch and it often *worsens* INP and battery. Reserve smooth-scroll libs for desktop-led experiences and disable them under `prefers-reduced-motion` and on coarse pointers.
- The old `-webkit-overflow-scrolling: touch` is obsolete (momentum is default since iOS 13). Don't cargo-cult it.
- **Trap:** wrapping the whole page in a JS scroll-hijack to get "buttery" scroll trashes mobile performance, breaks `position: sticky`, fights the URL-bar resize, and disables the OS's native fast-scroll/scrollbar affordances. The native scroller is better on touch.

## 6.2 `overscroll-behavior` — stop chaining & accidental refresh 🟢

Controls what happens at a scroll boundary. Two big wins, one line each.
```css
body { overscroll-behavior-y: contain; }  /* kill accidental pull-to-refresh + scroll chaining */
.modal, .drawer, .chat-log { overscroll-behavior: contain; } /* scroll stays inside; page behind doesn't move */
```
- `contain` = no chaining to the parent, but native effects (rubber-band) stay. `none` = also suppress the bounce/refresh. Chrome/Firefox since 2018, **Safari 16+ (2022)** — universal in practice; MDN's "Limited" banner is stale.
- **When:** any inner scroll area (modal, sidebar, chat, map), and on `body` to stop the pull-to-refresh from firing when a user flicks up at the top.
- **Trap:** without `contain` on a scrollable modal, reaching its end *chains* the scroll to the page behind it — close the modal and you're somewhere random on the page.

## 6.3 Locking body scroll under an overlay

When a full-screen menu/sheet is open, the page behind must not scroll. The naive `overflow: hidden` on `body` **scrolls the page to the top on iOS** (a long-standing Safari bug) and loses scroll position.
- Robust idiom: record `scrollY`, set `body { position: fixed; top: -scrollY; width: 100% }`, and restore on close. Or use a vetted `body-scroll-lock` util. `overscroll-behavior: contain` (§6.2) on the overlay reduces but doesn't fully replace the lock.
- **Trap:** the iOS scroll-to-top jump on `overflow: hidden` surprises everyone once. Save and restore the position.

## 6.4 Scroll-snap for carousels & galleries ✅

CSS scroll-snap gives native, momentum-respecting, accessible horizontal carousels with no JS.
```css
.carousel { display: flex; overflow-x: auto; scroll-snap-type: x mandatory; gap: 1rem;
            scroll-padding-inline: 1rem; }
.carousel > * { scroll-snap-align: start; flex: 0 0 85%; }  /* peek next card */
```
- The `flex: 0 0 85%` "peek" hint (showing a sliver of the next item) signals swipeability far better than dots.
- **Trap:** `scroll-snap-type: x mandatory` can *trap* the user if items are taller than the viewport or if content is added dynamically mid-scroll — prefer `proximity` when item sizes vary, and never put a mandatory-snap on a region the user must scroll *through* to reach more content.

## 6.5 `content-visibility` for long pages 🟢

`content-visibility: auto` skips rendering (layout + paint) of off-screen sections until they approach the viewport — a large scroll-perf and initial-render win on long mobile pages.
```css
.below-fold-section { content-visibility: auto; contain-intrinsic-size: auto 600px; }
```
- Baseline *newly available* Sept 2024 — Chrome 85+, Firefox 125+, **Safari 18 (Sept 2024)** was the gate. Recent enough to treat as enhancement on a long page, not load-bearing.
- Always pair with `contain-intrinsic-size` (an estimated height — recommended, not required) or the scrollbar jumps as sections render.
- **Trap:** Safari's find-in-page historically does **not** search `content-visibility: auto` skipped content, and a wildly-off intrinsic size breaks anchor/Ctrl-F jump positioning. Estimate sizes reasonably and don't hide must-be-findable text behind it.

---

# 7. The keyboard & forms

Mobile forms are where conversions die. Every wrong attribute adds a tap or a zoom.

## 7.1 `type` & `inputmode` — summon the right keyboard

The input type changes the *on-screen keyboard layout*, validation, and autofill. `inputmode` tunes the keyboard without changing semantics.
```html
<input type="email"    inputmode="email"        autocomplete="email">
<input type="tel"      inputmode="tel"          autocomplete="tel">
<input type="text"     inputmode="numeric" pattern="[0-9]*" autocomplete="one-time-code"> <!-- OTP -->
<input type="url"      inputmode="url"          autocomplete="url">
<input type="search"   enterkeyhint="search">
```
- `type="number"` is for *amounts you'd do math on*, **not** phone numbers, OTPs, card numbers, or ZIPs (it strips leading zeros, allows `e`/`-`, and shows spinners). Use `inputmode="numeric"` on a `type="text"` for those.
- `enterkeyhint` relabels the keyboard's return key (`go`, `search`, `send`, `next`, `done`) so the action is obvious.
- **Trap:** `type="number"` for a phone field is the classic mistake — it blocks `+`, parentheses, and spaces and mangles formatting. Use `type="tel"`.

## 7.2 Autocomplete & autofill tokens

Correct `autocomplete` tokens let the browser/keychain fill name, address, email, and **one-time codes** (`autocomplete="one-time-code"` lets iOS surface the SMS code above the keyboard) — huge friction reduction.
- Use the granular tokens: `given-name`, `family-name`, `address-line1`, `postal-code`, `cc-number`, `cc-exp`, `new-password`/`current-password`.
- **Trap:** `autocomplete="off"` on login/checkout fields fights password managers and autofill, *lowering* completion and security. Don't disable it except for genuinely one-off, never-reused fields (and even then browsers increasingly ignore it).

## 7.3 Labels, sizing & layout

- Real `<label>` elements (not placeholder-as-label) — placeholders vanish on focus, fail low-vision/contrast, and give nothing to tap. The label is also a bigger tap target that focuses the field.
- Inputs ≥16px font (§4.1), full-width on phones, generous vertical padding (≥44px tall touch target), single-column. Multi-column forms don't fit a phone.
- Show errors **inline, next to the field**, not in a summary at the top the user has to scroll back to.
- **Trap:** placeholder-only "labels" are the most common mobile form a11y failure — once the user types, they've lost the field's name, and screen readers may not announce it.

## 7.4 The keyboard covering the input

When the on-screen keyboard opens, it overlays the bottom of the page (§1.2). A focused input or a fixed submit bar near the bottom can end up *behind* it.
- `<meta name="viewport" content="..., interactive-widget=resizes-content">` 🟡 tells the browser to **shrink the layout viewport** when the keyboard opens, so `100dvh`/bottom-fixed elements reflow above it. (Default is `resizes-visual`, which doesn't.) Support: Chrome 108+, Firefox 132+ — **not Safari/iOS**, so this alone never covers the device that needs it most.
- For precise control, listen to `visualViewport.resize` and translate the action bar by the height delta.
- `el.scrollIntoView({ block: 'center' })` on focus as a fallback to bring the field into view.
- **Trap:** assuming the keyboard "pushes" the page up — by default it overlays. Without `interactive-widget` or a visual-viewport handler, your sticky CTA and the field above the keyboard are simply hidden.

## 7.5 Reduce typing entirely

The best mobile form field is the one the user doesn't type into.
- Native pickers: `type="date"`/`time`/`month`/`color` summon OS pickers (far better than a JS date widget on touch). `<select>` over a custom dropdown for short lists.
- Segmented controls, steppers, and chips beat free text for constrained choices.
- `accept` + `capture` on `type="file"` go straight to camera/photo library.
- **Trap:** a custom JS date picker that doesn't fall back to the native one is almost always worse on mobile — smaller targets, no OS familiarity, more taps. Use the native control unless you have a hard reason.

---

# 8. Performance — the mobile budget

The defining constraint. Your dev machine and iPhone are best-case; the median visitor has a fraction of the CPU and a worse network. Performance *is* mobile UX.

## 8.1 The reality to design against

- **CPU:** a mid-tier Android is ~4–6× slower than a modern laptop at parsing/executing JS. JS cost is paid hardest exactly where it's heaviest.
- **Network:** plan for 4G with high latency and packet loss, plus data caps. Every KB and every round-trip counts.
- **Set a budget:** e.g. ≤170KB compressed JS on the critical path, LCP < 2.5s on 4G, INP < 200ms, CLS < 0.1. A number you can fail is the point.
- **Trap:** "works fine on my phone" is the most expensive sentence in mobile. Test throttled (DevTools "Slow 4G" + 4–6× CPU) and on a real cheap Android.

## 8.2 Core Web Vitals on mobile

- **LCP (Largest Contentful Paint) < 2.5s** — usually the hero image or headline. Preload the LCP image, set `fetchpriority="high"`, don't lazy-load it, and don't gate it behind JS/fonts.
- **INP (Interaction to Next Paint) < 200ms** — replaced FID in 2024. Measures the latency of *every* tap/keypress to the next paint. Long tasks and heavy event handlers are the enemy.
- **CLS (Cumulative Layout Shift) < 0.1** — content jumping as images/ads/fonts load. The fix is reserving space (§8.5, §9.2).
- **Trap:** optimizing only the lab Lighthouse score while field (CrUX/RUM) INP tanks. INP is driven by real interactions Lighthouse doesn't perform — measure with the field data, not just lab.

## 8.3 JavaScript is the most expensive resource

Byte for byte, JS costs more than images: it must be downloaded, parsed, compiled, *and* executed on that slow CPU.
- Ship less: code-split by route, lazy-load below-fold and interaction-triggered components, tree-shake, drop heavy deps (a date lib, a whole UI kit for two components, moment.js).
- Prefer HTML/CSS solutions to JS ones — native `<details>`, CSS scroll-snap (§6.4), CSS animations, `<dialog>` — each removes runtime cost.
- Beware framework hydration: a fully client-rendered SPA pays a large parse+hydrate tax on mobile. Server-render / stream / use islands where possible.
- **Trap:** a 300KB JS bundle to render what is essentially an article. On a slow Android that's seconds of blocked main thread → bad INP, late LCP, and a visibly frozen page during hydration.

## 8.4 Main-thread discipline & INP

- Break long tasks (>50ms) into chunks; yield to the browser (`await scheduler.yield()` 🟡 — Chrome 129+ and Firefox (Aug 2025), **not Safari**; fall back to `setTimeout(…, 0)` / `isInputPending`) so taps get serviced.
- Mark scroll/touch listeners `{ passive: true }` (§2.4).
- Debounce/throttle scroll and resize work; never do layout-reading + writing in a loop (forced reflow).
- Move heavy compute to a Web Worker.
- **Trap:** an expensive `scroll` or `input` handler that runs synchronously on the main thread spikes INP — the page accepts the tap but can't paint the response for hundreds of ms, feeling frozen.

## 8.5 Loading strategy & CLS

- Preload critical assets (LCP image, key font); `preconnect` to required third-party origins.
- Defer non-critical JS (`defer`/`type=module`/`async`); inline critical CSS, load the rest non-render-blocking.
- Reserve space for everything async: `width`/`height` or `aspect-ratio` on images (§9.2), fixed slots for ads/embeds, `size-adjust`/`font-display` to tame font swap.
- **Trap:** a late-loading cookie banner, ad, or "subscribe" bar injected at the top shoves all content down → a large CLS *and* a mis-tap as the user reaches for a button that just moved. Reserve the slot or overlay it.

---

# 9. Images & media

Images are usually the largest bytes on the page and the LCP element — the highest-leverage perf lever on mobile.

## 9.1 Responsive images — `srcset` / `sizes` ✅

Serve a resolution matched to the device so a 360px phone doesn't download a 2000px desktop image.
```html
<img src="img-800.jpg"
     srcset="img-400.jpg 400w, img-800.jpg 800w, img-1600.jpg 1600w"
     sizes="(max-width: 48rem) 100vw, 50vw"
     width="800" height="600" alt="…" loading="lazy" decoding="async">
```
- `srcset` with `w` descriptors + `sizes` lets the browser pick by viewport *and* DPR. `sizes` must describe the image's *rendered* width at each breakpoint — getting it wrong defeats the whole mechanism.
- **Art direction** with `<picture>` + `<source media>` when the *crop* should change (a wide hero on desktop → a tighter portrait crop on mobile), not just the resolution.
- **Trap:** a single `sizes="100vw"` on an image that's actually half-width on desktop makes the browser download a 2× too-large file. And omitting `sizes` entirely makes `srcset` fall back to `100vw` assumptions.

## 9.2 Aspect-ratio to kill CLS ✅

Always reserve the image's box before it loads so surrounding content doesn't jump.
- Set HTML `width`/`height` attributes (the browser computes the ratio) **or** CSS `aspect-ratio: 16 / 9; width: 100%; height: auto`.
- **Trap:** a fluid image with `height: auto` and no `width`/`height` attrs and no `aspect-ratio` collapses to 0 height then snaps to full height on load — a guaranteed CLS hit and the most common layout-shift source on image-heavy pages.

## 9.3 Formats & compression

- **AVIF** 🟢 (best ratio) → **WebP** ✅ (great, universal) → JPEG fallback, via `<picture>` `type` sources. AVIF/WebP routinely cut 30–60% off JPEG at equal quality.
- Don't over-serve DPR: a "3×" image for a tiny thumbnail wastes bytes no one perceives — cap at 2× for most content.
- **Trap:** shipping a 4000px hero PNG. PNG for photos is the bytes killer; reserve it for flat graphics/transparency and use AVIF/WebP for photographs.

## 9.4 Lazy-loading — correctly

- `loading="lazy"` on below-the-fold images; **never** on the LCP/hero image (lazy-loading it delays your largest paint).
- `fetchpriority="high"` on the LCP image, `fetchpriority="low"` on decorative ones (🟢 Baseline newly available Oct 2024; degrades to normal priority where unknown — safe to use now). `loading`/`decoding` are ✅ widely available.
- `decoding="async"` to keep image decode off the main thread.
- **Trap:** blanket `loading="lazy"` on *every* image including the hero — a measured LCP regression. The fold image must load eagerly and at high priority.

## 9.5 Video & background media

- `<video autoplay muted playsinline loop>` — **`playsinline` is mandatory** or iOS forces fullscreen playback. `muted` is required for autoplay to be allowed at all.
- Mobile autoplay video is a data and battery cost; gate it behind `prefers-reduced-motion` (✅) and the `Save-Data` header / Network Information API (Chromium-only — see §12.2), provide a `poster`, and consider not autoplaying on cellular. (Note: `prefers-reduced-data` is **not implemented in any browser** as of 2026 — don't rely on it; §12.1.)
- `background-attachment: fixed` (parallax) is **janky-to-broken on mobile** and disabled on iOS — don't rely on it for parallax; use a proper technique or skip it on touch.
- **Trap:** an autoplaying, unmuted, fullscreen-hijacking hero video that eats 8MB on a metered connection — the worst-case mobile landing experience. Muted, inline, posterted, and data-aware, or not at all.

---

# 10. Motion on mobile

## 10.1 `prefers-reduced-motion` is mandatory ✅

A meaningful share of users enable Reduce Motion (vestibular disorders, battery, preference). Every non-trivial animation needs a reduced alternative — typically a crossfade or instant state.
```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after { animation-duration: .01ms !important; transition-duration: .01ms !important;
                           scroll-behavior: auto !important; }
}
```
- That global reset is a *safety net*, not a substitute — design intentional reduced variants for key moments.
- **Trap:** large parallax, auto-advancing carousels, and big scroll-scrubbed motion with **no** reduced-motion path can literally make people nauseated and is a WCAG 2.3.3 (AAA) / usability failure.

## 10.2 Animate only `transform` & `opacity`

These are GPU-compositable and skip layout/paint; everything else (width, height, top, margin, box-shadow) triggers reflow and stutters on slow mobile GPUs.
- Use `translate`/`scale`/`rotate` for movement; animate a wrapper's `opacity` for fades.
- `will-change: transform` *sparingly* and remove it after — each hint creates a GPU layer that costs memory; over-using it on a memory-limited phone backfires.
- **Trap:** animating `height`/`top`/`box-shadow` in a scroll handler is the classic "why is my mobile scroll janky" — it forces layout on every frame. Animate `transform` and fake the shadow with a pseudo-element opacity fade.

## 10.3 Scroll-driven & touch-aware motion

- Native CSS scroll-driven animations (`animation-timeline: scroll()/view()`) 🟡 run off the main thread — far smoother on mobile than JS scroll listeners, and degrade cleanly where unsupported (Firefox).
- On touch there's no hover to trigger reveals — drive entrance animations off `IntersectionObserver`/`view()` timelines, not hover.
- Respect that mobile scroll has *momentum and velocity* the user controls; scroll-jacking that fights their flick feels broken on touch in a way it doesn't with a mouse wheel.
- **Trap:** porting a desktop scroll-scrub WebGL hero to mobile unchanged — it murders the frame rate and battery. Degrade heavy scroll effects to lighter motion (or none) under `pointer: coarse` and the `Save-Data` signal (§12.2).

---

# 11. PWA & app-like feel

Make the web app installable and native-feeling without the app store. See `app-design-taxonomy.md` for the broader native-app pattern language; this is the web-delivery layer.

## 11.1 Web App Manifest & installability ✅

A `manifest.webmanifest` + a service worker (with a fetch handler) makes the site installable to the home screen.
```json
{ "name": "...", "short_name": "...", "start_url": "/?source=pwa",
  "display": "standalone", "theme_color": "#0b0b0b", "background_color": "#0b0b0b",
  "icons": [{ "src": "/icon-192.png", "sizes": "192x192", "type": "image/png" },
            { "src": "/icon-512.png", "sizes": "512x512", "type": "image/png" },
            { "src": "/maskable.png", "sizes": "512x512", "purpose": "maskable" }] }
```
- `display: standalone` removes browser chrome → app-like. Provide a **maskable** icon or Android crops your icon into a circle awkwardly.
- **Trap:** forgetting the maskable-purpose icon (Android safe-zone crop) and an Apple touch icon (`<link rel="apple-touch-icon">`) — iOS ignores the manifest icon for the home screen.

## 11.2 `theme-color`, status bar & splash

- `<meta name="theme-color">` (and the `media` variant for light/dark) tints the Android status bar / browser UI to match your brand.
- iOS standalone needs `apple-mobile-web-app-capable` / `apple-mobile-web-app-status-bar-style` and generated splash screens; its PWA support is shallower than Android's.
- **Trap:** assuming iOS honors the full manifest. It's partial — test installed behavior on a real iPhone; several manifest fields are silently ignored.

## 11.3 Offline & install UX

- A service worker can cache the shell for instant repeat loads and offline tolerance — even a basic cache-first-for-assets strategy is a big perceived-speed win on flaky mobile networks.
- Use the `beforeinstallprompt` event (Android/Chromium) 🔴 to offer install at a *relevant* moment, not on first paint. Chromium-only — iOS Safari has no equivalent (install is manual via the Share sheet), so never gate installability on it.
- **Trap:** a service worker with a bad cache strategy serves stale assets forever — users get an old broken build with no way to refresh. Version your caches and have an update/skip-waiting path.

## 11.4 App-like transitions

- The View Transitions API 🟢 (same-document) gives native-feeling page/state transitions (shared-element morphs, cross-fades) with a few lines — the cheapest "this feels like an app" upgrade. Baseline newly available since Firefox 144 (~Oct 2025) joined Chrome/Safari. Cross-document (`@view-transition`) 🟡 — Chrome/Safari only, Firefox ignores it (snaps, no animation).
- **Trap:** gating *content* behind the transition — if the animation fails or reduced-motion is on, the content must still be there. Enhance, don't depend.

---

# 12. Capability detection & adaptation

Adapt to what the device *can do*, not to a guessed device class from width.

## 12.1 The capability media queries ✅

- `pointer: coarse|fine`, `hover: hover|none` (§2.2) — input precision and hover availability.
- `prefers-reduced-motion` ✅, `prefers-color-scheme` ✅, `prefers-contrast` 🟢 (all engines now) — user/system preferences, safe to use.
- `prefers-reduced-data` ☠️ — **spec'd but implemented in no browser** as of June 2026 (Chrome shipped then removed it). Use the `Save-Data` header instead (§12.2). `prefers-reduced-transparency` 🔴 — Chromium-only (no Firefox/Safari).
- `dynamic-range: high` / `(color-gamut: p3)` — richer color on modern phone displays (use OKLCH/P3 accents that fall back).
- `resolution`/DPR for asset selection (usually handled by `srcset` instead).
- **Trap:** equating `pointer: coarse` with "small screen." A desktop touchscreen is coarse-pointer at 1440px; a stylus tablet is fine-pointer. Decouple input from size — query each independently.

## 12.2 Network & device signals

- `navigator.connection` (Network Information API) 🔴 (Chromium-Android) exposes `effectiveType` (`'4g'`/`'3g'`/`'slow-2g'`) and `saveData` — gate autoplay, prefetch, and heavy assets when data is constrained.
- The `Save-Data: on` request header (Chromium-only — Chrome/Edge/Opera send it when Data Saver is on) is the practical "user wants light" signal — honor it server-side or via the Network Information API by skipping video, lowering image quality, and deferring prefetch. Its CSS counterpart `prefers-reduced-data` is **unimplemented everywhere** (☠️), so there is no portable client-only equivalent today.
- `navigator.deviceMemory` 🔴 hints at RAM for tuning heavy features.
- **Trap:** treating these as reliable everywhere — they're Chromium-leaning and absent on iOS. Use them to *enhance* (lighten when you detect constraint), never as a hard gate that breaks Safari.

## 12.3 Progressive enhancement as the baseline

Build the core experience in HTML/CSS that works with no JS and on any engine; layer JS-driven and experimental features on top with feature detection (`@supports`, `if ('IntersectionObserver' in window)`).
- **Trap:** an experience that ships *blank* without JS (client-only render) is one failed/slow bundle away from a white screen on a slow mobile connection — the worst failure mode. Render meaningful HTML first.

---

# 13. Accessibility on mobile

Mobile a11y is its own discipline — gestures, target size, zoom, and orientation all differ from desktop. Many items here are also legal requirements (WCAG 2.2).

## 13.1 Don't disable zoom (1.4.4 / 1.4.10)

Covered in §1.1: no `user-scalable=no`, no `maximum-scale`. Users must be able to pinch-zoom to 200%+ and the layout must reflow (no two-axis scrolling) down to a 320px-equivalent width. ☠️ to block it.

## 13.2 Target size (2.5.8 / 2.5.5)

≥24px (AA) / ≥44px (AAA) touch targets with adequate spacing (§2.1). This is now a normative WCAG 2.2 criterion, not just a guideline.

## 13.3 Screen-reader gestures

VoiceOver (iOS) and TalkBack (Android) navigate by swipe and double-tap, reading the accessibility tree.
- Semantic HTML and correct roles/labels are what they read — an icon-only button needs an `aria-label`; a custom control needs proper roles and keyboard/gesture support.
- Manage focus on route changes and when opening sheets/dialogs (`<dialog>` and `inert` help); announce dynamic updates with live regions.
- **Trap:** custom swipe/drag interactions with no accessible alternative are invisible to screen-reader users, who can't perform the gesture. Provide a button-based path to the same action.

## 13.4 Orientation, contrast & real-world conditions

- Don't lock orientation (§1.5) — WCAG 1.3.4.
- Phones are used **outdoors in glare**. Push contrast past the bare 4.5:1 minimum for real legibility in sunlight; thin light-gray text that "looks elegant" on your monitor is unreadable on a bright sidewalk.
- Don't rely on hover-revealed or color-only information (§2.2) — neither survives touch + outdoor + color-blind conditions.
- **Trap:** designing in a dark room at full brightness and shipping low-contrast type. Test outside, at low brightness.

---

# 14. Testing, debugging & QA

## 14.1 Real devices beat emulators

DevTools device mode resizes the viewport but uses your machine's CPU, your mouse (not touch), and a non-Safari engine — it cannot reproduce iOS Safari quirks, real touch behavior, the keyboard, or true performance.
- Keep a **cheap real Android** and an **iPhone** in the test loop. The mid-tier Android is the performance truth-teller.
- **Remote debug:** iOS Safari via macOS Safari Web Inspector (Develop menu, USB); Android Chrome via `chrome://inspect`. These give real DOM/console/network/perf on the actual device.
- **Trap:** signing off on responsive design from desktop DevTools alone. It catches layout, misses touch, keyboard, Safari bugs, and performance entirely.

## 14.2 Throttle everything

Test with DevTools **CPU 4–6× slowdown + "Slow 4G"** network throttling, and ideally a real device on real cellular. Your unthrottled fiber + M-series machine hides every problem your users have.
- Run Lighthouse in **mobile** mode, but treat lab scores as a floor — pair with **field data** (CrUX / RUM) for INP and LCP, which depend on real interactions and networks.
- **Trap:** "Lighthouse says 99" while field INP is 400ms. Lab ≠ field; the lab run never taps your buttons.

## 14.3 The matrix that matters

- Engines: **iOS Safari (WebKit)** — the real constraint, since *every* iOS browser is WebKit underneath — and **Chromium-Android**. Cover both; they diverge most on the topics in this doc (viewport, keyboard, video, PWA).
- States: smallest supported width (~320px), large OS font scale, 200% zoom, landscape, dark mode, reduced-motion, keyboard-open, offline/flaky.
- **Trap:** testing only the latest iPhone in portrait. The failures live at the edges — 320px, big fonts, landscape, keyboard open, slow network.

## 14.4 The recurring iOS Safari quirk list

Worth a dedicated pass because they bite everyone: `100vh` overflow (§1.3); `position: fixed` + keyboard (§7.4); `overflow: hidden` body-lock scroll jump (§6.3); inputs <16px zoom (§4.1); `<video>` needing `playsinline` (§9.5); `background-attachment: fixed` broken (§9.5); `:hover` sticking after tap (tap leaves the hover state applied until you tap elsewhere); `100vw` including the scrollbar; partial PWA/manifest support (§11).
- **Trap:** assuming "works in Chrome Android" means "works on iOS." WebKit is the divergent engine and the one you can't swap out on iOS.

---

# 15. Graceful degradation & capability-tiered experiences

The principle the corpus forgets: **"mobile is redesigned, not shrunk."** Heavy desktop flourishes — WebGL heroes, custom cursors, magnetic buttons, 40-viewport scroll-scrub — are an *enhancement layer*, not the baseline. Build the experience that works on a cheap Android first, then *add* the spectacle for devices that can carry it. Two distinct moves: **degrade** (same layout, lighter effects) and **diverge** (a genuinely different mobile composition).

## 15.1 The capability map — what survives mobile, what you swap

| Desktop move | On mobile | Strategy |
|---|---|---|
| WebGL / Three.js / shader hero | Works, but battery/thermal/memory heavy and dies on low-end GPUs | Swap to a poster image, muted looped `<video>`, CSS gradient-mesh, or a pre-rendered still. Don't even mount the canvas on low tiers. |
| Scroll-triggered reveals (IntersectionObserver / ScrollTrigger / CSS `view()`) | **Work fine** | Keep. Just don't gate them behind hover, and handle the address-bar resize (§15.5). |
| Scroll-scrub pinned sequences (image-sequence, long pins) | Work, but heavy and jump on address-bar resize | Shorten the pin, cut frame count, or convert to a simple reveal. |
| Parallax | `background-attachment: fixed` is broken on iOS (§9.5); transform parallax works but janks on low-end | Reduce magnitude, or drop under `prefers-reduced-motion` / `pointer: coarse`. |
| Custom cursor / cursor-follower / magnetic buttons | **Meaningless** — there is no cursor on touch | Remove entirely under `hover: none`. Not a fallback — a deletion. |
| Hover-reveal menus / tooltips | Invisible or double-tap-trapped (§2.2) | Show by default, or convert to tap-toggle / drawer. |
| Heavy `backdrop-filter`, big blurs, large SVG filters, huge shadows | GPU/compositing cost, dropped frames | Flatten, reduce radius, or replace with a solid/static treatment. |
| Scroll-velocity skew / marquee / inertia effects | Work, but cost frames | Keep listeners `{passive:true}`, cap the magnitude. |
| Autoplay background video | Data + battery cost | Poster + `muted playsinline`, gate on `Save-Data` (§9.5). |

## 15.2 The detection levers — how to switch

- `@media (hover: none) and (pointer: coarse)` — the "this is a touch device" gate for cursor/hover/magnetic effects.
- `@media (prefers-reduced-motion: reduce)` — kill or replace motion.
- **`matchMedia()` in JS to branch which experience you mount** — the key move. Don't instantiate the WebGL scene, then hide it; check first and *never create it* on mobile.
- **`gsap.matchMedia()`** — set up desktop vs mobile timelines with automatic cleanup on breakpoint change, plus a `(prefers-reduced-motion: reduce)` branch. The idiomatic way to ship two motion designs from one codebase.
- Feature-detect the WebGL context before mounting; `Save-Data` / Network Information API / `deviceMemory` (Chromium, §12.2) for a low-power tier.
- **Lazy-mount with dynamic `import()`** — only fetch the heavy module when the capability check passes. This degrades the *bytes*, not just the render (ties §8.3). The single most impactful pattern here.

## 15.3 Degrade vs diverge

- **Degrade** — identical layout, lighter payload: shader→poster, parallax reduced, cursor removed. The default for most marketing pages.
- **Diverge** — a different layout/nav/composition when the desktop *concept* doesn't translate: desktop top-nav → bottom-nav or drawer; multi-column editorial → single narrative column; hover mega-menu → off-canvas drawer; horizontal scroll-gallery → vertical stack or snap-carousel; sprawling grid → reordered linear flow. When the desktop idea is a custom cursor over a big canvas, the mobile version is its own design, not a CSS squeeze.
- **Trap — `display: none` is not degrading.** Hiding a heavy element in CSS still **downloads and often still executes** it: the WebGL bundle parses, the `<video>` fetches, the canvas keeps running its `requestAnimationFrame` loop draining battery for an element nobody sees. To actually degrade you must *not mount/fetch* it — a JS capability guard, a conditional `import()`, or `<picture>`/`<source media>` so the wrong asset is never requested.

## 15.4 Keep content parity — don't ship two truths

The mobile version must carry the same **content and actions**; only the presentation changes.
- **Trap:** Google indexes **mobile-first** — what you hide on mobile is largely what it *sees*. Cutting copy, nav items, or structured content "to simplify mobile" cuts it from your ranking and hurts users who came for it. Reflow and restructure it; don't delete it. Use a drawer/accordion to manage density, not omission.

## 15.5 Scroll-triggered on mobile, specifically

- ScrollTrigger, IntersectionObserver, and CSS scroll-driven animations **all work on touch.** The trigger mechanism is not the bottleneck — the payload behind it is.
- **The real gotcha: the address-bar show/hide.** It fires `resize` and changes the viewport height mid-scroll, so pinned and `vh`-anchored triggers recalculate and *jump*. Fixes: GSAP `ScrollTrigger.config({ ignoreMobileResize: true })`, optionally `ScrollTrigger.normalizeScroll()`, and anchor heights to `svh` not `vh` (§1.3).
- Prefer `IntersectionObserver` or CSS `view()` timelines for simple entrance reveals — cheapest, off-main-thread, and immune to the resize headache.
- Keep `scrub` sequences short and light. A 40-viewport pinned WebGL scrub is a desktop luxury; on mobile, cut the length and the per-frame cost or replace it with a plain reveal.

---

# 16. The mobile anti-pattern catalog

The recurring sins — each maps to a section above. Treat as a pre-ship scan.

- **`100vh` for full-screen sections** → clips under the address bar. Use `svh`/`dvh` (§1.3).
- **`user-scalable=no` / disabled zoom** → WCAG failure. Never (§1.1, §13.1). ☠️
- **Sub-16px inputs** → iOS focus-zoom jump (§4.1).
- **`type="number"` for phones/OTP/cards/ZIP** → strips zeros, blocks symbols (§7.1).
- **Placeholder-as-label** → vanishes on focus, fails a11y (§7.3).
- **Tiny/cramped tap targets** (the 12px modal ×, dense link lists) → mis-taps (§2.1).
- **Hover-dependent menus/actions** → invisible on touch (§2.2).
- **Hidden primary nav behind a hamburger on a small site** → lost discoverability (§5.2).
- **Fixed bottom bar with no `safe-area-inset` / behind the keyboard** → stolen targets, hidden input (§1.4, §5.5, §7.4).
- **Horizontal overflow / sideways wiggle** → an unshrunk flex child or fixed width (§3.4).
- **`overflow: hidden` on body to hide overflow** → masks the bug, breaks sticky (§3.4, §5.3).
- **No `overscroll-behavior: contain` on modals** → scroll chains to the page behind (§6.2).
- **Body not scroll-locked under an open menu** → page scrolls behind the overlay (§6.3).
- **Unsized images / no `aspect-ratio`** → CLS, content jumps (§9.2).
- **Lazy-loading the hero/LCP image** → delayed largest paint (§9.4).
- **Autoplaying, unmuted, non-`playsinline` video** → fullscreen hijack, data burn (§9.5).
- **Heavy JS SPA that ships blank without hydration** → white screen on slow networks, bad INP (§8.3, §12.3).
- **JS scroll-hijack on touch** → jank, broken sticky, battery drain (§6.1).
- **Desktop scroll-scrub/WebGL ported unchanged** → frame-rate and battery collapse (§10.3, §15.1).
- **`display: none` to "disable" a heavy desktop effect** → the asset still downloads/executes; the canvas keeps its rAF loop running. Don't mount/fetch it instead (§15.3).
- **Cutting content/nav on mobile to "simplify"** → mobile-first indexing means you cut it from your ranking too. Reflow, don't delete (§15.4).
- **Custom cursor / magnetic buttons left active on touch** → dead weight, no cursor exists. Remove under `hover: none` (§15.1).
- **No `prefers-reduced-motion` path** → nausea, WCAG failure (§10.1).
- **App-install interstitials / full-page newsletter pop-ups on entry** → Google penalizes intrusive mobile interstitials, and they're rage-inducing on a small screen.
- **Low-contrast "elegant" gray text** → unreadable outdoors (§13.4).
- **"Works on my iPhone 15 over wifi" as the QA bar** → hides every real-world failure (§8.1, §14).
