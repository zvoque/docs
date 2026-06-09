# docs

[![CommitCrimes](https://commitcrimes.dev/badge/zvoque.svg)](https://commitcrimes.dev/u/zvoque)

> Reference playbooks that push AI coding agents past their defaults — toward the frontier and craft features they forget exist, with the support-status honesty to keep it shippable.

## The problem these solve

AI coding agents regress to the mean of their training data. Ask one for a layout and you get flexbox; ask for a card and you get `rounded-2xl shadow-lg` on a gray background. The powerful half of the platform — grid cell-overlap, `:has()`, scroll-driven animations, oklch ramps, variable-font axes, leading-trim — is **rare in the corpus, needs visual iteration to tune, and is craft rather than copy-paste snippet.** Those are exactly the three traits that make a feature get dropped.

These docs are the corrective. Each is written to be read by a person *or* fed to an agent as context, biased toward what gets forgotten — but every frontier feature is tagged with real browser-support status, so it's **frontier with honesty, not novelty for its own sake.** The goal isn't "newest" — it's "the best tool for the job, including the ones the agent wouldn't reach for on its own."

Scope: frontend & design — CSS, motion, design direction, typography, color. Tool-agnostic (Claude Code, Cursor, Copilot, or your own eyes).

## How to use

- **As agent context** — import or `@`-mention the relevant file in your `CLAUDE.md` / `.cursorrules` / system prompt, or paste it inline. The agent stops defaulting to the safe attractor.
- **As a human reference** — read directly. Each entry is: what it is, when to reach for it, the senior idiom, the trap.

## Contents

| Document | The default an agent reaches for → what's here instead |
| --- | --- |
| [`css-playbook.md`](css-playbook.md) | Flexbox + `rounded-xl` + one blurry shadow → the frontier/craft half of CSS: container queries, `:has()`, subgrid, anchor positioning, scroll-driven animations, View Transitions, oklch, masks, SVG filters, leading-trim — each tagged ✅🟢🟡🔴 for support. |
| [`design-style-taxonomy.md`](design-style-taxonomy.md) | Generic "modern SaaS" web look → a field guide to **web/marketing** design direction: styles, type, color, motion, components, layout, design systems, with the trap on each. |
| [`ai-design-tropes.md`](ai-design-tropes.md) | The default attractor an agent emits when given no direction → a named catalog of every AI design trope (hero, section order, the grid, components, type, color, effects, motion, imagery, copy, the code fingerprint), each with the tell and why it emerges. Descriptive, not prescriptive — it names the default so you can see it, and stops there. The inverse of the taxonomy: not the styles you can pick, but the one you get when you pick nothing. |
| [`app-design-taxonomy.md`](app-design-taxonomy.md) | One-size web patterns bolted onto an app → **application** design across native iOS/Android, desktop, PWA, wearable, spatial — platform foundations, navigation, components, behavior. |
| [`gsap-playbook.md`](gsap-playbook.md) | A fade-in and a basic scroll listener → the complete [GSAP](https://gsap.com) 3.13 toolkit: scroll suite, every plugin, framework integration, WebGL, with native-CSS-vs-JS guidance. |

## What qualifies as a doc here

A reference earns a place only if it:

1. **Counters a real, nameable default** — there's a specific thing agents reach for that this pushes past.
2. **Is verified** — checked against primary sources (MDN, specs, official docs), not vibes.
3. **Tags the risk** — frontier features carry honest support/maturity status so nothing ships recklessly.

## Notes

- Living references — dated where trend-sensitive, timeless where foundational.
- Brand-neutral by design: no project- or client-specific content.
