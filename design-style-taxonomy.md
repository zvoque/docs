# Master Web Design Taxonomy

> Part of a frontier/craft reference set for steering coding agents and designers past the default. Default reach: the generic "modern SaaS" look. Use the **trap** on each entry to avoid the cliché.

A working reference for design direction. Covers: **aesthetic styles/movements** (incl. illustration), **typography styles** (compositional treatments), **color palette styles**, **animation styles**, **components** (navbar, button, card, form, overlay, hero… by axis), **layout & composition**, **imagery & media**, **surface & effects**, **accessibility**, **UX patterns & states**, **page-type anatomy**, **branding & identity**, **data visualization**, **emerging & AI-era interfaces**, **design systems & tokens**, and a **font reference** (Google Fonts grouped by type, last). Each entry explains what it is, where it came from, its defining visual traits, when to reach for it, and the trap to avoid.

Compiled June 2026. Trend-sensitive entries are dated; foundational entries are timeless.

---

## How to use this doc

- **Pick one dominant style, not three.** Most great sites commit to a single aesthetic and let typography, color, and motion reinforce it. Mixing peers (e.g. brutalism + glassmorphism) usually reads as indecision.
- **Style → type → color → motion is a stack.** The aesthetic constrains everything below it. Choose top-down.
- **"Trend" ≠ "right."** A trend tells you what's current, not what fits the brand. Foundational movements (Swiss, Bauhaus, minimalism) age better than internet-aesthetic waves (Frutiger Aero, Y2K).
- **Accessibility is a veto.** Several popular styles (neumorphism, glassmorphism, heavy gradients) routinely fail contrast. If a style can't hit WCAG AA, it loses.

---

## Table of contents

- [How to use this doc](#how-to-use-this-doc)
- [1. Aesthetic styles & movements](#1-aesthetic-styles--movements)
  - [1.1 Foundational movements](#11-foundational-movements-timeless-still-in-active-use)
  - [1.2 Brutalist family](#12-brutalist-family)
  - [1.3 "Morphism" / surface styles](#13-morphism--surface-styles)
  - [1.4 Flat lineage](#14-flat-lineage)
  - [1.5 Layout systems](#15-layout-systems)
  - [1.6 Retro-futurism & nostalgia waves](#16-retro-futurism--nostalgia-waves)
  - [1.7 Illustration & texture-driven styles](#17-illustration--texture-driven-styles)
  - [1.8 Playful, cartoon & character styles](#18-playful-cartoon--character-styles)
  - [1.9 Gamified styles](#19-gamified-styles)
  - [1.10 Mood & cultural aesthetics](#110-mood--cultural-aesthetics)
- [2. Typography styles](#2-typography-styles)
  - [2.1 Scale & presence](#21-scale--presence)
  - [2.2 Arrangement & structure](#22-arrangement--structure)
  - [2.3 Layering & depth](#23-layering--depth)
  - [2.4 Mixing & contrast](#24-mixing--contrast)
  - [2.5 Decoration & expression](#25-decoration--expression)
  - [2.6 Motion-based treatments](#26-motion-based-treatments)
  - [2.7 Editorial system foundations](#27-editorial-system-foundations)
- [3. Color palette styles](#3-color-palette-styles)
  - [3.1 Harmony schemes](#31-harmony-schemes-color-wheel-logic)
  - [3.2 Aesthetic / mood palettes](#32-aesthetic--mood-palettes)
- [4. Animation styles](#4-animation-styles)
  - [4.1 Web / UI motion techniques](#41-web--ui-motion-techniques)
  - [4.2 Motion physics & easing](#42-motion-physics--easing)
  - [4.3 Motion-graphics styles](#43-motion-graphics-styles-video--brand)
  - [4.4 3D / WebGL on the web](#44-3d--webgl-on-the-web)
  - [4.5 Overall motion philosophies](#45-overall-motion-philosophies)
- [Quick decision checklist](#quick-decision-checklist)
- [5. Components](#5-components)
  - [5.1 Navbar — position & anchor](#51-navbar--position--anchor)
  - [5.2 Navbar — shape](#52-navbar--shape)
  - [5.3 Navbar — surface](#53-navbar--surface-inherits-the-aesthetic)
  - [5.4 Navbar — behavior & scroll state](#54-navbar--behavior--scroll-state)
  - [5.5 Navbar — content layout](#55-navbar--content-layout)
  - [5.6 Button — shape](#56-button--shape)
  - [5.7 Button — surface](#57-button--surface-inherits-the-aesthetic)
  - [5.8 Button — state & interaction](#58-button--state--interaction)
  - [5.9 Cards](#59-cards)
  - [5.10 Forms & inputs](#510-forms--inputs)
  - [5.11 Overlays — modals, drawers, popovers, toasts](#511-overlays--modals-drawers-popovers-toasts)
  - [5.12 Tabs, accordion & disclosure](#512-tabs-accordion--disclosure)
  - [5.13 Tables & data display](#513-tables--data-display)
  - [5.14 Hero sections](#514-hero-sections)
  - [5.15 Footers](#515-footers)
  - [5.16 Marketing & content blocks](#516-marketing--content-blocks)
  - [5.17 Small parts](#517-small-parts)
  - [5.18 Search, filter & sort](#518-search-filter--sort)
  - [5.19 Component signature reference](#519-component-signature-reference)
- [6. Layout & composition](#6-layout--composition)
  - [6.1 Grid systems](#61-grid-systems)
  - [6.2 Spacing & rhythm](#62-spacing--rhythm)
  - [6.3 Hierarchy & reading patterns](#63-hierarchy--reading-patterns)
  - [6.4 Container & width strategy](#64-container--width-strategy)
  - [6.5 Responsive & fluid](#65-responsive--fluid)
  - [6.6 Page structure patterns](#66-page-structure-patterns)
- [7. Imagery & media](#7-imagery--media)
  - [7.1 Photography styles](#71-photography-styles)
  - [7.2 Image treatments](#72-image-treatments)
  - [7.3 Iconography](#73-iconography)
  - [7.4 Illustration & 3D (technique)](#74-illustration--3d-technique)
  - [7.5 Video & motion media](#75-video--motion-media)
  - [7.6 Backgrounds, textures & patterns](#76-backgrounds-textures--patterns)
- [8. Surface & effects](#8-surface--effects)
  - [8.1 Elevation & shadow](#81-elevation--shadow)
  - [8.2 Borders, strokes & radius](#82-borders-strokes--radius)
  - [8.3 Blur, glass & backdrop](#83-blur-glass--backdrop)
  - [8.4 Glow, grain & overlays](#84-glow-grain--overlays)
  - [8.5 Fills, gradients, blend modes & masks](#85-fills-gradients-blend-modes--masks)
  - [8.6 Dividers & section transitions](#86-dividers--section-transitions)
- [9. Accessibility — the aesthetic veto](#9-accessibility--the-aesthetic-veto)
  - [9.1 Contrast](#91-contrast)
  - [9.2 Color & meaning](#92-color--meaning)
  - [9.3 Focus](#93-focus)
  - [9.4 Target size & touch ergonomics](#94-target-size--touch-ergonomics)
  - [9.5 Motion](#95-motion)
  - [9.6 Reflow & text spacing](#96-reflow--text-spacing)
  - [9.7 Keyboard](#97-keyboard)
  - [9.8 Semantics & structure](#98-semantics--structure)
  - [9.9 ARIA](#99-aria)
  - [9.10 CSS media features](#910-css-media-features-user-preferences)
  - [9.11 Media, cognition & language](#911-media-cognition--language)
  - [9.12 Tooling](#912-tooling-necessary-not-sufficient)
- [10. UX patterns, states & microcopy](#10-ux-patterns-states--microcopy)
  - [10.1 The full state set](#101-the-full-state-set)
  - [10.2 Feedback mechanisms](#102-feedback-mechanisms)
  - [10.3 UX laws (verified)](#103-ux-laws-verified)
  - [10.4 Core patterns](#104-core-patterns)
  - [10.5 Microcopy & UX writing](#105-microcopy--ux-writing)
  - [10.6 Forms UX](#106-forms-ux)
  - [10.7 Sensory feedback](#107-sensory-feedback)
  - [10.8 Dark patterns — forbidden](#108-dark-patterns--forbidden)
- [11. Page-type anatomy](#11-page-type-anatomy)
  - [11.1 Marketing](#111-marketing)
  - [11.2 Commerce](#112-commerce)
  - [11.3 App / product](#113-app--product)
  - [11.4 System](#114-system)
- [12. Branding & identity](#12-branding--identity)
  - [12.1 Logo types](#121-logo-types)
  - [12.2 Logo construction & usage](#122-logo-construction--usage)
  - [12.3 Favicon & app icons](#123-favicon--app-icons)
  - [12.4 Color in branding](#124-color-in-branding)
  - [12.5 Type in branding](#125-type-in-branding)
  - [12.6 Brand systems](#126-brand-systems)
  - [12.7 Motion & sonic branding](#127-motion--sonic-branding)
  - [12.8 Imagery & iconography as identity](#128-imagery--iconography-as-identity)
- [13. Data visualization](#13-data-visualization)
  - [13.1 Selection framework](#131-selection-framework)
  - [13.2 Chart selection](#132-chart-selection)
  - [13.3 Data color](#133-data-color)
  - [13.4 Dashboard design](#134-dashboard-design)
  - [13.5 Principles](#135-principles)
  - [13.6 Accessibility](#136-accessibility)
- [14. Emerging & AI-era interfaces](#14-emerging--ai-era-interfaces)
  - [14.1 Conversational UI](#141-conversational-ui)
  - [14.2 AI assistant patterns](#142-ai-assistant-patterns)
  - [14.3 Agentic UI](#143-agentic-ui)
  - [14.4 Trust & safety UX](#144-trust--safety-ux)
  - [14.5 Generative & variable design](#145-generative--variable-design)
  - [14.6 Spatial & immersive](#146-spatial--immersive)
  - [14.7 Voice & multimodal](#147-voice--multimodal)
  - [14.8 AI imagery & the authenticity backlash](#148-ai-imagery--the-authenticity-backlash)
- [15. Design systems & tokens](#15-design-systems--tokens)
  - [15.1 Design tokens](#151-design-tokens)
  - [15.2 Theming](#152-theming)
  - [15.3 Atomic design](#153-atomic-design)
  - [15.4 Component API design](#154-component-api-design)
  - [15.5 System architecture](#155-system-architecture)
  - [15.6 Documentation & governance](#156-documentation--governance)
  - [15.7 Notable systems (reference)](#157-notable-systems-reference)
- [16. Google Fonts (grouped by type)](#16-google-fonts-grouped-by-type)
  - [16.1 Neo-grotesque / grotesque sans](#161-neo-grotesque--grotesque-sans-neutral-ui-body)
  - [16.2 Geometric sans](#162-geometric-sans-modern-brand-headline)
  - [16.3 Humanist sans](#163-humanist-sans-warm-readable-body)
  - [16.4 Old-style / transitional serif](#164-old-style--transitional-serif-body-editorial)
  - [16.5 Modern / Didone serif](#165-modern--didone-serif-elegant-fashion-display)
  - [16.6 Slab serif](#166-slab-serif-sturdy-confident-headline)
  - [16.7 Display / expressive](#167-display--expressive-headline-only)
  - [16.8 Monospace](#168-monospace-technical-editorial-accent)
  - [16.9 Handwriting / script](#169-handwriting--script-accent-only)
  - [16.10 Notable variable fonts](#1610-notable-variable-fonts-animatable-axes)

---

# 1. Aesthetic styles & movements

## 1.1 Foundational movements (timeless, still in active use)

### Bauhaus
The German art school (1919–1933) that fused art, craft, and industry. Design language: strict geometry, primary colors (red/yellow/blue) plus black and white, sans-serif type, and a belief that **form follows function**. Everything is reduced to circle, square, triangle. Reach for it when you want intellectual rigor, timelessness, and an "engineered" feel. Trap: can read cold or academic without a warm accent. **Components:** bar — full-bleed square, primary-color block; button — square, solid color, flat.

### Swiss / International Typographic Style
Emerged in Switzerland in the 1940s–50s. The grandparent of modern web layout: mathematical grids, generous whitespace, flush-left/ragged-right type, Helvetica/Akzidenz-Grotesk, photography over illustration, and objectivity over decoration. It prizes clarity and universal legibility. Best for editorial, corporate, and any brand that wants to feel credible and precise. Trap: easy to make boring — needs one bold typographic or color move to come alive. **Components:** bar — full-bleed square, hairline rule, transparent or solid; button — square or text, no radius.

### Art Deco
Peaked in 1920s–30s France. The aesthetic of luxury and the machine age: bold symmetrical lines, stepped/zigzag geometry, sunbursts, rich jewel + gold palettes, high-contrast display type. Signals glamour, heritage, opulence. Good for spirits, fashion, hospitality, premium brands. Trap: heavy ornament fights digital legibility; use as accent, not body. **Components:** bar — centered-logo symmetrical, gold hairline; button — square, thin metallic border, uppercase.

### Constructivism
Russian, post-1917. Propaganda-poster energy: hard diagonals, red/black/cream, photomontage, oversized condensed type set at angles, asymmetry as a weapon. Communicates urgency, movement, ideology. Useful for activist, music, or editorial brands wanting tension. Trap: politically loaded; the angularity tires the eye if overused. **Components:** bar — asymmetric, hard diagonal, red/black; button — angled, bold condensed, no radius.

### Memphis (Postmodern, 1980s)
Founded by Ettore Sottsass and the Memphis Group in Milan, 1981. A deliberate rebellion against "good taste": clashing pastels, black-and-white squiggle/grid patterns, confetti shapes, childlike geometry. Playful, ironic, energetic. Revived constantly for youthful, creative, fun brands. Trap: reads dated or chaotic if literal — modern use should sample its energy, not copy it wholesale. **Components:** bar — clashing color, playful borders; button — color-blocked square or pill, hard shadow.

### Psychedelic (1960s–70s)
Born from counterculture poster art. Warped, melting typography, vibrating complementary colors, kaleidoscopic symmetry, organic swirls. Signals music, festivals, mind-expansion, rebellion. Trap: legibility is intentionally sacrificed — keep it to hero moments.

### Pop Art
1950s–60s (Warhol, Lichtenstein). Mass-culture imagery, Ben-Day halftone dots, comic framing, bold primary blocks, repetition. Loud, accessible, ironic. Good for retail, entertainment, bold campaigns. Trap: can feel kitschy/derivative without a fresh twist.

### Minimalism
Roots in early-20th-c. modernism, mainstream since the 1960s; the dominant digital default for a decade. Strip to essentials — every element must earn its place. Lots of whitespace, limited palette, restrained type, content-first. Signals confidence, clarity, premium calm. Trap: under-designed minimalism is just "empty"; the discipline is hard, not the look. **Components:** bar — thin transparent top, hairline, sticky; button — ghost or text, subtle pill, soft hover-lift.

### Maximalism
The deliberate opposite: more is more. Dense layered compositions, saturated clashing color, multiple typefaces, pattern-on-pattern, ornament everywhere. Signals personality, abundance, creative fearlessness. Surging as a reaction to a decade of flat minimalism. Trap: without an underlying grid it collapses into noise. **Components:** bar — solid or gradient, bold; button — solid clashing color, pill or square.

### Grunge
1990s, derived from punk/zine and music culture. Distressed textures, torn paper, ink splatter, dirty overlays, broken icons, hand-scrawled type. Raw, rebellious, anti-corporate. Trap: dirt-for-dirt's-sake dates fast; works best with a clean structural skeleton underneath.

### Vintage / Retro
An umbrella for era-referencing palettes and type (50s diner, 70s earth tones, 80s neon, 90s rave). Built on nostalgia and authenticity. Choose the specific decade deliberately — each carries different emotional baggage. Trap: pastiche; borrow the era's grammar, don't cosplay it.

---

## 1.2 Brutalist family

### Brutalism
Named from *béton brut* ("raw concrete," 1950s architecture). In web form: raw HTML energy, default system fonts, unstyled or harshly styled elements, monochrome or jarring color, exposed structure, intentional "ugliness." Anti-commercial, honest, attention-grabbing. Popular with artists, devs, fashion. Trap: genuinely hostile to usability — only for audiences who read the rawness as a statement. **Components:** bar — unstyled/system, hard border; button — system, square, no radius.

### Neo-brutalism / Neubrutalism (2022– )
Brutalism domesticated for commercial use. Keeps the high contrast, thick black borders, hard offset drop shadows, and clashing saturated colors, but adds structure, grids, and quirky-but-legible type. Looks confident and "indie-startup." Everywhere on dev-tool and SaaS landing pages. Trap: now a cliché; the thick-border + hard-shadow combo is the new "default startup look." **Components:** bar — thick black border, hard offset shadow, often floating; button — square bordered, offset shadow, press-drop.

### Brutal grunge
A hybrid: brutalist structure plus grunge texture. Punk/DIY feel with raw layout and distressed surfaces. Niche, expressive, music/streetwear adjacent.

### Anti-design
Intentional rejection of design conventions: broken grids, default browser styling, awkward spacing, system fonts, "wrong" choices made on purpose. A critique of polished sameness. Trap: indistinguishable from incompetence unless the intent is unmistakable.

### Cute-alism
A 2024–25 mashup: brutalist boxes and monospace functionality collided with candy neon, glitter, smiley emojis, and rounded buttons. The clash of harsh + adorable is the point. Playful, Gen-Z, chaotic-charming. Trap: very of-the-moment; will date quickly.

---

## 1.3 "Morphism" / surface styles

### Skeuomorphism
Digital elements mimic real-world materials and objects — leather textures, paper, realistic buttons, shadows that imply physical depth. Dominant in early iOS (pre-2013). Intuitive because it borrows real-world affordances. Returning in moderation after a decade of flat. Trap: heavy realism feels dated and bloats assets. **Components:** bar — textured/beveled; button — glossy, beveled, gradient-lit.

### Neumorphism (Soft UI)
A 2020 reimagining of skeuomorphism: elements appear extruded from or pressed into the background using a dual light/dark shadow on a same-color surface. Soft, tactile, calm. Suits wellness/minimal tool UIs. Trap: notoriously fails contrast — borders and states are nearly invisible, an accessibility minefield. **Components:** soft same-color extrude (rare; avoid for primary CTAs — low contrast).

### Glassmorphism
Frosted-glass panels: background blur, transparency, subtle borders, layered depth. Popularized by Apple (Big Sur) and Windows Acrylic. Feels modern, light, premium. Trap: text-over-blur contrast is fragile; needs a solid scrim behind copy. **Components:** bar — floating glass pill, transparent→solid on scroll; button — glass, soft radius, shine on hover.

### Glassmorphism 2.0 / Liquid Glass (2025)
Apple's iOS 26 / macOS Tahoe evolution. Glass becomes a functional, dynamic layer — refraction, real-time depth, gradients, and motion-reactive translucency rather than a static blur. The most current "premium OS" look. Trap: heavy GPU cost and the same contrast risks, amplified. **Components:** bar — dynamic refractive glass, transparent→solid; button — translucent, motion-reactive (watch GPU + contrast).

### Claymorphism
Successor to neumorphism: puffy, inflated 3D shapes with rounded corners, a double inner shadow plus an outer shadow, and an optional inner glow. Buttons look like jelly or clay and deform/bounce on press. Friendly, tangible, works on any background color (its advantage over neumorphism). Great for playful apps. Trap: too soft for serious/data-dense products. **Components:** bar — puffy floating rounded card; button — puffy claymorphic, bounce on press.

### Aurora / mesh / deep-glow gradients
Multi-point gradients that blend several hues into soft, cloudy fields (Stripe-style), now pushed into "deep glow" — intense light blooms and layered neon. Adds warmth, motion, and depth to otherwise flat layouts. Trap: gradients behind text kill legibility; reserve for backgrounds and accents.

---

## 1.4 Flat lineage

### Flat design
Since ~2013 (Microsoft Metro, then iOS 7). Removes all depth cues — no shadows, gradients, or texture. Pure color, simple shapes, clean sans type, icon-driven. Fast, scalable, legible. Still the SaaS/app workhorse. Trap: removing affordances can hurt usability (what's clickable?). **Components:** bar — solid, sticky; button — solid or soft-tinted, rounded-rect, hover-shadow.

### Flat 2.0 / Semi-flat
Flat design that reintroduces *just enough* depth — subtle long shadows, faint gradients, slight layering — to restore affordance without going skeuomorphic. The pragmatic middle ground most modern UIs actually use.

### Material Design
Google's system (2014– ). Treats UI as layers of physical "paper" with elevation, consistent shadows, deliberate motion, and a strict component/spacing spec. Less an aesthetic than a comprehensive, accessible design system. Best when you want proven patterns and Android-native feel. Trap: can look generically "Google" without customization. **Components:** bar — solid elevated, shrink-on-scroll; button — filled/tonal, rounded-rect, ripple press.

### Corporate Memphis (a.k.a. Alegria / "Big Tech" illustration)
The flat illustration style of the late-2010s tech boom: figures with bendy, disproportionate limbs, tiny heads, non-representational skin tones (blue/purple), against flat color. Friendly, inoffensive, infinitely scalable — which is exactly why it became a punchline for soulless sameness. Trap: instantly signals "generic startup"; avoid unless subverted.

---

## 1.5 Layout systems

### Bento grid
Named for the compartmentalized Japanese lunchbox. Content is organized into a modular grid of asymmetric boxed tiles of varying sizes. Popularized by Apple keynotes and adopted by Samsung, Microsoft, Google. Excellent for feature showcases and dashboards — scannable, flexible, responsive. Dominant 2023–26. Trap: becoming overused; needs hierarchy so it isn't just "boxes of equal weight." **Components:** bar — full-bleed or floating rounded-rect; button — rounded-rect, soft-tinted.

### Asymmetric / broken grid
Deliberately off-balance layouts — overlapping elements, uneven columns, content breaking the grid lines. Creates tension, energy, editorial sophistication. Trap: requires real craft; sloppy asymmetry just looks broken.

### Neo-minimalism
Minimalism softened with warmth and texture — muted organic color, subtle grain, a tactile touch — so it feels human rather than clinical. The current evolution of "clean." 

### Resonant Stark (2025–26)
A reaction to maximalist fatigue: strip the page to essentials, then layer in subtle emotional detail — ultra-thin fonts, soft gradients, abundant whitespace, micro-moments of delight. Quiet but not empty.

### Dual aesthetics
Strategically merges minimal structure with maximalist expression — a clean, orderly grid rendered in bold clashing colors, or novel type set in generous whitespace. Lets a brand feel both credible and creative.

---

## 1.6 Retro-futurism & nostalgia waves

### Y2K revival
The early-2000s dot-com optimism: chrome and metallic textures, pixelation, scanlines, neon pink-purple-cyan gradients, star icons, monospace, blobby shapes, "more is more." Driven by Gen-Z nostalgia for an era they didn't live through. Trap: very faddish and visually loud. **Components:** bar — chrome/gradient floating pill; button — glossy chrome, inflated, shine.

### Y3K / Hyperfuturism
Y2K cranked into the far future: sleek, experimental, surreal "advanced material" looks, liquid metal, otherworldly UI. Speculative and high-concept.

### Frutiger Aero
The late-2000s glossy-optimism look (Windows Vista/Aero era): wet-glass reflections, bubbles, lens flares, nature imagery (water, grass, sky), soft gradients, eco-techno positivity. Currently in heavy nostalgic revival. Trap: dates to a very specific 2007–2012 window. **Components:** bar — glossy glass, soft gradient; button — glossy skeuomorphic, beveled.

### Vaporwave
Early-2010s internet aesthetic and music genre. Greek statues, glitch, VHS artifacts, pastel pink/cyan, Japanese text, retro computing imagery, ironic consumer-capitalism critique. Niche but influential — seeded both Y2K and Frutiger Aero revivals.

### Synthwave / Outrun
80s sci-fi nostalgia: neon grids receding to a horizon, sunset gradients, chrome type, retro-future cityscapes, *Tron*/*Miami Vice* energy. Big in music, gaming, crypto. Trap: heavily associated with a specific subculture. **Components:** bar — dark transparent, neon hairline; button — outline neon-glow, dark fill.

### Retrofuturism
Broad umbrella: any past era's vision of the future. Fuses vintage optimism with modern execution — neon, chrome, pixel art, bold gradients from sci-fi and arcade culture.

### Cyberpunk
"High-tech, low-life" since the 1980s (*Blade Runner*, *Neuromancer*). Gritty neon-drenched dystopian cities, glitch, dense HUD overlays, dark backgrounds with electric accents. Signals edge, tech, rebellion. Trap: visual density hurts usability; commit to dark-mode legibility. **Components:** bar — dark transparent, neon hairline, HUD overlays; button — outline neon-glow, dark fill.

### Steampunk / Dieselpunk / Atompunk
Alternate-history retro-futures: Steampunk = Victorian brass, gears, leather; Dieselpunk = interwar industrial; Atompunk = 1950s atomic-age optimism. Rich, narrative, niche. Trap: ornament-heavy; better for theming than for conversion-focused product UI.

### Risograph
Mimics the riso printing process: grainy texture, limited vivid spot inks, slight misregistration, organic imperfection. Artsy, tactile, indie-editorial. Trap: the "flaw" aesthetic can look like a rendering bug if not deliberate.

### Holographic / iridescent
Shifting cyan-magenta-green sheens that imply movement and high-tech materiality. Futuristic, premium-playful. Trap: hard to reproduce in print/across screens; mostly a digital accent.

### Acid graphics
Rave/club-flyer energy: corrosive neon, chrome 3D type, distortion, glitch, melting forms, Y2K-adjacent. Loud, youthful, music-led.

---

## 1.7 Illustration & texture-driven styles

### Abstract 3D
Sculptural, experimental 3D forms — blobs, ribbons, geometric installations rendered digitally. Adds depth and a designed, premium feel. Trap: render-heavy; can feel generic ("default Spline scene").

### 3D realism / hyperreal
Photoreal textures, physics-based lighting, cinematic depth. Lifelike and memorable. Trap: expensive to produce and to load.

### Collage / cut-paper
Mixed-media assembly — photography, scanned texture, torn paper, type fragments layered together. Roots in Constructivism and Dada. Tactile, editorial, human. Trap: needs compositional skill to avoid looking like a junk drawer.

### Organic / blobby shapes
Fluid, soft, irregular forms used as backgrounds, dividers, and accents. Friendly, modern, calming counter to hard grids.

---

## 1.8 Playful, cartoon & character styles

### Cartoon / illustrative
Flat or shaded character-driven scenes with expressive personality. Warm, approachable, brand-humanizing. Good for consumer apps, education, fintech-softening. Trap: style must be custom — stock cartoon = forgettable.

### Mascot-driven
A recurring brand character guides the experience (Duolingo's owl is the canonical example). Mascots reportedly lift engagement meaningfully by adding emotional continuity and personality. Trap: a weak or off-brand mascot is worse than none.

### Doodle
Hand-sketched, quirky, often animated squiggles and marks. Casual, fun, low-pressure. Great for playful or creative brands. Trap: can undercut perceived seriousness/premium-ness.

### Kawaii / cute
Japanese "cute" culture: rounded forms, big eyes, smiley faces, soft pastels, tiny characters. Disarming and friendly. Trap: skews young; hard to pair with authority.

### Sticker style
Die-cut white-outline shapes with drop shadows, layered like physical stickers. Playful, collectible, tactile.

### Comic / pop
Panels, speech bubbles, halftone dots, bold outlines. Energetic storytelling. Trap: niche; reads as "comic brand."

### Hand-drawn / sketch
Pencil, ink, imperfect linework. Signals craft, authenticity, humanity — the antidote to AI-perfect polish.

### Illustration sub-styles (technique-level)
- **Flat illustration** — solid color, no depth; fast and scalable.
- **Gradient illustration** — soft blended fills for richness.
- **Isometric** — objects drawn on 30° axes, giving 3D depth in 2D without perspective distortion; ideal for product/infographic/process visuals.
- **Line art / outline** — stroke-only; perfect for self-drawing scroll animations and wordmarks.
- **3D illustration** — rendered depth, from realistic to stylized.
- **Low-poly** — faceted, angular 3D built from visible polygons; retro-geometric.
- **Spot illustration** — small accent illustrations punctuating text/UI.

---

## 1.9 Gamified styles

### Gamified UI
Borrows game mechanics to drive engagement: progress bars, levels, XP, badges, achievements, streaks. Turns passive flows into active ones. Now an expectation, not a novelty, in many consumer products. Trap: hollow points/badges feel manipulative if they don't map to real value.

### Reward mechanics
Spin-to-win wheels, scratch cards, quizzes, mystery rewards — used at conversion moments (signup, exit-intent, seasonal). Boost opt-in rates. Trap: gimmicky if overused; can cheapen a premium brand.

### Quest / onboarding journeys
Staged, unlockable onboarding that frames setup as a journey with milestones. Improves completion. Trap: don't gate genuinely needed features behind "quests."

### Leaderboard / social validation
Ranks, trophies, public progress. Powerful for competitive/community products. Trap: demotivating for users at the bottom; offer non-comparative framings too.

---

## 1.10 Mood & cultural aesthetics

### Cottagecore
Romanticized rural/pastoral life: soft natural palettes, florals, handmade craft textures, warmth and escapism. Surged 2019–22. Suits lifestyle, food, craft, wellness brands.

### Dark academia
Classical-scholar mood: muted earth tones, gothic architecture, vintage serif type, candlelit melancholy, intellectualism. Suits books, education, heritage, moody editorial.

### Earthy / organic / eco
Muted naturals, recycled-paper textures, biophilic greens. Signals sustainability and authenticity. Trap: greenwashing optics if the substance isn't there.

### Minimal / quiet luxury
Restrained premium: tiny logos, generous space, muted neutrals, impeccable type, no loud branding. Confidence through reduction. Suits high-end fashion, finance, design. **Components:** bar — centered-logo split or minimal, transparent→solid; button — outline or text, square/squircle, border-draw.

---

# 2. Typography styles

These are **compositional treatments** — how type is sized, arranged, layered, and expressed on the page — independent of *which* typeface is used. (Typeface categories and specific font names live in the final section, [§16 Google Fonts](#16-google-fonts-grouped-by-type).) Pick one or two dominant treatments per layout; stacking five expressive moves on one screen reads as chaos.

## 2.1 Scale & presence

### Mega-type / oversized display
Type set so large it becomes the layout itself — a headline that fills most or all of a section, sometimes so big it crops at the viewport edges and requires scrolling to read in full. The words *are* the visual; no image needed. Maximum confidence and brand voice. Trap: only works with a short, strong phrase and a typeface that holds up huge; long copy at this scale is unreadable.

### Typographic hero
Using type — not photography or illustration — as the primary hero. The opening screen leads with a bold statement set large. Fast-loading, brand-forward, and increasingly the default for modern marketing sites. Trap: needs strong copy and hierarchy or it feels empty.

### Dramatic scale contrast
Extreme jumps between sizes on the same screen — a giant headline next to tiny supporting text. The "burger" stack of big + small creates tension and intrigue and guides the eye instantly. Trap: the jump must be *decisive* (e.g. 8×, not 1.5×) or it just looks inconsistent.

### Full-bleed type
Type that runs edge to edge, bleeding off the canvas. Implies the words continue beyond the frame — immersive and energetic. Common with mega-type. Trap: cropping must look intentional, never accidental.

## 2.2 Arrangement & structure

### Stacked type
Lines stacked tightly on top of each other, often with reduced leading so the block reads as one dense mass. Can mix sizes/weights per line ("burger stacking"). Punchy, poster-like, graphic. Trap: tight leading can collide ascenders/descenders — tune line-height per case.

### Centered stack
Stacked lines centered for a symmetrical, monument-like feel. Calm, classic, ceremonial. Trap: centered ragged blocks are harder to scan than left-aligned; keep them short.

### Justified block / type as a rectangle
Text justified on both edges so the paragraph forms a solid, tidy rectangle — magazine-column discipline. Structured and editorial. Trap: justification creates "rivers" of white space and is generally discouraged on the web without hyphenation; safest in print or wide, well-hyphenated columns.

### Multi-column / editorial grid
Content flowed into two or more columns on a baseline grid, like a newspaper or magazine. Signals depth, authority, long-form quality. Trap: too many narrow columns hurt readability on small screens — collapse responsively.

### Asymmetric type layout
Type placed off-center, off-grid, or unevenly weighted across the canvas for energy and sophistication. Trap: requires genuine compositional skill; sloppy asymmetry just looks broken.

### Vertical / rotated type
Text rotated 90° or set to run vertically. Editorial, fashion, and architectural feel; great for sidebars, spines, and labels. Trap: rotated reading is effortful — keep it to short accents, not body.

### Diagonal / angled type
Type set on a slant for dynamism and movement (Constructivist DNA). Bold and kinetic. Trap: angles fight legibility and grid order; use as a deliberate accent.

### Type on a path / circular / radial
Letters following a curve, circle, or arbitrary path — badges, seals, spirals, orbiting words. Decorative and distinctive. Trap: curved baselines distort letter spacing; reserve for short strings.

### Type wrap (around image or shape)
Body text flowing around the contour of an image or object. Classic magazine integration of word and picture. Trap: ragged wrap edges can create awkward gaps; needs careful tuning.

### Constrained-to-shape / shaped text
Type forced to fill or conform to a shape — a circle, a silhouette, a country outline, a product form. The paragraph *becomes* the shape. Striking and editorial. Trap: legibility drops fast; works best as a graphic centerpiece, not for reading.

### Ragged vs. justified alignment
The baseline decision: flush-left/ragged-right (most readable on screen), flush-right (accent), centered (short blocks), or justified (formal columns). Each sets a different rhythm. Trap: flush-right and centered tire the eye over long passages.

## 2.3 Layering & depth

### Overlapping type
Words or letters that overlap each other or other elements, creating depth and intentional collision. Modern, expressive, layered. Trap: overlap must preserve enough contrast to stay readable.

### Type-over/behind image (sandwich)
Type layered between or across imagery — partly behind a subject, partly in front — to weave word and picture into one plane. Cinematic and immersive. Trap: needs a scrim or careful placement so text never disappears into the photo.

### Outlined / stroke-only type
Letters drawn as outlines with no fill. Light, airy, architectural; pairs well with a solid counterpart. Trap: thin outlines vanish at small sizes and on busy backgrounds.

### Knockout / reverse type
Text cut out of a solid shape so the background shows through the letterforms (or light text on a dark block). Bold and high-contrast. Trap: thin or small knockout text loses legibility.

### Type masking image (image-filled type)
An image or video clipped *inside* the letterforms, so the type becomes a window onto a picture. Rich, premium, attention-grabbing. Trap: choose imagery with enough contrast inside the letter shapes, and use a heavy display weight so there's room for the image to read.

### Extruded / layered-shadow type
3D extrusion or stacked offset shadows giving letters physical depth. Retro, poster-like, playful or chunky. Trap: can date quickly; easy to overdo.

### Repetition / echo type
A word or phrase repeated — tiled, fading, or echoing across the canvas — for rhythm, emphasis, or texture. Trap: repetition without variation becomes monotonous wallpaper.

### Background / ghost / watermark type
Oversized, low-opacity type sitting behind content as texture or a section label. Adds depth and brand presence without competing with foreground copy. Trap: keep opacity low enough that it never fights real content.

## 2.4 Mixing & contrast

### Mixed weights
Combining light and heavy weights of the same family in one headline or block to build hierarchy and emphasis without changing typefaces. Clean and systematic. The safest expressive move.

### Mixed typefaces
Pairing two or three typefaces (e.g. grotesque sans + editorial serif + mono) for contrast and personality. Trap: more than three voices fragments the design; pair by deliberate contrast, not similarity.

### Case contrast / mixed case
Playing ALL-CAPS against lowercase, or small-caps against full caps, within a composition. Sets tone — caps shout, lowercase whispers. Trap: long all-caps passages are hard to read.

### Inline size mixing
Changing size mid-line or mid-sentence to spotlight key words. Expressive and editorial. Trap: too many size shifts per line look erratic.

### Highlighted / marked text
Words wrapped in highlight blocks, underlines, circles, or marker strokes to draw attention. Friendly, annotative, human. Trap: overuse dilutes the emphasis.

### Color-blocked words
Individual words or lines set in different colors or on color blocks for rhythm and emphasis. Bold and graphic. Trap: maintain contrast and a limited palette.

## 2.5 Decoration & expression

### Expressive / decorative type
Type used as ornament and personality — flourishes, ligatures, swashes, decorative display faces. Rich and characterful. Trap: decoration competes with reading; isolate to headlines/marks.

### Type as illustration / pictorial
Letterforms built from or transformed into imagery (a letter made of leaves, a word shaped like its meaning). Clever and memorable. Trap: cleverness can obscure the word.

### Distorted / warped / liquified type
Letters stretched, melted, bent, or fluid-simulated for an experimental, acid, or surreal feel. Very current. Trap: legibility is sacrificed by design — hero moments only.

### Glitch type
Digitally corrupted letterforms — RGB split, datamosh, scanlines. Edgy, cyber, music-led. Trap: niche and faddish.

### Chrome / 3D / inflated display
Glossy metallic, rendered 3D, or balloon-inflated letterforms (Y2K and bubble revivals). Playful and bold. Trap: heavy, era-specific, can feel gimmicky.

### Textured / filled type
Letters filled with photographic texture, grain, gradients, or pattern. Tactile and rich. Trap: busy fills hurt legibility at small sizes.

### Annotation marks
Underlines, strike-throughs, circles, arrows, and hand-marks layered onto type for a human, editorial, "marked-up" feel.

### Drop caps & initial caps
An oversized opening letter starting a paragraph or article — classic editorial signal of long-form quality and a strong entry point for the eye.

### Pull quotes & standfirsts
Enlarged extracted quotes (pull quotes) and intro paragraphs set apart (standfirst/lede) to break up text and create scanning anchors. Core editorial hierarchy tools.

## 2.6 Motion-based treatments

### Kinetic typography
Type animated to move, scale, rotate, or sequence — built for attention and rhythm. Spans subtle hover shifts to full motion-graphic sequences.

### Liquid / morphing type
Letters that flow, melt, or morph between words; fluid and organic. Mesmerizing in loops.

### Variable-axis animation
Animating a variable font's weight/width/slant axes live — type that breathes, thickens, or stretches in response to scroll, cursor, or time. Smooth and lightweight (one font file).

### Marquee / scrolling type
Looping horizontal (or vertical) text bands. Editorial, energetic, good for announcements and logo/word tickers.

### Reveal / mask-in type
Text that wipes, masks, or staggers into view on scroll or load. The default "entrance" treatment for modern hero copy.

## 2.7 Editorial system foundations

### Typographic hierarchy
The deliberate ordering of content by importance using size, weight, color, spacing, and position so the eye knows where to go first. The backbone of every layout.

### Type scale / modular scale
A mathematical ratio (e.g. 1.25× per step) generating harmonious size steps from caption to display. Brings consistency and rhythm across a system.

### Eyebrow / kicker
A small label above a headline giving category or context. Cheap, effective orientation.

### Caption & footnote styling
Small, often muted or italic type for image credits, asides, and fine print — the quiet bottom of the hierarchy.

---

# 3. Color palette styles

## 3.1 Harmony schemes (color-wheel logic)

- **Monochromatic** — one hue across many tints (add white), tones (add gray), and shades (add black). Cohesive, calm, sophisticated; risk of flatness.
- **Analogous** — 3–5 hues adjacent on the wheel. Smooth, harmonious, easy on the eye; low contrast so pick clear value steps.
- **Complementary** — two opposite hues. Maximum contrast and energy; tiring in large doses — use one as accent.
- **Split-complementary** — a base plus the two hues flanking its complement. High contrast with less tension than pure complementary.
- **Triadic** — three evenly spaced hues. Vibrant and balanced; let one dominate.
- **Tetradic / square** — four hues in two complementary pairs. Rich but hard to balance; needs a clear lead color.

## 3.2 Aesthetic / mood palettes

- **Pastel** — low saturation, high lightness. Soft, gentle, friendly; can feel weak without a darker anchor.
- **Neon / fluorescent** — hyper-bright, glowing hues. Energetic, screen-native, attention-grabbing; harsh for body backgrounds.
- **Earth tones** — muted, medium-saturation naturals (clay, olive, ochre). Grounded, organic, warm.
- **Jewel tones** — deep, rich, saturated (emerald, sapphire, ruby, amethyst). Luxurious and dramatic.
- **Muted / desaturated** — dusty, grayed-down hues. Calm, mature, editorial.
- **Vibrant / saturated** — bold, pure color at full strength. Maximal, youthful, confident.
- **Black & white / monochrome** — pure contrast, no hue. Timeless, editorial, distraction-free.
- **Grayscale + single accent** — neutral base with one pop color directing attention.
- **Duotone** — a two-color gradient mapped onto a photo's shadows/highlights. Bold, branded, cohesive.
- **Tritone** — three-color version of duotone for more tonal range.
- **Gradient / mesh** — multi-stop color blends, from subtle tone-on-tone to bold high-contrast and aurora meshes. Adds depth and motion.
- **Iridescent / holographic** — shifting, light-reactive sheens. Futuristic, premium-playful.
- **High-contrast / clash** — intentionally jarring pairings (neo-brutalist). Loud and memorable.
- **Retro / vintage** — era-specific palettes (70s mustard/avocado, 80s neon, 90s teal/purple).
- **Y2K** — pink-purple-cyan plus chrome/silver.
- **Dark mode** — dark surfaces with carefully tuned accents and glow; now a baseline expectation, not a style. Requires its own contrast tuning (avoid pure black + pure white).
- **Warm-dominant / cool-dominant** — palette led by temperature to set mood (warm = inviting/energetic, cool = calm/credible).
- **Nature / biophilic** — greens, water-blues, sky tones, organic neutrals.

---

# 4. Animation styles

## 4.1 Web / UI motion techniques
- **Micro-interactions** — tiny feedback animations (button press, toggle flip, like burst) that confirm actions and add polish. The highest-ROI motion category.
- **Hover effects** — instant visual cues on cursor-over; aim for ~200ms transitions.
- **Scroll-triggered reveals** — elements fade/slide/scale in as they enter the viewport; the backbone of modern storytelling pages.
- **Scroll-driven (CSS scroll-timeline)** — animation progress tied to scroll *position* rather than time; native, performant, deterministic.
- **Parallax** — background layers move slower than foreground, creating depth and immersion.
- **Page transitions** — animated handoffs between routes (GSAP + Barba/Highway, or Next.js + Framer Motion) for app-like continuity.
- **Staggered animation** — children animate in sequence with offset delays; adds rhythm to lists/grids.
- **Skeleton loaders** — animated placeholder shapes mirroring final layout; improve *perceived* performance for loads over ~1s.
- **Loading / progress** — spinners, bars, shimmer; honest feedback for waits.
- **Number counters** — count-up reveals for stats/metrics.
- **Pull-to-refresh / gesture feedback** — branded mobile interactions.
- **Sticky / pinned scroll** — an element locks in place while related content scrolls past; great for step-by-step narratives.
- **Cursor-follow / custom cursor** — bespoke pointer or an element that tracks the cursor; signals craft (use sparingly).
- **Marquee / infinite ticker** — looping horizontal scroll for logos/announcements.

## 4.2 Motion physics & easing
- **Linear** — constant speed; mechanical, almost always wrong for UI.
- **Ease-in / ease-out / ease-in-out** — acceleration/deceleration curves; ease-out is the safe UI default (fast start, soft landing).
- **Spring physics** — motion driven by mass, stiffness, and damping rather than duration; feels alive and natural. The modern standard (Framer Motion, iOS).
- **Bounce / elastic** — overshoot then settle; playful, attention-drawing.
- **Inertia / momentum** — fling-and-decay for drag and scroll; mimics real-world physics.
- **Anticipation + follow-through** — classic animation principles (squash/stretch, wind-up) that make motion read as intentional.

## 4.3 Motion-graphics styles (video / brand)
- **2D animation** — frame-by-frame or vector; flexible and affordable.
- **3D animation** — spatially modeled; cinematic, lifelike, memorable.
- **2D + 3D hybrid** — flat simplicity with 3D depth; a dominant 2025 look.
- **Frame-by-frame / traditional** — each frame drawn; expressive, labor-intensive.
- **Cel / cartoon** — flat character animation.
- **Morphing** — one shape blends seamlessly into another; smooth and eye-catching.
- **Liquid motion** — flowing, stretchy, organic shapes and seamless loops.
- **Kinetic typography** — animated, expressive text as the primary visual.
- **Thin-line / Lottie line** — minimal stroke animations; lightweight, scalable (Lottie/SVG).
- **Seamless / match-cut transitions** — continuous visual flow between scenes.
- **Whiteboard / explainer** — hand-drawn reveal for teaching.
- **Particle / generative** — systems, swarms, and fields driven by code.
- **Sophisticated VFX** — simulation, glow, distortion, compositing.
- **Retro motion** — VHS wobble, grain, analog artifacts.
- **Stop-motion / claymation look** — deliberate frame jitter and tactile texture.
- **Glitch / datamosh** — digital corruption, RGB split, frame tearing as aesthetic.
- **Isometric motion** — animated 30°-angle 3D-flat scenes.

## 4.4 3D / WebGL on the web
- **Interactive 3D (Spline / Three.js)** — draggable, explorable scene objects.
- **Physics-based** — gravity, collisions, cloth, fluid simulation.
- **Shader effects** — GPU distortion, ripple, noise, gradient meshes.
- **Deep glow / light bloom** — radiant, immersive lighting.
- **Camera-on-scroll** — the 3D camera moves through a scene as the user scrolls.

## 4.5 Overall motion philosophies
- **Minimalist motion** — subtle, purposeful, quiet; motion only where it aids comprehension.
- **Maximal / playful motion** — bold, energetic, expressive; motion as personality.
- **Functional motion** — orientation and feedback only (the Material Design stance).
- **Storytelling motion** — choreographed sequences that unfold a narrative.
- **Ambient / idle loops** — background life with no trigger; sets atmosphere.

---

## Quick decision checklist

1. **Who's the audience, and what must they feel in 3 seconds?** That sets the style family.
2. **Pick one aesthetic.** Let it cascade.
3. **Choose type to match the aesthetic's era and mood** (geometric sans for modern/tech, editorial serif for premium/credible, display for personality).
4. **Build the palette from one harmony scheme + one mood,** then verify WCAG AA on every text/background pair.
5. **Choose a motion philosophy, not a pile of effects.** Minimalist for tools, playful for consumer, storytelling for marketing.
6. **Stress-test accessibility and performance** before falling in love with glass, gradients, or heavy 3D.

---

# 5. Components

Navbars, buttons, cards, forms, overlays — none is a single "style." Each is a stack of **independent axes** that multiply together. Mixing them up is what makes this category feel confusing. Separate them and it resolves:

- **Shape** (geometry) and **behavior** (scroll/state) are **free axes** — choose them independently of the aesthetic. An editorial site *usually* wears a square full-bleed bar, but a floating pill can work for it too; the grid underneath doesn't care.
- **Surface** (glass, brutalist border, neumorphic extrude, flat fill…) is **not a free axis** — it's the §1 aesthetic applied to a small element. So this section does **not** re-describe glassmorphism or neo-brutalism; it points back to §1. Where a design style implies a specific navbar/button, that's noted on the style's entry as a **Components:** line, and consolidated in [§5.19](#519-component-signature-reference).
- **Layout** (where the logo, links, and CTA sit) is mostly free, lightly nudged by the aesthetic.

Rule of thumb: **the design style sets the default on each axis; it doesn't lock it.** Start from the default, deviate deliberately.

## 5.1 Navbar — position & anchor

Where the bar physically sits. The single biggest structural decision — it sets the page's whole spatial frame.

### Docked top bar (full-bleed)
The bar spans edge to edge at the top of the viewport and touches the sides. The default, expected, "serious" position — newspapers, corporate, editorial, most of the web. Maximum trust and scannability; zero novelty. Reach for it when credibility matters more than personality. Trap: so standard it's invisible — lean on type and surface to give it voice.

### Floating / detached bar
The bar is inset from all edges with a margin around it, hovering over the content as a discrete object (often a pill or rounded card). Feels modern, light, app-like, "designed." Dominant on SaaS and portfolio sites 2023–26. Trap: the margin steals vertical space and the float can feel gimmicky over dense content; needs a surface (shadow/glass/border) to read as intentional, not misaligned.

### Centered island / "dynamic island"
A short floating capsule centered horizontally, holding only the essentials — logo or a few links — expanding on interaction. Borrowed from iPhone's Dynamic Island. Compact, focused, playful-premium. Great for minimal sites with few destinations. Trap: hides navigation; only works when the IA is genuinely shallow.

### Sidebar / vertical nav
Navigation runs down the left (or right) edge as a column. Signals app, dashboard, documentation, or fashion-editorial. Scales to many items and frees the top for content. Trap: eats horizontal space and is awkward on mobile (collapses to a drawer anyway); overkill for a marketing site with five links.

### Bottom bar
A fixed bar pinned to the bottom edge, thumb-reachable. App-native (iOS/Android tab bars); increasingly used on mobile web for primary actions. Trap: unconventional on desktop web; reserve for app-like or mobile-first products.

### Split / segmented bar
Elements broken into separate floating clusters — e.g. logo pinned left, a links pill floating center, a CTA pinned right — rather than one continuous bar. Editorial, fashion, and agency feel; lots of breathing room. Trap: more moving parts to align; the clusters must feel related, not scattered.

## 5.2 Navbar — shape

The geometry of the bar's container. A free axis — pick it for the feel you want, then let surface dress it.

### Full-width rectangle
Hard-cornered bar flush to the viewport edges. Structural, neutral, editorial. The shape that disappears so content leads. Trap: needs a strong type or a hairline rule to avoid blandness.

### Pill / capsule
Fully-rounded floating container. Friendly, modern, soft, app-like. The default shape for floating bars right now. Trap: now a cliché of the "modern SaaS" look; the radius reads as generic unless the surface or contents differentiate it.

### Rounded-rect card
Floating bar with a moderate corner radius — softer than square, more grounded than a pill. The safe middle ground; pairs with almost any aesthetic. Trap: forgettable by design; it's the beige of navbar shapes.

### Hard square / bordered box
Sharp corners, often with a visible border. Editorial, brutalist, or technical. Confident and structural. Trap: can feel severe; one wrong color and it reads as a wireframe.

## 5.3 Navbar — surface (inherits the aesthetic)

How the bar's container is filled and finished. **This axis is your §1 aesthetic in miniature** — see those entries for the full treatment and traps. Quick map:

- **Transparent** — no background; the bar sits directly over the hero, just logo + links + CTA floating on the imagery. Immersive, premium, editorial. Almost always pairs with a **transparent→solid on scroll** behavior (§5.4) so it stays legible past the hero. Trap: contrast over a busy hero — needs a gradient scrim or a guaranteed-dark hero zone.
- **Solid fill** — opaque background. Maximum legibility, zero fuss. The trustworthy default.
- **Glassmorphic** — blur + translucency (see §1.3). Modern, light, premium; lets content ghost through underneath. Trap: text-over-blur contrast; needs a tint floor.
- **Outlined / hairline** — no fill, just a thin border or a single bottom rule. Quiet, editorial, Swiss. Trap: a 1px rule can vanish on some displays — give it enough contrast.
- **Brutalist** — thick border + hard offset shadow (see §1.2). Confident, indie. Trap: now the default "startup" look.
- **Gradient / mesh** — aurora or duotone fill (see §1.3 / §3). Warm and characterful. Trap: kills contrast for the links sitting on it.
- **Floating drop-shadow** — solid (or glass) bar lifted off the page with a soft shadow. Reads as a distinct, tappable object. The standard finish for floating bars.

## 5.4 Navbar — behavior & scroll state

How the bar responds to scroll and interaction. A **free axis**, fully independent of shape and surface — but the highest-impact one for perceived polish.

### Static
The bar scrolls away with the page; no special behavior. Honest and simple. Fine for short pages. Trap: on long pages the user loses navigation and must scroll back up.

### Sticky / fixed
The bar stays pinned at the top as the page scrolls. The modern default — navigation always reachable. Trap: a tall sticky bar permanently eats viewport on mobile; keep it short or pair with hide-on-scroll.

### Hide-on-scroll-down / show-on-scroll-up
The bar slides away when scrolling down (reading mode, max content) and reappears the instant the user scrolls up (intent to navigate). The best-of-both default for content-heavy pages. Trap: the reveal must be fast and the threshold tuned, or it feels twitchy.

### Transparent → solid on scroll
The bar starts transparent over the hero and fades to a solid/glass fill once the user scrolls past it. Premium, immersive, ubiquitous on marketing sites. Trap: the transition needs an easing and a scroll threshold; an abrupt swap looks broken, and the transparent state must stay legible over the hero.

### Shrink / condense on scroll
The bar reduces height, shrinks the logo, and tightens padding after a small scroll, reclaiming space without disappearing. Polished and space-efficient. Trap: too much shrink causes a layout jump; animate height, don't snap it.

### Morph-to-pill on scroll
A full-bleed bar detaches and contracts into a floating pill (or island) as the user scrolls. A current showpiece move — signals craft. Trap: high-effort, easy to overdo; the morph must be smooth or it's worse than nothing.

### Mega-menu
Hovering or clicking a top item drops a full-width panel of grouped links, often with imagery. For deep IA — e-commerce, enterprise, large content sites. Trap: overkill for a handful of pages; adds hover-intent complexity and mobile-collapse work.

### Hamburger / drawer collapse
Links fold behind a menu icon that opens a panel or drawer. Mandatory responsive fallback; sometimes a deliberate minimal choice on desktop too. Trap: hiding desktop nav behind a burger when there's room hurts discoverability — only do it when minimalism is the point.

## 5.5 Navbar — content layout

Where logo, links, and CTA sit inside the bar. Mostly free; the aesthetic nudges it.

### Logo-left + center links + CTA-right
The universal three-zone layout. Balanced, expected, scannable. Trap: its very ubiquity — differentiate with type and spacing, not by breaking it for novelty's sake.

### Logo-left + links-right (+ CTA)
Everything pushed right of the logo. Tighter, slightly more editorial/utilitarian. Common on docs and apps.

### Centered logo, split nav
Logo dead-center with links flanking it left and right. Symmetrical, fashion/luxury/editorial, ceremonial. Trap: needs a roughly even number of links per side or it looks lopsided; fragile responsively.

### Minimal (logo + burger)
Just the wordmark and a menu trigger, even on desktop. Maximum restraint — gallery, portfolio, fashion. Trap: hides everything; only for sites where the work *is* the navigation.

### Command / search-led
A search field or command bar is the primary nav element. For search-first products — docs, large catalogs, tools. Trap: presumes users know what to type; pair with browsable fallbacks.

## 5.6 Button — shape

The button's silhouette. A free axis. Keep it **consistent across the whole site** — shape is the cheapest way to read as systematic or as sloppy.

### Pill (fully rounded)
Radius equals half the height; ends are semicircles. Friendly, soft, modern, approachable. The dominant CTA shape in consumer and SaaS. Trap: so common it's neutral; carries no opinion on its own.

### Rounded-rect
Small-to-medium corner radius. The pragmatic default — softer than square, more grounded than a pill, fits nearly every aesthetic. Trap: the safe, characterless choice; the radius value itself is a brand signal, so pick it deliberately.

### Square / sharp corner
Zero radius. Editorial, brutalist, technical, luxury. Confident and structural. Trap: can feel hard or dated outside a committed aesthetic; pair with the right type.

### Circle (icon button)
Round button holding a single icon. For compact, repeated actions — play, add, close, social. Trap: icon-only loses meaning; needs a tooltip or obvious context.

### Squircle
A superellipse between square and circle (Apple's icon math). Soft but precise, premium-modern. Trap: subtle — at small sizes it's indistinguishable from a rounded-rect, so the effort can be invisible.

## 5.7 Button — surface (inherits the aesthetic)

How the button is filled and finished. **This axis is your §1 aesthetic applied to a control** — see those entries. Across a page you'll also stack these by *hierarchy* (one solid primary, ghost secondary, text tertiary), independent of the aesthetic. Quick map:

- **Solid filled** — opaque fill, the primary-action default. Highest emphasis. Trap: only one solid primary per view, or hierarchy collapses.
- **Outline / ghost** — border only, transparent center. The standard secondary action. Trap: low emphasis; don't use for the thing you most want clicked.
- **Text / link** — no chrome at all, just colored/underlined label. Tertiary, low-commitment actions. Trap: weak affordance; reserve for "cancel"-tier actions.
- **Soft / tinted** — low-opacity fill of the accent color. Gentle emphasis between solid and ghost; calm, modern. Trap: can fail contrast if the tint is too pale.
- **Gradient** — multi-stop fill (see §3). Energetic, premium-playful. Trap: trendy and can muddy the label; keep text contrast high.
- **Glassmorphic** — blur + translucency (§1.3). Premium over imagery. Trap: legibility over busy backgrounds.
- **Neumorphic** — soft same-color extrude (§1.3). Tactile, calm. Trap: notoriously fails contrast and hides state — an accessibility minefield; avoid for primary CTAs.
- **Brutalist** — hard border + solid offset shadow (§1.2); the shadow often collapses on press so the button "drops." Confident, indie, tactile. Trap: a cliché now; the press-drop must not shift surrounding layout.
- **3D / extruded** — a visible bottom edge ("lip") that compresses on press, like a physical key. Playful, satisfying, game-like. Trap: era/skeuomorphic flavor; easy to overdo.
- **Skeuomorphic** — glossy, beveled, gradient-lit to mimic a real button (§1.3). Nostalgic, Y2K/Frutiger Aero. Trap: dates instantly outside a deliberate retro frame.
- **Claymorphic** — puffy, inflated, double-shadow (§1.3); deforms/bounces on press. Friendly, tangible, works on any background. Trap: too soft for serious/data-dense products.

## 5.8 Button — state & interaction

How the button reacts to hover, focus, and press. Free axis — but **never skip it**: a button with no feedback feels broken (see §4.1 micro-interactions, §4.2 easing).

### Hover lift / shadow
On hover the button rises (translateY) and/or its shadow deepens. The cheapest, highest-ROI feedback. Aim ~150–200ms ease-out. Trap: don't move so far it shifts neighbors; keep it subtle.

### Press depth-collapse
On press the button visually compresses — 3D lip flattens, brutalist shadow snaps to zero, or a slight scale-down. Confirms the click physically. Trap: the collapse must reserve its space (no layout shift) and snap back fast.

### Magnetic
The button (or its label) drifts toward the cursor as it approaches, then snaps back. Signals craft; agency/portfolio favorite. Trap: pure showmanship — disorienting if overused, and useless on touch; respect `prefers-reduced-motion`.

### Shine / sweep
A specular highlight sweeps across the button on hover. Premium, glossy, draws the eye to the CTA. Trap: gimmicky if it loops; fire it once per hover.

### Border-draw / fill-wipe
On hover a border draws itself around the button, or a fill wipes in from one edge. Elegant, editorial, deliberate. Trap: must complete fast enough to not delay the perceived affordance.

## 5.9 Cards

The universal container — the unit most pages are actually built from. Same axis model: **shape** (corner radius), **surface** (→§1: elevated/flat/glass/bordered), **behavior** (hover), plus a **composition** sub-axis (where the image and text sit).

- **Elevated card** — solid fill lifted by a drop shadow (see §8 elevation). Reads as a distinct, tappable object; the default for grids. Trap: too much shadow on every card flattens hierarchy — vary elevation by importance.
- **Flat / bordered card** — no shadow, a hairline border instead. Quiet, editorial, dense-friendly. Trap: borders multiply into visual noise on busy grids; consider gaps-only separation.
- **Filled / tinted card** — a soft background tint instead of border or shadow. Calm, modern, groups related content. Trap: low contrast against the page if the tint is too faint.
- **Glass card** — frosted translucency over imagery (§1.3). Premium, layered. Trap: text legibility over the blur.
- **Image-top / split card** — image occupies the top (or one side), text below/beside. The blog/product workhorse. Trap: inconsistent image aspect ratios break the grid — enforce one ratio.
- **Image-cover card** — full-bleed image with text overlaid via a scrim or gradient. Immersive, editorial. Trap: text contrast over photography; always scrim.
- **Bento tile** — asymmetric sized card in a bento grid (§1.5). Trap: needs hierarchy or it's just equal boxes.

**Hover behaviors** (free axis): lift/shadow-deepen · border or ring glow · 3D tilt/parallax (cursor-reactive) · spotlight (cursor-follow glow) · content reveal (CTA or text fades in) · image zoom-within-frame. Trap: pick one; stacking tilt + glow + zoom is chaos.

## 5.10 Forms & inputs

Where users actually do work. Highest usability stakes in the doc — get state and feedback right or the brand feels broken. **Surface** follows §1; **shape** is the field's radius; the critical axis is **state**.

- **Field surface styles** — outlined (border box, the safe default) · filled (tinted background, Material-style) · underlined (bottom rule only, minimal/editorial) · ghost (no chrome until focus). Trap: underline and ghost have weak affordance; risky for unfamiliar forms.
- **Label patterns** — top-aligned (most scannable, the default) · floating label (animates from placeholder to top on focus) · inline/left (compact, dense forms) · placeholder-as-label (avoid — disappears on input, fails a11y). 
- **Controls** — text field · textarea · select/dropdown · multi-select (removable chips) · combobox/autocomplete · checkbox · radio · toggle/switch · slider/range · number stepper (+/−) · segmented control · date/time picker · date-range (dual-calendar) · file upload (button, dropzone) · OTP/pin · tags/token input · password-reveal · rating. Trap: a date *range* built from two independent single pickers doubles the work and invites start-after-end errors — constrain the second field to the first.
- **States** (non-negotiable): default · hover · focus (visible ring — a11y requirement) · filled · disabled · error (color + message + icon) · success · loading. Trap: skipping focus or error states is the single most common form failure.
- **Validation timing** — inline-on-blur (best) · on-submit · real-time. Trap: real-time validation that fires mid-typing nags the user.
- **Layout** — single-column (fastest to complete; the rule) · multi-column (only for short related fields like city/state/zip) · multi-step/wizard (long forms, with progress) · inline/row (filters, search bars).

## 5.11 Overlays — modals, drawers, popovers, toasts

Layers that sit above the page. Distinguished by **where they enter from**, **how much they block**, and **how dismissable** they are.

- **Modal / dialog** — centered, dims the page behind (scrim), blocks interaction until resolved. For focused decisions and short forms. Trap: overused for things that should be inline; never trap the user without a clear close.
- **Drawer / sheet** — slides in from an edge (side drawer for nav/filters; bottom sheet for mobile actions). Keeps context visible. Trap: side drawers compete with the page; bottom sheets must be swipe-dismissable.
- **Popover** — small floating panel anchored to a trigger (menus, date pickers, detail cards). Non-blocking. Trap: must reposition to stay on-screen near edges.
- **Tooltip** — tiny *non-interactive* hint revealed on hover/focus, wired via `aria-describedby`. Supplementary text only. Trap: the moment it needs to hold a link, action, or survive touch, a tooltip is the wrong control — reach for a toggletip.
- **Toggletip** — click/tap-triggered info bubble that stays until dismissed; works on touch and keyboard, announced through a `role="status"` live region. Use whenever the hint must be interactive or reliably reachable. Trap: wiring it like a tooltip (`aria-describedby`) makes a screen reader read it before the click, so the trigger appears to do nothing.
- **Toast / snackbar** — transient message that auto-dismisses (save confirmed, error). Non-blocking, corner or bottom. Trap: don't put critical errors that need action in an auto-dismissing toast.
- **Banner / inline alert** — persistent message in the page flow (cookie notice, system status, validation summary). Trap: banner blindness; reserve for things that matter.
- **Command palette** — keyboard-summoned (⌘K) search-and-act surface (a search/command pattern that happens to render as an overlay → see §5.18). Power-user navigation; signals a "pro" tool. Trap: discoverability — pair with a visible entry point.

## 5.12 Tabs, accordion & disclosure

Patterns that hide content until requested — the tools for managing density.

- **Tabs** — switch between peer views in the same space. For parallel, equally-important content. Trap: don't bury content users need to compare side-by-side.
- **Accordion** — stacked expandable rows; multiple or one-at-a-time. For FAQs, settings, progressive detail. Trap: hiding content that should just be on the page hurts scannability and SEO.
- **Disclosure / "show more"** — a single expandable region. Tames long text or option lists. Trap: hiding primary actions behind a toggle.
- **Wizard / multi-step flow** — sequential disclosure with a progress indicator, for multi-stage tasks (checkout, onboarding). (Distinct from the *number stepper* input in §5.10.) Trap: don't gate steps users want to skip or revisit.
- **Segmented control** — compact inline toggle between 2–4 options (often a tab substitute on mobile). Trap: breaks down past ~4 segments.

## 5.13 Tables & data display

Where dense information lives. The axis here is **density + readability**, not decoration.

- **Data table** — rows × columns, the spreadsheet model. Sortable, filterable, paginated. Trap: too many columns on mobile — collapse to cards or prioritize columns responsively.
- **Density modes** — comfortable · compact · condensed. Let power users tighten rows. Trap: one density rarely fits both scanning and dense analysis.
- **Row treatments** — zebra striping (aids horizontal scanning) · row borders · borderless + generous spacing (editorial). Trap: striping plus borders plus shadows = noise.
- **Sticky header / first column** — keeps context while scrolling large tables. Near-mandatory for big data.
- **Bulk-select + action bar** — row checkboxes with a contextual toolbar that appears on selection. Trap: a "select all" that silently means *this page only*, not the whole filtered set — state the scope.
- **Column controls** — user-driven reorder, pin/freeze, and show/hide of columns. Trap: a fixed column set forces horizontal scrolling for data the user could have hidden.
- **Tree / grouped rows** — expandable parent rows for hierarchical data. Trap: deep nesting with no expand-all/collapse-all is unnavigable.
- **Inline actions / expandable rows** — per-row controls or a drawer of detail. Trap: hiding the primary action where it's not discoverable.
- **Definition / spec list** — key–value pairs (not tabular). For product specs, metadata. Cleaner than a 2-column table.
- **Stat / metric blocks** — big-number callouts with label and trend. The dashboard headline unit (pairs with §4.1 number counters).

## 5.14 Hero sections

The opening screen — the single highest-stakes block on a marketing site. Categorized by **what leads** and **how the layout splits**.

- **Type-led hero** — a bold headline *is* the hero, no imagery (→§2.1 typographic hero). Fast, brand-forward, the modern default. Trap: needs strong copy and hierarchy or it's empty.
- **Split hero** — copy on one side, image/product/illustration on the other. Balanced, classic, conversion-friendly. Trap: the 50/50 split is so common it's invisible; break the symmetry.
- **Centered hero** — headline, subhead, CTA stacked and centered over a simple or gradient background. Calm, focused. Trap: generic if the background does nothing.
- **Full-bleed media hero** — edge-to-edge photo or video behind overlaid copy. Immersive, premium. Trap: text contrast (scrim required) and video weight/performance.
- **Background-video / cinemagraph hero** — looping motion behind copy. Atmospheric. Trap: file size, autoplay/accessibility, and motion-distraction from the CTA.
- **Interactive / WebGL hero** — 3D scene, shader, or cursor-reactive canvas (→§4.4). Maximum "wow," signals craft. Trap: GPU cost, load time, and mobile fallback.
- **Bento hero** — the hero *is* a bento grid of feature tiles. Product-forward. Trap: dilutes a single clear message.
- **Animated / kinetic hero** — staggered reveal, marquee, or variable-font motion on entry (→§2.6, §4.1). Trap: don't delay the CTA behind a long sequence.

## 5.15 Footers

The closing block — often an afterthought, always a chance to reinforce brand and aid navigation.

- **Fat / sitemap footer** — multi-group link directory, newsletter, social, legal. For large sites; aids SEO and discovery. Trap: a wall of links with no hierarchy.
- **Minimal footer** — logo, a few links, copyright. For focused or single-page sites. Trap: too sparse can feel unfinished on a content-heavy site.
- **CTA footer** — a final conversion push (big headline + button) above the standard footer. High-performing on marketing sites.
- **Mega footer** — fat footer plus featured content, recent posts, or a map. For content/e-comm.
- **Brand-statement footer** — oversized wordmark or tagline as a closing graphic moment (→§2.1 mega-type). Trap: style over function — keep real navigation present.

## 5.16 Marketing & content blocks

The repeatable sections that compose a landing page between hero and footer.

- **Feature blocks** — alternating image/text rows · icon-grid of features · bento feature showcase · side-by-side comparison. Trap: the 3-icon-column row is the most generic block on the web — vary the rhythm.
- **Social proof** — testimonial card/carousel · logo wall ("trusted by") · star-rating summary · case-study highlight · stat band (big numbers). Trap: vague unattributed quotes read as fake.
- **Pricing** — tiered cards (3-column standard) · comparison table · toggle (monthly/annual) · single-plan. Trap: the middle "most popular" highlight is expected — but don't dark-pattern the comparison.
- **FAQ** — accordion (§5.12) or two-column list. Cheap trust + SEO. 
- **CTA band** — a focused full-width conversion strip between sections.
- **Newsletter / lead capture** — inline signup block (often footer-adjacent).
- **Integration / "works with" grid** — grid of connector/partner logos, often filterable by category. Trap: an undifferentiated logo dump reads as filler, not capability.
- **Comparison / "vs" table** — feature matrix positioning the product against named alternatives. Trap: stacking the deck too obviously erodes the trust it's meant to build.
- **Logo / press strip · stats strip · steps/how-it-works · team grid · blog/resource teasers** — the standard supporting cast.

## 5.17 Small parts

The vocabulary of tiny elements that texture an interface.

- **Badge / chip / tag** — category tag, removable filter chip, count badge. Trap: too many colors dilutes meaning — fix a small status palette.
- **Notification badge / dot** — count or unread-dot overlaid on an icon (bell, avatar, tab). Trap: an uncapped number (no "99+") or a dot that never clears erodes trust in the signal.
- **Status indicator** — standalone state dot/pill (online/offline, healthy/degraded, live). Trap: color-only status fails colorblind users — pair with shape, label, or icon.
- **Avatar** — circle/squircle user image; initials or icon fallback; stacked/overlapping group. 
- **Tag / token input** — free-entry chips for keywords, recipients, or filters. Trap: no de-dupe or paste-splitting makes bulk entry painful.
- **Kbd / shortcut hint** — `⌘K`-style key caps shown inline or in menus. Trap: showing platform-specific keys (⌘) to non-Mac users without detecting the OS.
- **Breadcrumb** — hierarchical path for deep sites. Trap: pointless on shallow IA.
- **Pagination** — numbered · prev/next · **load-more** (visible button; keeps the footer reachable — the recommended middle path) · infinite scroll. Trap: infinite scroll loses the footer and "where am I" — wrong for goal-directed browsing.
- **Progress** — spinner (short, discrete actions: save/auth/pay) · skeleton mirroring the incoming layout (§4.1; content arriving in a known shape) · determinate bar (known-duration/multi-step) · ring · step-dots. Trap: a spinner where a skeleton belongs makes a 3s wait *feel* like 4.5s — match the indicator to **what** is loading, not just how long.
- **Empty state** — the screen before data exists: illustration + one-line explanation + a primary action. Trap: a blank void instead of an onboarding moment is a wasted first impression.
- **Divider / separator** — rule, spacing, or labeled divider (§8). 
- **Carousel** (auto/rotating promo) · **content slider/swiper** (manual peer content) · **gallery/lightbox** (tap-to-zoom media viewer) — three distinct patterns often conflated. Trap: the warning is about the *rotating promo carousel* — it hides content and rarely gets swiped past slide one, so never put critical info there; a tap-to-zoom gallery is fine.
- **Cookie / consent banner** — legally required, brand-damaging if clumsy; keep it small and honest.

## 5.18 Search, filter & sort

Finding-and-narrowing UI — scattered across forms, tables, and small parts elsewhere, gathered here as the pattern it actually is.

- **Search input** — text field with a search affordance, debounced inline results, and a clear (×). Trap: a magnifying-glass icon with no submit, no clear, and no feedback leaves users unsure it fired.
- **Autocomplete / combobox** — typeahead suggestions narrowing as you type (→§5.10). For large known option sets.
- **Command palette** — ⌘K search-and-act surface (→§5.11). Power-user navigation and actions in one input.
- **Faceted filter panel** — multi-dimension refinement (sidebar on desktop, bottom-sheet on mobile) with a result count per facet. Trap: showing facets that don't apply to the category (sleeve-length on shoes) bloats cognitive load — surface only applicable facets.
- **Active-filter chips** — applied filters as removable pills above the results, each labeled with its facet ("Color: Blue", not "Blue"). Trap: unlabeled chips collide when the same value spans facets; keep a ≥44px tap target on mobile.
- **Sort control** — explicit sort dropdown or sortable-column affordance, distinct from filtering, with the active direction always visible. Trap: conflating sort with filter, or hiding which column/direction is active.

## 5.19 Component signature reference

The default navbar + button each design style reaches for. **Defaults, not rules** — these are the combinations that read as "correct" for the aesthetic; deviate when you have a reason. Surface terms map to §1; shape/behavior map to §5.1–5.8.

| Design style (§1) | Navbar default | Button default |
|---|---|---|
| **Swiss / International** | Full-bleed square, hairline bottom rule, transparent or solid | Square or text, no radius, solid primary |
| **Bauhaus** | Full-bleed square, solid primary-color block | Square, solid color block, flat |
| **Minimalism** | Thin transparent top, hairline, sticky | Ghost / text, subtle pill, soft hover-lift |
| **Neo-minimalism / quiet luxury** | Centered-logo split or minimal, transparent→solid | Outline or text, square/squircle, border-draw |
| **Maximalism** | Solid or gradient bar, bold | Solid, clashing color, pill or square |
| **Memphis** | Bar with playful borders/clashing color | Square or pill, color-blocked, hard shadow |
| **Brutalism** | Square, unstyled/system, hard border | Square, system, no radius |
| **Neo-brutalism** | Thick black border, hard offset shadow, often floating | Square, bordered, offset shadow, press-drop |
| **Glassmorphism / Liquid Glass** | Floating glass pill, transparent→solid | Glass, soft radius, shine on hover |
| **Neumorphism** | Soft same-color extrude (rare; low contrast) | Soft-extrude (avoid for primary CTAs) |
| **Claymorphism** | Puffy floating rounded card | Puffy claymorphic, bounce on press |
| **Flat / Flat 2.0** | Solid bar, sticky | Solid or soft-tinted, rounded-rect, hover-shadow |
| **Material** | Solid elevated bar, shrink-on-scroll | Filled/tonal, rounded-rect, ripple press |
| **Bento** | Full-bleed or floating rounded-rect | Rounded-rect, soft-tinted |
| **Editorial / dark academia** | Full-bleed square, centered-logo split, serif type | Square or text, hairline |
| **Y2K** | Chrome/gradient floating pill | Glossy chrome, inflated, shine |
| **Synthwave / cyberpunk** | Dark transparent bar, neon hairline | Outline neon-glow, dark fill |
| **Frutiger Aero** | Glossy glass bar, soft gradient | Glossy skeuomorphic, beveled |

---

# 6. Layout & composition

How elements are arranged on the canvas — the structural grammar beneath every aesthetic. Where §1 decides the *flavor*, this decides the *skeleton*. Most "AI-looking" design (the thing to avoid) is a composition failure, not a color one: equal-weight three-column rows, dead-centered everything, no rhythm. Composition is where a page earns sophistication.

## 6.1 Grid systems

The invisible scaffold that aligns everything. Pick one and commit — inconsistent alignment is the fastest tell of amateur work.

The four canonical grid types (Müller-Brockmann's taxonomy) are **manuscript, column, modular, hierarchical** — the rest below are web-specific systems and treatments built on them.

- **Manuscript grid** — a single text block/column; the structure for long-form and books. Trap: comfortable line length is ~45–75 characters (≈66 ideal) — an unconstrained measure tires the eye.
- **Column grid** — multiple vertical columns (magazine/web). The **12-column grid** is the web standard — divides evenly into 2/3/4/6. Trap: defaulting every section to the same split is what creates "template" sameness.
- **Modular grid** — columns *and* rows, creating cells. For dense, magazine-like or dashboard layouts.
- **Hierarchical grid** — proportion-driven rather than fixed cells; columns/rows sized to content and visual weight. The structure behind most editorial hero and asymmetric-poster layouts. Trap: "no grid" and "hierarchical grid" look alike to amateurs — the discipline is invisible, not absent.
- **Baseline grid** — horizontal rhythm so type lines up across columns. Signals real typographic craft.
- **Bento / modular tile grid** — asymmetric boxed tiles (→§1.5). 
- **Broken / asymmetric grid** — deliberate overlaps and off-grid breaks for tension (→§1.5, §2.2). Trap: needs the grid *underneath* to break against; sloppy ≠ asymmetric.

**Layout primitives** (how grids are actually built in CSS):
- **CSS Grid vs Flexbox** — Grid is two-dimensional (rows *and* columns, content placed into a defined structure); Flexbox is one-dimensional (a single row/column that distributes and wraps). Grid for page/section scaffolds; Flexbox for component-internal runs (toolbars, button groups, tag lists). Trap: forcing Flexbox to fake a 2D grid with nested wrappers and manual width math.
- **Subgrid** — a nested grid inherits its parent's track lines, so child elements align to the outer grid (card titles/footers lining up across a row despite uneven content). Baseline-available since 2024. Trap: reaching for fixed heights or JS to fake alignment subgrid gives for free.
- **Intrinsic / fluid layouts** ("Every Layout" patterns) — breakpoint-free layouts that respond to content and available space: Stack, Sidebar, Switcher, Cluster, Cover, and `repeat(auto-fit, minmax())` grids, built from `min()`/`max()`/`clamp()`. The modern alternative to breakpoint-thunked design. Trap: peppering breakpoints where one intrinsic rule would self-adjust.

## 6.2 Spacing & rhythm

The single highest-leverage, most-ignored variable. Generous, *systematic* space is what reads as premium.

- **Spacing scale** — a fixed set of steps so gaps are consistent, never arbitrary. The canonical convention is the **8-point grid** (8/16/24/32/48/64…), with the **4-point grid** (4/8/12/16/20…) as the finer-grained variant for tight UI. The backbone of a clean UI. Trap: eyeballing one-off pixel values destroys rhythm.
- **Whitespace / negative space** — intentional emptiness to group, separate, and let content breathe; used *actively* it points, isolates, and creates pause, not just leftover margin. Confidence through restraint. Trap: cramped layouts read cheap; "not enough whitespace" is the most common fix.
- **Vertical rhythm / section pacing** — consistent (or deliberately varied) spacing between sections so the page has cadence, not a uniform mush. Trap: every section the same height/padding = monotony.
- **Density** — comfortable vs compact vs dense, chosen for the audience (marketing = airy; pro tools = dense). 
- **Gestalt principles** — proximity, similarity, closure, continuity, figure/ground, common region: how the eye groups elements pre-attentively, and *why* proximity and whitespace communicate structure at all. Trap: fighting Gestalt — equal gaps between unrelated items so everything reads as one undifferentiated group.
- **Balance — symmetric vs asymmetric** — symmetry reads stable, formal, safe; asymmetry reads dynamic and is the antidote to dead-center "AI" layouts, but must still balance *visual weight* (a large quiet area against a small dense one). Trap: confusing asymmetry with imbalance — off-center still needs a counterweight.
- **Optical alignment** — aligning by perceived edge, not bounding box (overshooting round shapes, nudging punctuation and icons). The detail that separates crafted from mechanically-aligned. Trap: trusting pixel-perfect math when the eye reads it as off.
- **Rule of thirds / golden ratio** — placing focal elements off-center on third-lines or φ proportions for natural emphasis; a counter to dead-centering. Trap: treating φ as magic — it's one tool, not a guarantee of beauty.

## 6.3 Hierarchy & reading patterns

Directing the eye in the right order.

- **Visual hierarchy** — ordering by size, weight, color, contrast, and position so the eye knows what's first (→§2.7). The backbone of every layout.
- **Focal point** — one dominant element per view that anchors attention. Trap: competing focal points cancel out — fight for one.
- **Reading patterns** — **F-pattern** (per NN/g, what users *fall back into* when content is poorly formatted — a symptom, not a target; varies to E-shape / inverted-L) · **Z-pattern** (sparse pages; eye zigzags to the CTA) · **layer-cake / lawn-mower** (structured comparison content) · **Gutenberg diagram** (the four quadrants — primary optical area top-left, terminal area bottom-right where the CTA canonically lands). Trap: designing *for* the F-pattern instead of disrupting it (subheads, front-loaded paragraphs, information-carrying first words) bakes in poor scannability.
- **Above the fold** — what loads in the first viewport; the hero's job to communicate value + offer one action before any scroll. Trap: cramming everything above the fold; the fold is softer than people think.
- **Scannability** — headings, eyebrows, pull quotes, chunking, and bullets so users can skim. Most users don't read; they scan.

## 6.4 Container & width strategy

How content relates to the viewport edges.

- **Contained / max-width** — content capped at a comfortable width and centered, with margins growing on large screens. The readable default. Trap: a too-wide container wrecks line length (keep body to ~45–75ch) and feels unanchored.
- **Full-bleed** — a section spans the entire viewport width, edge to edge (media, color bands, heroes). Creates impact and rhythm against contained sections. 
- **Breakout** — an element pushes wider than the text column but not full-bleed (images, quotes, code). Editorial sophistication.
- **Split-screen / 50-50** — viewport halved into two panels (often one fixed, one scrolling). Bold, balanced. Trap: ubiquitous — break the symmetry to avoid template feel.
- **Edge-to-edge vs framed** — whether the whole design sits in a margin/frame (gallery feel) or bleeds to the browser edge.

## 6.5 Responsive & fluid

Behavior across screen sizes.

- **Mobile-first** — design the small screen first, enhance up. The discipline that prevents desktop-only thinking. 
- **Breakpoints** — the widths where layout reflows (typical: ~640/768/1024/1280). Trap: designing only for standard device widths instead of where *your content* breaks.
- **Fluid type & space** — `clamp()` scaling so type and spacing flex smoothly between breakpoints instead of jumping. The modern standard.
- **Aspect-ratio control** — locking media proportions so layouts don't shift as images load (also a CLS/performance win).
- **Container queries** — components responding to *their container's* width, not the viewport — true modular responsiveness. Baseline widely available (2024+); production-ready, not emerging.
- **Responsive images & art direction** — `srcset`/`sizes` for resolution-switching; `<picture>` for art direction (a different crop/aspect per breakpoint, not just a smaller file). Trap: shipping one desktop crop scaled down — the subject becomes an unreadable speck on mobile.
- **Safe areas / notches** — `env(safe-area-inset-*)` so content clears notches, rounded corners, and home indicators. Trap: edge-to-edge full-bleed that tucks a CTA under the home bar.
- **RTL / i18n layout** — logical properties (`margin-inline`, `inset-inline-start`) so layouts mirror for right-to-left languages and tolerate text expansion (German/Finnish run ~30% longer). Trap: hard-coded `left`/`right` and fixed-width labels that clip when translated.
- **Reflow patterns** — multi-column → stacked · table → cards · sidebar → drawer · horizontal scroll on small screens.

## 6.6 Page structure patterns

Whole-page compositional archetypes.

- **Single-column / long-scroll** — one narrative column, section after section. The marketing-site default. 
- **Scrollytelling** — content choreographed to scroll: pinned sections, step-through reveals, scroll-driven animation (→§4.1). Immersive storytelling. Trap: heavy and easy to overdo; can hijack the scroll.
- **Sticky / pinned panels** — one side fixed while the other scrolls (product feature walkthroughs). 
- **Magazine / editorial** — asymmetric, multi-column, image-rich, broken grid (→§2.2). High craft.
- **Dashboard / app shell** — persistent nav + content region, widget grid, dense data. 
- **Gallery / grid-first** — the work *is* the layout; minimal chrome (portfolios, e-comm PLP).
- **Zigzag / alternating** — feature rows that alternate image side for rhythm. Trap: the most generic marketing structure — vary it.

**Layout mechanics worth naming:**
- **Sticky positioning** — `position: sticky` for elements that scroll then pin within their container (section nav, table headers, summary rails). Trap: a sticky ancestor with `overflow: hidden` silently kills it; over-sticky UIs eat the mobile viewport.
- **Scroll snap** — `scroll-snap-type`/`scroll-snap-align` for carousels, full-page sections, and step decks without JS. Trap: mandatory snap that traps the user and fights momentum scrolling.
- **The fold, qualified** — not a hard line (viewport heights vary, scrolling is expected behavior), but the first viewport disproportionately drives engagement. Design so above-the-fold *sets up the scroll*, not so everything fits above it.

---

# 7. Imagery & media

The visual content that fills the layout. A site's "flavor" is carried as much by its imagery treatment as its type or color — a default stock photo can undo an otherwise sharp design. (Illustration *aesthetics* live in §1.7; this section is about photographic and media *treatment* and craft.)

## 7.1 Photography styles

- **Editorial / lifestyle** — candid, narrative, human moments; warm and authentic. The antidote to stock.
- **Product / studio** — clean, lit, isolated subject (often on seamless or gradient). E-comm and hardware. 
- **Environmental / contextual** — product or person in real setting; shows use and scale.
- **Flat-lay / top-down** — arranged objects shot from above; tactile, editorial, food/craft.
- **Documentary / candid** — unposed, journalistic; trust and realism.
- **Conceptual / art-directed** — staged, surreal, or stylized for brand voice.
- **Black-and-white / monochrome** — timeless, editorial, removes color noise.
- **AI-generated** — fast and flexible but risks an uncanny, generic sheen — art-direct it or it reads as filler. Trap: the new "stock photo" tell.

## 7.2 Image treatments

How photos are processed to fit the brand — the difference between "stock" and "designed."

- **Duotone / tritone** — photo mapped to two/three brand colors (→§3). Instantly cohesive and branded.
- **Color grade / LUT** — a consistent color cast across all imagery so a mixed set feels like one shoot.
- **Grain / noise overlay** — film texture over images; tactile, editorial, anti-digital (→§8.4).
- **Blur / depth** — background blur for depth or to sit text over imagery.
- **Masking & clipping** — images clipped into shapes, type (→§2.3), or organic blobs (→§1.7).
- **Blend modes** — multiply/screen/overlay to fuse image with color fields (→§8.5).
- **Cutout / knockout** — subject isolated from background; floats over layouts, breaks the grid.
- **Halftone / dithering / posterize** — limited-palette / tonal-reduction looks: halftone simulates continuous tone with varying dot size (a print process); dithering approximates colors with patterned noise (quantization); posterize *reduces* tonal levels into banding (an effect, not a print process). Halftone → §1 pop art / risograph.
- **Frames & crops** — aspect ratio, focal-point cropping (`object-fit: cover` + `object-position`), rounded vs hard corners, polaroid/bordered framing. Trap: a default center-crop decapitates faces on mobile.

**Delivery & performance** (the pipeline that decides whether good imagery actually loads well):
- **Formats** — **AVIF** (smallest, HDR/wide-gamut, ~94% support — use with a fallback) · **WebP** (~97%, the safe default) · **JPG** (photos, universal) · **PNG** (lossless, transparency, UI assets) · **SVG** (vector marks/icons/diagrams). Trap: PNG for photos bloats payload; AVIF with no fallback breaks old Safari.
- **Responsive images** — `srcset`/`sizes` to resolution-switch; `<picture>` to swap formats (AVIF→WebP→JPG) and art-direct crops. Trap: omitting `sizes` makes `srcset` pick the wrong file.
- **LQIP / BlurHash / ThumbHash** — a tiny encoded blur shown while the full image loads; kills the blank-flash and layout shift (built into `next/image` `placeholder="blur"`). Trap: skipping it = jarring pop-in and a CLS penalty.
- **Lazy-loading** — native `loading="lazy"` for below-fold images, paired with width/height to reserve space. Trap: lazy-loading the above-fold LCP image delays the hero and tanks Core Web Vitals.
- **Image CDN / DPR** — Cloudinary, imgix, Cloudflare Images, `next/image`: resize/reformat/focal-crop per request and serve 2×/3× density variants. Trap: a 1× asset on a 3× phone reads soft.

**Accessibility:**
- **Alt text — meaningful vs decorative** — informative images get descriptive `alt`; purely decorative ones get `alt=""` so screen readers skip them. Trap: verbose alt on decoration, or no alt on a meaningful chart.
- **Text-on-image contrast** — text over photography needs a scrim/overlay (→§8.4) to hold WCAG contrast. Trap: low-contrast captions burned onto busy imagery.
- **Motion / autoplay** — honor `prefers-reduced-motion` for looping/background video and cinemagraphs; offer a pause control for anything auto-looping >5s. Trap: unstoppable autoplay triggers vestibular issues and fails WCAG 2.2.

## 7.3 Iconography

A small but pervasive style signal — mismatched icons betray a system instantly.

- **Line / outline** — stroke-only; light, modern, the UI default. Pairs with self-drawing animation (→§2.6).
- **Filled / solid** — higher weight and contrast; better at small sizes and for active states.
- **Duotone / two-tone** — outline plus a single filled accent shape for depth and brand color (e.g. Phosphor's Duotone weight).
- **3D / rendered** — dimensional icons; playful-premium, heavier.
- **Hand-drawn / sketch** — imperfect, human (→§1.8).
- **Pictogram / glyph** — minimal universal symbols (wayfinding, dense UI).
- **Emoji** — instant tone and color; casual, risky for premium. 
- Sets worth knowing: **Lucide** (clean line; the actively-maintained fork of the now-dormant **Feather**, ISC license) · **Phosphor** (six weights incl. duotone, MIT) · **Heroicons** (Tailwind-native, MIT) · **Material Symbols** (variable, Apache) · **Tabler** (MIT) · **Remix** (Apache). Trap: never mix sets — stroke width and corner style won't match.

## 7.4 Illustration & 3D (technique)

Cross-references the aesthetic entries in §1.7–1.8; here as a media slot. Technique axis: **flat · gradient · isometric · line-art · 3D-rendered · low-poly · spot · collage/cut-paper · hand-drawn**. Choose one technique and keep it consistent across the site; a custom style beats stock, and a *mixed* set of styles reads as borrowed. Trap: "default Spline scene" and corporate-Memphis (§1.4) both signal generic — subvert or commission.

## 7.5 Video & motion media

- **Background video** — looping ambient footage behind content; atmospheric (→§5.14). Trap: file weight, autoplay/a11y, motion-distraction.
- **Cinemagraph** — mostly-still frame with one moving element; subtle, premium, light.
- **Product demo / screencast** — UI in motion; the clearest way to show software.
- **Explainer / motion graphic** — animated storytelling (→§4.3).
- **Looping micro-video** — short tactile loops in cards and features. Trap: ship muted MP4/WebM via `<video>`, not an actual `.gif` — GIF is an obsolete delivery format (huge files, 256 colors).
- **Scroll-scrubbed video** — frames tied to scroll position (Apple AirPods-style). High craft, heavy. Trap: bandwidth and decode cost.
- **Formats / codecs** — H.264 **MP4** (universal baseline) · **WebM**/VP9 and **AV1** (smaller, narrower support) — serve via multiple `<source>`. Always set a **poster** frame so the player isn't a black box before load. Trap: a single AV1 source with no MP4 fallback fails on older devices.
- **Lottie / SVG animation** — lightweight vector motion for icons and spots (→§4.3). Note: dotLottie state machines (2025) added interactive, input-driven Lottie — it's no longer playback-only.
- **Rive** — interactive vector animation with a real state-machine + data-binding runtime; files ~10× smaller than equivalent Lottie, GPU-rendered. For input-driven UI motion (toggles, mascots, hovers). Trap: heavier authoring than a static Lottie when you only need a play-once loop.

## 7.6 Backgrounds, textures & patterns

The layer behind content — often what separates flat-and-cheap from rich-and-designed.

- **Solid / flat color** — the honest default.
- **Gradient / mesh / aurora** — multi-stop color fields (→§1.3, §3). Depth and warmth behind flat content. Trap: gradients behind text kill legibility.
- **Noise / grain** — subtle texture over flat color or gradients; kills banding, adds tactility (→§8.4).
- **Geometric patterns** — dot grid, line grid, graph-paper/blueprint, crosshatch. Technical, structured. Pattern libraries (Hero Patterns, SVG Backgrounds) give tileable SVGs fast. Trap: stock patterns read generic at default opacity/color — tint to brand.
- **Organic / blob shapes** — soft fluid forms as accents (→§1.7).
- **Glow / spotlight fields** — radial light blooms, often cursor-reactive (→§4.4 deep glow).
- **Textures** — paper, concrete, fabric, halftone (→§1: grunge, risograph). 
- **Render target — SVG vs Canvas vs WebGL** — SVG: crisp, lightweight, DOM-addressable, best for static/simple shapes. Canvas 2D: many particles, raster. WebGL/shaders: GPU gradients, fluid/flow fields, the heavy-craft tier. Trap: WebGL for what an SVG gradient would do = needless bundle + battery cost.
- **Animated / generative backgrounds** — particle fields, shader gradients, flow fields (→§4.4). Trap: performance and distraction.
- **Decorative dividers** — wave, slant, curve, or zigzag section transitions. Trap: the literal SVG "wave divider" reads dated (a 2018–2020 tell) — prefer sharp angles, color-band changes, or none.

---

# 8. Surface & effects

The finishing craft applied to elements — depth, edges, light, texture. These are the low-level primitives the §1 "morphism" styles are *built from*; pulled together here as their own vocabulary because every aesthetic mixes them. Most define a small **scale** (a fixed set of steps), exactly like spacing and type.

## 8.1 Elevation & shadow

Implying depth and layering with light.

- **Drop shadow** — the standard lift; soft and subtle for modern UI, hard for retro/brutalist.
- **Elevation scale** — a defined ladder of depth steps mapped to importance. Note the model shifted: **Material 3 now leads with *tonal elevation*** (a surface-tint that lightens with level) and uses shadow only secondarily for strong separation — shadow is no longer the default depth cue. Trap: ad-hoc shadows per element flatten hierarchy.
- **Contact (key) + ambient shadow** — the realistic two-part model: one tight contact shadow + one soft ambient layer (what "layered shadow" means). Far more believable than a single blurry shadow.
- **Inner / inset shadow** — depth *into* the surface (`box-shadow: inset`; pressed, neumorphic §1.3).
- **Long shadow** — flat extended diagonal (flat-design era).
- **Colored / glow shadow** — shadow tinted with the element's color; modern, vivid, "neon-lift."
- **Hard / offset shadow** — solid, unblurred, displaced (neo-brutalism §1.2).
- **box-shadow vs `drop-shadow()`** — `box-shadow` traces the rectangular border box; `filter: drop-shadow()` traces the element's *alpha shape* (PNGs, clipped shapes, text). Trap: box-shadow on a transparent cut-out boxes the shadow.
- **Soft / diffuse** — large-radius low-opacity; premium calm. Trap: pure-black shadows look muddy — tint toward a darkened surface/brand hue (e.g. `color-mix` in oklch), not pure black and not the literal background color (which is invisible).
- **Dark-mode elevation** — shadows barely read on dark surfaces; convey depth with *lighter* surface tints (raised = lighter) plus hairline borders. Trap: faking depth with glow — glow reads as emphasis, not a cast shadow.

## 8.2 Borders, strokes & radius

The edge treatment of every box.

- **Border weight** — hairline (1px, quiet/editorial) · medium · thick (brutalist §1.2). 
- **Border style** — solid · dashed/dotted (informal, draft) · double · gradient border · animated/drawn border (→§5.8).
- **Corner radius scale** — a consistent set of radii (sharp 0 · subtle 4–8 · rounded 12–16 · pill 9999). **Keep one scale** — mixed radii is a top sloppiness tell. Sharp = editorial/technical; rounded = friendly/modern.
- **Hairline / sub-pixel border** — true 1px borders blur on HiDPI; hold a crisp rule with a `box-shadow` hairline, a scaled pseudo-element, or `0.5px`.
- **Focus ring** — the visible focus indicator; an accessibility requirement (WCAG **2.4.7 Focus Visible**, plus **2.4.13 Focus Appearance** in WCAG 2.2 for size/≥3:1 contrast), not decoration (→§5.10).
- **`:focus-visible` vs `:focus`** — `:focus-visible` shows the ring only for keyboard/AT focus, suppressing it on mouse click; the modern default. Trap: never `outline: none` without a `:focus-visible` replacement.
- **`outline-offset`** — pushes the ring off the element so it breathes (e.g. 3px outline + 2px offset) and draws it outside `overflow: hidden` clipping.
- **Outline vs border** — outline doesn't affect layout (good for focus/hover); border occupies space.

## 8.3 Blur, glass & backdrop

- **Backdrop blur** — `backdrop-filter` frosts whatever sits behind (glassmorphism §1.3, glass nav §5.3). ~88–90% support; needed `-webkit-` prefix until Safari 18, so gate with `@supports` and a solid fallback. Trap: large radii (>20px) and stacked instances jank on mobile; text contrast is fragile.
- **Layered transparency** — stacked translucent panels for depth (a compositing/multiple-background technique, kin to §8.5).
- **Gaussian / content blur** — blurring imagery for depth or to host text.
- **Progressive blur / gradient blur** — blur that ramps across an element (strengthening toward a sticky bar); the real technique is *stacked layers each with increasing `blur()` + a `mask` linear-gradient* — a single blur reads as a bloom, not a progression. A current premium detail.
- **Frosted scrim / glass contrast token** — a blurred + tinted layer guaranteeing text legibility over media; pair backdrop-blur with a semi-opaque tint token, since blur alone never guarantees WCAG contrast.

## 8.4 Glow, grain & overlays

- **Glow / bloom** — radiant light around elements; neon, dark-mode, futuristic (→§1.6, §4.4).
- **Grain / noise** — fine texture over surfaces; adds film tactility *and* dithers away gradient banding. The cheapest way to de-flatten a design. Ship it procedurally via **SVG `feTurbulence`** (resolution-independent, no raster asset).
- **Gradient banding / dithering** — smooth gradients band on 8-bit displays; fix with a faint noise overlay, a dithered gradient, or wider-gamut `oklch` interpolation. (This is the *mechanism* behind "grain kills banding.")
- **Gradient overlay / scrim token** — a fade over media so overlaid text stays readable; near-mandatory for text-on-photo. Centralize it as a named scrim token (e.g. `scrim-40`) reused for modal backdrops, text-on-media, and bottom-sheet dimming.
- **Vignette** — darkened edges focusing the center; cinematic.
- **Light leaks / lens flare** — analog light artifacts (Frutiger Aero §1.6, retro).
- **Dot / scanline overlays** — halftone or CRT texture (pop art, cyberpunk).

## 8.5 Fills, gradients, blend modes & masks

**Fills & gradients** (the cheapest non-flat surface):
- **Gradients as surface** — `linear` · `radial` · `conic` · `repeating-*`; mesh/multi-stop fields are the current premium look (→§3, §1.3). Trap: 2-stop gradients band — add a third stop or noise (§8.4).
- **Multiple backgrounds** — comma-stacked `background` layers (gradient over image over color) composited in one property; the basis for scrims, grain-over-photo, and texture stacks.
- **`color-mix()` / relative color** — derive tints, shades, shadow-tints, and dark-mode variants in CSS (`color-mix(in oklch, …)`, `rgb(from …)`), no preprocessor. Baseline widely available (2026).
- **CSS filter functions** — `blur · brightness · contrast · saturate · grayscale · sepia · hue-rotate · invert · drop-shadow`, chainable *on* an element (vs `backdrop-filter` on what's behind, §8.3).

**Blend modes & masks:**
- **Blend modes** — multiply/screen/overlay/difference to fuse layers (image + color, type + image). Rich, designed compositing. Trap: unpredictable across backgrounds — test on real content.
- **Clipping mask** — content shown only inside a shape or letterform (`clip-path`; →§2.3 image-in-type, §7.2).
- **SVG / alpha / gradient mask** — `mask-image` with an SVG or gradient fades an element to transparent (edge fades, scroll-edge fades on lists). `-webkit-mask` prefix still needed on some engines.
- **`shape-outside`** — wraps inline text around a non-rectangular float (circle, image alpha, polygon); an editorial surface primitive.
- **Mix-blend on text** — type that inverts against whatever scrolls behind it (`mix-blend-mode: difference`). A striking modern move. Trap: contrast becomes unpredictable.

## 8.6 Dividers & section transitions

- **Rule / hairline** — a simple line; the quiet editorial separator.
- **Spacing-only** — whitespace as the divider; the cleanest option.
- **Labeled divider** — a line broken by a word or icon ("or", section name).
- **Color-band transition** — adjacent full-bleed sections in different colors (→§6.4).
- **Shape transition** — slant, curve, wave, zigzag between sections. Trap: the literal wave divider reads dated; prefer sharp angles, a color-band change, or none.
- **Gradient fade** — one section melting into the next.

---

# 9. Accessibility — the aesthetic veto

Accessibility is not a layer you add — it's a constraint that outranks taste. WCAG 2.2 Level AA is the practical floor (legal baseline in most jurisdictions: ADA, EAA, AODA). When a visual choice fails a success criterion (SC), the visual choice loses. Below: the SCs that actually bite designers, verified against the spec. AAA is noted where relevant but is aspirational, not the bar.

## 9.1 Contrast

- **Text contrast** — body text needs **4.5:1**, large text **3:1** against its background (SC 1.4.3, AA). "Large" = **≥18pt (24px) regular, or ≥14pt (~18.66px) bold**. Measured as a ratio of relative luminance, background included. Trap: text over a photo passes in one crop, fails in another — gate the worst-case region, not the hero shot.
- **Non-text contrast** — UI components (input borders, toggles, focus rings) and meaningful graphics (icons, chart segments) need **3:1** against adjacent colors (SC 1.4.11, AA). The usual casualties of "clean" design: ghost buttons, 1px hairline inputs, low-contrast icons. Trap: a *decorative* border is exempt; a border that's the *only* signal "this is a field" is not.
- **Don't pair pure black on pure white** — `#000` on `#fff` is ~21:1 and induces halation, worse for astigmatism and dyslexia. Use off-black (`#1a1a1a`–`#222`) on off-white. A craft rule, not a WCAG rule — the spec won't stop you getting it wrong.
- **Trap: contrast is a luminance ratio, not "looks different."** Two saturated colors at equal luminance (red on green) read as zero contrast to the tool and to color-blind users while looking vivid to you.

## 9.2 Color & meaning

- **Color is never the sole signal** — information, state, or "which to click" must not rely on color alone (SC 1.4.1, A). Add text, icon, underline, pattern, or position. Casualties: required-field red, error/success states, active tabs, chart legends, link-vs-body. Trap: removing link underlines — color-only links fail unless they hit 3:1 against surrounding text *and* show a non-color cue on hover/focus.

## 9.3 Focus

The three focus SCs are distinct — get the numbering right:
- **Focus Visible** — every keyboard-operable control has a visible focus indicator (SC 2.4.7, **AA**). Trap: `outline: none` with nothing replacing it is the single most common AA failure.
- **Focus Not Obscured (Minimum)** — a focused component must not be *entirely* hidden by author content (SC 2.4.11, **AA**). Casualties: sticky headers/footers, cookie bars, chat widgets floating over the just-tabbed element. (Enhanced — *no part* hidden — is 2.4.12, AAA.)
- **Focus Appearance** — the indicator covers **≥ a 2px-thick perimeter** of the component and hits **3:1 contrast** vs the unfocused state (SC 2.4.13, **AAA**). Aspirational, but it's the spec's definition of a *good* ring — design to it.
- **Trap: don't reorder DOM for visual layout** — focus follows source order; a CSS-reordered grid sends focus jumping around the screen.

## 9.4 Target size & touch ergonomics

- **Target Size (Minimum)** — pointer targets ≥ **24×24 CSS px**, or 24px spacing between centers (SC 2.5.8, **AA**). Exceptions: inline text links, UA defaults, essential. Casualties: icon buttons, close (×) buttons, dense toolbars, pagination dots.
- **Target Size (Enhanced)** — ≥ **44×44 CSS px** (SC 2.5.5, **AAA**) — the number Apple HIG (44pt) and Material (48dp) already enforce. Treat 44 as the *design* target, 24 as the *legal* floor.
- **Touch ergonomics** — thumb-reach zones and spacing matter beyond raw hit area. Trap: hit area ≠ visual size — pad the clickable region, don't inflate the glyph.

## 9.5 Motion

- **Pause, Stop, Hide** — anything moving/blinking/scrolling that auto-starts, lasts **>5s**, and runs alongside other content needs a pause/stop/hide control (SC 2.2.2, A). Casualties: carousels, autoplay background video, marquees, animated backgrounds.
- **Animation from Interactions** — interaction-triggered motion (parallax, scroll-jacking, large transitions) must be disable-able unless essential (SC 2.3.3, **AAA**) — the honest implementation is honoring `prefers-reduced-motion`.
- **Three Flashes** — nothing flashes more than **3×/second** (SC 2.3.1, A). Seizure risk — a hard veto, not a preference.
- **Trap: `prefers-reduced-motion` means reduce, not delete** — swap large transforms/parallax for opacity fades; don't ship a dead, transition-less page.

## 9.6 Reflow & text spacing

- **Reflow** — content works at **320 CSS px** wide (≈400% zoom on a 1280px screen) with no 2-D scrolling (SC 1.4.10, AA). Exceptions: data tables, maps. Casualties: fixed-width layouts, wide tables, `min-width` forcing horizontal scroll.
- **Text Spacing** — no content lost when users override: line-height **1.5×**, paragraph **2×**, letter-spacing **0.12×**, word-spacing **0.16×** of font size (SC 1.4.12, AA). Trap: fixed-height buttons/cards/nav that clip when users bump spacing — design containers that grow.

## 9.7 Keyboard

- **Keyboard operable** — all functionality via keyboard, no timing-dependent keystrokes (SC 2.1.1, A). Every hover-only menu or drag-only reorder needs a keyboard path.
- **No keyboard trap** — focus that can enter a component can leave it via keyboard (SC 2.1.2, A). Casualties: custom modals/date-pickers/embeds that swallow Tab — implement Esc + focus return.
- **Focus order** — sequential focus preserves meaning (SC 2.4.3, A); follows DOM order, so CSS visual reordering desyncs it.
- **Skip links** — a "skip to main content" bypass for repeated blocks (SC 2.4.1, A). Trap: skip links hidden with `display:none` aren't focusable — use visually-hidden-until-focused.

## 9.8 Semantics & structure

- **Headings & landmarks** — logical `h1`–`h6` (no skipped levels for styling) plus landmark regions (`header/nav/main/footer`). Screen-reader users navigate by these. Trap: a styled `<div>` that *looks* like a heading is invisible to AT.
- **Alt text** — meaningful images get descriptive `alt`; decorative get `alt=""` (empty, not omitted). Trap: `alt="image"` or a filename is worse than empty.
- **Form labels** — every input has a programmatic `<label>` (or `aria-label`). Placeholder text is **not** a label — it vanishes on input and often fails contrast.
- **Name, Role, Value** — every component exposes an accessible name, role, and state to AT (SC 4.1.2, A). Casualties: any custom control built from `<div>`/`<span>` — toggles, tabs, comboboxes, sliders.

## 9.9 ARIA

- **First rule of ARIA: don't use ARIA** — if a native element has the semantics, use it. A real `<button>` beats `<div role="button" tabindex="0">` on every axis. ARIA changes semantics but adds zero behavior — you still wire keyboard handling yourself.
- **`aria-live`** — announces dynamic changes (toasts, validation, async results). `polite` waits for a pause; `assertive` interrupts (reserve for errors). Trap: the live region must exist in the DOM *before* content changes — injecting region and content together announces nothing.
- **Roles** — match the role to the actual pattern, then honor that pattern's full keyboard contract (a `role="tablist"` owes arrow-key nav). Trap: declaring a role you don't implement is worse than none.

## 9.10 CSS media features (user preferences)

- **`prefers-reduced-motion`** — `reduce` vs `no-preference`; the mechanism behind SC 2.3.3.
- **`prefers-contrast`** — `more`/`less`/`custom`; honor `more` by firming up borders and contrast.
- **`prefers-color-scheme`** — `light`/`dark`; re-check every contrast ratio per scheme.
- **`forced-colors`** — Windows High Contrast active; the OS overrides your colors. Trap: `background-image` backgrounds vanish; `box-shadow`/`outline` may be stripped — test it.

## 9.11 Media, cognition & language

- **Captions & transcripts** — synchronized captions for video, transcripts for audio.
- **Cognitive load** — short line lengths (~45–75 chars), generous whitespace, predictable layout, errors that say how to fix them. Load-bearing for cognitive disabilities, helps everyone.
- **Plain language** — short sentences, common words, front-loaded meaning, expanded acronyms. The cheapest accessibility win, the most ignored.
- **Screen-reader basics** — design is read linearly in DOM order; visual grouping ≠ semantic grouping. Icon-only buttons are silent without an accessible name; anything purely visual (color, position, proximity) doesn't exist to AT unless encoded in markup.

## 9.12 Tooling (necessary, not sufficient)

- **axe / axe DevTools** — the most accurate automated engine; catches missing labels, contrast, ARIA misuse.
- **Lighthouse** — bundled in Chrome DevTools; an axe subset plus perf/SEO. Convenient first pass, shallower.
- **Contrast checkers** — WebAIM Contrast Checker, DevTools picker, Figma plugins — catch ratios at design time.
- **Trap: automation catches ~30–40% of issues.** Keyboard-only walkthroughs, real screen-reader testing (VoiceOver/NVDA), and zoom/reflow checks find the rest. A clean axe scan is a floor, not a pass.

*Sources: [WCAG 2.2](https://www.w3.org/TR/WCAG22/); [Target Size (Minimum)](https://www.w3.org/WAI/WCAG22/Understanding/target-size-minimum.html).*

---

# 10. UX patterns, states & microcopy

Accessibility is a veto. Any pattern below that fails keyboard, screen-reader, contrast, or motion-sensitivity requirements (§9) is wrong here regardless of how good it looks.

## 10.1 The full state set

Every screen is a state machine. Designing only the happy path ships eight unhandled realities — enumerate all of them before calling a screen done.
- **Empty** — no data yet, by design (new account, fresh list). Not an error — an opportunity; pair with onboarding copy + a primary action. Trap: a blank rectangle that reads as "broken" instead of "nothing here yet."
- **Loading** — data in flight; spinner vs skeleton is a semantic choice (→§5.17). Trap: no loading state, so a slow network looks frozen.
- **Error** — say what broke + how to recover, never just "Something went wrong." Trap: a dead-end error with no retry or support path.
- **Success** — often a transient confirmation, sometimes a full state (receipt). Trap: silent success — user can't tell the click registered.
- **Partial** — some data loaded/failed, or the set is incomplete (paginated, streaming, degraded). Show what you have, flag what's missing.
- **Offline** — distinguish "you're offline" from "our server is down" — different user actions. Trap: generic "Network error" that blames the user's wifi when the API is 500-ing.
- **Zero-results** — data exists, this query missed (≠ empty). Offer escape hatches (clear filters, broaden, suggestions). Trap: "No results" with no way back.
- **First-run** — the highest-stakes empty state; set expectations, reduce to one obvious next move. Trap: dumping the full UI on someone with zero context and zero data.

## 10.2 Feedback mechanisms

- **Toast** — transient, non-blocking, corner-anchored; for confirmations and low-stakes status. Route through a live region; give dismiss a keyboard path. Trap: toasts for errors that need action — they auto-dismiss before the user reads them.
- **Inline validation** — message attached to the field it concerns; highest signal-to-noise. Trap: a summary-only error atop a long form, forcing a scavenger hunt.
- **Banner** — persistent, in-flow, page/section-level; for conditions that outlive one action (degraded service, trial expiring). Trap: banner blindness from overuse.
- **Optimistic UI** — apply the change immediately, before the server confirms, then reconcile; needs a rollback path. Trap: optimism on operations that fail often or are unsafe to show as done (payments, irreversible writes).
- **Undo vs Confirm — prefer Undo** — a confirm dialog interrupts *every* action to guard the *rare* mistake, training reflexive "Yes." Undo lets the action proceed and offers a grace-period reversal. Reserve confirmation for genuinely destructive-and-irreversible. Trap: a confirm dialog on a reversible action — pure friction, zero added safety.
- **Destructive-action confirmation** — name the consequence and object ("Delete 3 invoices? Can't be undone"), label the button with the verb, require deliberate friction for the catastrophic (type the name). Trap: destructive button styled like cancel, or pre-focused so Enter fires it.

## 10.3 UX laws (verified)

Laws every interface inherits. Source: Laws of UX unless noted — attribute them right or don't cite them.
- **Jakob's Law** (Nielsen) — users spend most time on *other* sites and expect yours to work like them. Convention is a feature; novelty is a tax. Trap: reinventing a solved pattern for distinctiveness.
- **Hick's Law** (Hick–Hyman) — decision time grows with the number/complexity of choices. Trap: using it to justify hiding *necessary* options — a well-categorized long list can beat five vague buckets.
- **Fitts's Law** (Fitts, 1954) — acquisition time scales with target distance and size; bigger + closer = faster. Use for primary buttons, edge/corner targets. Trap: tiny tap targets; destructive actions a hair from common ones.
- **Miller's Law** (Miller, 1956) — short-term memory holds ~7±2 *chunks* — but Miller called "seven" rhetorical; it described 1-D absolute judgment, not a UI cap, and modern working-memory estimates are ~3–4. The real lesson is **chunking**. Trap: citing "7±2" to cap menus at seven — that's the debunked myth.
- **Tesler's Law** (Conservation of Complexity) — every system has irreducible complexity; the only question is who absorbs it, user or builder. Trap: pushing inherent complexity onto users to keep code simple.
- **Postel's Law** (Robustness Principle) — be liberal in what you accept, conservative in what you send. Accept phone numbers with/without spaces, trimmed whitespace. Trap: rejecting valid intent over formatting — or over-liberalism that silently corrupts data.
- **Doherty Threshold** (Doherty & Thadhani, 1982) — productivity soars when response stays under **400ms**. Tools: optimistic UI, skeletons. Trap: bending it toward "addictive" pacing — speed serves the user, not the hook.
- **Peak-End Rule** (Kahneman) — people judge an experience by its most intense moment and its end. Invest in the peak and the closer. Trap: a flawless flow ending on a cold dead-end screen.
- **Aesthetic-Usability Effect** — users perceive attractive designs as more usable and forgive minor friction. Trap: polish masking real defects in testing.
- **Von Restorff Effect** (Isolation Effect) — the item that differs is the one remembered; use for a single primary CTA. Trap: emphasizing everything (so nothing stands out), or isolating by color *alone*.
- **Serial Position Effect** (Ebbinghaus) — list start (primacy) and end (recency) recalled best; the middle sags. Put the critical items first and last.
- **Zeigarnik Effect** — people feel pull toward *incomplete* tasks; use for progress bars and setup checklists. Trap: weaponizing it into nagging or never-resolving incompleteness.

## 10.4 Core patterns

- **Progressive disclosure** — show the common path first; reveal advanced options on demand. Trap: burying *frequently-needed* controls behind a disclosure.
- **Recognition over recall** (Nielsen heuristic) — let users recognize options rather than remember them (show choices, recent items, autocomplete). Trap: empty inputs with no scaffolding.
- **Smart defaults** — pre-fill the most likely value (locale, "Today", common plan). Trap: defaults serving the business over the user (pre-checked upsells = a dark pattern).
- **Forgiving formats** — accept input however the user provides it; normalize on the backend (Postel applied). Trap: rejecting valid data for one rigid format.
- **Inline help** — contextual assistance at the point of need. Trap: critical instructions only in a tooltip (hidden on touch, invisible to AT).
- **Onboarding** — three honest forms, ranked: **empty-state-as-onboarding** (teach through the real first action — most durable), **checklists** (Zeigarnik-driven), **tours** (coach-marks — use sparingly; most users skip them). Trap: a mandatory tour before the user has context.
- **Wayfinding / IA** — **hierarchical** (tree — broad catalogs), **hub-and-spoke** (central home — focused apps), **sequential** (linear — checkout, wizards). The **hamburger** hides nav behind a low-discoverability icon and depresses engagement with buried items — fine for secondary nav, costly for primary. Trap: hamburger on desktop where space is abundant.
- **Search-first** — lead with search when the content set is large or recall-driven. Trap: search-first for a small set faster to scan, or search that can't handle typos/synonyms.

## 10.5 Microcopy & UX writing

- **Button labels** — verb + object, describing the outcome: "Create account", "Delete project". Trap: "Submit", "OK", "Yes" describe the mechanism, not the result.
- **Error messages** — what happened + why (if useful) + how to fix, plain language, no codes, no blame. "That email's already registered — sign in instead?" beats "Error 409." Trap: blaming the user, vague dead-ends, raw stack traces.
- **Empty-state copy** — explain what goes here and how to start. Trap: a lone "No data" at a teachable moment.
- **Placeholder ≠ label** — placeholders vanish on input, tax memory, fail contrast. Every field needs a persistent visible label; use placeholders only for *example* format. This is an accessibility veto.
- **Tone / voice** — voice is constant (who you are); tone flexes with context. Calm in errors, warm in success, never jokey during a failure or payment.
- **Confirmation copy** — state the consequence and object specifically. Trap: generic "Are you sure?"
- **404 copy** — acknowledge plainly, then route out. Trap: a cute 404 with no navigation.

## 10.6 Forms UX

- **Single-column layout** — top-aligned labels; eyes flow straight down. Trap: side-by-side fields that break the vertical scan (exception: tightly-coupled pairs like Expiry/CVV).
- **Inline validation timing** — validate on blur or after a debounce, never before first input. Trap: red errors firing while the user is mid-typing their email.
- **Required vs optional marking** — mark whichever set is the minority, consistently; if most fields are required, label the *optional* ones. Trap: `*` alone (unexplained, color-only — fails AT and color-blind users).
- **Input masking** — format structured data as typed (card spacing, phone grouping) but keep the value forgiving and never block paste.
- **Autofill / autocomplete attributes** — correct `autocomplete` tokens (`email`, `tel`, `one-time-code`) + matching `inputmode`. Trap: omitting them, breaking autofill on mobile.

## 10.7 Sensory feedback

- **Custom cursor** (→§4.1) — reinforces brand and signals interactivity in expressive desktop work. Trap: a laggy/oversized cursor obscuring the click point (Fitts penalty); meaningless on touch; never hide the system cursor without reason.
- **Haptics** — vibration confirming a meaningful state change on mobile/wearables, subtly. Trap: haptics on every scroll-tick (battery, annoyance) — respect OS settings.
- **UI sound** — audio cues for notable, often non-visual events. Trap: sound by default with no mute, or info carried by audio *only* (fails deaf/HoH users). Default silent; let users opt in.

## 10.8 Dark patterns — forbidden

This doc has an anti-manipulation ethos. Named so they can't hide — don't ship them.
- **Confirmshaming** — guilting the user out of declining ("No thanks, I hate saving money"). Decline copy must be neutral.
- **Roach motel** — easy in, deliberately hard out (buried cancellation). Exit must be as easy as entry — increasingly a legal requirement.
- **Forced continuity** — a "free trial" that silently converts with no reminder and a hidden cancel. Warn before charging.
- **Disguised ads** — advertising masquerading as content or system UI (fake "Download" buttons). Ads must be unmistakably labeled.
- **Nagging** — relentless repeat prompts ignoring "not now". Respect a decline; provide a real "don't ask again". *The Zeigarnik, Von Restorff, and Doherty effects can each be bent toward these — the line: does it help the user finish* their *goal, or trap them in ours?*

*Sources: [Laws of UX](https://lawsofux.com/laws/); [UX Myths — the 7±2 myth](https://uxmyths.com/post/931925744/myth-23-choices-should-always-be-limited-to-seven); [NN/g](https://www.nngroup.com/).*

---

# 11. Page-type anatomy

Conventional block sequence + the highest-leverage note per page type. Heroes, footers, nav, and marketing blocks are catalogued in §5 — this section is about *order* and *job*, not the parts. Commerce/checkout claims trace to Baymard Institute and NN/g.

## 11.1 Marketing

- **Landing / home** — orient a cold visitor and route to one next step: hero (→§5.14) → social-proof strip → 2–4 value props → how-it-works → testimonial → pricing teaser → FAQ → final CTA + footer. Make-or-break: one dominant CTA, a hero stating value in <5s. Trap: three coequal CTAs; a hero describing the company, not the visitor's problem.
- **Product / feature** — prove one capability: feature hero → problem framing → capability breakdown (alternating media/text, not a 3-up grid) → proof/metric → CTA. Make-or-break: every section ladders to one outcome. Trap: a generic 3-column "features" wall.
- **Pricing** — let a ready buyer self-select: plan comparison (2–4 tiers, one anchored "most popular") → feature matrix → billing toggle → FAQ (billing, cancellation, refunds) → CTA. Make-or-break: anchor a recommended tier; answer objections at the point of doubt. Trap: "Contact sales" on a self-serve product; a matrix needing a glossary.
- **About** — build trust via mission, people, traction: narrative hero → mission → team → milestones/values → press → careers + CTA. Make-or-break: a real point of view. Trap: stock-photo platitudes.
- **Contact** — short intro → method picker (form/email/phone/chat) → form → response-time expectation → map/hours. Make-or-break: minimal fields + "what happens next." Trap: a 12-field form as the only path.
- **Careers (index + role)** — culture hero → values/benefits → team life → open roles → role detail (summary → responsibilities → requirements → comp/location → apply). Make-or-break: honest comp/location + frictionless apply.
- **Blog index** — header → featured/recent → category filter → card grid (title, excerpt, date, read-time) → pagination → newsletter CTA. Make-or-break: scannable cards + working filtering. Trap: infinite undated cards with no taxonomy.
- **Blog article** — title + byline/date → lede → body (headings, pull quotes, TOC for long reads) → author bio → related → CTA. Make-or-break: skimmable structure + fast first paragraph.
- **Case study** — client/result headline → context → challenge → solution → quantified outcome → pull quote → CTA. Make-or-break: a hard metric up top. Trap: process narrative with no numbers.
- **Resource / docs hub** — prominent search → category cards → getting-started → recently-updated → sidebar nav inside. Make-or-break: working search + sane hierarchy. Trap: category sprawl with no search.
- **Comparison / "vs"** — framing intro → at-a-glance table → dimension breakdown → "best for" segmentation → switch CTA. Make-or-break: concede where the competitor wins — credibility buys the close. Trap: a rigged table readers see through.
- **Legal** — last-updated date → TOC/anchors → numbered sections → contact → effective date. Make-or-break: anchored nav + plain-language summaries beside dense clauses.

## 11.2 Commerce

- **Category / PLP** — header + breadcrumb → filter/sort rail → product grid (image, title, price, rating, swatches) → pagination → SEO copy. Make-or-break: filtering that maps to how people shop + a live-updating result count. Trap: filters that reload and lose scroll.
- **Product detail / PDP** — gallery → title + price + rating → variant selector → **buy box (Add to Cart)** → shipping/returns → description/specs → reviews → cross-sell. Make-or-break: an unbroken buy box, clear variant state, **sticky Add-to-Cart on mobile** (Baymard). Trap: a gallery hiding most images; variant ambiguity.
- **Cart** — line items (image, variant, qty, price, remove) → editable quantities → subtotal + shipping/fees estimate → reassurance → "Checkout" + "Continue shopping". Make-or-break: surface *total* cost (shipping/tax) before checkout — surprise fees are the #1 abandonment driver (Baymard). Trap: hidden shipping until step 3.
- **Checkout (steps)** — guest/account choice → contact → shipping → delivery method → payment → review → place order. Keep to ~5 phases / ≤8 fields (Baymard: most sites use 11, need 8). Make-or-break: **prominent guest checkout** (forcing accounts is a top abandonment cause). Trap: account wall before the cart is captured; a progress bar that lies.
- **Order confirmation** — headline + order # → summary → tracking estimate → next steps → soft cross-sell. Make-or-break: a real expectation ("ships in 2 days, tracking emailed"). Trap: dead-end page with no order number or support path.
- **Search results** — query echo + count → filter/sort → grid → zero-results state with suggestions → recent/popular fallback. Make-or-break: a useful no-results state, never a blank page. Trap: ignoring typos/synonyms.
- **Wishlist / saved** — saved grid (image, price, in-stock/price-change flag) → move-to-cart → share → empty state. Make-or-break: price-drop / back-in-stock signals. Trap: losing the list on logout.

## 11.3 App / product

- **Dashboard / overview** — greeting/context bar → key KPIs → activity/feed → quick actions → secondary modules. Make-or-break: answer "what should I do next?" above the fold. Trap: a vanity-metric wall with no action.
- **Settings** — grouped sections (account, team, billing, notifications, security) → nav/search → per-setting controls with inline save → destructive actions isolated. Make-or-break: logical grouping + immediate save feedback. Trap: destructive actions next to benign toggles.
- **Profile** — avatar + identity header → editable fields → role/permissions → activity → connected accounts. Make-or-break: clear edit affordance + clean view↔edit transition. Trap: conflating "profile" with "account settings."
- **Onboarding / setup** — welcome → progressive steps (profile → config → invite/connect) → progress indicator → skip → success → empty-state handoff. Make-or-break: show progress, allow skip, end at an *activated* state. Trap: a mandatory wall before any value.
- **Data table / list view** — toolbar (search, filter, bulk actions) → sortable headers → rows → row actions → pagination → empty/loading/error states (→§5.13). Make-or-break: sticky header + sort/filter that survive navigation. Trap: unbounded rows; no empty/loading state.
- **Detail / record view** — header (title, status, primary actions) → key attributes → tabs (activity, related, notes) → audit/history. Make-or-break: primary action + status obvious on entry. Trap: burying the status.
- **Billing** — current plan + usage → payment method → invoice history → upgrade/downgrade → cancellation. Make-or-break: transparent next-charge preview; findable cancellation (not dark-patterned). Trap: hiding the cancel path.
- **Notifications / inbox** — filter (all/unread) → grouped list → read/unread state → bulk actions → per-item deep link → empty state. Make-or-break: clear unread affordance + "mark all read"; each item links to its source.
- **Empty workspace** — illustration/headline → one-line explanation → primary "create/import" CTA → template shortcut → docs link. Make-or-break: a single obvious first action. Trap: a literal empty page.

## 11.4 System

- **Auth (login / signup / SSO / reset / 2FA)** — logo → form (email+password, or SSO first) → primary action → secondary links (forgot, switch mode) → consent on signup. Reset: request → email-sent confirmation → new-password → success. Make-or-break: persistent labels, inline validation ~500ms after typing stops, SSO surfaced before manual entry where it's the norm. Trap: placeholder-as-label; vague "invalid credentials"; a reset flow with no "email sent" confirmation.
- **404 / not-found** — plain-language headline ("This page doesn't exist", not "Error 404") → retained nav + footer → search → ~4 helpful links → optional personality. Make-or-break: keep nav + search so it's an offramp, not a wall (NN/g). Trap: a bare "404" with no navigation.
- **500 / server error** — plain apology → "not your fault" → retry/refresh → status-page/support link → keep nav. Make-or-break: a retry path + reassurance data is safe; never a stack trace.
- **Maintenance** — status headline → what's happening → ETA → status-page link → contact. Make-or-break: a concrete ETA, not "back soon."
- **Coming-soon / waitlist** — teaser hero → value prop → email capture (single field) → social proof/launch date → share/referral. Make-or-break: one field + a reason to care; confirm the signup.
- **Paywall / gate** — value reminder → plan/price → primary unlock CTA → trust/guarantee → "maybe later" escape. Make-or-break: anchor the gate to the value just reached; always offer a graceful exit. Trap: a hard wall with no back-out.

*Sources: [Baymard — checkout UX](https://baymard.com/blog/current-state-of-checkout-ux); [Baymard — product page](https://baymard.com/research/product-page); [NN/g — 404s](https://www.nngroup.com/articles/improving-dreaded-404-error-message/).*

---

# 12. Branding & identity

Identity is the system, not the logo. The logo is one artifact; the system is what makes two unrelated screens read as the same brand. Accessibility-gated throughout — a mark, color, or motion that fails contrast or reduced-motion isn't "bold," it's broken. Cross-refs: color → §3, type → §2 / §16, imagery & icons → §7.

## 12.1 Logo types

Standard taxonomy is the **seven-type framework** (lettermark, wordmark, pictorial, abstract, combination, emblem, mascot); dynamic/responsive marks are the modern extension.
- **Wordmark / logotype** — the full name in a distinctive, often custom face; no symbol (Google, Visa). When: short, distinctive name you want *read* and remembered. Trap: long/generic names turn to mush small — and you still owe a separate symbol for the favicon.
- **Lettermark / monogram** — initials, typographically styled (IBM, HBO). When: long/multi-word names; density. Trap: initials say nothing about what you do; collision-prone.
- **Pictorial mark** — a recognizable literal image (Apple, Target). When: the image maps cleanly, or you've earned symbol-only recognition. Trap: only the already-famous can drop the name.
- **Abstract mark** — a bespoke geometric form for a feeling, not a thing (Nike swoosh, Mastercard). When: diversified/category-spanning brands wanting emotion over description. Trap: meaning must be *built* through exposure.
- **Combination mark** — symbol + wordmark, usable jointly or split; the default safe choice. When: new brands needing recognition *and* a name. Trap: you must design the split deliberately or the symbol never earns independence.
- **Emblem / badge** — name enclosed in a contained shape (Starbucks, university seals). When: heritage, craft, institutional, automotive. Trap: detail-dense emblems collapse at favicon/embroidery scale.
- **Mascot logo** — an illustrated character (Mailchimp's Freddie, Michelin Man). When: family/consumer brands, sports. Trap: the worst-scaling mark; expensive to keep consistent; can read childish for B2B.
- **Dynamic / responsive logo** — one identity as a *system* adapting to context/data (MIT Media Lab, MTV). When: media/culture/tech across many surfaces. Trap: needs an ironclad rule set or it stops reading as one brand.

## 12.2 Logo construction & usage

- **Clear space / exclusion zone** — mandatory margin defined in terms of the mark itself ("keep 1× cap-height clear"). Trap: defining it in fixed px — breaks on resize.
- **Minimum size** — smallest size where it stays legible, per medium; below it switch to a simpler variant.
- **Lockups** — the *approved* fixed arrangements (horizontal, stacked, symbol-only). Ship a set; forbid ad-hoc recombination.
- **Responsive logo scaling** — staged simplification: **full lockup → compact → icon-only**; detail drops as size drops. Trap: one bitmap scaled down.
- **Monochrome / knockout versions** — single-color positive, reversed/white, and black/white variants. Trap: a logo that only exists in full color dies on an uncontrolled background.
- **Do's & don'ts** — the explicit misuse gallery (no stretching, recoloring, rotating, effects, low-contrast placement). Accessibility veto: every approved placement must clear contrast.

## 12.3 Favicon & app icons

Current best practice is the **lean modern set**, not the legacy 20-file dump.
- **Favicon (.ico / SVG)** — ship `favicon.svg` as primary (scales, supports dark-mode swaps) + a multi-res `favicon.ico` (16/32/48) fallback. Trap: shipping only a 16×16 PNG.
- **Apple touch icon** — `apple-touch-icon.png` at **180×180**, **opaque** (Safari fills transparency with black). iOS rounds it for you. Trap: transparent background → black corners.
- **PWA maskable icons + safe zone** — manifest icons `"purpose": "maskable"` so launchers crop to any shape; keep critical content inside a **center circle of 40% radius (≈80%)** — the outer 10% per edge may be cropped. Provide 192 + 512 with generous padding. Trap: reusing tight favicon art as maskable.
- **theme-color** — `<meta name="theme-color">` tints the browser/OS chrome; pair light/dark. Trap: a theme-color failing contrast against system UI.

## 12.4 Color in branding

Brand palette and *UI tokens* are different layers — never paint UI straight from raw brand hex (→§3, §15).
- **Primary / secondary / accent roles** — primary carries the brand; secondary supports; accent is the scarce high-energy color for CTAs and focus. Roles, not just swatches. Trap: three equal-weight "brand colors" with no hierarchy.
- **Semantic colors** — success/warning/error/info, bound to function. Trap: reusing the brand accent as the error color.
- **Neutrals** — the grayscale doing 90% of real UI work (text, borders, surfaces). Trap: pure `#000`/`#fff` only, or a flat gray with no tint relationship to the brand.
- **60-30-10 rule** — ~60% dominant/neutral, ~30% secondary, ~10% accent; keeps the loud color scarce. A balance heuristic, not pixel-math.
- **Brand hue → accessible token** — raw brand hex is a *source*, not a token; map through a token layer where every pairing is contrast-validated. When a brand hue fails contrast, the token shifts — the brand bends, the requirement doesn't.

## 12.5 Type in branding

Cross-ref §2 and §16.
- **Brand typeface vs system stack** — a display/brand face carries identity in headlines and the wordmark; a system/subset stack carries body and dense UI for speed. Most brands run both. Trap: forcing a characterful display face into 14px body.
- **Type as brand voice** — typeface choice *is* tone (grotesque = neutral-modern, humanist serif = trustworthy-editorial, mono = technical, rounded sans = friendly). Trap: a face whose personality contradicts the copy's voice, or a trendy face that fails at body sizes / lacks language coverage.

## 12.6 Brand systems

- **Brand guidelines / style guide** — the canonical rulebook (logo, color tokens, type, imagery, voice, motion, do's/don'ts); the single source of truth. Trap: a 90-page PDF nobody opens — guidelines must be living and linked to actual tokens/components.
- **Voice & tone** — voice is the constant personality; tone flexes by context. Document with real do/don't examples. Trap: defining voice with adjectives only ("bold, human, smart").
- **Brand architecture** — **masterbrand/branded-house** (one master endorses all — Google) vs **house-of-brands** (independent, hidden parent — P&G) vs endorsed/hybrid. Governs naming and inherited equity. Trap: picking an architecture by accident as products accrete.
- **Naming** — descriptive vs evocative vs abstract, plus trademark/URL clearance and lockup fit. Trap: clever names that can't be trademarked or are unpronounceable.
- **Taglines** — the short ownable line carrying positioning ("Just Do It"), distinct from a campaign slogan. Trap: a tagline describing a feature instead of a stance.

## 12.7 Motion & sonic branding

- **Logo animation** — the canonical reveal (build, draw-on, morph) for splashes, intros, loaders; one signature gesture. Trap: a 4-second hero animation gating content every load. Accessibility veto: honor `prefers-reduced-motion`; never flash beyond 3/second.
- **Brand motion principles** — system-wide rules for *how* the brand moves (shared easing curves, duration scale, personality). Motion is an identity layer. Trap: ad-hoc per-screen animation with no shared curves.
- **Sonic logo / audio identity** — the short ownable signature (Netflix "ta-dum", Intel bong) plus UI feedback tones. Trap: auto-playing sound with no mute, or meaning carried by audio *only* — always pair with a visual/haptic equivalent.

## 12.8 Imagery & iconography as identity

Cross-ref §7.
- **Photography / illustration style** — a defined, repeatable treatment (subject, lighting, color grade, crop) that makes images recognizable as *yours* before the logo appears. Trap: a mood board with no enforceable rules — the feed drifts to stock within a quarter.
- **Iconography as identity** — a cohesive set with fixed grid, stroke weight, radius, and metaphor language tuned to the brand. Consistency *is* the signal. Trap: mixing icon families/weights; icon-only controls with no accessible label.

*Sources: [VistaPrint — types of logos](https://www.vistaprint.com/hub/types-of-logos); [web.dev — maskable icons](https://web.dev/articles/maskable-icon); [Evil Martians — favicons](https://evilmartians.com/chronicles/how-to-favicon-in-2021-six-files-that-fit-most-needs).*

---

# 13. Data visualization

The chart is an argument, not decoration. Every mark either carries meaning or steals attention from one that does. Pick the form from the *question*, not the spreadsheet. Accessibility is a veto: a chart that excludes readers fails however it looks.

## 13.1 Selection framework

Match the chart to the question, not the data shape. Five questions cover most cases: *Which is bigger? How is it changing? How is it spread? What is it made of? What relates to what?*
- **Comparison → bar** — ranks categories by one value; the workhorse. Trap: unordered bars — sort by value unless category order is meaningful.
- **Comparison → grouped bar** — 2–3 sub-groups per category. Trap: >~3 series becomes a striped wall — switch to small multiples.
- **Comparison → stacked bar** — totals + rough breakdown. Trap: only the bottom segment shares a baseline; middle slices are hard to compare across bars.
- **Comparison → bullet** — one measure vs a target with bands; a compact gauge replacement. Trap: needs labels or the bands read as noise.
- **Trend → line** — a continuous value over ordered time; the default for "how is it changing." Trap: connecting categorical points implies false continuity — use bars.
- **Trend → area** — magnitude emphasis or cumulative total. Trap: overlapping filled areas occlude; stacked areas inherit the baseline problem.
- **Trend → sparkline** — a word-sized trend, no axes; in tables. Trap: don't add gridlines/labels — defeats the point.
- **Trend → candlestick** — OHLC per period; finance-specific. Trap: state the up/down color convention.
- **Distribution → histogram** — shape of one continuous variable. Trap: bin width *is* the analysis — too wide hides structure, too narrow shows noise.
- **Distribution → box plot** — median/quartiles/outliers, compact across groups. Trap: hides multimodality.
- **Distribution → violin** — box plot + full density curve. Trap: unfamiliar to general audiences; needs enough data per group.
- **Distribution → scatter** — every raw point; reveals clusters/outliers. Trap: overplotting — use opacity, binning, or a heatmap.
- **Distribution → beeswarm** — every point along one axis, nudged to avoid overlap. Trap: doesn't scale to large n — collapses into a blob.
- **Composition → pie** — parts of a single whole, at a glance. Reach **only** for ~2–5 slices with one dominant share. Trap: humans compare angles poorly — more than ~5 slices, near-equal slices, or any cross-pie comparison and a bar wins. Often the right move is *not* a pie.
- **Composition → donut** — a pie with a center label; same constraints, no better at the angle problem.
- **Composition → 100% stacked bar** — part-to-whole across categories. Trap: only the end segments compare easily.
- **Composition → treemap** — nested rectangles sized by value; many hierarchical parts. Trap: area reads less accurately than length; thin slivers become unlabelable.
- **Composition → waterfall** — how a start value reaches an end through +/− steps (revenue → profit). Trap: needs up/down encoding not reliant on color alone.
- **Relationship → scatter** — correlation between two quantities. Trap: correlation ≠ causation; a fitted line implies more confidence than the cloud supports.
- **Relationship → bubble** — scatter with a third variable as dot size. Trap: scale by *area*, not radius; a fourth (color) dimension is near the legibility limit.
- **Relationship → heatmap** — a value across two categorical axes via color. Trap: relies entirely on color — use a perceptually-uniform scale and label extremes.
- **Relationship → network** — nodes + edges for topology/clusters. Trap: past a few dozen nodes it's a hairball.
- **Geospatial → choropleth** — a metric shaded by region. Trap: shades by area, so empty regions dominate — **normalize to a rate** (per capita), never raw counts.
- **Geospatial → symbol map** — sized markers at points; absolute counts. Trap: overlapping symbols occlude — cluster/aggregate.
- **Hierarchy → sunburst** — radial rings from a root. Trap: outer rings have tiny angular slices — rarely beats a treemap or indented list.
- **Single value → big number / KPI** — one metric as large type with a delta. Trap: a number with no comparison (target, prior period) is context-free.
- **Single value → gauge** — *the gauge debate*: wastes space for one number and the dial distorts perception. Reach for a bullet or KPI-with-delta instead. Trap: using a gauge at all is usually the trap.
- **Flow → sankey** — quantities flowing/splitting between stages; widths encode volume. Trap: many crossing flows become spaghetti.
- **Flow → funnel** — drop-off across ordered stages (signup → activation → purchase). Trap: implies strict sequential progression — misleading when users skip or re-enter.

## 13.2 Chart selection

- **Question before data** — the same table answers different questions with different charts; choose by intent.
- **Bar vs line** — bars for discrete categories compared against each other; lines for a continuous variable where the *connection between points* is meaningful.
- **Pie discipline** — max ~5 slices, one dominant share, no cross-pie comparison; when in doubt, a sorted bar.
- **Fewer chart types per surface** — a dashboard speaking three chart vocabularies forces re-learning at each panel. Standardize.

## 13.3 Data color

Color encodes data, not mood; the palette type must match the data type or the chart lies.
- **Categorical (qualitative)** — distinct hues for unordered groups; ~6–8 distinguishable max before switching to shape/position/small-multiples.
- **Sequential** — one hue ramping light→dark for ordered low→high; light = low, don't invert.
- **Diverging** — two hues meeting at a meaningful midpoint (zero, average). Trap: a diverging scale on data with no real center invents one.
- **Colorblind-safe is non-negotiable** — ~**8% of men** (~0.5% of women) have red-green deficiency, the most common dashboard combination. Use vetted palettes — **ColorBrewer** (flags colorblind-safe schemes) or **viridis** (perceptually uniform, colorblind-safe by design). Verify with a simulator.
- **Never color alone** — direct-label lines/segments instead of a legend round-trip; add pattern/shape/position so the chart survives grayscale and color blindness.

## 13.4 Dashboard design

A dashboard is an information *hierarchy*, not a grid of every chart you have.
- **Most-important-top-left** — Western readers scan in an F-pattern (→§6.3); put the headline KPI there, bury detail bottom-right.
- **Density, deliberately** — high data density is good (Tufte) but needs hierarchy; group related panels, leave whitespace as structure.
- **KPI cards** — big number + delta vs prior/target + optional sparkline; one glance, full context.
- **Drill-down** — summary on top, detail one interaction away.
- **Small multiples** — a grid of identical small charts with shared axes; compare many series without overplotting, learn the encoding once.

## 13.5 Principles

Sourced to Edward Tufte unless noted; attribute when you cite.
- **Data-ink ratio** — maximize the share of ink encoding data; erase the rest. Trap: zealotry — stripping every gridline until unreadable.
- **Chartjunk** — remove decorative non-data elements (3-D, heavy gridlines, gradients, background images).
- **Sparklines** — word-sized, axis-free graphics inline; show shape without breaking reading flow.
- **Small multiples** — a series of small, same-scale charts; the most honest way to compare many categories.
- **Lie factor** — the ratio of visual change shown to numerical change in the data; truthful sits near **1.0** (~0.95–1.05).
- **Axis honesty** — **start bar-chart axes at zero** (bar length encodes magnitude; a truncated baseline exaggerates). Line charts measuring *change* may legitimately zoom — but label it, never silently truncate.
- **Aspect ratio / banking to 45°** — proportions change the story; banking the average slope toward ~45° aids rate-of-change judgment.
- **Annotation over legends** — label data directly; a legend forces a color→meaning lookup every glance.
- **Mobile / responsive dataviz** — charts must reflow, not shrink: drop ticks, rotate/truncate labels, switch dense charts to summaries. Design the small breakpoint as its own chart.

## 13.6 Accessibility

- **Alt text + table fallback** — every chart needs a text alternative stating the *takeaway*, plus the underlying data as an accessible `<table>`.
- **Contrast** — data marks, labels, and axes meet contrast minimums (§9), including the lightest end of a sequential ramp.
- **Patterns + color, never color alone** — encode with texture/shape/line-style/position so it survives color blindness and grayscale.
- **Focus on interactive charts** — tooltips, filters, drill-down must be keyboard-reachable with a visible focus indicator and an accessible name. Hover-only info is invisible to keyboard/touch.

*Sources: [Tufte — Wikipedia](https://en.wikipedia.org/wiki/Edward_Tufte); [red-green deficiency prevalence — PubMed](https://pubmed.ncbi.nlm.nih.gov/22472762/); ColorBrewer; viridis.*

---

# 14. Emerging & AI-era interfaces

**Dated 2026. High volatility — treat like the Y2K / Frutiger-Aero entries (§1.6).** Patterns here are 12–36 months old, conventions are still hardening, vendor libraries churn quarterly, and the regulatory floor (provenance disclosure) shifts in 2026. Re-audit annually. Hype vs load-bearing is flagged inline. Accessibility is a veto: none ship if they break keyboard, screen-reader, reduced-motion, or contrast (§9).

## 14.1 Conversational UI

- **Chat thread** — the linear message log repurposed as the default AI shell; dominant since ChatGPT (2022) made it the public mental model. Cheap, familiar, scales badly — long reasoning, tables, and branching don't fit a stream. Trap: defaulting to chat for what's really a form or a filter.
- **Message bubbles** — rounded, role-tinted containers from messaging apps. Wastes horizontal space, fights long-form/code. Trap: bubbling a 600-word answer with code — many 2025 tools dropped the AI-side bubble for full-width prose.
- **The blank input box** — an empty field with no affordance for *what to type*; the biggest cold-start failure. Trap: shipping the empty box alone — pair with starters or examples, always.
- **Suggested prompts / starters** — clickable seed prompts on empty state or after a turn; the standard antidote to the blank box. Trap: stale, generic, context-blind suggestions erode trust faster than none.
- **System vs user roles** — the conversational triad (system/user/assistant) leaking into UI. Trap: exposing raw system-prompt scaffolding to end users.

## 14.2 AI assistant patterns

- **Streaming / token-by-token output** — text rendered progressively; the expected default (an instant full response reads as canned). Masks latency, lets users bail early. Trap: layout shift as tokens land, jumpy scroll, no stop button; honor `prefers-reduced-motion`.
- **"Thinking" / reasoning states** — a visible affordance the model is deliberating (collapsible chain-of-thought); mainstreamed by reasoning models (2024–25). Trap: theater — fake/padded thinking is dishonest; exposing raw scratchpad confuses. Collapsible, never mandatory reading.
- **Citations & source attribution** — inline footnote chips tracing a claim to a source; the core trust primitive for RAG. Trap: *citation theater* — plausible links that don't support the claim (a CJR study found ChatGPT misattributed 76% of 200 quotes). A citation nobody checks is decoration; worse, it manufactures false confidence.
- **Inline AI actions** — AI invoked in place on selected content (rewrite, explain, fix). Keeps flow, scopes context. Trap: ✨-sparkle-everywhere — bolting an AI button onto every surface with no real job.
- **Prompt UI: slash commands & @-mentions** — `/command` for actions, `@mention` for context (files, tools); conventionalized by Copilot, Cursor, Linear. Trap: hidden grammar with no menu/autocomplete — a worse blank box.
- **Regenerate / edit** — re-roll the answer, or edit a prior turn and re-run; table-stakes recovery. Trap: regenerate that silently discards the prior answer with no compare/undo.
- **Confidence / uncertainty signaling** — surfacing model uncertainty (hedges, "I'm not sure, but…"); recommended by NN/g, rare in practice. Trap: false precision (a "92% confident" badge the model can't justify) is worse than honest hedging.
- **AI loading states** — staged status ("Searching… Reading… Writing…") for the gap before a response. Trap: a generic spinner for a 40-second agent run — show *what* it's doing.
- **Copilots / sidebars vs inline** — assistant as persistent docked panel vs summoned at the cursor. Sidebar = ongoing companion; inline = scoped edits. Trap: a sidebar stealing 30% of width for a feature used 5% of the time.
- **⌘K command-bar-as-AI** — the command palette fused with a prompt box; ⌘K now means "ask or act." Keyboard-first, blends search + commands + generation. Trap: keyboard-only discovery — needs a visible entry point too.

## 14.3 Agentic UI

- **Plan / step display** — the agent's intended sequence as a checklist before/while executing; lets users course-correct. Trap: a read-only plan the user can see but not stop or edit is narration, not control.
- **Tool-call transparency** — exposing which tool was invoked, with what args and result (expandable cards); the agentic analog of citations. Trap: a firehose of raw JSON nobody reads — or hiding tool calls entirely (an unaccountable black box).
- **Human-in-the-loop approval** — agent pauses at consequential actions (send, pay, delete, deploy) for sign-off; the primary safety gate. Trap: **confirmation fatigue** — too many approvals and users rubber-stamp; also the known bug of the approved payload mutating between approval and execution — pin it, gate only what matters.
- **Long-running progress** — durable progress for minute-to-hour tasks (status timeline, partial results, notify-on-done); lets users leave and return. Trap: progress bars that lie (stuck at 90%), or no way to background the task.

## 14.4 Trust & safety UX

- **Hallucination guardrails in UI** — verify-this prompts, source-required modes, "I couldn't find that" over invention; shifts burden to checking the output. Trap: UI can *frame* uncertainty; it cannot *make* the answer true.
- **"AI can make mistakes" disclaimers** — the ubiquitous small-print; legally defensive, behaviorally near-worthless. Trap: using the disclaimer as the *entire* trust strategy — banner-blind users never read it. A floor, not a feature.
- **Undo / review for AI actions** — preview-diff-before-apply and reversible edits (accept/reject, revert); makes AI mutation safe to try. Trap: irreversible AI actions with no diff and no undo — the fastest way to lose trust.
- **Provenance / watermarking** — C2PA Content Credentials (signed manifest; ISO/IEC 22144, 2025) + invisible watermarks (SynthID). Increasingly *mandatory* (California SB 942 in effect Jan 2026; EU AI Act Art. 50 enforcement Aug 2026). Trap: assuming a watermark survives a screenshot/re-encode — metadata strips easily, which is why the two-layer approach exists. Disclosure is no longer optional.

## 14.5 Generative & variable design

- **AI-generated layouts / themes** — interfaces synthesized on demand (generative UI, streamed components from tool results). Bespoke-at-scale first drafts. Trap: ungoverned generation produces inconsistent, inaccessible, off-brand UI — constrain to a token system + component allowlist or it's slop with a layout (→§7.1).
- **Personalization at scale** — per-user adaptive layout/content driven by inference. Trap: filter-bubble UI where no two users see the same thing — undermines shared reference, support, QA; inferred attributes are a privacy/bias liability.
- **Variable / parametric brand systems** — brand as a parameterized system flexing per context (→§12.1 dynamic logos). Trap: "flexible" sliding into formless — without hard invariants it stops reading as one brand.

## 14.6 Spatial & immersive

- **visionOS / spatial UI** — depth-layered, translucent "glass" interfaces floating in 3D space for glanceability and gaze focus; refreshed as "Liquid Glass" in visionOS 26 (→§1.3). Trap: neck strain (content too high/low), legibility over busy real-world backgrounds, porting flat 2D layouts unchanged.
- **Gaze + pinch** — look-to-target, pinch-to-select; visionOS's signature input. Trap: tiny targets (gaze is imprecise — needs generous hit areas); no fallback for users who can't reliably gaze/pinch. Accessibility veto bites hard here.
- **AR overlays** — digital content registered onto the live world view (labels, try-on). Trap: overlay clutter occluding the world, registration drift, safety. Phone-AR remains niche.
- **3D web** — WebGL/WebGPU/Three.js scenes in pages (→§4.4). Trap: weight, jank, battery, and frequently-inaccessible motion-heavy defaults.

## 14.7 Voice & multimodal

- **Voice UI** — speech as primary I/O; matured by low-latency speech-to-speech models (2024–25) handling interruption. Hands-free, natural for short tasks. Trap: voice-only for tasks needing review/precision (no scannable record); discoverability; privacy in shared spaces. Pair with a visible transcript.
- **Multimodal input** — mixed image + text + voice + file in one turn (point camera, ask). Matches how people reference the world. Trap: opaque failure when one modality is misread — show the interpreted input back.
- **Ambient computing** — always-available, low-attention AI woven into the environment. Trap: mostly aspirational in 2026 — proactivity reads as creepy without exquisite restraint; always-listening privacy cost is real and under-disclosed. High hype-to-shipping ratio.

## 14.8 AI imagery & the authenticity backlash

- **AI imagery aesthetics** — the recognizable generated look (waxy skin, gradient mush, uncanny hands, default-vibrant lighting) (→§7.1). Trap: the "default AI look" now signals *low effort* to a sensitized audience — futuristic in 2023, cheap in 2026.
- **AI slop** — high-volume, low-quality generated content; Merriam-Webster's 2025 Word of the Year (usage up ~9× in 2025). The negative-space term for what to avoid. Trap: becoming it — volume without craft is the failure mode.
- **Anti-AI authenticity / human-made premium** — visible craft, imperfection, and "made by a human" as a value position; a real 2026 movement (Gartner: ~50% of US consumers prefer brands avoiding generative AI in ads). Trap: performative authenticity — faux-handmade that's actually generated is worst-of-both when caught. Note: the reflexive 3-column hero / generic SaaS template *is* the slop aesthetic — distinctiveness is the antidote.

*Sources: [NN/g — AI hallucinations](https://www.nngroup.com/articles/ai-hallucinations/); [Vercel — AI Elements](https://vercel.com/changelog/introducing-ai-elements); [Apple — spatial design Q&A](https://developer.apple.com/news/?id=fi8ne6ji); [AI slop — Wikipedia](https://en.wikipedia.org/wiki/AI_slop).*

---

# 15. Design systems & tokens

The meta-layer: how to operationalize every flavor in this doc. A flavor is a look; a system is the machinery that ships that look consistently across surfaces, teams, and platforms without re-deciding it each time. Tokens are the atomic unit — where a decision stops being a vibe and becomes a value other tools can read.

## 15.1 Design tokens

A **design token** is a named, platform-agnostic variable holding one design decision — coined at Salesforce (~2014), now a W3C Community Group standard. Single source of truth, transformable into CSS/iOS/Android/JSON. Trap: tokenizing everything — a token used once is a variable with ceremony; tokenize shared decisions, hardcode one-offs.

The three-tier chain — **primitive → semantic → component** — is the load-bearing idea: change the value once at the bottom, or re-point an alias in the middle, and every consumer updates.
- **Primitive / global (Tier 1)** — the raw value, no meaning (`blue-500: #3B82F6`, `space-4: 16px`); named by what they *are*. Reference these only from semantic tokens. Trap: shipping primitives into components — dark mode and rebrand then hunt every usage.
- **Semantic / alias (Tier 2)** — a primitive given a role (`color-action-primary → blue-500`, `space-inset-md`); the layer a theme swaps, the contract components depend on. Trap: leaking the primitive's identity into the alias name (`color-blue-button`).
- **Component-specific (Tier 3)** — a semantic token scoped to one component (`button-primary-bg`); optional, for components that genuinely need to drift. Trap: minting Tier-3 for every component by reflex — most consume Tier-2 directly.

**Categories** — color (palette → bg/surface/text/border/action/feedback/focus, with state + on-* pairs) · spacing (one 4/8px-base scale, split inset/stack/inline) · typography (family/size/weight/line-height + composite type-styles) · radius · shadow/elevation · motion (duration + named easing) · z-index (a named scale, never `9999`) · border · opacity · breakpoints.

**Naming** — `category-concept-property-variant-state` (`color-action-primary-hover`); name semantic tokens by role, never appearance (`color-text-danger`, not `color-text-red`). Trap: encoding the value in the name (`space-16`) — the name should survive the value changing.

**Format & tooling** — the **W3C DTCG format** (JSON, `$type` + `$value`; group `$type` cascades; reached its first stable version Oct 2025) is the canonical on-disk format; **Style Dictionary** (built at Amazon, OSS 2017) transforms it into platform code. Trap: treating generated output as truth — the JSON is canon, generated files are disposable build artifacts.

## 15.2 Theming

A theme is a swap at the **semantic tier** — primitives and components stay; only aliases re-point. If theming forces component edits, the architecture is broken.
- **Light / dark** — two semantic mappings over one primitive palette; dark mode is a deliberate re-mapping, not "invert" (elevated surfaces get *lighter*; pure-black + pure-white is a contrast trap — §9). Drive with CSS custom properties under `[data-theme]` / `prefers-color-scheme`.
- **Multi-brand / white-label** — same component layer, swapped primitive + semantic sets per brand; structure (spacing, radius, APIs) holds, brand owns color/type/tone. Honors brand isolation.
- **Density modes** — comfortable/compact, driven almost entirely by spacing + line-height tokens.
- **High-contrast theme** — first-class, not an afterthought: thicker borders, stronger ratios, explicit focus; respect `forced-colors`. An accessibility requirement.
- **Runtime theming** — CSS custom properties flip themes at runtime by re-setting variables on a root scope, zero rebuild. Trap: build-time SCSS variables bake in at compile — you ship N stylesheets and can't switch live.

## 15.3 Atomic design

**Atomic design** (Brad Frost, 2013) — compose UI from smallest to largest; five non-linear stages, a shared vocabulary for granularity, not a folder mandate.
- **Atoms** — irreducible elements (label, input, button, icon).
- **Molecules** — small groups doing one job (search field = label + input + button).
- **Organisms** — complex standalone sections (header, product card).
- **Templates** — page-level layout with components placed, real content absent.
- **Pages** — templates filled with real content; where the system gets stress-tested.

Maps to code as a granularity ladder, not gospel. Trap: litigating whether a thing is "a molecule or an organism" — Frost himself says the labels don't matter; the value is the part/whole mindset.

## 15.4 Component API design

A component's props are its public contract — design them like an API: small, orthogonal, hard to misuse.
- **Variants** — discrete modes via one enumerated prop (`variant="primary | ghost | danger"`); don't expose raw style props that let callers invent off-system looks.
- **Sizes** — a constrained scale tied to tokens (`size="sm | md | lg"`), never arbitrary px.
- **States** — every interactive component defines **default, hover, focus(-visible), active, disabled, loading, error**. Focus-visible is non-negotiable (§9); loading and error are the ones teams forget until production.
- **Slots / composition** — inject content via children/slots (`<Card.Header>`) instead of a prop per region. Composition scales; a `leftIconAndAlsoBadge` prop does not.
- **Controlled vs uncontrolled** — controlled = parent owns state (`value`/`onChange`); uncontrolled = component owns it (`defaultValue`). Document which. Trap: a "controlled" component with internal state that silently diverges.
- **Prop naming** — booleans as adjectives (`disabled`, `loading`), events as `onX`; match platform convention.

## 15.5 System architecture

- **Single source of truth** — one canonical token + component definition; two sources = drift, the thing a system exists to prevent.
- **Figma ↔ code sync** — keep design and code reading the *same* tokens via **Figma Variables** (native, mode-switching) and **Tokens Studio** (plugin → DTCG JSON → Style Dictionary). Trap: hand-syncing Figma to code — they diverge within a sprint.
- **Primitives vs patterns** — primitives are unopinionated blocks (Button, Stack); patterns are opinionated compositions (a settings form). Patterns consume primitives, never the reverse.
- **Headless / unstyled vs styled** — headless libraries ship behavior, a11y, and state with no visual opinion (**Radix**, **Ark UI**, **React Aria**); you bring the tokens. For a distinctive flavor, headless + your own tokens is the move. Trap: re-implementing a focus-trapped, ARIA-correct dropdown by hand.
- **Design system as a product** — treat it as an internal product with users, roadmap, versioning, support, adoption goals — not a ship-once side project that rots.

## 15.6 Documentation & governance

- **Usage docs** — purpose, props/API, live examples, a11y notes per component. Undocumented = misused.
- **Do / Don't** — paired visual examples kill more inconsistency than prose; show the wrong way explicitly.
- **Contribution model** — a defined path (RFC → review → merge); without it the system ossifies or forks.
- **Versioning / changelog** — semver the system, communicate breaking changes loudly; a token rename is a breaking change.
- **Adoption metrics** — measure real uptake (% of surfaces on current components, token coverage). "Is anyone using this?" should have a number.
- **Team models** — **centralized** (consistent, can bottleneck) · **federated** (scales, needs governance) · **hybrid** (small core + federated contribution — where most mature systems land).

## 15.7 Notable systems (reference)

Study for conventions; don't clone — each encodes its org's constraints, not yours.
- **Material (Google)** — token-driven with dynamic color; reference for theming depth, motion.
- **Apple HIG** — guidelines, not a component library; reference for platform-native principles, spatial.
- **Carbon (IBM)** — enterprise, framework-agnostic; reference for data-dense UI, density, governance.
- **Polaris (Shopify)** — admin/merchant UX; reference for content/writing guidelines.
- **Atlassian** — token-first, multi-product; reference for unification under one token layer.
- **Primer (GitHub)** — multi-implementation (CSS, React, Rails); reference for parity from shared tokens.
- **Fluent 2 (Microsoft)** — vast cross-platform reach; reference for platform-respecting consistency.
- **Spectrum (Adobe)** — scale + density, React Aria-backed.

*Sources: [Style Dictionary — DTCG](https://styledictionary.com/info/dtcg/); [DTCG first stable version (Oct 2025)](https://www.w3.org/community/design-tokens/2025/10/28/design-tokens-specification-reaches-first-stable-version/); [Atomic Design, Ch. 2 — Brad Frost](https://atomicdesign.bradfrost.com/chapter-2/).*

---

# 16. Google Fonts (grouped by type)

A reference of widely-used, free **Google Fonts**, grouped by typeface classification. This is intentionally last and somewhat redundant — the *style* decisions above matter more than the specific file. Use this to fill a slot once a style and a classification are chosen. All are free for commercial use and self-hostable.

> A few of the best-known modern faces are **not** on Google Fonts — **Geist** (Vercel, free), and **Clash Display / General Sans / Switzer / Neue Montreal / Editorial New** (Fontshare, free). Worth knowing since they appear constantly in current work. Helvetica, Futura, and Avenir are licensed (not free).

## 16.1 Neo-grotesque / grotesque sans (neutral, UI, body)
The objective, modern workhorses. Default choice for product UI and clean body text.
- **Inter** — the de facto UI sans; huge weight range, variable, hyper-legible.
- **Roboto** / **Roboto Flex** — Android default; Flex is deeply tunable (variable).
- **Work Sans** — friendly grotesque, good display and text.
- **Archivo** / **Archivo Narrow** — sturdy grotesque superfamily.
- **Manrope** — semi-geometric, clean, popular (variable).
- **Hanken Grotesk** — warm modern grotesque (variable).
- **Schibsted Grotesk** — editorial-leaning grotesque.
- **Figtree**, **Mulish**, **Public Sans** — neutral, reliable text sans.

## 16.2 Geometric sans (modern, brand, headline)
Built from circles and lines; clean and contemporary, slightly cooler.
- **Poppins** — geometric, rounded, extremely popular for branding.
- **Montserrat** — geometric, urban-signage roots; ubiquitous headlines.
- **Outfit** — clean modern geometric (variable).
- **Sora** — techy geometric, good for product brands (variable).
- **Lexend** — geometric tuned for reading proficiency (variable).
- **Jost** — Futura-like geometric, free alternative.
- **Sora**, **Space Grotesk** — techy/quirky geometric display-sans.
- **Quicksand** — rounded geometric, soft/friendly.

## 16.3 Humanist sans (warm, readable, body)
Calligraphic warmth and open apertures; the most comfortable sans for long reading.
- **Open Sans** — the dependable humanist standard.
- **Source Sans 3** — Adobe's clean humanist (variable).
- **Lato** — warm, slightly rounded, hugely popular.
- **Nunito Sans** — soft humanist (variable).
- **PT Sans**, **Fira Sans**, **Cabin**, **Karla** — solid humanist text faces.

## 16.4 Old-style / transitional serif (body, editorial)
Calligraphic, readable serifs for long-form and credible editorial tone.
- **Lora** — balanced, screen-optimized text serif (variable).
- **Source Serif 4** — Adobe's editorial serif (variable).
- **PT Serif** — neutral, readable workhorse.
- **Spectral** — designed for screens, generous range.
- **Crimson Pro** / **Crimson Text** — book-like, classical.
- **EB Garamond** — free Garamond revival; classic body.
- **Bitter** — slab-ish transitional, sturdy for text.
- **Newsreader** — news/editorial serif (variable).

## 16.5 Modern / Didone serif (elegant, fashion, display)
High thick/thin contrast; elegant headlines, fragile small.
- **Playfair Display** — the go-to high-contrast headline serif.
- **Bodoni Moda** — Didone, fashion-grade (variable).
- **DM Serif Display** / **DM Serif Text** — elegant, free, expressive.
- **Cormorant** — refined, decorative display serif.
- **Marcellus** — light, classical, luxury feel.

## 16.6 Slab serif (sturdy, confident, headline)
Heavy blocky serifs; strong and grounded.
- **Roboto Slab** — clean, modern slab.
- **Zilla Slab** — Mozilla's contemporary slab.
- **Arvo**, **Aleo**, **Bitter** — solid geometric/transitional slabs.

## 16.7 Display / expressive (headline only)
Personality faces for large sizes; never body text.
- **Anton** — ultra-bold condensed; poster impact.
- **Bebas Neue** — tall condensed caps; ubiquitous in display.
- **Archivo Black** — heavy grotesque display.
- **Oswald** — condensed gothic; headlines and UI accents.
- **Abril Fatface** — Didone display, editorial flair.
- **Syne** — quirky modern display family.
- **Bricolage Grotesque** — characterful editorial display (variable).
- **Unbounded**, **Climate Crisis**, **Honk** — experimental/novelty display.

## 16.8 Monospace (technical, editorial accent)
Fixed-width; code-native, increasingly used for branding texture.
- **JetBrains Mono** — readable code mono.
- **IBM Plex Mono** — characterful, design-literate.
- **Space Mono** — quirky, editorial-accent favorite.
- **Roboto Mono**, **Source Code Pro**, **Fira Code**, **DM Mono** — clean mono options.

## 16.9 Handwriting / script (accent only)
Joined or casual handwriting; for personality accents, never body.
- **Caveat** — natural marker handwriting.
- **Dancing Script** — flowing casual script.
- **Pacifico** — bold retro brush script.
- **Satisfy**, **Sacramento**, **Kalam** — varied casual/formal scripts.

## 16.10 Notable variable fonts (animatable axes)
Single files with adjustable weight/width/slant/optical axes — best for §2.6 motion treatments and responsive type.
- **Inter**, **Roboto Flex**, **Source Serif 4**, **Bricolage Grotesque**, **Hanken Grotesk**.
- **Fraunces** — "old-style with character"; optical-size + soft/wonky axes; superb editorial display.
- **Recursive** — sans↔mono + casual↔linear axes in one family; very flexible.
