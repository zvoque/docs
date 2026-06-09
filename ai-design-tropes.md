# The AI Design Tropes

A field guide to the design defaults that AI coding agents reach for unprompted — and the on-purpose alternative for each. This is the inverse of a style taxonomy: not "styles you can choose," but **the single style you get when you choose nothing.** Ask an agent for a landing page with no direction and the output converges on a narrow attractor — the statistical mean of 2021–2025 startup/SaaS sites, Tailwind defaults, and shadcn/ui out of the box. The result is competent, tasteful, and indistinguishable from ten thousand other sites.

Each entry names the trope, shows the tell (including the code signature where there is one), explains **why it emerges** from how the corpus is shaped, and gives the **antidote** — what a designer reaches for on purpose instead. None of these tropes is *wrong*; each is fine when chosen for fit. They are dangerous only as **unexamined defaults** — reached for because they are frequent, not because they are right. Frequency ≠ fit.

Compiled June 2026. The specific tells are dated (they describe the current attractor); the underlying mechanism — regression to the corpus mean — is not.

---

## How to use this doc

- **This is a checklist of suspects, not a ban list.** If you ship an eyebrow label or a 3-column grid because the content genuinely wants it, fine. Ship it because you decided to, not because it appeared on its own.
- **Tropes travel in bundles.** Pull one (the eyebrow kicker) and the rest tag along — pill badge, gradient word, bento grid, FAQ accordion, CTA band. They are a single memorized gestalt, not 30 independent choices. Catching one is often a thread that unravels the whole sweater. See [§12 Meta-patterns](#12-meta-patterns--why-the-tropes-travel-together).
- **The antidote is rarely "the opposite."** The fix for a centered hero is not "left-align everything"; it is "let the content decide." Most antidotes are about deriving the decision from the brand, the era, and the content instead of from the corpus.
- **Feed it to the agent, or read it yourself.** As agent context it names the attractor so the model can be told to avoid it. As a human reference it is a pre-flight scan: read your own draft back and count the tells.

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
- [The antidote, in one page](#the-antidote-in-one-page)

---

# 1. The hero

The single most overfit region of any generated page. The corpus is saturated with one hero, and the agent rebuilds it from muscle memory.

### Centered everything
The default hero is dead-center: eyebrow, then a two-line headline, then one muted subhead sentence, then exactly two buttons (solid primary + ghost/outline secondary). Everything stacked, everything `text-center`, everything on a `max-w-2xl mx-auto`. **Why it emerges:** it is the lowest-risk arrangement and the most common one in the training data — symmetric, balanced, hard to get visibly "wrong." **Antidote:** asymmetry is information. A left-aligned headline against negative space, an editorial split (type one side, a real artifact the other), a single oversized statement with no subhead — any of these carries a point of view that dead-center cannot. Center because the composition wants a focal axis, not because centering is safe.

### The eyebrow / kicker
A tiny uppercase, letter-spaced label floating above the h1 — `FEATURES`, `INTRODUCING`, `WHY US` — often with a leading dot or inside a pill. **Why it emerges:** it is a free hierarchy crutch; it lets the model add a "category" without thinking about whether one is needed. **Antidote:** most heroes do not need a label telling you what section you are in — the headline should do that work. If you need a pre-headline, make it earn its place (a real category, a date, a dateline, a status), not decorative throat-clearing.

### The announcement pill / badge
A `rounded-full` capsule in the hero: "✨ Now with AI", "v2.0 is live", "Backed by [accelerator]", usually with a pulsing dot and a faint border. **Why it emerges:** every launch-stage SaaS site in the corpus has one, so it reads as "what a serious product does." **Antidote:** if there is genuine news, put it where news goes (a banner, a changelog link, a real announcement). A decorative pill with no click target is theater. Kill the pulsing dot entirely.

### Gradient-clip on one word
The headline is plain except for one word in `bg-clip-text text-transparent` with a violet→fuchsia→cyan gradient. **Why it emerges:** it is the single most copy-pasted "expressive type" move in the Tailwind era — one line, instant "designed" feel. **Antidote:** emphasis through weight, size, a genuinely chosen accent color, a different typeface, or a real graphic relationship between words. If you want color on type, choose a color that belongs to the brand, not the default gradient.

### Floating tilted product screenshot
A dashboard screenshot in a fake browser-chrome frame, rotated a few degrees in perspective, with a soft glow underneath. **Why it emerges:** it is the canonical "show the product" solution and it is everywhere. **Antidote:** show the product doing one specific thing, at the moment it matters, full-bleed or cropped into the layout — not a whole UI shrunk and tilted into a generic mockup. Or show the *output* the product creates, not its chrome.

### Aurora / mesh-gradient background
Soft cloudy blobs of violet and blue blurred behind the hero, sometimes drifting. **Why it emerges:** Stripe popularized it, and it became the default way to make a flat hero "not empty." **Antidote:** a background should come from the brand world — a real texture, a photograph, a typographic field, a structural grid, flat confident color. If you reach for a gradient, choose its hues from the palette and give it a reason to be there.

### Cursor-spotlight & edge-faded grid
A radial glow that follows the mouse, over a dot- or line-grid masked to fade at the edges (`mask-image: radial-gradient(...)`). **Why it emerges:** it is a near-universal "tech/AI" background snippet. **Antidote:** if the background needs motion or texture, tie it to content or brand — otherwise leave it flat. The faded-edge grid is now as generic as a drop shadow.

---

# 2. The page skeleton — the section order itself

The most invisible trope is not any single section but their **order**, memorized as one unit. The agent emits the whole sequence because the whole sequence is what the corpus contains.

### The canonical stack
`nav → hero → logo wall → feature grid → stats band → testimonials → pricing → FAQ → final CTA → footer.` Full-width bands stacked vertically, each on a `max-w-7xl` container, each introduced by a centered `max-w-2xl` heading + muted subhead. **Why it emerges:** it is the literal modal page in the training set. **Antidote:** order sections by the argument *this* product needs to make. Some products lead with proof, some with a demo, some with a manifesto, some with price. Cut sections that exist only because the template has them. A page that omits three of these and nails the remaining argument beats the full ten-section ritual.

### The logo wall
"Trusted by" over a row of grayscale customer logos at `opacity-60`, brightening on hover. **Why it emerges:** social-proof convention, copied wholesale. **Antidote:** if the logos are real and impressive, show them at full strength — graying them out signals "we are obligated to include these." If they are not impressive, a single specific number or named customer story does more.

### The stats band
Three or four big numbers with tiny labels, evenly spaced: "99.9% uptime · 2M users · 150 countries." Often with a count-up animation. **Why it emerges:** it is the default "credibility" block. **Antidote:** one number that actually matters, framed in context, beats four round numbers in a row. Make the stat specific enough that a competitor could not copy-paste it.

### The final CTA band
A full-width section near the footer, gradient or dark background, centered "Ready to get started?" + a button or email field. **Why it emerges:** every funnel template ends this way. **Antidote:** a closing moment can be a real argument, a striking image, a single sentence, a genuine question — not a recycled hero with new copy.

---

# 3. The grid problem

The corpus loves the number three, and it loves the equal-column grid. Together they produce the most recognizable AI layout of all.

### The 3-column feature grid
`grid md:grid-cols-3 gap-8`, three cards, each an icon-in-a-rounded-square + a Title-Case feature name + a muted sentence. **Why it emerges:** three columns is the path of least resistance — it fills width, balances, and needs no compositional judgment. **Antidote:** vary the rhythm. A feature can be a full-width row with a real image, a two-up with unequal weight, a stepped sequence, a single hero feature with secondary ones listed below. Let importance set size; not everything deserves an equal third.

### Three of everything
Three pricing tiers (middle one scaled up, "Most Popular"), three testimonials, three steps, three stats. **Why it emerges:** the corpus mean is three, and the agent inherits it. **Antidote:** the count should match reality — two plans if there are two, five steps if there are five. Forcing content into threes distorts it.

### The bento grid
The "sophisticated" escape hatch from the 3-column grid: asymmetric tiles of varied size in a packed mosaic, one big feature tile anchoring it. **Why it emerges:** it became the 2023–24 antidote to the boring grid and is now itself the default "modern" move. **Antidote:** bento is fine when the content genuinely has a size hierarchy and the tiles relate. It is a trope when it is a grab-bag of unrelated boxes arranged for visual novelty. Earn the asymmetry with meaning.

### Centered section intros
Every section opens with `max-w-2xl mx-auto text-center` — a centered heading and one balanced paragraph. **Why it emerges:** it is the safe, symmetric default applied uniformly. **Antidote:** vary alignment and width by section. A left-aligned intro, a wide one, a section with no intro at all — variety in the section openings is half of what makes a page feel composed rather than stamped.

---

# 4. Components

Component-level tells are the easiest to spot because they are nearly always the shadcn/Tailwind default, untouched.

### Icon-in-a-rounded-square
Every feature, every list item, gets a small Lucide icon centered in a `rounded-lg` tinted square. **Why it emerges:** it is the default feature-card anatomy. **Antidote:** icons should clarify, not decorate. Use them where they aid scanning; drop them where the label is self-evident. If you keep them, consider a real custom set over the universal Lucide stroke.

### Checkmark bullet lists
Feature and plan lists always use green checkmarks, never plain bullets or numbers. **Why it emerges:** it is the default "benefits list." **Antidote:** plain text, numbers, or a real typographic list is often cleaner. Reserve the checkmark for genuine yes/no comparisons (this plan has X, that one does not).

### Oversized step numerals
"01 / 02 / 03" set huge and faint behind or beside process steps. **Why it emerges:** common "how it works" treatment. **Antidote:** fine if the sequence matters and the numerals are a deliberate type choice; a trope when they are decorative ghosts. Make them part of the type system or drop them.

### The testimonial card
Avatar circle + name + "@handle · Title at Company" + a quote one size up, in a bordered card, three across. **Why it emerges:** it is the canonical social-proof card. **Antidote:** a single strong quote at display size with real attribution beats three identical cards. Or pull the proof into the narrative instead of quarantining it in a card row.

### Gradient-border & glass cards
Cards with a 1px gradient border (the padding-box trick) or `backdrop-blur bg-white/5 border border-white/10` glass. **Why it emerges:** they are the two default "premium card" treatments of the era. **Antidote:** choose card surface from the chosen aesthetic — a flat bordered card, a solid raised card, a paper card, a borderless card defined by spacing alone. Glass and gradient-border are two options among many, not the surface.

### The sticky blur nav
A top bar that is `sticky top-0 backdrop-blur`, semi-transparent, shrinking or solidifying on scroll. Logo left, links centered, CTA button right. On mobile, a hamburger opening a full-screen overlay. **Why it emerges:** it is the single most common nav in the corpus. **Antidote:** nav position, anchoring, and behavior should suit the site — a static nav, a side nav, a minimal corner nav, a nav that hides until you scroll up. The blur-sticky-shrink combo is a choice, not a given.

---

# 5. Typography

Type is where the lack of a point of view shows most, because the default is *no* typographic personality.

### The neutral grotesk default
Inter, Geist, or a Söhne-clone — a neutral sans for everything. **Why it emerges:** these fonts dominate the corpus and are the framework defaults; they are never *wrong*, so they are always chosen. **Antidote:** type is identity. A serif body, a grotesk paired with a display face, a mono accent, a genuinely expressive headline font — the typeface is one of the cheapest ways to escape the mean. Choose a face that says something about the brand.

### Muted-gray body, huge-bold hero
Body text in `text-gray-500/600`, headings in `text-6xl/7xl font-bold`, and almost nothing in between. **Why it emerges:** it is the default contrast strategy — big bold thing, quiet gray thing. **Antidote:** build a real type scale with meaningful mid-tiers, and question the gray — low-contrast body is both a trope and an accessibility risk. Confident type does not need to whisper the body to make the headline loud.

### Gradient text as the one flourish
The only "expressive" typographic move is the gradient-clipped word (see [§1](#gradient-clip-on-one-word)). **Why it emerges:** it is the one expressive snippet the corpus reliably contains. **Antidote:** real typographic expression — scale contrast, weight contrast, mixing families, leading-trim, optical alignment, a display face used with conviction.

### Auto-balanced everything
`text-balance` / `text-pretty` reflexively on every heading and paragraph. **Why it emerges:** new, widely-recommended, so the agent applies it everywhere. **Antidote:** `text-balance` is genuinely good on headings; it is overkill on body and can fight intentional line breaks. Apply it where ragged lines actually hurt, not as a blanket.

---

# 6. Color

### Neutral base + single accent
Slate/zinc/gray neutrals plus one accent — almost always indigo, violet, or blue. The "Linear/Vercel palette." **Why it emerges:** it is the dominant palette of the corpus's dominant era, and it is impossible to make look bad. **Antidote:** choose a palette with a point of view — a warm neutral, an unexpected accent, a two-color system, a high-chroma brand color used with confidence. Build it in a perceptual space (oklch) so the ramp is even. The safe palette is forgettable precisely because it is safe.

### Dark mode as the premium tell
Defaulting to a dark theme to signal "serious/technical/premium." **Why it emerges:** dev-tool and AI sites skew dark, so dark reads as those categories. **Antidote:** dark is a choice that should suit the content and the reading context, not a shortcut to gravitas. Plenty of premium is bright. Decide based on mood and legibility.

### The three-stop gradient
Violet → fuchsia → cyan, the same three hues, on backgrounds, buttons, and text. **Why it emerges:** it is *the* gradient of the era. **Antidote:** if you use a gradient, derive its stops from the palette and limit where it appears. A two-stop gradient in brand colors reads as intentional; the default tri-stop reads as a template.

### Accent only on the CTA and one word
Color appears solely on buttons and a single highlighted word; everything else is gray. **Why it emerges:** the safe "one accent" rule applied minimally. **Antidote:** color can organize a whole page — section tints, a secondary accent, colored type, colored backgrounds. Hoarding color for the CTA is one strategy, not the only one.

---

# 7. Surface & effects

### Rounded-everything
`rounded-xl` / `rounded-2xl` on every card, button, input, image. Sharp corners never appear. **Why it emerges:** the soft-rounded look is the corpus default and the framework default. **Antidote:** corner radius is an aesthetic decision with a wide range — crisp 0px (Swiss, brutalist, editorial), a single small radius, fully circular, or mixed radii with intent. A page where everything is `2xl` has made no decision.

### Soft shadow + hairline border
Every raised surface gets a soft diffuse shadow plus a faint `border-gray-200` / `border-white/10`. **Why it emerges:** default elevation treatment. **Antidote:** elevation has range — hard offset shadows (neo-brutalism), no shadow with borders alone, layered realistic shadows, color shadows, inner shadows. Pick an elevation language; do not default to the soft blur.

### Glassmorphism by reflex
Frosted `backdrop-blur` panels applied as the default "modern surface." **Why it emerges:** it is a high-frequency, high-"premium-signal" snippet. **Antidote:** glass is a legitimate style (see a style taxonomy) but a poor *default* — it routinely fails text contrast and reads as of-the-moment. Use it when the depth is the point, with a solid scrim behind copy.

### Decorative noise & grain
A grain overlay added "for texture" with no relationship to the rest of the design. **Why it emerges:** a popular one-line way to make flat design feel "crafted." **Antidote:** texture should belong to a material world the brand inhabits. Grain on an otherwise pristine gradient is decoration derived from nothing.

---

# 8. Motion

### Fade-up-on-scroll, everywhere, identically
Every section enters with the same `opacity: 0; translateY(20px)` and the same easing, staggered. **Why it emerges:** it is *the* default scroll animation, one snippet applied globally. **Antidote:** motion should vary with the content's role and have a consistent *physics*, not a consistent *single move*. Some things should snap, some drift, some not animate at all. Uniform fade-up is the motion equivalent of muted-gray body text.

### The whole spring-config monoculture
Framer Motion (or equivalent) on everything, with the same spring/tween config copy-pasted throughout. **Why it emerges:** one library, one example config, applied wholesale. **Antidote:** define a small motion system — two or three intentional curves with assigned meaning — and respect `prefers-reduced-motion`.

### The animation grab-bag
Number count-ups, infinite-scroll logo marquees, headline word-rotators ("Build [apps|teams|dreams]"), hover-lift cards (`translateY(-4px)` + shadow), magnetic buttons, vanilla-tilt cards. **Why it emerges:** each is a popular standalone snippet; the agent assembles several because each is individually common. **Antidote:** pick motion that serves the specific page. Any one of these is fine with a reason; all of them together is a demo reel, not a design.

---

# 9. Imagery & iconography

### Lucide, exclusively
Thin-stroke rounded Lucide icons everywhere. **Why it emerges:** it ships with the default component libraries. **Antidote:** a chosen icon set (heavier, sharper, duotone, custom) is an identity signal. At minimum, decide the icon language rather than inheriting the default stroke.

### The abstract 3D blob
A glossy, blobby gradient 3D render (Spline-style) used as the hero visual when there is no real asset. **Why it emerges:** it is the default "abstract premium graphic." **Antidote:** a real artifact, a photograph, a typographic composition, a diagram of the actual thing — almost anything tied to the product beats a meaning-free 3D blob.

### Emoji as section markers
🚀 ⚡ 🎯 ✨ standing in for icons or punctuating headings. **Why it emerges:** a low-effort way to add color and "personality." **Antidote:** if the brand is playful enough for emoji, commit to a real illustrative voice; if not, drop them. Sprinkled emoji read as filler.

### Generic stock / AI-generated imagery
Interchangeable "diverse team in an office" stock, or obviously AI-generated hero images. **Why it emerges:** it is the default placeholder that never gets replaced. **Antidote:** specific, real imagery — actual product, actual people, actual artifacts. There is an active authenticity backlash against generic and AI imagery; specificity is the differentiator.

---

# 10. Copy & voice

The text has tells too, and they are as overfit as the layout.

### The em-dash hype rhythm
"Not just X — but Y." Em-dashes everywhere, the rule of three in every sentence, relentless parallel structure. **Why it emerges:** it is the cadence of marketing copy in the corpus (and of LLM prose generally). **Antidote:** vary sentence length and structure. Let some sentences be short and flat. Cut two of every three tricolons.

### The adjective set
"Seamlessly," "effortlessly," "powerful yet simple," "lightning-fast," "supercharge," "unlock," "elevate," "transform your workflow." **Why it emerges:** these are the highest-frequency SaaS-marketing tokens. **Antidote:** replace adjectives with specifics. "Effortless" tells the reader nothing; "two clicks, no config file" does the persuading for you.

### Vague abstraction headlines
"The platform for modern teams." "Build better, faster." Hype with zero concrete content. **Why it emerges:** it is the safe, universally-applicable headline — which is exactly why it says nothing. **Antidote:** a headline should be true of *this* product and false of its competitors. If a competitor could paste it onto their own site unchanged, it is a trope.

### Default CTA copy
"Get Started," "Start free," "Book a demo," uniformly. **Why it emerges:** the corpus default. **Antidote:** action copy specific to the offer — what literally happens on click. Specific CTAs convert better and read as human.

---

# 11. The code fingerprint

When the design tells fail you, the source confirms it. These class and pattern signatures are the literal fingerprint of the default attractor.

- `bg-gradient-to-r from-violet-X via-fuchsia-X to-cyan-X` + `bg-clip-text text-transparent` — the gradient headline word.
- `backdrop-blur-md bg-white/5 border border-white/10` — the glass surface.
- `grid md:grid-cols-3 gap-6/8` — the feature grid.
- `max-w-7xl mx-auto px-4` outer + `max-w-2xl mx-auto text-center` section intro — the container rhythm.
- `rounded-2xl shadow-lg` on a near-white/near-black card — the default surface.
- `ring-1 ring-inset` borders; `rounded-full` pills with a leading dot.
- Lucide imports; shadcn/ui components with zero prop overrides or theme changes.
- **Tailwind's default scale only** — no custom tokens, no off-grid spacing, every value on the 4/8px step. **Why it emerges:** the agent uses the defaults because the defaults are what the corpus uses. **Antidote:** a real design system defines its own tokens — a bespoke type scale, intentional spacing (including deliberate off-grid moments), named brand colors in oklch, a chosen radius and elevation language. Custom tokens are the single strongest signal that a human made decisions. The untouched default scale is the strongest signal that no one did.

---

# 12. Meta-patterns — why the tropes travel together

The individual tells matter less than the three forces underneath them. Fix these and the symptoms resolve in bulk.

- **Tropes are a bundle, not a list.** They co-occur in the training data as a single "what a landing page is" gestalt, so the agent emits them together. Eyebrow drags in pill, gradient word, bento, FAQ, CTA band. This is why catching one trope usually means catching ten — and why a single deliberate decision (a real typeface, a committed aesthetic) can displace the whole bundle at once.
- **Symmetry is the comfort zone.** The defaults are overwhelmingly centered, balanced, equal-column, evenly-spaced. The corpus rewards "can't look obviously wrong," and symmetry is the safest way to never look wrong. Deliberate asymmetry and intentional whitespace imbalance are most of what separates composed from stamped.
- **No era, no place, no view.** The default site could belong to any company, anywhere, in any year from roughly 2022 to 2025. It references no design movement, no cultural moment, no specific audience. **Decoration is not derived from content** — there is a glow because glows are common, not because anything in the content called for light. The deepest antidote is to give the design a *position*: an era it is in conversation with, a place it is from, a point of view it argues for. A style taxonomy is the menu of positions; this doc is the list of what happens when you order nothing.
- **"Tasteful" is the ceiling, not the floor.** The attractor maxes out at inoffensive. It is never ugly on purpose, never loud, never austere to the point of risk, never weird. Real design routinely chooses one of those on purpose. If your output could never be called *too much* or *too stark*, it has probably defaulted to the safe middle.

---

## The antidote, in one page

The fix for every entry above reduces to four moves:

1. **Commit to a position.** Pick an aesthetic, an era, a point of view — and let it constrain type, color, motion, and layout top-down. (A design-style taxonomy is the menu.) No position is how you get the default.
2. **Derive decoration from content and brand.** Every glow, gradient, texture, and animation should trace back to something real. If you cannot say why it is there, it is a trope.
3. **Break symmetry on purpose.** Vary alignment, width, column count, and rhythm by section. Let importance set size. Equal thirds and dead-center are decisions, not defaults.
4. **Define your own tokens.** A bespoke type scale, intentional spacing, named brand colors, a chosen radius and elevation and motion language. Custom tokens are the proof a human decided; the untouched framework scale is the proof no one did.

Run a finished page back against this doc and count the tells. Zero is not the goal — *intentional* is. Every trope you keep should be one you chose.
