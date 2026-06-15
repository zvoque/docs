# docs

[![CommitCrimes](https://commitcrimes.dev/badge/zvoque.svg)](https://commitcrimes.dev/u/zvoque)

> Reference playbooks that push AI coding agents past their defaults — toward the frontier and craft features they forget exist, with the support-status honesty to keep it shippable.

## The problem these solve

AI coding agents regress to the mean of their training data. Ask one for a layout and you get flexbox; ask for a card and you get `rounded-2xl shadow-lg` on a gray background. The powerful half of the platform — grid cell-overlap, `:has()`, scroll-driven animations, oklch ramps, variable-font axes, leading-trim — is **rare in the corpus, needs visual iteration to tune, and is craft rather than copy-paste snippet.** Those are exactly the three traits that make a feature get dropped.

These docs are the corrective. Each is written to be read by a person *or* fed to an agent as context, biased toward what gets forgotten — but every frontier feature is tagged with real browser-support status, so it's **frontier with honesty, not novelty for its own sake.** The goal isn't "newest" — it's "the best tool for the job, including the ones the agent wouldn't reach for on its own."

Scope: frontend & design — CSS, shaders/WebGL, motion, design direction, typography, color — plus end-to-end AI-assisted video creation: pre-production, generation, code-rendered & motion graphics, editing, and audio. Tool-agnostic (Claude Code, Cursor, Copilot, Higgsfield, Hyperframes, or your own eyes).

## How to use

- **As agent context** — import or `@`-mention the relevant file in your `CLAUDE.md` / `.cursorrules` / system prompt, or paste it inline. The agent stops defaulting to the safe attractor.
- **As a human reference** — read directly. Each entry is: what it is, when to reach for it, the senior idiom, the trap.

## Contents

| Document | The default an agent reaches for → what's here instead |
| --- | --- |
| [`css-playbook.md`](css-playbook.md) | Flexbox + `rounded-xl` + one blurry shadow → the frontier/craft half of CSS: container queries, `:has()`, subgrid, anchor positioning, scroll-driven animations, View Transitions, oklch, masks, SVG filters, leading-trim — each tagged ✅🟢🟡🔴 for support. |
| [`design-style-taxonomy.md`](design-style-taxonomy.md) | Generic "modern SaaS" web look → a field guide to **web/marketing** design direction: styles, type, color, motion, components, layout, design systems, with the trap on each. |
| [`ai-design-tropes.md`](ai-design-tropes.md) | The default attractor an agent emits when given no direction → a named catalog of every AI design trope (hero, section order, the grid, components, type, color, effects, motion, imagery, copy, the code fingerprint), each with the tell and why it emerges — plus the **keyword-collapse** biases, where a vague descriptor ("modern," "premium," "clean," "bold") resolves to one canned rendering instead of a decision (defined style names like "brutalist" are explicitly exempt). Descriptive, not prescriptive — it names the default so you can see it, and stops there. The inverse of the taxonomy: not the styles you can pick, but the one you get when you pick nothing. |
| [`app-design-taxonomy.md`](app-design-taxonomy.md) | One-size web patterns bolted onto an app → **application** design across native iOS/Android, desktop, PWA, wearable, spatial — platform foundations, navigation, components, behavior. |
| [`video-editing-taxonomy.md`](video-editing-taxonomy.md) | Cut on every word, zoom-transition everything, corporate-explainer pace → the **editor's timeline craft**: editing theory (continuity vs montage, Murch, Kuleshov), the full cut/transition grammar, pacing & ASL, montage forms, editing by genre (advertising, cinematic/trailer, short-form/social, music video, doc, sports, news), time/speed, sound-and-the-cut, **assembling AI-generated footage**, and a default-edit trap index — each with the trap. |
| [`motion-graphics-taxonomy.md`](motion-graphics-taxonomy.md) | Flat blue explainer + generic lower-third + teal-orange on everything → the **visual language of video**: promptable camera grammar & motion presets for AI generation (Higgsfield/Hyperframes/Veo/Kling), motion-graphics styles, titles & broadcast graphics, named color-grading looks, LUT/format/frame-rate/compositing, and AI-era video — written to be fed to AI video tools, with the trap and a **prompt cue** on each. |
| [`video-preproduction-taxonomy.md`](video-preproduction-taxonomy.md) | Skip straight to generating clips with no plan → the **plan layer**: treatments & briefs, story structures (3-act, hero's journey, Save the Cat) and ad structures (AIDA, PAS, hook-retain-payoff), AV scriptwriting + VO timing math, storyboards & shot lists, and sound-off on-screen copy — each with the trap. |
| [`ai-video-generation-playbook.md`](ai-video-generation-playbook.md) | Type a vague prompt into the trending model → a **model-selection & workflow playbook**: which model for which job (Higgsfield/Veo/Kling/Seedance/Hailuo), image-gen for start frames, pricing & credit economics, iterate-cheap-finish-expensive, and the AI-look failure modes. Time-sensitive specs flagged. |
| [`code-rendered-video-playbook.md`](code-rendered-video-playbook.md) | Force a diffusion model to render exact type, brand color & data → the **deterministic lane**: code → frames → mp4 with Remotion, HyperFrames, Motion Canvas & FFmpeg; the in-code animation toolkit; fps/aspect/brand-token/caption/audio-sync concerns; when code beats diffusion (and when it can't). |
| [`video-audio-taxonomy.md`](video-audio-taxonomy.md) | Drop one trending track under everything at a flat level → the **sound half**: voiceover (TTS + direction), music (gen/selection, BPM-to-pace), sound-design layers, the mix (ducking, LUFS), sync, and licensing — each with the trap. |
| [`gsap-playbook.md`](gsap-playbook.md) | A fade-in and a basic scroll listener → the complete [GSAP](https://gsap.com) 3.13 toolkit: scroll suite, every plugin, framework integration, WebGL, with native-CSS-vs-JS guidance. |
| [`mobile-web-playbook.md`](mobile-web-playbook.md) | "Shrink the desktop + one `@media (max-width: 768px)`" → the real mobile-web craft: dynamic viewport units (`dvh`/`svh`), safe-area insets, touch hit-targets, the keyboard/visual-viewport problem, `overscroll-behavior`, the INP performance budget, responsive images, PWA feel, and mobile a11y — each tagged ✅🟢🟡🔴 for support, with the trap on each. |
| [`shaders-playbook.md`](shaders-playbook.md) | Paste a Shadertoy snippet and hope it compiles → the **web-shader craft layer**: the SDF / noise / raymarching toolkit, post-processing & GPGPU, the GLSL ES 3.00 ↔ WGSL cross-reference, and WebGL2-vs-WebGPU-vs-Three/TSL integration — each tagged ✅🟢🟡🔴 for support, plus a "should this even be a shader?" gut-check and the compile-breaking bugs AI ships. |

## What qualifies as a doc here

A reference earns a place only if it:

1. **Counters a real, nameable default** — there's a specific thing agents reach for that this pushes past.
2. **Is verified** — checked against primary sources (MDN, specs, official docs), not vibes.
3. **Tags the risk** — frontier features carry honest support/maturity status so nothing ships recklessly.

## Notes

- Living references — dated where trend-sensitive, timeless where foundational.
- Brand-neutral by design: no project- or client-specific content.
