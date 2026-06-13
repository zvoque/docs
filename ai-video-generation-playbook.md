# AI Video Generation Playbook

> Part of a frontier/craft reference set for steering AI tools, editors, and creators past the default. Default reach: type a vague prompt into whatever model is trending, generate a 5-second clip, accept the first warped result. Use the **trap** on each entry to avoid the cliché — and the **decision matrix** to pick the right model instead of the loudest one.

A working reference for *choosing and driving* AI video models — which model for which job, how to feed it a start frame, what it costs, and the workflow patterns that turn credits into usable footage. Covers: **the model landscape**, **the decision matrix**, **image generation for start frames**, **pricing & credit economics**, **workflow patterns**, and **the AI-look failure modes**.

This is the *generation* layer. The promptable *vocabulary* (camera moves, looks, presets, prompt structure) lives in [`motion-graphics-taxonomy.md`](motion-graphics-taxonomy.md) §1 and isn't repeated here — this doc is selection, cost, and workflow. Once you have clips, [`video-editing-taxonomy.md`](video-editing-taxonomy.md) §10 is how you stitch them; [`video-preproduction-taxonomy.md`](video-preproduction-taxonomy.md) is the shot list (with a per-shot *source* column) that tells you what to generate vs. code vs. shoot; [`code-rendered-video-playbook.md`](code-rendered-video-playbook.md) is the deterministic alternative when diffusion is the wrong tool.

> **Time-sensitive — read this first.** Model names, capabilities, availability, and especially **pricing change monthly**. Every number below is a mid-2026 snapshot and is flagged. Treat the *patterns* (how to choose, how to iterate, what fails) as durable and the *specifics* (this model, this price) as something to re-verify before you commit a budget.

Compiled June 2026.

---

## How to use this doc

- **Match the model to the job, not the hype.** No model wins everything. The fastest/cheapest is wrong for a hero shot; the most cinematic is wrong for a 200-variant ad batch. The decision matrix exists because the right answer changes per shot.
- **Most tools are image-to-video — so the still is the real prompt.** The start frame determines composition, identity, lighting, and look; the text prompt mostly controls *motion*. Spend effort on the image, then animate it. ([§3](#3-image-generation-for-start-frames).)
- **Iterate cheap, finish expensive.** Generate many low-res/fast drafts to find the winning seed and motion, then re-run the keeper at high quality and upscale. Credits are the constraint; the draft-then-finish pattern is how you respect it.
- **Plan around the failure modes, don't fight them.** Warping hands, melting backgrounds, drift, and flicker are predictable. Keep clips short, motion simple, hands out of close-up, and cut away from the tells ([§6](#6-the-ai-look-failure-modes)).
- **Generation is one shot, not a film.** Each clip is 2–15s with one clean camera move. The *edit* (and the grade, captions, and audio) is what makes a sequence — don't expect the model to deliver a finished video.

---

## Table of contents

- [How to use this doc](#how-to-use-this-doc)
- [1. The model landscape](#1-the-model-landscape)
- [2. Decision matrix](#2-decision-matrix)
- [3. Image generation for start frames](#3-image-generation-for-start-frames)
- [4. Pricing & credit economics](#4-pricing--credit-economics)
- [5. Workflow patterns](#5-workflow-patterns)
- [6. The AI-look failure modes](#6-the-ai-look-failure-modes)
- [7. The AI-generation trap index](#7-the-ai-generation-trap-index)
- [Quick decision checklist](#quick-decision-checklist)

---

# 1. The model landscape

The current top text/image-to-video models, mid-2026. **All specs and availability are time-sensitive — verify before relying on them.** "i2v" = image-to-video, "t2v" = text-to-video.

| Model | Best at | Max clip | Aspect / res | i2v · t2v | Native audio | Consistency / motion control |
|---|---|---|---|---|---|---|
| **Higgsfield Cinema Studio** (+ DoP) | Cinematic camera control; the 60+ named camera-move presets; viral looks | ~4–15s | 16:9 / 9:16 / 1:1, 4:3/3:4 | i2v (start+end) · via preset | optional | preset camera library; **Soul ID** character refs; genre control (action/horror/comedy/western/suspense/intimate/spectacle) |
| **Higgsfield Marketing Studio** | One-click product ads, UGC, TikTok/Reels | ~4–15s | all incl. 21:9 | i2v · — | optional | hooks/settings, ad-reference recreation, avatars + product refs |
| **Google Veo 3.1** (+ 3, Lite) | Ultra-realistic, top-tier cinematic, strong **native audio** | 4/6/8s | 16:9 / 9:16 | i2v (start; Lite start+end) · t2v | **yes** | quality tiers (basic/high/ultra); timestamp prompting; ingredients/refs |
| **Kling 3.0** (+ 2.6) | Multi-shot, **motion transfer**, advanced physics | 3–15s | 16:9 / 9:16 / 1:1 (std/pro/4k) | i2v (start+end) · t2v | yes | **Motion Brush** (6 elements), **Motion Control** (transfer motion from a driving video) |
| **Bytedance Seedance 2.0** | Reference-driven **consistent identity**, multi-SKU/product | 4–15s | up to 1080p, 21:9→9:16 | i2v (image+video+audio refs, start+end) · — | no (gen) | strongest identity/product consistency; cinematic genre hint |
| **MiniMax Hailuo** | Natural physics + **facial emotion** | 6/10s | up to 1080p | i2v (start+end) · t2v | varies | realistic micro-expression and physics |
| **Wan 2.6 / 2.7** | Stylized/experimental (2.6, open-weight); audio + character-consistent (2.7) | 5/10/15s | 16:9 / 9:16 / 1:1 | i2v · t2v | 2.7: yes | artistic/open-weight flexibility |
| **Runway Gen-4 / 4.5** | Cinematic quality + **character consistency** | ~5–10s | 16:9 / 9:16 / 1:1 | i2v · t2v | partial | references, keyword camera direction |
| **Luma Ray2 / Dream Machine** | Composable camera moves; **keyframes / extend / loop** | ~5–10s | multiple | i2v · t2v | varies | 15+ natural-language moves, start/end keyframes |
| **Pika 2.x** | One-click physics VFX, keyframe transitions | ~5–10s | multiple | i2v · t2v | varies | **Pikaffects** (explode/melt/inflate…), **Pikaframes** (transition across ≤5 images) |
| **OpenAI Sora 2** | High-quality, strong physics/coherence | ~10–20s | multiple | i2v · t2v | yes | ⚠ **availability flux** — see note |
| **xAI Grok Imagine (1.5)** | Fast text+image→video with audio direction | 1–15s | 16:9 / 9:16 / 1:1 | i2v (start) · t2v | yes | preview-tier, fast iteration |

> **⚠ Sora 2 availability (verify):** reporting indicates the standalone Sora app/web was being **discontinued (~April 2026)** and the **Sora API sunset (~September 2026)**, with the **Sora 2 model remaining available inside paid ChatGPT**. If a pipeline depends on a standalone Sora endpoint, confirm current status first.

> **Aggregators:** Higgsfield (and others) route to several of these engines under one credit system — e.g. Higgsfield exposes Kling, Seedance, Veo, and its own Cinema/Marketing/Soul models, so "which model" and "which tool" are separate questions. Pick the *engine* for the shot and the *tool* for the workflow/budget.

---

# 2. Decision matrix

Which model to reach for by job (mid-2026; the *reasoning* outlasts the specific names).

| The job | Reach for | Why |
|---|---|---|
| **Cinematic hero shot** (specific camera move, filmic look) | Higgsfield Cinema Studio; Veo 3.1; Kling 3.0 | Named camera presets (Higgsfield) or top-tier realism + audio (Veo); pick by whether you need a *specific move* or maximum realism |
| **Product / e-commerce ad** (consistent product across angles) | Seedance 2.0; Higgsfield Marketing Studio | Reference-driven identity/multi-SKU consistency; Marketing Studio's hook/setting templates |
| **Talking avatar / lip-sync** | Dedicated avatar tools (HeyGen, etc.) + Veo/Kling for inserts | General video models still weak at arbitrary lip-sync; use a purpose-built avatar product |
| **Anime / stylized** | Wan; Kling; stylized image model → i2v | Open-weight/artistic flexibility; or generate a stylized still and animate it |
| **Cheap, fast batch** (many drafts/variants) | Veo 3.1 Lite; Seedance "fast" mode; Grok | Budget/fast tiers exist precisely for iteration volume |
| **Long, consistent character across shots** | Seedance 2.0; Runway Gen-4; Higgsfield Soul ID | Character/identity references are the differentiator here |
| **Vertical social (9:16)** | Higgsfield Marketing Studio; Veo (9:16); Kling | Native 9:16 + social-ad framing |
| **Physics-heavy action** | Kling (physics + motion transfer); Hailuo; Sora 2 | Best motion coherence and physical plausibility |
| **Native-audio one-shot** (clip + sound together) | Veo 3.1; Kling 3.0; Wan 2.7; Grok | These generate synced audio in the same pass |
| **Precise type / data / brand UI** | **none — code-render instead** | Diffusion mangles exact text/numbers/brand color → [`code-rendered-video-playbook.md`](code-rendered-video-playbook.md) |

---

# 3. Image generation for start frames

Because most video models are **image-to-video**, the still is the highest-leverage decision: it fixes composition, identity, lighting, lens, and look before a single frame of motion. A strong first frame is most of a strong clip.

### The current image models (mid-2026, verify)
| Model | Best at |
|---|---|
| **GPT Image 2 / 1.5** (OpenAI) | Top overall quality and **text rendering**; marketing, branding, complex compositions |
| **FLUX.1.1 Pro / FLUX 2** (Black Forest Labs) | Realism + commercial use; open-source flexibility/customization; **FLUX.1 Kontext** for image editing |
| **Midjourney v7** | **Aesthetics** — the most striking, art-directed look |
| **Google Imagen 4 Ultra / Gemini 3 Pro Image ("nano-banana")** | **Photorealism** (skin, fabric, light), speed, Google-ecosystem integration |
| **Ideogram** | **Text-in-image** accuracy (signage, packaging, titles) |
| **Recraft v3** | **Speed** + vector/brand/design control |
| **Seedream 4.5** (Bytedance) | Budget-conscious **e-commerce/product** |
| **Hunyuan Image 3.0** | **Anime / character** art |
| **Higgsfield Soul / Soul Cinema** | Cinematic, editorial "feels shot" stills; **Soul ID** trains a reusable consistent character |

### The start-frame craft
- **Compose the still as the first frame of the shot** — the shot size, angle, and framing you want the video to *start* on. The model animates *from* it. **Trap:** a beautiful but badly-composed still animates into a badly-composed clip.
- **Bake in the look** — grade, lens character, lighting direction, depth of field. The video inherits all of it; fixing it after is a grade in post, not a re-gen. **Trap:** a flat, evenly-lit still gives a flat clip; put the cinematography in the image.
- **Lock identity with a character reference** (Soul ID, Seedance/Runway refs) when the same person/product must recur across shots. **Trap:** generating each shot's still independently → a "same" character whose face drifts shot to shot.
- **Keep hands, text, and tiny faces out of the start frame** where you can — they're where both image and video models break. **Trap:** a hero close-up of hands holding the product is the single most warp-prone setup.
- **Match the still's aspect to the target** (9:16 still → 9:16 clip); don't generate 16:9 and crop. **Trap:** crop-to-vertical loses the framing you generated.

---

# 4. Pricing & credit economics

**All figures are mid-2026 snapshots and change frequently — verify before budgeting.** Most tools are subscription + a **credit** system; credits-per-clip scale with model, resolution, duration, and audio.

### Rough tiers (verify)
- **Higgsfield** — Starter ~$15/mo (200 credits), Plus ~$39/mo (1,000), Ultra ~$99/mo (3,000), billed annually; a 5s Kling-3.0 720p clip ≈ 6 credits (~$0.12–0.20 on Ultra). Frontier models (Seedance 2.0, Veo 3, Sora 2) burn credits faster.
- **Kling** — Free, Standard ~$10, Pro ~$37, Premier ~$92, Ultra ~$180/mo.
- **Runway** — ~$15–30/mo for cinematic/character work.
- **Google Veo 3** — ~$20/mo (via Gemini/Flow tiers).
- **Pika / Luma** — entry plans ~$10/mo.
- **Per-second economics (across tools):** roughly **$0.05–0.75/sec**, most premium models **$0.10–0.40/sec**. Mid-2026 reference points: Kling 3.0 ≈ $0.10/sec, Veo 3.1 fast ≈ $0.15/sec, **Sora 2 ≈ $0.75/sec** (premium). A 30-second piece can run ~$1.50–$22.50 in raw generation depending on model.

### Iterate cheap, finish expensive
The core cost discipline: **generate many drafts on a fast/cheap tier** (low res, fast mode, short) to find the winning seed, framing, and motion; then **re-run only the keeper** at high quality and **upscale**. Don't burn frontier-model credits exploring. **Trap:** iterating at full quality/resolution — you pay 5–10× to discover the same thing a draft would have told you. **Second trap:** no budget cap — generation costs are easy to run away with at $0.40/sec across dozens of takes.

---

# 5. Workflow patterns

Reference patterns, not a fixed pipeline. (Prompt *vocabulary* is in [`motion-graphics-taxonomy.md`](motion-graphics-taxonomy.md) §1.)

- **Text-to-video vs. image-to-video** — t2v for fast ideation and imagined scenes (weakest control); i2v when look/identity matter (the prompt then describes *motion*, not the scene). **Trap:** using t2v when you needed a consistent character or exact look — that's i2v's job.
- **Generate-the-still-then-animate** — make the start frame in a dedicated image model ([§3](#3-image-generation-for-start-frames)), then animate it. The dominant high-control pattern. **Trap:** skipping it and hoping t2v lands the look.
- **Consistency / character references** — lock a face/product across shots with refs (Soul ID, Seedance, Runway). **Trap:** relying on prompt text alone to keep a character the same — it won't.
- **Generate-many-pick-one** — every model is stochastic; generate a batch, pick the cleanest take. **Trap:** accepting the first result; the second-best of five is usually far better than the first of one.
- **Start / end frame & keyframe interpolation** — fix the first (and optional last) frame; tools like Pikaframes/Luma interpolate between supplied frames. Doubles as an edit tool (end clip A and start clip B on the same frame = a built-in match cut). **Trap:** big gaps between supplied frames → morphing.
- **Extend & loop** — continue a clip past the duration cap (quality drifts each extension) or match ends into a seamless loop. **Trap:** extending too many times until identity/look degrades.
- **Upscaling & frame interpolation** — gen low/fast, then upscale resolution and (optionally) interpolate frames for smooth slow-mo. **Trap:** upscaling artifacts on already-warped footage — fix the gen first.
- **Reframe / aspect retarget** — retarget one master to 9:16 / 1:1 / 4:5. **Trap:** blind auto-crop decapitates subjects — plan framing for the target ratio up front.

---

# 6. The AI-look failure modes

Predictable artifacts that mark a clip as generated. Design and cut around them rather than fighting them. *(Also catalogued in [`motion-graphics-taxonomy.md`](motion-graphics-taxonomy.md) §1.5 and editing §10.)*

- **Warping / morphing hands & faces** — the #1 tell. Avoid hand close-ups; keep faces mid-distance; regenerate until clean.
- **Melting / morphing backgrounds** — worst behind orbits and pull-backs, where the model invents geometry. Keep those moves slow and short.
- **Flicker / temporal shimmer** — texture and lighting jittering frame to frame. Simpler scenes and shorter clips reduce it.
- **Plastic / waxy skin** — denoising strips pore detail. Fix with a subtle ~15–20% film-grain overlay in post.
- **Slow identity drift** — the subject mutating across a long clip. Keep clips short; lock with references.
- **Gibberish text & fake logos** — keep text out of frame and add it in post (or code-render it).
- **Physics violations & extra limbs** — floaty/teleporting objects, duplicated faces, sixth fingers. Simpler action, more takes.
- **The general "AI sheen"** — over-clean, slightly-floaty footage. Break it with grain, short cuts, and motivated motion. **Overall trap:** masking these with stacked filters instead of shorter clips, simpler motion, and cutting away from the tell.

---

# 7. The AI-generation trap index

- **Hype-driven model choice** — using the trending model for every job instead of matching model to shot.
- **Vague-prompt-into-t2v** — expecting a one-line text prompt to deliver a consistent, art-directed clip; the still is the prompt.
- **Iterating at full quality** — burning frontier credits to discover what a fast draft would have shown.
- **No budget cap** — $0.40/sec across dozens of takes adds up fast and silently.
- **The hands-and-text hero shot** — framing exactly what the models break.
- **One-and-done** — accepting the first stochastic result instead of generating a batch and picking.
- **Generate-then-crop** — making 16:9 hero clips and crop-to-vertical at the end, losing the framing.
- **Trusting raw gens to match** — assembling shots whose character/look subtly drifted, with no unifying grade.
- **Expecting a finished video** — treating a 5s gen as a film instead of one shot to be edited, graded, captioned, and scored.
- **Forcing diffusion to be exact** — handing precise type, data, or brand UI to a model that approximates; code-render it instead.

---

## Quick decision checklist

1. **Pick the model for the shot** (matrix in [§2](#2-decision-matrix)) — cinematic move, product consistency, cheap batch, native audio? Different winners.
2. **If it's i2v, make the still first** — composed as the first frame, with the look and identity baked in.
3. **Lock identity with references** when a character or product recurs.
4. **Draft cheap, then finish** — many fast/low-res takes to find the keeper, then high-quality + upscale; cap the budget.
5. **Generate a batch, pick the cleanest** — never one-and-done.
6. **Frame for the target aspect** up front; don't generate-then-crop.
7. **Keep clips short, motion simple, hands/text out** — design around the failure modes.
8. **Hand off to the edit** — one gen is a shot; the cut, grade, captions, and audio make the video.
9. **Re-verify pricing & availability** — every number here is a volatile mid-2026 snapshot.
