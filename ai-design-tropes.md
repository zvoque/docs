# The AI Design Tropes

A catalog of the design defaults that AI coding agents reach for unprompted. This is the inverse of a style taxonomy: not "styles you can choose," but **the single style you get when you choose nothing.** Ask an agent for a landing page with no direction and the output converges on a narrow attractor — the statistical mean of 2021–2025 startup/SaaS sites, Tailwind defaults, and shadcn/ui out of the box.

This doc is descriptive, not prescriptive — deliberately. It names each trope, shows the tell (including the code signature where there is one), and explains **why it emerges** from how the corpus is shaped. It does **not** tell you what to build instead. Prescribing a fix would just install a new default — "always avoid the eyebrow" becomes its own reflex, and the corpus mean shifts rather than disappears. The purpose here is recognition, not redirection: see the trope clearly and the decision of whether to keep, drop, or replace it stays yours.

None of these tropes is *wrong*. Each is fine when chosen for fit. They are notable only as **unexamined defaults** — reached for because they are frequent, not because they were decided. Frequency ≠ fit.

Compiled June 2026. The specific tells are dated (they describe the current attractor); the underlying mechanism — regression to the corpus mean — is not.

---

## How to use this doc

- **A list of suspects, not a ban list.** Presence of a trope is not a defect. An eyebrow label or a 3-column grid shipped on purpose is a decision; the same thing shipped because it appeared on its own is a default. This doc only helps you tell which is which.
- **Tropes travel in bundles.** Pull one (the eyebrow kicker) and the rest tend to be present too — pill badge, gradient word, bento grid, FAQ accordion, CTA band. They co-occur in the training data as a single memorized gestalt, not 30 independent choices. See [§12 Meta-patterns](#12-meta-patterns--why-the-tropes-travel-together).
- **Feed it to the agent, or read it yourself.** As agent context it names the attractor so the model can be pointed at it. As a human reference it is a pre-flight scan: read your own draft back and count the tells.

---

## Table of contents

- [How to use this doc](#how-to-use-this-doc)
- [1. The hero](#1-the-hero)
- [2. The page skeleton](#2-the-page-skeleton--the-section-order-itself)
- [3. The grid problem](#3-the-grid-problem)
- [4. Components](#4-components)
- [5. Typography](#5-typography)
- [6. Color](#6-color)
- [7. Surface & effects](#7-surface--effects)
- [8. Motion](#8-motion)
- [9. Imagery & iconography](#9-imagery--iconography)
- [10. Copy & voice](#10-copy--voice)
- [11. The code fingerprint](#11-the-code-fingerprint)
- [12. Meta-patterns](#12-meta-patterns--why-the-tropes-travel-together)

---

# 1. The hero

The single most overfit region of any generated page. The corpus is saturated with one hero, and the agent rebuilds it from muscle memory.

### Centered everything
The default hero is dead-center: eyebrow, then a two-line headline, then one muted subhead sentence, then exactly two buttons (solid primary + ghost/outline secondary). Everything stacked, everything `text-center`, everything on a `max-w-2xl mx-auto`. **Why it emerges:** it is the lowest-risk arrangement and the most common one in the training data — symmetric, balanced, hard to get visibly "wrong."

### The eyebrow / kicker
A tiny uppercase, letter-spaced label floating above the h1 — `FEATURES`, `INTRODUCING`, `WHY US` — often with a leading dot or inside a pill. **Why it emerges:** it is a free hierarchy crutch; it lets the model add a "category" label without deciding whether one is needed.

### The announcement pill / badge
A `rounded-full` capsule in the hero: "✨ Now with AI", "v2.0 is live", "Backed by [accelerator]", usually with a pulsing dot and a faint border. **Why it emerges:** nearly every launch-stage SaaS site in the corpus has one, so it reads as "what a serious product does."

### Gradient-clip on one word
The headline is plain except for one word in `bg-clip-text text-transparent` with a violet→fuchsia→cyan gradient. **Why it emerges:** it is the single most copy-pasted "expressive type" move in the Tailwind era — one line, instant "designed" feel.

### Floating tilted product screenshot
A dashboard screenshot in a fake browser-chrome frame, rotated a few degrees in perspective, with a soft glow underneath. **Why it emerges:** it is the canonical "show the product" solution and it is everywhere.

### Aurora / mesh-gradient background
Soft cloudy blobs of violet and blue blurred behind the hero, sometimes drifting. **Why it emerges:** Stripe popularized it, and it became the default way to make a flat hero "not empty."

### Cursor-spotlight & edge-faded grid
A radial glow that follows the mouse, over a dot- or line-grid masked to fade at the edges (`mask-image: radial-gradient(...)`). **Why it emerges:** it is a near-universal "tech/AI" background snippet.

---

# 2. The page skeleton — the section order itself

The most invisible trope is not any single section but their **order**, memorized as one unit. The agent emits the whole sequence because the whole sequence is what the corpus contains.

### The canonical stack
`nav → hero → logo wall → feature grid → stats band → testimonials → pricing → FAQ → final CTA → footer.` Full-width bands stacked vertically, each on a `max-w-7xl` container, each introduced by a centered `max-w-2xl` heading + muted subhead. **Why it emerges:** it is the literal modal page in the training set.

### The logo wall
"Trusted by" over a row of grayscale customer logos at `opacity-60`, brightening on hover. **Why it emerges:** social-proof convention, copied wholesale.

### The stats band
Three or four big numbers with tiny labels, evenly spaced: "99.9% uptime · 2M users · 150 countries." Often with a count-up animation. **Why it emerges:** it is the default "credibility" block.

### The final CTA band
A full-width section near the footer, gradient or dark background, centered "Ready to get started?" + a button or email field. **Why it emerges:** every funnel template ends this way.

---

# 3. The grid problem

The corpus favors the number three and the equal-column grid. Together they produce the most recognizable AI layout of all.

### The 3-column feature grid
`grid md:grid-cols-3 gap-8`, three cards, each an icon-in-a-rounded-square + a Title-Case feature name + a muted sentence. **Why it emerges:** three columns is the path of least resistance — it fills width, balances, and needs no compositional judgment.

### Three of everything
Three pricing tiers (middle one scaled up, "Most Popular"), three testimonials, three steps, three stats. **Why it emerges:** the corpus mean is three, and the agent inherits it regardless of how many items the content actually has.

### The bento grid
The "sophisticated" escape hatch from the 3-column grid: asymmetric tiles of varied size in a packed mosaic, one big feature tile anchoring it. **Why it emerges:** it became the 2023–24 reaction to the boring grid and has since become its own default "modern" move.

### Centered section intros
Every section opens with `max-w-2xl mx-auto text-center` — a centered heading and one balanced paragraph. **Why it emerges:** the safe, symmetric default applied uniformly across every section.

---

# 4. Components

Component-level tells are the easiest to spot because they are nearly always the shadcn/Tailwind default, untouched.

### Icon-in-a-rounded-square
Every feature, every list item, gets a small Lucide icon centered in a `rounded-lg` tinted square. **Why it emerges:** it is the default feature-card anatomy.

### Checkmark bullet lists
Feature and plan lists always use green checkmarks, never plain bullets or numbers. **Why it emerges:** it is the default "benefits list."

### Oversized step numerals
"01 / 02 / 03" set huge and faint behind or beside process steps. **Why it emerges:** the common "how it works" treatment.

### The testimonial card
Avatar circle + name + "@handle · Title at Company" + a quote one size up, in a bordered card, three across. **Why it emerges:** it is the canonical social-proof card.

### Gradient-border & glass cards
Cards with a 1px gradient border (the padding-box trick) or `backdrop-blur bg-white/5 border border-white/10` glass. **Why it emerges:** they are the two default "premium card" treatments of the era.

### The sticky blur nav
A top bar that is `sticky top-0 backdrop-blur`, semi-transparent, shrinking or solidifying on scroll. Logo left, links centered, CTA button right. On mobile, a hamburger opening a full-screen overlay. **Why it emerges:** it is the single most common nav in the corpus.

---

# 5. Typography

Type is where the lack of a point of view shows most, because the default is *no* typographic personality.

### The neutral grotesk default
Inter, Geist, or a Söhne-clone — a neutral sans for everything. **Why it emerges:** these fonts dominate the corpus and are the framework defaults; they are never visibly "wrong," so they are always chosen.

### Muted-gray body, huge-bold hero
Body text in `text-gray-500/600`, headings in `text-6xl/7xl font-bold`, and little in between. **Why it emerges:** it is the default contrast strategy — big bold thing, quiet gray thing — and the low-contrast gray body is an accessibility risk as well as a tell.

### Gradient text as the one flourish
The only "expressive" typographic move on the page is the gradient-clipped word (see [§1](#gradient-clip-on-one-word)). **Why it emerges:** it is the one expressive type snippet the corpus reliably contains.

### Auto-balanced everything
`text-balance` / `text-pretty` applied reflexively to every heading and paragraph. **Why it emerges:** the properties are new and widely recommended, so the agent applies them everywhere rather than where ragged lines actually hurt.

---

# 6. Color

### Neutral base + single accent
Slate/zinc/gray neutrals plus one accent — almost always indigo, violet, or blue. The "Linear/Vercel palette." **Why it emerges:** it is the dominant palette of the corpus's dominant era, and it is very hard to make look bad.

### Dark mode as the premium tell
Defaulting to a dark theme to signal "serious/technical/premium." **Why it emerges:** dev-tool and AI sites skew dark, so dark reads as those categories.

### The three-stop gradient
Violet → fuchsia → cyan, the same three hues, on backgrounds, buttons, and text. **Why it emerges:** it is *the* gradient of the era.

### Accent only on the CTA and one word
Color appears solely on buttons and a single highlighted word; everything else is gray. **Why it emerges:** the safe "one accent" rule applied as minimally as possible.

---

# 7. Surface & effects

### Rounded-everything
`rounded-xl` / `rounded-2xl` on every card, button, input, image. Sharp corners almost never appear. **Why it emerges:** the soft-rounded look is both the corpus default and the framework default.

### Soft shadow + hairline border
Every raised surface gets a soft diffuse shadow plus a faint `border-gray-200` / `border-white/10`. **Why it emerges:** the default elevation treatment.

### Glassmorphism by reflex
Frosted `backdrop-blur` panels applied as the default "modern surface." **Why it emerges:** it is a high-frequency, high-"premium-signal" snippet — and it routinely fails text contrast.

### Decorative noise & grain
A grain overlay added "for texture" with no relationship to the rest of the design. **Why it emerges:** a popular one-line way to make flat design feel "crafted."

---

# 8. Motion

### Fade-up-on-scroll, everywhere, identically
Every section enters with the same `opacity: 0; translateY(20px)` and the same easing, staggered. **Why it emerges:** it is *the* default scroll animation, one snippet applied globally.

### The spring-config monoculture
Framer Motion (or equivalent) on everything, with the same spring/tween config copy-pasted throughout, and `prefers-reduced-motion` usually unhandled. **Why it emerges:** one library, one example config, applied wholesale.

### The animation grab-bag
Number count-ups, infinite-scroll logo marquees, headline word-rotators ("Build [apps|teams|dreams]"), hover-lift cards (`translateY(-4px)` + shadow), magnetic buttons, vanilla-tilt cards. **Why it emerges:** each is a popular standalone snippet, so the agent assembles several because each is individually common.

---

# 9. Imagery & iconography

### Lucide, exclusively
Thin-stroke rounded Lucide icons everywhere. **Why it emerges:** it ships with the default component libraries.

### The abstract 3D blob
A glossy, blobby gradient 3D render (Spline-style) used as the hero visual when there is no real asset. **Why it emerges:** it is the default "abstract premium graphic."

### Emoji as section markers
🚀 ⚡ 🎯 ✨ standing in for icons or punctuating headings. **Why it emerges:** a low-effort way to add color and "personality."

### Generic stock / AI-generated imagery
Interchangeable "diverse team in an office" stock, or obviously AI-generated hero images. **Why it emerges:** it is the default placeholder that never gets replaced; there is an active authenticity backlash against both.

---

# 10. Copy & voice

The text has tells too, and they are as overfit as the layout.

### The em-dash hype rhythm
"Not just X — but Y." Em-dashes everywhere, the rule of three in every sentence, relentless parallel structure. **Why it emerges:** it is the cadence of marketing copy in the corpus, and of LLM prose generally.

### The adjective set
"Seamlessly," "effortlessly," "powerful yet simple," "lightning-fast," "supercharge," "unlock," "elevate," "transform your workflow." **Why it emerges:** these are the highest-frequency SaaS-marketing tokens.

### Vague abstraction headlines
"The platform for modern teams." "Build better, faster." Hype with zero concrete content — true of the product and equally true of every competitor. **Why it emerges:** it is the safe, universally-applicable headline, which is exactly why it says nothing.

### Default CTA copy
"Get Started," "Start free," "Book a demo," uniformly, regardless of what actually happens on click. **Why it emerges:** the corpus default.

---

# 11. The code fingerprint

When the visual tells fail you, the source confirms it. These class and pattern signatures are the literal fingerprint of the default attractor.

- `bg-gradient-to-r from-violet-X via-fuchsia-X to-cyan-X` + `bg-clip-text text-transparent` — the gradient headline word.
- `backdrop-blur-md bg-white/5 border border-white/10` — the glass surface.
- `grid md:grid-cols-3 gap-6/8` — the feature grid.
- `max-w-7xl mx-auto px-4` outer + `max-w-2xl mx-auto text-center` section intro — the container rhythm.
- `rounded-2xl shadow-lg` on a near-white/near-black card — the default surface.
- `ring-1 ring-inset` borders; `rounded-full` pills with a leading dot.
- Lucide imports; shadcn/ui components with zero prop overrides or theme changes.
- **Tailwind's default scale only** — no custom tokens, no off-grid spacing, every value on the 4/8px step. **Why it emerges:** the agent uses the defaults because the defaults are what the corpus uses. The untouched default scale is the clearest signal that no design decisions were made.

---

# 12. Meta-patterns — why the tropes travel together

The individual tells are surface symptoms of three forces underneath.

- **Tropes are a bundle, not a list.** They co-occur in the training data as a single "what a landing page is" gestalt, so the agent emits them together: eyebrow drags in pill, gradient word, bento, FAQ, CTA band. Finding one trope is a reliable predictor that the rest are present.
- **Symmetry is the comfort zone.** The defaults are overwhelmingly centered, balanced, equal-column, evenly-spaced. The corpus rewards "can't look obviously wrong," and symmetry is the safest way to never look wrong, so the attractor is symmetric by construction.
- **No era, no place, no view.** The default site could belong to any company, anywhere, in any year from roughly 2022 to 2025. It references no design movement, no cultural moment, no specific audience. Its decoration is not derived from content — there is a glow because glows are common in the corpus, not because anything in the content called for light.
- **"Tasteful" is the ceiling, not the floor.** The attractor maxes out at inoffensive. It is never ugly on purpose, never loud, never austere to the point of risk, never weird — because none of those survive the "can't look wrong" filter that produced it.
