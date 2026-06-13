# Master Motion Graphics & Video Visual-Language Taxonomy

> Part of a frontier/craft reference set for steering AI video tools, editors, and designers past the default. Default reach: the flat blue corporate-explainer, the generic animated lower-third, the teal-and-orange grade on everything, "cinematic" meaning a black-bar 24p LUT. Use the **trap** on each entry to avoid the cliché — and the **prompt cue** to actually get the thing out of a generation model.

A working reference for the *visual language* of video — everything about how a frame looks and moves, as opposed to how two frames join (that's the sibling doc, [`video-editing-taxonomy.md`](video-editing-taxonomy.md)). Covers: **camera language & motion** (shot grammar and the promptable moves/presets generation models understand), **animation principles & timing**, **motion-graphics styles**, **title & text in motion**, **broadcast & brand graphics packages**, **color grading looks**, **LUT & emulation vocabulary**, **format, frame & aspect**, **frame rate as a look**, **compositing & texture looks**, **notable references**, **emerging & AI-era video**, and a **trap index**. Each entry: what it is, where it came from, its defining traits, when to reach for it, the trap to avoid, and — where it helps a generation tool — the exact prompt cue.

This doc is written to be *promptable*. Most entries carry a **Prompt cue** — the literal vocabulary that gets the look out of an image/video model (Higgsfield, Hyperframes, Veo, Kling, Runway, Seedance, Hailuo, Luma, Pika). The names are the API: a model that's never heard "make it cinematic" reliably understands "anamorphic, 2.39:1, teal-orange grade, shallow depth of field, 35mm grain, slow dolly in."

Compiled June 2026. Trend-sensitive entries (mograph trends, AI-tool capabilities, current grade discourse) are dated; named-look origins are historically stable. Disputed origins and soft terminology are flagged inline.

---

## How to use this doc

- **This is a frame vocabulary, not a timeline one.** When you're deciding *how a shot looks or moves*, you're here. When you're deciding *where to cut*, you're in the sibling doc. They're meant to be used together.
- **One look is a stack, and order matters.** Camera move → shot size → grade → texture is a render order, not a pile. Stacking signifiers — teal-orange *and* heavy grain *and* halation *and* light leaks *and* anamorphic flare *and* a vignette at once — is the single most common tell of amateur (and AI) work. Restraint and motivation are the whole game.
- **Prompt one clean move per clip.** Every current generation model obeys *one* camera move per generation. "Dolly in and orbit" produces warped chaos. Put the camera term at the end of the prompt, let the model build the scene first, then move through it. ([§1.5](#15-generation-prompt-craft--the-ai-look-tells).)
- **Name the look; don't describe the vibe.** Models resolve named looks far better than adjectives. "Premium" is nothing; "Kodak 2383 print emulation, soft highlight rolloff, fine grain, 2.39:1" is a render. Reach into [§6](#6-color-grading-looks)–[§10](#10-compositing--texture-looks) for the names.
- **Motion has principles, not just keyframes.** A move reads as designed when it has weight, easing, anticipation, and follow-through ([§2](#2-animation-principles--timing)) — "animate the title in" without them produces the linear, lifeless default.
- **Accessibility and legibility are still a veto.** Captions and supers must clear platform UI and the title-safe area; several grading looks (crushed blacks, heavy haze, neon-on-neon) routinely fail contrast. A look that can't be read loses, on TV and on a phone alike.

---

## Table of contents

- [How to use this doc](#how-to-use-this-doc)
- [1. Camera language & motion (for generation prompts)](#1-camera-language--motion-for-generation-prompts)
  - [1.1 Shot sizes & framing](#11-shot-sizes--framing)
  - [1.2 Camera moves](#12-camera-moves)
  - [1.3 Camera-move quick reference](#13-camera-move-quick-reference)
  - [1.4 Named generation presets](#14-named-generation-presets)
  - [1.5 Generation prompt craft & the AI-look tells](#15-generation-prompt-craft--the-ai-look-tells)
  - [1.6 Composition & framing](#16-composition--framing)
- [2. Animation principles & timing](#2-animation-principles--timing)
- [3. Motion-graphics styles](#3-motion-graphics-styles)
- [4. Title & text in motion](#4-title--text-in-motion)
- [5. Broadcast & brand graphics packages](#5-broadcast--brand-graphics-packages)
- [6. Color grading looks](#6-color-grading-looks)
- [7. LUT & emulation vocabulary](#7-lut--emulation-vocabulary)
- [8. Format, frame & aspect](#8-format-frame--aspect)
- [9. Frame rate as a look](#9-frame-rate-as-a-look)
- [10. Compositing & texture looks](#10-compositing--texture-looks)
- [11. Notable references](#11-notable-references)
- [12. Emerging & AI-era video](#12-emerging--ai-era-video)
- [13. Current trends 2025-2026](#13-current-trends-2025-2026)
- [14. The default-look trap index](#14-the-default-look-trap-index)
- [Quick decision checklist](#quick-decision-checklist)

---

# 1. Camera language & motion (for generation prompts)

The grammar of how the camera sees and moves. This is the single most prompt-critical section for generation tools: the named shot sizes and camera moves below are the vocabulary models were trained on, and the difference between "make a cool shot" and a controlled result. **Universal rule:** one clean camera move per clip; too fast warps, too slow shows no motion; put the camera term last.

## 1.1 Shot sizes & framing

How much of the subject is in frame — the first decision of any shot.

- **Extreme wide / establishing shot** — subject tiny in a vast environment; sets place and scale. **Prompt cue:** `extreme wide shot`, `establishing shot`, `wide landscape, tiny figure`. **Trap:** faces won't render at this scale — don't rely on identity here.
- **Wide / full shot** — the full setting, subject visible head-to-toe. **Prompt cue:** `wide shot`, `full body shot`.
- **Medium-wide (cowboy)** — mid-thigh up. **Prompt cue:** `medium wide shot`, `cowboy shot`.
- **Medium shot** — waist up; the safe default for a talking subject. **Prompt cue:** `medium shot`, `waist up`.
- **Medium close-up** — chest and shoulders up; best balance of identity and expression. **Prompt cue:** `medium close-up`.
- **Close-up** — the face fills the frame. **Prompt cue:** `close-up on [subject]'s face`.
- **Extreme close-up** — eyes, lips, or a single detail. **Prompt cue:** `extreme close-up`, `macro detail of`. **Trap:** tiny motion warps features fast.
- **Over-the-shoulder (OTS)** — framed past one person's shoulder onto another; the dialogue staple. **Prompt cue:** `over-the-shoulder shot`. **Trap:** the back-of-head may morph in a gen.
- **Two-shot** — two subjects in frame. **Prompt cue:** `two-shot`. **Trap:** identity bleed between the two faces is common in generation.
- **POV** — the camera is the subject's eyes. **Prompt cue:** `first-person POV`, `from [subject]'s point of view`.
- **Dutch / canted angle** — tilted horizon for unease. **Prompt cue:** `Dutch angle`, `canted angle`.
- **Aerial / bird's-eye** — directly overhead, looking down. **Prompt cue:** `aerial view`, `top-down shot`, `overhead`.
- **Low-angle / worm's-eye** — looking up; the subject towers and reads powerful. **Prompt cue:** `low-angle shot`, `looking up at [subject]`.
- **High-angle** — looking down; the subject diminished. **Prompt cue:** `high-angle shot`.
- **Macro** — extreme magnified detail. **Prompt cue:** `macro shot`, `macro lens`, paired with `shallow depth of field`.

## 1.2 Camera moves

How the camera travels. Each cues a different feeling; each is a discrete promptable token.

- **Dolly in / push-in** — the whole camera moves toward the subject (distinct from zoom — no perspective change). Intimacy, rising tension. **Prompt cue:** `slow dolly in toward [subject]`, `push in`. **Trap:** at high speed it becomes a crash zoom; models often invent geometry as they approach.
- **Dolly out / pull-back** — the camera retreats; reveals context, isolation, an ending. **Prompt cue:** `dolly out`, `pull back to reveal`. **Trap:** the worst place for melting/morphing backgrounds — keep it slow.
- **Truck / track (left-right)** — the camera slides laterally; parallax, moving alongside. **Prompt cue:** `truck left`, `tracking shot parallel to [subject]`. **Trap:** models confuse "track" with follow-the-subject — say "parallel to subject" to disambiguate.
- **Pan** — the camera rotates horizontally from a fixed position (a turned head, not a step sideways). **Prompt cue:** `pan left`, `slow pan across [scene]`. **Trap:** if you want sideways *travel*, say truck/track, not pan.
- **Tilt** — the camera rotates vertically from a fixed position. **Prompt cue:** `tilt up to reveal`, `tilt down`. **Trap:** some tools read bare "tilt" as a Dutch angle — say "tilt up/down."
- **Pedestal / boom** — the camera body rises or lowers while staying level. **Prompt cue:** `pedestal up`, `boom down`. **Trap:** the weakest-parsed move; "crane" is more reliable if you can accept the arc.
- **Crane / jib** — the camera sweeps up or down on an arm, often arcing; one of the best-parsed cinematic moves. **Prompt cue:** `crane up revealing`, `high-angle crane shot`, `jib down`.
- **Zoom (optical)** — focal length changes, camera stationary; flat magnification, no parallax. **Prompt cue:** `slow zoom in`. **Trap:** reads "flat/digital" vs. a dolly — prefer dolly for depth.
- **Crash zoom** — a violent fast zoom; shock, comedy, sudden emphasis. **Prompt cue:** `crash zoom in`, `rapid zoom`. **Trap:** high warp risk on faces — keep the subject simple.
- **Dolly zoom (vertigo / Hitchcock)** — dolly one way while zooming the other; the background warps while the subject stays the same size. Dread, the ground shifting underfoot. **Prompt cue:** `dolly zoom`, `vertigo effect`, `dolly in while zooming out`. **Trap:** hard for weaker models — a dedicated preset nails it where a generic prompt just does a normal zoom.
- **Orbit / arc** — the camera circles partway around the subject; hero moment, product reveal. **Prompt cue:** `orbit around [subject]`, `180-degree arc shot`. **Trap:** the far side of the subject and the background must regenerate — watch for melt.
- **360 orbit** — a full circle; the complete showcase. **Prompt cue:** `360 orbit around [subject]`. **Trap:** the most warp-prone move; identity drifts by the back half.
- **FPV drone** — fast, low, weaving first-person flight; energy, chase, immersion. **Prompt cue:** `FPV drone shot`, `fast low drone weaving through`. **Trap:** aggressive motion blur smears fine detail and faces.
- **Handheld** — subtle organic shake; documentary realism, immediacy. **Prompt cue:** `handheld`, `slight camera shake`. **Trap:** handheld + a busy scene can over-jitter into flicker.
- **Steadicam glide** — smooth floating follow, no shake; a polished walk-with. **Prompt cue:** `smooth gliding steadicam shot following [subject]`.
- **Whip pan** — an ultra-fast pan that smears to motion blur; transition and energy (also a hidden-cut tool — see the sibling doc). **Prompt cue:** `whip pan to [next]`. **Trap:** the mid-blur frames are intentionally unusable; very overused.
- **Tracking / follow shot** — the camera moves to keep a moving subject framed. **Prompt cue:** `tracking shot, camera follows [subject] as they [action]`.
- **Bullet time** — the camera arcs around a frozen or slowed subject; the Matrix freeze. **Prompt cue:** `bullet time, frozen subject, camera orbits`. **Trap:** generic models approximate it poorly — a named preset is the reliable path.
- **Snorricam** — the camera is rigidly mounted to the subject; the subject stays fixed while the world moves. Disorientation, intoxication, panic. **Prompt cue:** `snorricam, camera mounted to subject, background moves`. **Trap:** niche; reliable mainly as a named preset.
- **Robo-arm / motion-control** — a fast, mechanically precise programmed move; slick product reveals. **Prompt cue:** `robotic arm camera move`, `motion control camera`. **Trap:** freeform prompts rarely hit the precision — use the preset.
- **Rack focus / focus pull** — focus shifts between foreground and background planes; directs attention, reveals depth. **Prompt cue:** `rack focus from [A] to [B]`, plus `shallow depth of field`. **Trap:** needs shallow DoF to read at all.
- **Low-to-high reveal** — starts low, rises and tilts up to expose scale; grandeur, a hero entrance. **Prompt cue:** `low angle rising to high angle, tilt up to reveal`. **Trap:** a composite move — give it an explicit "from X to Y" or it stalls.

## 1.3 Camera-move quick reference

| Move | Feeling it cues | Prompt cue | Gen gotcha |
|---|---|---|---|
| Dolly in / push-in | Intimacy, rising tension | `slow dolly in toward [subject]` | Invents geometry at speed |
| Dolly out / pull-back | Reveal, isolation, ending | `pull back to reveal` | Melting backgrounds — go slow |
| Truck / track | Parallax, moving alongside | `tracking shot parallel to [subject]` | Confused with follow — disambiguate |
| Pan / tilt | Survey, look up/down | `slow pan across`, `tilt up to reveal` | "Track" if you mean travel; "tilt up/down" |
| Crane / jib | Epic reveal, descend | `crane up revealing` | One of the best-parsed moves |
| Zoom | Flat magnification | `slow zoom in` | Reads digital — prefer dolly |
| Crash zoom | Shock, comedy beat | `crash zoom in` | Warps faces |
| Dolly zoom | Dread, ground-shift | `dolly zoom, vertigo effect` | Use a preset; generic = normal zoom |
| Orbit / 360 | Hero showcase | `orbit around [subject]` | Background melt; 360 drifts identity |
| FPV drone | Energy, chase, immersion | `FPV drone shot, weaving` | Motion-blur smear |
| Handheld | Doc realism, immediacy | `handheld, slight camera shake` | Over-jitters busy scenes |
| Steadicam | Polished follow | `smooth gliding steadicam following` | — |
| Whip pan | Transition, energy | `whip pan to [next]` | Mid-blur frames unusable |
| Bullet time | Matrix freeze | `bullet time, camera orbits` | Use a preset |
| Rack focus | Shift attention, depth | `rack focus from [A] to [B]` | Needs shallow DoF |

## 1.4 Named generation presets

Most consumer AI-video tools expose *named* camera and motion presets — trained moves you select rather than describe, which hit far more reliably than free text. The taxonomy is tool-agnostic but these are the real libraries as of mid-2026; treat the names as a vocabulary that will keep churning.

### Cinematic camera-control libraries
The deepest is **Higgsfield's** 60+ camera-control presets — a near-complete map of the moves in [§1.2](#12-camera-moves) plus combinations: `Dolly In/Out/Left/Right`, `Super Dolly In/Out`, `Double Dolly`, `Crash Zoom In/Out`, `Rapid Zoom In/Out`, `YoYo Zoom`, `Dolly Zoom In/Out`, `Crane Up/Down`, `Crane Over The Head`, `Jib Up/Down`, `Arc Left/Right`, `360 Orbit`, `3D Rotation`, `Lazy Susan` (360 around a static subject), `Bullet Time`, `Snorricam`, `Robo Arm`, `FPV Drone`, `Aerial Pullback`, `Whip Pan`, `Pan Left/Right`, `Tilt Up/Down`, `Dutch Angle`, `Fisheye`, `Handheld`, `Static`, `Focus Change` (rack focus), `Eyes In` / `Mouth In` (push into a feature), `Through Object In/Out`, `Hero Cam`, `Car Grip` / `Car Chasing` / `Road Rush` (vehicle-mounted), `Hyperlapse`, `Timelapse` (Human/Landscape/Glam), `Low Shutter` (motion-blur look), `Wiggle`, `Glam` (a flattering beauty move). **Prompt cue:** select the preset, then write only the *scene and subject* — the move is handled. **Trap:** combining a preset move with a second move in the text prompt fights it.

### Scene / action presets (content templates)
A second class bundles a whole look + action + camera into one selectable template — e.g. `Drift Racing`, `CGI Breakdown` (mesh→beauty render reveal), `Android Assemble` / `Free Fall` (parts snap together), `Storm Giant`, `Earth Zoom In/Out`, `Disintegration`, `Bullet Time` fight beats, `2000's Paparazzi`, `Office CCTV`, `Night Vision`, `Red Carpet`, `Summer Haze` (lomo home-movie with light leaks). These are great for viral social moments and bad for bespoke direction — you're buying a known result. **Trap:** the template *is* the look; everyone using it gets the same video. Distinctiveness comes from the subject, not the preset.

### Per-tool motion systems (cross-reference)
- **Kling** — six master moves (Horizontal/Vertical/Pan/Tilt/Zoom/Roll), plus **Motion Brush** (paint motion paths for up to 6 elements) and **Motion Control** (transfer motion from a driving video onto a character).
- **Runway Gen-4** — keyword camera direction: `locked tripod`, `dolly forward`, `tracking shot`, `crane`, `orbit`, `dolly zoom`, `whip pan`, `FPV racing style`, `boom-and-track`, plus speed terms (`slow motion 50%`, `timelapse`, `speed ramping`).
- **Pika** — **Pikaffects** one-click physics VFX on a subject (`Explode`, `Melt`, `Crush`, `Inflate`, `Cake-ify`, `Squish`, `Dissolve`, `Levitate`, `Ta-da`) and **Pikaframes** keyframe transitions across up to 5 images.
- **Luma Dream Machine (Ray2)** — 15+ composable natural-language moves plus **Keyframes**, **Extend**, **Loop**.
- **Hailuo / MiniMax "Director"** — 15 named camera movements via natural language.

## 1.5 Generation prompt craft & the AI-look tells

The conventions that get clean output, and the artifacts that mark a clip as AI.

### Prompt structure
Two dialects converge across tools. **Rich paragraph** (Veo, Sora, Hailuo): `[cinematography] + [subject] + [action] + [context] + [style & ambiance]` as a descriptive sentence. **Terse keyword stack** (Runway, Kling): `[camera move] + [scene] + [action] + [details]`, plain English, start simple. Universal recipe: **subject + action + camera move + lens/mm + lighting + setting + style/era**. Scene first, camera term last, one move only.

### What models handle well vs. poorly
**Well:** a single clear subject and action; one camera move; explicit lighting (direction + temperature + quality); 5–10s beats; concrete nouns; named film eras and looks. **Poorly:** multiple simultaneous camera moves; sequencing words (`then`, `next`, `after` → chaos or unwanted cuts); hands and fingers; legible on-screen text; precise counts; crowds; tiny faces; rapid complex action.

### Negative prompts
Only some models expose a dedicated negative field (Kling, Wan, Seedance, Hailuo); others (Veo, Runway) prefer *positive* phrasing ("a desolate landscape with no buildings" beats "no buildings"). Keep negatives to ~8–12 terms — over-stacking degrades output. Starter set: `deformed hands, extra fingers, extra limbs, warped face, duplicated face, flicker, jitter, warping, morphing, soft focus, text overlay, watermark`.

### Workflow concepts (promptable controls)
**Text-to-video** (concept, weakest control) vs **image-to-video** (strongest control — the prompt describes the *motion*, not the scene). **Start frame** (fixed first frame) and optional **end frame** (target last frame) for control and built-in match cuts. **Keyframe interpolation** fills motion between supplied frames. **Motion strength** dials movement (low = stable, high = dynamic and warp-prone). **Consistency/character reference** locks a face across shots. **Extend** continues a clip past the 5–15s cap (quality drifts each extension); **Loop** matches ends. **Reframe** retargets aspect (16:9 ↔ 9:16 ↔ 1:1). Current models cluster at 4–15s clips, accept a start (often + end) frame, output 16:9/9:16/1:1/4:3/3:4/21:9, and increasingly take a **genre hint** (`action`/`horror`/`comedy`/`noir`/`drama`/`epic`) and optional generated audio.

### The "AI video look" tells to avoid
The artifacts that read as synthetic — design and cut around them: **morphing/warping hands and faces** (the #1 tell — avoid hand close-ups, regenerate until clean); **flicker/temporal shimmer** (texture and light jittering frame to frame); **plastic/waxy skin** (denoising strips pore detail — fix with a subtle ~15–20% film-grain overlay in post); **melting/morphing backgrounds** (worst behind orbits and pull-backs, where the model invents geometry); **slow uncanny drift** (identity mutating across a long clip — keep clips short); **gibberish text and fake logos** (keep text out of frame, add it in post); **duplicated faces, extra limbs, physics violations**. **Trap:** trying to *fix* these with stacked filters instead of shorter clips, simpler motion, and cutting away from them (see the sibling doc's [§10](video-editing-taxonomy.md#10-assembling-ai-generated-footage)).

## 1.6 Composition & framing

How the subject sits in the frame — promptable vocabulary that steers generation framing and reads as deliberate rather than snapshot. Kept brief by design; this is the framing layer of the visual language, not a full cinematography course.

- **Rule of thirds** — place the subject (or its key line — a horizon, an eyeline) on a third, not dead-center. The default "this looks composed" framing. **Prompt cue:** `rule of thirds, subject on the left third`. **Trap:** rote thirds on everything; sometimes dead-center or off-balance is the stronger choice.
- **Headroom** — the space above the subject's head; too much "floats" them, too little crops them. **Prompt cue:** `balanced headroom`. **Trap:** the floating-subject-with-a-sea-of-headroom snapshot look.
- **Lead room / nose room** — space in front of a subject's gaze or motion, so they look/move *into* the frame, not off the edge. **Prompt cue:** `lead room in front of the subject`. **Trap:** a subject pinned to the edge looking out of frame — feels wrong without the viewer knowing why.
- **Leading lines** — roads, rails, edges, light that draw the eye to the subject. **Prompt cue:** `strong leading lines toward [subject]`. **Trap:** lines that lead *away* from the subject or to nothing.
- **Symmetry / centered framing** — deliberate central balance (Kubrick one-point perspective, Wes Anderson frontality). **Prompt cue:** `symmetrical composition, centered, one-point perspective`. **Trap:** the meme-coded "perfectly symmetrical" look when unmotivated.
- **Depth & foreground framing** — layered foreground / midground / background, or a "frame within a frame" (a doorway, a window) for depth and focus. **Prompt cue:** `foreground framing, layered depth, frame within a frame, shallow depth of field`. **Trap:** flat, single-plane compositions that read as a snapshot.
- **Negative space** — large empty areas that isolate and elevate the subject. **Prompt cue:** `lots of negative space, minimal composition, isolated subject`. **Trap:** empty space that reads as "forgot to fill the frame" rather than intentional.
- **Balance & weight** — distributing visual mass (a large subject offset by a small bright element); asymmetric balance feels dynamic, symmetric feels stable. **Trap:** one heavy corner with nothing to counter it — the frame "tips."

---

# 2. Animation principles & timing

What separates *designed* motion from a default keyframe slide. Almost everything here descends from Disney's "12 basic principles of animation" (Ollie Johnston & Frank Thomas, *The Illusion of Life*, 1981), adapted to motion graphics — plus the easing and timing vocabulary that is the modern mograph craft. These are also the right words to *instruct* motion: "ease out with a small overshoot and a 3-frame settle" is a render; "animate it in nicely" is not.

## The principles, adapted to mograph

- **Squash & stretch** — volume-preserving deformation that conveys weight and elasticity; a logo that squashes on impact and stretches on launch reads as physical. **Trap:** squash with no volume conservation looks like a smear, not a bounce.
- **Anticipation** — a small wind-up before an action (a pull-back before a punch, a dip before a jump). It tells the eye what's about to happen. **Reach for it** on every significant move. **Trap:** none functionally — its *absence* is the trap; motion with no anticipation feels abrupt and cheap.
- **Staging** — directing the eye to one idea at a time; clear silhouettes, one focal action per moment. **Trap:** everything animating at once, so nothing reads.
- **Straight-ahead vs. pose-to-pose** — two construction methods: straight-ahead (frame by frame, fluid, unpredictable) vs. pose-to-pose (key poses first, then in-betweens — the mograph default via the graph editor). **Trap:** pose-to-pose with no breakdowns reads stiff; straight-ahead with no plan drifts.
- **Follow-through & overlapping action** — parts keep moving after the main mass stops, and secondary elements lag the lead (hair, cloth, trailing letters, a settling card). The biggest single upgrade to "flat" motion. **Prompt/instruct cue:** `follow-through, overlapping action, secondary elements settle late`. **Trap:** everything stopping on the same frame — the dead, mechanical halt.
- **Slow in & slow out (easing)** — real motion accelerates and decelerates; nothing moves linearly. The single most important mograph principle (detailed below). **Trap:** linear interpolation — the unmistakable amateur/default tell.
- **Arcs** — natural movement follows curved paths, not straight lines. **Trap:** elements sliding on perfectly straight vectors read robotic.
- **Secondary action** — a supporting motion that enriches the main one (a subtle scale-pulse under a slide, a shadow shifting). **Trap:** secondary action that competes with, rather than supports, the primary.
- **Timing & spacing** — the number of frames and the distance between them set weight and mood; close spacing = slow/heavy, wide spacing = fast/light. **Trap:** uniform timing across every element — no rhythm, no hierarchy.
- **Exaggeration** — pushing past the literal for clarity and appeal (a bigger overshoot, a snappier scale). **Trap:** exaggeration with no restraint reads as cartoonish where the brand wanted poise.
- **Solid drawing (solid space)** — consistent volume, weight, and dimensional logic; in 3D mograph, objects that obey one coherent space and light. **Trap:** elements that flatten or break perspective mid-move.
- **Appeal** — the charisma and clarity of the design itself; motion can't rescue a shape with no appeal. **Trap:** animating a weak design instead of fixing the design.

## Easing & timing vocabulary

- **Linear** — constant speed, no acceleration. **Trap:** the default to *avoid* — almost nothing in nature moves linearly; linear motion is the #1 "untouched keyframes" tell.
- **Ease-in / ease-out / ease-in-out** — accelerate from rest, decelerate to rest, or both. Ease-*out* (fast start, soft landing) is the workhorse for UI and titles. **Prompt/instruct cue:** `ease out`, `ease in-out`.
- **Custom bezier / the graph editor** — hand-shaped acceleration curves (cubic-bezier) for exact feel; the difference between "fine" and "designed." **Trap:** never opening the graph editor — preset eases everywhere reads generic.
- **Spring / overshoot & settle** — the element passes its target and settles back (a bounce), giving snap and life. **Prompt/instruct cue:** `overshoot and settle`, `springy`. **Trap:** overshoot on everything (the "everything boings" look) or on content where it reads unserious.
- **Stagger / offset (cascade)** — starting a row of elements at offset times so they ripple in rather than arrive together. The signature of polished list/menu/type animation. **Prompt/instruct cue:** `staggered cascade`, `offset by a few frames each`. **Trap:** a stagger so slow the user waits for the content.
- **Hold / moving hold** — a deliberate pause (or a barely-moving hold to keep it alive) that gives a beat room to land. **Trap:** dead-still holds that feel frozen — keep a whisper of motion.
- **Loop / cycle** — motion authored to return seamlessly to its start (idents, backgrounds, social loops). **Trap:** a visible "pop" at the loop seam.
- **Motion blur** — blur proportional to speed; the thing that makes fast motion read as fast rather than strobed. **Prompt/instruct cue:** `add motion blur`. **Trap:** fast moves with motion blur *off* — the cheap, strobey "no-blur" tell.
- **Anticipation & settle framing** — the rhythm of wind-up → action → settle as a three-beat unit; the spine of a single satisfying move. **Trap:** action with no wind-up and no settle — a slide, not a gesture.

---

# 3. Motion-graphics styles

The named aesthetics of designed motion — what an explainer, ident, music visual, or title background *looks* like. Format: what it is / origin / traits / when to reach / trap / currency.

### Kinetic typography
Animated text where words and letters move, scale, and time to audio, becoming the primary visual rather than a label. Invented for film titles by Saul Bass (1958–60) and codified for the digital era by the After Effects type-in-motion community. Type synced to VO or beat, scale-punch on stressed words, kinetic "walls," rhythm over legibility — the 2025 flavor adds rubbery bounce and elastic distortion. **Reach for it** in lyric videos, manifesto and brand-anthem spots, talking-head emphasis, and social hooks. **Prompt cue:** `kinetic typography, bold animated text, words timed to voiceover, scale punch on key words`. **Trap:** the "every word literally illustrated + whoosh SFX" template; text moving so much it can't be read. **Currency:** evergreen and actively trending — bold expressive type is a top 2025–26 direction; the flat-grey-background version is tired.

### Flat / vector "corporate explainer"
Clean 2D vector characters, icons, and simple shape transitions narrating a product pitch. The Google-Material / flat-design wave (~2013–16) and the startup-explainer industrial complex. Limited flat palette, rounded geometric "blob people," rigged limbs, ease-in/out morphs, friendly VO. **Reach for it** for B2B onboarding and internal comms — when clarity and budget beat distinctiveness. **Trap:** *the* archetypal generic/AI look; interchangeable "Corporate Memphis / Alegria" oversized-limb characters read dated and soulless. **Currency:** functional but heavily clichéd; 2025–26 brands are fleeing it toward craft and texture.

### Swiss / editorial / grid motion design
Type-and-grid systems set in motion — strict grids, big confident type, generous whitespace, restrained palette, a precise sense of layout that *moves*. The International Typographic Style ported to motion; the look of high-end fashion titles, design-conference packages, and editorial idents. **Reach for it** in premium brand, fashion, design, and culture work that wants intelligence and restraint. **Prompt cue:** `Swiss design motion, grid layout, bold Helvetica-style type, lots of negative space, precise`. **Trap:** "Swiss" as an excuse for static, cold, lifeless layout; rigor without a single bold move to bring it alive. **Currency:** IN / premium — the antidote to both blob-explainer and maximalist noise.

### 2.5D / parallax
Flat layers separated in Z-depth and offset against a camera move to fake dimensionality. From Disney's 1937 multiplane to the After Effects camera + sliced-Photoshop technique. Foreground/mid/background layers, displacement on stills, "a photo comes alive." **Reach for it** in documentary stills sequences, history and archival pieces, budget-friendly depth — revived 2024–26 by AI depth-map tools. **Prompt cue:** `2.5D parallax, layered depth, slow camera move across separated planes`. **Trap:** the "Ken Burns on steroids" stock-photo parallax with visible flat-cutout edges. **Currency:** stable workhorse, neither hot nor dead.

### Liquid / morph / fluid / blob
Organic flowing shapes, ink and paint spreads, metaballs merging and splitting, seamless shape-to-shape morphs. Cel-animation smear heritage popularized via Cinema 4D and AE shape-morph (mid-2010s). Gooey transitions, blob menus, ink-bleed reveals. **Reach for it** in beauty/wellness, fluid-metaphor brand work, transitions, music visuals. **Trap:** gratuitous "liquid transition pack" wipes between unrelated scenes. **Currency:** steady; overlaps the hotter Y2K-metaball revival below.

### Cel / frame-by-frame animation
Each frame hand-drawn; full character animation with traditional squash-stretch timing and FX-animation smears (smoke, fire, lightning). 20th-century hand-drawn tradition, revived via Procreate/TVPaint. Visible line boil, hand-crafted timing. **Reach for it** in premium brand films, music videos, anything signaling human craft and luxury. **Trap:** faux-cel that's actually a one-click "boil" filter over vector. **Currency:** rising / premium — "craft as luxury" is an explicit 2026 trend (*Flow* winning Best Animated Feature on Blender, a broad hand-drawn revival).

### Line-art / doodle / hand-drawn
Animated single-weight strokes, self-drawing lines, whiteboard and editorial doodle. The RSA-Animate whiteboard explainer (~2010) loosened into editorial marginalia. Stroke write-on reveals, sketch wobble, monochrome or duotone. **Reach for it** in education, process explainers, charming low-fi brand voice. **Trap:** the literal whiteboard-hand-drawing-itself video — instantly "2012 explainer." **Currency:** dated in whiteboard form; loose editorial line-art rides the authenticity trend.

### Isometric
Objects drawn in isometric/axonometric projection (parallel lines, no convergence) and animated — 30° angles, modular cities, servers, devices, infinite-loop "isometric worlds." Technical-drawing and pixel-art heritage; mograph staple ~2015–19. **Reach for it** for genuine spatial/system explanation — infrastructure, cloud, IoT. **Trap:** the "isometric city of icons building itself" tech cliché. **Currency:** dated/peaked as decoration; fine for real spatial content.

### Glitch / datamosh
Intentional digital-error aesthetics — signal corruption, pixel-sorting, compression artifacts, datamoshed frame-bleed, RGB split, scanlines. Datamoshing entered the mainstream via Kanye West's "Welcome to Heartbreak" (2009). **Reach for it** in tech/gaming/crypto, edgy music videos, "disruption" messaging, hard transitions. **Prompt cue:** `glitch, datamosh, pixel sorting, RGB split, compression artifacts`. **Trap:** one-click glitch transition packs as energy filler; "digital = glitch" reflex. **Currency:** mature/borderline tired as garnish, reviving via AI-assisted datamosh and the analog wave.

### VHS / analog / retro-CRT
Simulated tape/CRT degradation: tracking errors, head-switching noise, bloom, tungsten warmth, timecode overlays, color bleed. Nostalgia revival of 80s–90s consumer video. **Reach for it** in nostalgia/memory framing, retro product drops, analog horror, lo-fi music. **Prompt cue:** `VHS look, scanlines, tracking error, tape distortion, CRT, date stamp`. **Trap:** a stock VHS overlay dumped over modern 4K with no motivation; the date-stamp-in-corner reflex. **Currency:** strongly IN — "analog nostalgia" is a named 2026 trend; cliché only when it's a lazy overlay rather than an integrated grade.

### Y2K / chrome / metaball / Frutiger Aero
Late-90s/2000s digital futurism: liquid chrome type, glassy bubbles, gel buttons, aqua gradients, lens-flared optimism. "Frutiger Aero" was coined 2017 (Sofi Xian / CARI) for the mid-2000s glossy-gradient/nature-tech look and re-emerged ~2023 as Gen-Z nostalgia. **Reach for it** in fashion/beauty/music for Gen-Z, hyperpop, "nostalgic-future" moments. **Prompt cue:** `Y2K chrome, liquid metal type, metaballs, glossy gradients, aqua`. **Trap:** chrome-blob-everything sameness; conflating Y2K (cyber/grunge) with Frutiger Aero (clean/glossy/nature) — distinct eras. **Currency:** peak hype 2024–26 and *late-cycle* — chrome type nearing saturation.

### Vaporwave / synthwave (retro-futurism)
'80s-coded neon: synthwave grids and Outrun sunsets vs. vaporwave statues, marble, and mall-nostalgia glitch. Music/visual microgenres (~2010–12). Magenta-cyan palette, perspective wireframe grid, chrome sunset type, lo-fi overlay. **Reach for it** in electronic/retrowave music, gaming, retro-tech. **Prompt cue:** `synthwave, neon grid, sunset gradient, chrome type, 80s retro-futurism`. **Trap:** the neon-grid-and-sunset default reads 2015-meme-era. **Currency:** established/maturing under the broader retro-futurism umbrella.

### Brutalist / anti-design
Deliberately raw, "ugly," system-default aesthetics: bare Helvetica/Arial, exposed grids, harsh cuts, no easing, visible construction. Web brutalism (~2016) migrated into motion (~2022–24). **Reach for it** in fashion, art/culture institutions, indie music, anti-corporate brands. **Trap:** "ugly on purpose" with no craft underneath — undisciplined ≠ brutalist. **Currency:** IN / ascendant — the explicit reaction against polished corporate-flat and "AI sameness."

### Maximalist / collage / scrapbook
Dense layered mixed media: cut-out paper, mismatched type, stickers, tape, halftone, hand-scrawl, intentional overload ("ransom-note" type). Punk/zine and Dada photomontage lineage. **Reach for it** in music/festival, youth/streetwear, editorial, "scrappy authentic" energy. **Trap:** clutter with no hierarchy — noise without composition. **Currency:** IN — the counter-swing to minimalism; watch for fatigue.

### Risograph / print-texture / grain
Emulated Riso/screen-print: 1–3 spot inks, deliberate mis-registration, heavy dot grain, overprint, paper texture in motion. Riso revival in illustration ported to motion. **Reach for it** in indie/editorial, cultural events, craft-forward brands. **Trap:** grain or Riso as a one-click overlay with no real color-separation logic. **Currency:** IN / craft-aligned — tactile texture counters the too-smooth digital and AI look.

### Data-driven / infographic motion
Animated charts, counters, maps, and stats — bar/line/pie builds, ticking counters, choropleth maps, lower-third stats, bar-chart races. Broadcast/news data graphics plus the ~2014 motion-infographic boom. **Reach for it** in finance, sports, news, annual-report and explainer content. **Trap:** chart-junk — over-animated graphs that obscure the data; the gratuitous bar-chart race (~2019–20). **Currency:** evergreen utility, increasingly procedural/coded; AR data overlays are the growth edge.

### 3D mograph — the C4D + Octane/Redshift look
The glossy abstract-3D aesthetic: soft-body jiggle, cloth and inflatables, displaced organic surfaces, translucent/subsurface materials, dreamy gradient HDRI lighting, "satisfying" abstract loops. Cinema 4D MoGraph + GPU renderers maturing ~2016–20 — the dominant studio-reel look. **Reach for it** in tech/product launch beauty shots, title backgrounds, brand idents. **Prompt cue:** `abstract 3D, soft-body, displacement, gradient lighting, glossy render, octane`. **Trap:** the "abstract gradient blob with no message" reel-filler that looks like everyone else's demo. **Currency:** mature/saturated as the default agency look — differentiation now comes from art direction, not the technique.

### Photoreal 3D
Physically-accurate rendered CGI indistinguishable from live action — PBR materials, ray-traced reflection/GI, accurate optics, "is it real?" product hero shots. Film VFX democratized by Blender/Unreal + GPU render. **Reach for it** in product reveals (devices, automotive, packaging), architecture, impossible camera moves on real objects. **Trap:** uncanny-valley humans; over-perfect CGI sheen that kills believability. **Currency:** IN / rising — "3D realism" plus real-time (Unreal) and Blender adoption is a flagged 2025–26 shift.

### Mixed-media (live-action + graphics)
Real footage integrated with 2D/3D graphics, type, and illustration in one frame — type tracked into live scenes, illustrated overlays, seamless hybrid composites. The title-design and music-video tradition (Imaginary Forces et al.). **Reach for it** in title sequences, premium brand films, music videos, documentary. **Trap:** graphics that float "on top of" footage with no tracking or light-wrap — a slapped-on layer. **Currency:** IN / premium — core to high-end title work and the authenticity/craft trends.

### Particle / generative / procedural
Systems-driven motion: particle sims, flocking, physics, audio-reactive and code-generated visuals (Trapcode → Cavalry, Houdini, TouchDesigner, Notch, GLSL). Emergent flows, audio-reactivity, ASCII/data art, reactive physics. **Reach for it** in concert visuals, data art, tech idents, real-time installations. **Trap:** default particle presets ("Trapcode look") as filler; complexity with no read. **Currency:** IN / rising — "coded motion" is an explicit 2026 trend, procedural replacing keyframe-by-keyframe for systems work.

### ASCII / dot-matrix / text-mode
Type and imagery rendered in monospace characters, dot-matrix, or terminal/CRT "code" aesthetics — green-on-black terminals, ASCII-art reveals, pixel/dot grids. Hacker/computing nostalgia plus the procedural-art scene. **Reach for it** in tech/AI/crypto, hacker-coded brands, glitch-adjacent music. **Prompt cue:** `ASCII art animation, dot-matrix, terminal green-on-black, monospace`. **Trap:** "tech = green terminal" reflex; illegible at small sizes. **Currency:** niche-IN, rising with the coded-motion and brutalist waves.

### UI / product motion (Lottie / Rive)
Functional interface animation — app demos, micro-interactions, onboarding, animated icons — built as lightweight vector motion (Lottie, Rive) that ships *in* the product, not just in a video. A distinct discipline where motion is UX, not decoration. **Reach for it** in product demos, app stores, onboarding, design-system motion. **Trap:** decorative motion that slows the interface or distracts from the task; "look at our animation" over "use the product." **Currency:** IN / rising — "motion as UX" is a named 2025–26 shift; Rive's interactive state-machines are the growth edge.

### AR / spatial / lens graphics
Graphics composited into the real world in real time — face filters, world-lens effects, try-on, spatial/AR overlays, and the in-camera graphics of AR sports broadcasts. **Reach for it** in social AR (Snap/TikTok/Instagram effects), retail try-on, live-event and sports AR. **Trap:** poorly-tracked overlays that slide off the face/world; novelty filters with no use. **Currency:** IN — AR data overlays in broadcast and spatial-computing UI are an active frontier.

### Seamless-loop / "satisfying" mograph
Motion authored to cycle forever with no visible seam — looping idents, ambient backgrounds, "oddly satisfying" abstract or mechanical loops tuned for replay on social. **Reach for it** in social ambient content, idents, hold/standby screens, generative backgrounds. **Prompt cue:** `seamless loop, satisfying, perfectly cyclical motion`. **Trap:** a visible pop at the seam; "satisfying" content with no actual payoff. **Currency:** IN — loop content is strategically weighted by social platforms (it drives rewatch).

### Claymation / stop-motion look
Tactile handmade-object animation, real or simulated — clay, paper, miniatures, replacement — with on-twos timing, registration jitter, fingerprint texture, real lighting. Stop-motion film tradition, now also faked in Blender. **Reach for it** in craft/food/kids brands, premium charming spots, holiday content. **Prompt cue:** `claymation, stop-motion, handmade clay texture, on-twos timing`. **Trap:** the fake "stop-motion-style" 3D render that's too smooth to convince. **Currency:** IN / premium — named under "craft as luxury" 2026; a deliberate antidote to generative sameness.

---

# 4. Title & text in motion

Designed type and graphics as on-screen elements — titles, lower-thirds, captions, credits, callouts.

### Title card
A single static or lightly-animated card stating a title, chapter, or section — centered type on a plain or textured ground, a brief hold, a simple fade or cut. From silent-film intertitles. **Reach for it** in chapter breaks, episode titles, documentary act-breaks. **Trap:** the default centered-Helvetica-fade with no design intent. **Currency:** evergreen; minimalist type-on-black cards are in vogue (prestige-TV influence).

### Main-title sequence
The designed opening credits that establish tone and theme — revolutionized as standalone art by Saul Bass (1950s) and defined in the modern era by studios like Imaginary Forces. Sub-genres: **minimalist type-on-black** (stark type cut on black, sound design carrying tension — very IN), **kinetic-type** (credits as moving typography), **photo-montage / Bass cut-out** (collaged stills and paper cut-outs assembling the title world), **typographic-collage** (dense layered type — rides maximalism), **live-action-with-titles** (credits tracked into filmed scenes). **Reach for it** in film/TV/streaming openings and premium "title-sequence-as-film" brand work. **Trap:** credits over pretty B-roll with no concept — "background imagery" instead of thematic storytelling. **Currency:** prestige craft, very alive in the streaming era.

### Lower-thirds
A graphic in the lower title-safe area identifying a speaker or providing info (broadcast term; "chyron" colloquially). Variants: **bar** (solid/translucent bar + name + title — the broadcast default), **minimalist** (type only, thin rule, no box), **branded** (logo-locked color/shape matching the show), **animated** (slides/wipes in and out), **kinetic** (the type itself animates). **Reach for it** in interviews, news, docs, webinars, creator videos. **Trap:** a cluttered news-style L3 overloaded with logos/scores; a default template that doesn't match the brand. **Currency:** evergreen — broadcast trends dense/branded, social trends bold/animated/minimal.

### Name supers / nameplates
The specific name-plus-role overlay "supered" over picture (a lower-third subset): name large, role/affiliation small, brief hold, brand-locked. **Trap:** inconsistent type hierarchy across supers; the classic misspelled-chyron error. **Currency:** evergreen.

### Captions & subtitles
Two worlds. **Broadcast-standard captions** (CEA-608/708): fixed-position, often all-caps white-on-black-box (608 is the rigid legacy spec; 708 allows fonts/colors/positioning) — required for TV/legal accessibility. **Social "karaoke" / word-by-word captions:** animated captions that pop and highlight word-by-word in sync with speech — chunky bold font, active-word color/scale, centered, heavy outline, occasional emoji. The TikTok/Reels/Shorts creator era (~2020). The popular **"Hormozi" caption** is the aggressive bold multicolor word-by-word variant. **Reach for** karaoke captions for short-form retention; broadcast captions for compliance. **Prompt/instruct cue:** `word-by-word captions, bold sans, thick outline, active word highlighted`. **Trap:** over-styled captions that fatigue or cover the frame; the identical "TikTok default" look on every clip is now its own sameness cliché — custom styling differentiates. Place captions inside the safe area, clear of platform UI. **Currency:** word-by-word is dominant in short-form but the generic auto-style is peaking.

### End credits
**Scroll / roll** (continuous vertical crawl — film/TV legal credits) or **card-based** (discrete credit cards cut or faded in sequence — shorts, branded films, stylized endings). **Trap:** a default white-on-black roll when the brand warranted more; cards paced too fast to read. **Currency:** standard.

### Callouts / annotations / labels
Graphic markers identifying on-screen objects — leader lines, pin labels, highlight rings, arrow pointers, tracked tags. Instructional/technical and news-explainer heritage. **Reach for it** in tutorials, product feature tours, sports telestration. **Trap:** arrow-and-circle clutter; labels that don't track the moving object. **Currency:** evergreen; tracked/3D-space callouts are the polished version.

### Kinetic-type treatments (techniques)
The mechanics of animating text: **word-by-word** (words appear with the VO), **scale-punch** (the stressed word snaps larger), **typewriter** (characters type on — mono fonts, reads retro), **masked reveal** (type wiped through a moving mask edge — reads most current). **Trap:** combining all of them at once; a whoosh on every word. **Currency:** evergreen; masked-reveal + scale-punch read freshest.

---

# 5. Broadcast & brand graphics packages

The cohesive systems of branded on-screen graphics. Often the difference between "a video" and "a show."

### GFX package / show package / toolkit
The complete, cohesive set of branded graphic elements for a show or channel — intros, outros, lower-thirds, transitions, bumpers, backgrounds, supers — all sharing one design language (color, type, motion logic) and delivered as templates or real-time graphics. **Reach for it** for any recurring content: news, sports, podcasts/streams, series. **Trap:** a "package" that's really mismatched one-offs with no shared motion identity. **Currency:** evergreen core deliverable, increasingly built for real-time/automation (Chyron, Singular, Vizrt, Unreal) rather than rendered AE.

### Logo bug / DOG (digital on-screen graphic)
The small persistent channel/show logo in a screen corner — low-opacity, sometimes animated in then static, identifying the channel continuously. **Reach for it** in live TV, streams, always-on branding. **Trap:** an oversized/opaque bug that distracts. **Currency:** evergreen broadcast; streaming and social often drop it for clean frames.

### Bumpers / idents / stings
Short branded interstitials: **bumpers** bridge segments and ad-breaks ("we'll be right back"), **idents** brand the channel between programs, **stings** are very short audio-visual punctuations. 1–5s, logo + motion + signature sound. **Reach for it** in segment transitions, channel ID, podcast/stream breaks (the creator-economy equivalent is the subscribe/segment bumper). **Trap:** generic template stings unrelated to the brand's motion language. **Currency:** evergreen.

### Logo reveal / logo sting / animated logo
A short animation that builds to and "resolves" on the static brand logo — build-up motion → lockup → settle, often with an audio mnemonic; 2–6s. **Reach for it** in video intros/outros, brand idents, product reveals, sponsor billboards. **Prompt cue (for a generated background):** `logo reveal background, abstract build, resolve to center`. **Trap:** cheesy template stings — lens flares, generic 3D swoosh, "particles assemble into the logo." **Currency:** evergreen need; the quality bar is high — generic templates read amateur.

### Score bug / sports scorebug
The persistent on-screen graphic showing live score, clock, and stats during sports. Concept credited to Sky Sports' David Hill; US debut June 17, 1994 (ABC/ESPN World Cup); persistent bugs standard since. Corner-vertical vs. horizontal-strip layouts, team marks, score, clock, down/distance. **Trap:** an over-stuffed bug that buries the score; poor contrast/legibility. **Currency:** evergreen and actively evolving — 2026 league redesigns tracked closely; AR data overlays are the cutting edge.

### Ticker / crawl / news ticker
A horizontal scrolling (crawl) or vertical-cycling text strip carrying secondary info — headlines, scores, stocks — separate from the lower-third. News; permanent fixture since ~2001. **Trap:** information overload; a ticker present out of habit when it adds nothing. **Currency:** evergreen broadcast; largely absent from streaming/social (clean-frame preference).

### Chyron
Generically, broadcast text-overlay graphics — named after the Chyron Corp. character generator, now a catch-all for any keyed text overlay (L3, super, ticker). Modern systems are real-time graphics engines (PRIME, Singular, Vizrt). **Trap:** using "chyron" loosely — strictly it's the system/overlay, colloquially the lower-third. **Currency:** evergreen term.

### Branded transitions / stingers
Signature animated transitions carrying the brand between scenes or sources — a logo or shape wipe that masks a cut, often with sound. Broadcast wipes evolved into live-streaming "stinger transitions" (OBS/vMix). **Trap:** flashy stinger overuse every few seconds (Twitch-overlay syndrome). **Currency:** booming in live-streaming/esports.

### Endcards / outros / subscribe bumpers
The closing branded panel — CTA, social handles, subscribe button, next-video links (YouTube "end screens" = the last 5–20s interactive zone). **Reach for it** in YouTube/social endings, brand outros, course content. **Trap:** a cluttered endcard burying the CTA. **Currency:** IN / platform-driven — YouTube end-screen conventions dominate creator content.

### Broadcast vs. streaming vs. social GFX
Three registers. **Broadcast:** dense, persistent (bug + ticker + L3 at once), strict title-safe margins, real-time systems, info-maximal, 16:9 — reads "traditional TV." **Streaming/live:** cleaner, stinger transitions, overlay frameworks, brand-flexible, often drops the bug — esports-driven. **Social:** vertical-first (9:16), bold/large type for muted autoplay, karaoke captions, minimal persistent chrome, fast hooks, platform-native looks — the dominant growth area. **Trap:** porting broadcast density onto a phone, or social bareness onto a broadcast.

---

# 6. Color grading looks

Named grades treated as a design-language catalog — *what* a look is and how to call for it — not color science. The universal trap is **stacking** these; one look, motivated, beats five at once.

### Teal & orange
Shadows and backgrounds pushed cool blue-green, skin and highlights pushed warm orange — exploiting that skin sits in the orange wedge of the wheel and teal is its complement, so faces detach and pop. Rose with mid-2000s digital-intermediate grading; *Transformers* (2007) credited with the aggressive modern version, standard by ~2012. **Reach for it** for "expensive," high-production, blockbuster/action energy. **Prompt cue:** `teal and orange grade, warm skin, cool teal shadows, blockbuster cinematic`. **Trap:** *the* defining cliché of modern grading — critics call it homogenizing. Isolate skin vs. background; don't apply it globally. **Currency:** near-ubiquitous 2007–18, now a knowing default.

### Bleach bypass (silver retention / ENR)
Skipping the photochemical bleach step leaves metallic silver in the emulsion — desaturated color, crushed high-contrast, gritty, grainy, metallic sheen (now usually emulated). *Saving Private Ryan* (1998, Kamiński) is the canonical reference. **Reach for it** for war/dystopia/realism, "stripped of glamour," photojournalistic grit. **Prompt cue:** `bleach bypass, silver retention, desaturated high contrast, gritty, crushed blacks`. **Trap:** overdone it goes muddy and kills skin and shadow detail; a tonal cliché for "gritty." **Currency:** stable genre signal.

### Day-for-night
Shooting in daylight but making it read as night — underexpose ~2 stops, blue tint, darken in post (the blue references low-light "Purkinje" vision). French "la nuit américaine"; silent-era blue tinting. **Reach for it** for nocturnal mood on a budget. **Prompt cue:** `day for night, moonlight blue, underexposed, cool nocturnal`. **Trap:** the telltale bright-shadows-plus-blue-cast-plus-daytime-sky looks fake; less common now that cameras see in the dark. **Currency:** niche.

### Film emulation / "the film look"
Making digital read as celluloid — stock-specific color science, halation (red/amber halo on highlights), grain, soft highlight rolloff, gentle gate-weave. Stock names invoked as shorthand: Kodak Vision3, Portra, **2383** (print), Fuji Eterna, **3513**. **Reach for it** for warmth, organic texture, "soul," premium narrative. **Prompt cue:** `Kodak Vision3 / Portra emulation, halation, fine 35mm grain, soft highlight rolloff, organic film look`. **Trap:** stacking grain + halation + heavy fade reads as "filter," not film; uniform digital grain is the tell. **Currency:** strongly IN — "grain is the new gold," a reaction to clean digital and AI footage.

### Technicolor / Kodachrome (saturated vintage)
The rich, saturated, high-contrast color of classic Hollywood three-strip Technicolor and Kodachrome slide film — deep reds, vivid primaries, a "hyper-real golden-age" palette. **Reach for it** for nostalgia, glamour, period musicals, candy-colored worlds (*La La Land*-adjacent saturation). **Prompt cue:** `Technicolor, three-strip, saturated vintage Hollywood, vivid primaries, Kodachrome`. **Trap:** over-saturation into garish; reads as a costume rather than a grade if unmotivated. **Currency:** cyclical revival, pairs with the maximalist/retro waves.

### The "Netflix / streaming look"
Soft, low-contrast, evenly exposed, minimal shadow; cool teal/steel-blue shadows, global saturation pulled to ~80%. Associated with Netflix originals (and "Netflix lighting" — flat, shadowless). **Reach for it** for a clean, modern, "prestige streaming" consistency across a slate. **Prompt cue:** `streaming look, desaturated, teal shadows, low contrast, clean modern grade`. **Trap:** widely criticized 2024–26 for homogenizing — "gray and flat," less emotional depth. **Currency:** dominant but in active backlash. *("Netflix look" is descriptive shorthand, not an official spec.)*

### Dark & moody / crushed blacks
A moderate S-curve with blacks crushed *but lifted just short of pure black*, teal shadow shift offset by warmer highlights, reduced vibrance. Community-associated with Fincher (*Se7en*, *Gone Girl*). **Reach for it** for tension, dread, prestige thriller. **Prompt cue:** `dark and moody, crushed blacks, deep shadows, low saturation, cool tones`. **Trap:** crushing too hard flattens skin and goes muddy; the default cliché for "this is serious." **Currency:** evergreen drama signal. *(⚠ "Fincher look," "cold thriller," and "dark and moody" are overlapping colorist shorthands, not crisply distinct standards.)*

### Vibrant / punchy / saturated
High saturation and contrast, bold primaries — engineered to pop on small, compressed mobile screens. YouTube/social thumbnail culture (MrBeast-style, reds tuned to survive compression); music videos. **Reach for it** for energy, fun, youth, hype. **Prompt cue:** `vibrant, punchy, high saturation, bold colors, high contrast`. **Trap:** "+30%, not +200%" — over-saturation goes radioactive, clips channels, sunburns skin. **Currency:** the social/creator default.

### The beauty / commercial grade
Bright, clean, flattering — even skin tones, soft contrast, gentle warmth, controlled highlights, the "everything looks fresh and premium" commercial polish (beauty, food, lifestyle, pharma). **Reach for it** in beauty/skincare, food, hospitality, and aspirational lifestyle ads. **Prompt cue:** `clean commercial grade, flattering soft skin tones, bright, gentle contrast, premium`. **Trap:** so clean it's clinical and characterless; the over-retouched "stock-ad" sheen. **Currency:** evergreen advertising default.

### Faded / matte / lifted-blacks vintage
The black point lifted via a tone curve so the darkest tones turn dark-gray ("matte" milky shadows), often with a warm shadow tint and reduced sat. Mimics old prints losing true black. **Reach for it** for nostalgia, indie/lo-fi, soft melancholy. **Prompt cue:** `faded film, matte blacks, lifted shadows, washed-out vintage, low contrast`. **Trap:** lifting without compensating midtone contrast goes muddy; over-faded reads as a lazy Instagram preset. **Currency:** steady indie staple.

### Cross-process (X-Pro)
Emulates developing slide film in negative chemistry (or vice versa) — wild shifts: cyan-green shadows, yellow-green highlights, high contrast. Analog darkroom hack; Instagram's "X-Pro II" named for it. **Reach for it** for surreal, edgy fashion/music-video, retro-experimental. **Prompt cue:** `cross-processed, cyan-green shadows, yellow highlights, high contrast, lomo`. **Trap:** reads gimmicky and dated fast; clashes with natural skin. **Currency:** dated.

### Bleached / dreamy pastel
High-value tinted palette — soft pinks, pale yellows, light blues — lowered saturation, softened contrast, slight bloom, "sun-bleached" airiness. **Reach for it** for dreamy, romantic, whimsical, bright-and-airy. **Prompt cue:** `pastel grade, soft muted colors, dreamy, bright and airy, low contrast`. **Trap:** tips into weak and washed-out, "Pinterest preset," pasty skin. **Currency:** steady lifestyle/wedding staple.

### Monochrome & duotone
**B&W:** full desaturation, tonality and contrast carrying the image — timeless, noir, documentary. **Duotone/split-tone:** shadows mapped to one color, highlights to another (descends from tinted/toned silent film; revived as a graphic device by Spotify/editorial). **Reach for it** for austere artfulness (B&W) or bold graphic-poster energy (duotone). **Prompt cue:** `high-contrast black and white, film noir` / `duotone, teal-orange split toning`. **Trap:** B&W as "instant art" hiding a weak image; duotone with arbitrary hues reads as a dated trend. **Currency:** evergreen / cyclical.

### High-key vs. low-key
**High-key:** bright, soft, minimal shadow, low contrast — cheerful, airy, clean (comedy, beauty/food, sitcoms). **Low-key:** mostly shadow, high contrast, hard pools of light — mysterious, dramatic, tense (noir, horror). **Prompt cue:** `high-key lighting, bright airy, minimal shadows` / `low-key lighting, chiaroscuro, dramatic shadows, high contrast`. **Trap:** high-key going flat/clinical/"corporate"; low-key becoming unreadable murk or a horror cliché. **Currency:** evergreen lighting registers.

### Neon / cyberpunk
A teal/cyan + magenta core with black and amber accents — neon practicals, haze, bloom, neon reflections, high contrast. *Blade Runner* / *2049* (Deakins) as the canonical reference. **Reach for it** for futurism, tech-dystopia, nightlife, neo-noir. **Prompt cue:** `cyberpunk grade, neon magenta and cyan, neon glow, haze, bloom, neo-noir`. **Trap:** the most overused "futuristic" shortcut — purple-teal-everything; bloom + haze + fringing stacked = videogame-cutscene look. **Currency:** saturated but enduring.

### Golden hour / warm
A warm amber/orange cast, low soft contrast, glowing highlights — emulating sun near the horizon. "Magic hour." **Reach for it** for nostalgia, warmth, romance, memory. **Prompt cue:** `golden hour, warm amber tones, soft glow, sun flare, magic hour`. **Trap:** orange-everything is "the orange filter" cliché and sunburns skin; faux-golden-hour LUTs read instantly fake. **Currency:** evergreen.

### Wes Anderson pastel symmetry
Not just a grade but a total signature — flat frontal/symmetrical staging, a disciplined pastel palette with a dominant-color rule, bright colors over melancholy subjects (*The Grand Budapest Hotel*). **Reach for it** for whimsical, storybook, deadpan-precise, twee. **Prompt cue:** `Wes Anderson style, symmetrical composition, pastel palette, flat frontal framing, storybook`. **Trap:** now a meme template — symmetry + pastel alone is hollow imitation, reads as parody. **Currency:** viral but saturated.

### Sepia / vintage
Brown-toned monochrome or near-mono warm wash; historically a chemical toning. **Reach for it** (sparingly) for antiquity, memory, flashback. **Prompt cue:** `sepia tone, vintage brown, old photograph, flashback`. **Trap:** **the single most mocked "lazy" cinematic shortcut** — the "dreaded sepia filter" for "this is the past / this is the desert." **Currency:** cliché; use ironically or not at all.

### Night-vision / thermal / false-color
Stylized non-photographic looks: **night-vision** (monochrome green, grain, bloom, vignette), **thermal** (heat-mapped color), **infrared / false-color** (foliage white/pink, surreal channel-swaps). **Reach for it** for surveillance, military/tactical, sci-fi, surreal music-video moments. **Prompt cue:** `night vision, monochrome green, grain` / `thermal imaging, heat map` / `infrared false color`. **Trap:** novelty that wears off in seconds; reads as a gimmick outside a motivated context. **Currency:** niche/effect.

### Instagram-filter lineage & LUT culture
The consumer ancestry of one-click looks — early IG filters were RGB-curve presets (**Valencia**: warm midtones, purple-blue shadows, faded; **X-Pro II**: cross-process + deep shadows + vignette; **Clarendon**: cool, punchy) — which normalized "named look as a product" and matured into the pro LUT economy (sellable `.cube` creative grades). **Reach for it** by name for instant identity. **Prompt cue:** `Valencia-style warm fade`, `Clarendon-style cool punch`, `applied creative LUT`. **Trap:** recognizable presets date footage to an era and signal "filter, not craft"; a creative LUT on un-corrected footage breaks it. **Currency:** the named-look-as-product idea is now universal.

### Grade quick reference

| Look | Feel it cues | Prompt cue | The trap |
|---|---|---|---|
| Teal & orange | "Expensive," blockbuster | `teal and orange, warm skin, cool shadows` | The homogenizing default |
| Bleach bypass | Gritty war/realism | `bleach bypass, desaturated high contrast` | Muddy, kills skin |
| Film emulation | Warmth, "soul," premium | `Kodak Vision3, halation, 35mm grain` | Filter, not film, when stacked |
| Netflix/streaming | Clean prestige consistency | `streaming look, desaturated, teal shadows, low contrast` | Gray, flat, in backlash |
| Dark & moody | Tension, prestige thriller | `crushed blacks, low saturation, cool` | Muddy if over-crushed |
| Vibrant/punchy | Energy, hype, youth | `vibrant, high saturation, high contrast` | Radioactive over-sat |
| Beauty/commercial | Fresh, flattering, premium | `clean commercial grade, soft flattering skin` | Clinical stock-ad sheen |
| Faded/matte | Nostalgia, indie, lo-fi | `matte blacks, lifted shadows, washed-out` | Muddy, lazy preset |
| Neon/cyberpunk | Futurism, neo-noir | `neon magenta and cyan, haze, bloom` | Purple-teal-everything |
| Golden hour | Warmth, romance, memory | `golden hour, warm amber, soft glow` | The orange-everything cliché |
| Wes Anderson | Twee, storybook | `symmetrical, pastel, flat frontal` | Hollow meme imitation |
| Sepia | The past, flashback | `sepia tone, vintage brown` | The dreaded lazy filter |
| Technicolor | Vivid golden-age glamour | `Technicolor, saturated vintage, vivid primaries` | Garish, costume-y |
| B&W / duotone | Timeless / graphic | `high-contrast B&W` / `duotone split tone` | Hiding a weak image |

---

# 7. LUT & emulation vocabulary

The vocabulary-level concepts behind the looks above — enough to call for them precisely, not a colorist's manual.

### LUT (look-up table)
A file mapping input colors to output colors. A **1D LUT** handles a single axis (gamma/contrast); a **3D LUT** manipulates R/G/B together in a color cube (commonly 33³ points) for complex shifts. Standard format: `.cube`. Two kinds: **technical/transform** (e.g. Log→Rec.709 color-space conversion) and **creative** (a mood/film-stock look) — apply technical first, creative on top. **Trap:** a LUT assumes a specific input (exposure, white balance, color space); the wrong input clips or breaks. "Bake in a LUT and walk away" is the amateur tell.

### Film-stock emulation names
Shorthand that communicates a whole color-and-grain signature: Kodak Vision3 250D/500T, Portra, **2383** (print look), Ektachrome; Fuji Eterna, Provia, **3513**, Velvia (punchy). **Trap:** stock names get used loosely; emulation isn't the real photochemical response.

### Halation
A red/amber glow *hugging* bright highlights — on film, light passes the emulsion, reflects off the backing, and re-exposes the red layer. **Prompt cue:** `halation, red halo around highlights, film glow`. **Trap:** easy to overdo until highlights look like they're bleeding.

### Bloom / glow
Soft light scatter *spreading* around bright areas (broader, whiter than halation), lowering local contrast for an ethereal feel. **Prompt cue:** `bloom, soft glow, diffused highlights, dreamy haze`. **Trap:** too much goes foggy "Vaseline lens" mush.

### Grain (as a look)
A texture emulating film's silver-halide structure. The crucial distinction: true film grain is correlated and reacts to light and motion, while **digital noise is a uniform square matrix** — the dead giveaway. **Prompt cue:** `subtle 35mm film grain, organic texture`. **Trap:** bright, uniform, static grain "screams digital effect"; over-grain on clean 4K looks pasted on. **Currency:** a conscious 2025–26 trend against over-clean digital.

### Filmic vs. digital/clean
A core fork in any look brief. **Filmic:** soft rolloff, halation, grain, slight gate-weave, controlled imperfection. **Digital/clean:** clinical clarity, every detail sharp, neutral. Note that ultra-clean now reads "AI/CG-adjacent" — which is *why* grain is back. **Trap:** treating "filmic" as a checkbox of stacked plugins rather than coherent light and color.

---

# 8. Format, frame & aspect

The shape of the frame — a strong, underused authorial signal, and a hard delivery constraint.

### 16:9 (1.78:1)
HDTV/web standard widescreen — YouTube, broadcast, most horizontal web video. "Neutral/universal." **Trap:** reads as "TV/web default," not cinematic; wastes the mobile screen vertically. **Prompt cue:** `16:9`.

### 9:16 (vertical)
Full-height mobile portrait — the native social format (TikTok, Reels, Shorts). Maximum mobile fill and reach. **Trap:** algorithms letterbox non-9:16 and suppress reach, but 9:16 is hostile to wide establishing shots and groups — don't shoot wide and crop blindly. **Prompt cue:** `9:16 vertical`.

### 1:1 (square) & 4:5 (portrait)
**1:1:** legacy Instagram feed, a safe neutral crop. **4:5 (1080×1350):** strong feed real estate without going full vertical — the compromise when footage can't crop to 9:16. **Trap:** both are increasingly fallbacks, less immersive than 9:16. **Prompt cue:** `1:1 square`, `4:5 portrait`.

### 2.39:1 (anamorphic / scope)
Ultra-wide "CinemaScope" — native to 2× anamorphic lenses; the trained signal of high-end feature cinema (epic, vista, grandeur). **Trap:** hard-matting 16:9 to fake scope throws away resolution and reads as a poser move; tight for faces and verticals. **Prompt cue:** `2.39:1 anamorphic widescreen, cinematic scope`.

### 1.85:1 (flat) & 2:1 (Univisium)
**1.85:** US theatrical "flat," slightly wider than 16:9 — "cinema" without extreme width. **2:1 (Univisium):** Storaro's 1998 compromise between scope and 16:9, now heavy on Netflix originals — modern, clean, "streaming-cinematic." **Trap:** both can feel like a "safe middle" lacking either grandeur or fill. **Prompt cue:** `2:1 aspect ratio`.

### 4:3 (Academy) & IMAX
**4:3 (1.33 / 1.37):** boxy, the TV/early-cinema original — nostalgia, intimacy, claustrophobia, "period" (a deliberate art-film device: *First Reformed*, *The Lighthouse*). **IMAX:** 1.43:1 (true tall 70mm — nearly square, immersive) and 1.90:1 (digital projection); Nolan and *Dune* shoot select scenes tall and crop elsewhere. **Trap:** a loud authorial flag — unmotivated 4:3 reads gimmicky; mid-film aspect *jumps* jolt viewers. **Prompt cue:** `4:3 academy ratio, boxy, period`.

### Letterbox / pillarbox (as style)
**Letterbox** = black bars top/bottom (a wide image in a narrower frame); **pillarbox** = bars left/right (a narrow image in a wider frame). Added *on purpose* to signal "cinema" inside a 16:9 or vertical container, or to present period 4:3 honestly. **Trap:** fake bars are the beginner's "instant cinematic" crutch; baked-in bars wreck multi-format reframing.

### Title-safe / action-safe & multi-format reframing
**Action-safe** = the inner ~90%, **title-safe** = the inner ~80% (SMPTE; Netflix publishes specs) — keep critical visuals and all text inside, because device overscan and platform UI (captions, buttons, handles) overlay the edges, especially on 9:16. Modern delivery is **one shoot → many ratios** (16:9 master + 9:16/4:5/1:1 cutdowns), often via subject-tracking auto-reframe. **Trap:** text to the extreme edge; blind auto-crop that decapitates subjects and ignores baked-in graphics. Plan framing for every target ratio up front — "shoot loose, protect the center."

### Aspect-ratio quick reference

| Ratio | Name / use | Signals | Watch out for |
|---|---|---|---|
| 16:9 | HDTV/web standard | Neutral, "web video" | Not cinematic; wastes mobile height |
| 9:16 | Social vertical | Native, max reach | Hostile to wide shots; crop carefully |
| 1:1 | Square (legacy IG) | Safe, neutral | A fallback, not a hero format |
| 4:5 | Portrait feed | Feed real estate | Less immersive than 9:16 |
| 1.85:1 | Theatrical flat | "Cinema," subtle | Barely distinct from 16:9 |
| 2:1 | Univisium | Modern streaming-cinema | "Safe middle" |
| 2.39:1 | Anamorphic scope | Epic feature film | Fake-matting wastes res; tight on faces |
| 4:3 | Academy / period | Intimacy, nostalgia | A loud authorial flag |
| 1.43 / 1.90 | IMAX | Spectacle, scale | Aspect jumps jolt viewers |

---

# 9. Frame rate as a look

Frame rate is a feel, not just a spec — and a frequently-muddled one.

### 24fps (cinematic)
The theatrical standard; slight inherent motion blur the brain reads as "film." The default signal of "movie." **Prompt cue:** `24fps, cinematic motion, film cadence`. **Trap:** fast pans and action at 24p judder; "24p everything" is wrong for sports and screen-capture.

### 25fps (PAL) & 30fps (NTSC)
**25:** European broadcast, visually ~indistinguishable from 24. **30 (~29.97):** smoother than 24, culturally tied to news, sports, soaps, daytime TV → "video," "live," "real," *less* cinematic. The technical gap to 24 is tiny; the *perceptual* gap is large. **Trap:** 30fps reads "home video" when you wanted a movie; mixing 24/25/30 in one project causes cadence judder. **Prompt cue:** `30fps, video look, broadcast feel`.

### 60fps+ (hyperreal / the "soap-opera effect")
High-frame-rate smoothness — hyperreal, crisp, "live"; great for gaming/sports/screen content. **⚠ Important correction:** the "soap-opera effect" on TVs is caused by **motion interpolation** (the TV inventing frames between 24p), *not* by native 60p — though high native rates also read "TV/video" because we associate smoothness with live broadcast. **Trap:** kills the "film" feel; the *Hobbit* 48fps HFR famously alienated audiences as "too smooth." **Prompt cue:** `60fps, ultra-smooth, hyperreal`.

### High-speed (for slow motion)
Capturing at 60/120/240+ fps and playing at 24/30 for smooth slow motion (120→30 = quarter-speed) — drama, beauty, impact, the product hero. **Prompt cue:** `slow motion, smooth slow-mo, overcranked, shot at 120fps`. **Trap:** slow-mo overuse drains pacing; needs enough light/shutter or it strobes.

### Motion blur & shutter angle
A **180° shutter** (≈1/[2×fps]) gives the "natural cinematic" blur; a narrow angle (45–90°) gives sharp, staccato, jittery frames (the *Saving Private Ryan* / *Gladiator* combat look). **Prompt cue:** `180-degree shutter, natural motion blur` / `narrow shutter angle, crisp staccato, gritty action`. **Trap:** the wrong shutter for the rate gives unnatural stutter or smear; the narrow-shutter "war look" is itself a cliché.

### Timelapse / hyperlapse
**Timelapse:** many stills sped up (static camera). **Hyperlapse:** timelapse with the camera physically moving between frames ("moving timelapse"). Passage of time, scale, energy, cityscapes. **Prompt cue:** `timelapse, fast clouds` / `hyperlapse, moving timelapse`. **Trap:** overused as an establishing crutch; hyperlapse needs stabilization or it's a jittery mess.

### Frame-rate quick reference

| Rate | Reads as | Prompt cue | Watch out for |
|---|---|---|---|
| 24fps | "Film," cinematic | `24fps, cinematic motion` | Judders on fast pans |
| 25/30fps | "Video," live, news | `30fps, video look` | "Home video" feel; mixing rates judders |
| 48/60fps native | Hyperreal, smooth | `60fps, ultra-smooth` | Kills the film feel |
| 60i/120Hz interpolated | The "soap-opera effect" | (a TV artifact, avoid) | It's interpolation, not capture |
| 120/240fps | Smooth slow motion | `slow motion, overcranked 120fps` | Drains pace; needs light |
| 180° shutter | Natural cinematic blur | `180-degree shutter, natural blur` | Wrong shutter = stutter/smear |

---

# 10. Compositing & texture looks

Overlays and finishing treatments. Most composite via Screen/Lighten/Add blend modes; the universal trap is **filter soup** — stacking several at once.

- **Light leaks** — streaks of colored light bleeding across frame (mimicking a leaky camera back). Dreamy, nostalgic, analog warmth, transitions. **Prompt cue:** `warm light leak overlay, analog leak`. **Trap:** the default "vintage/wedding/lo-fi" cliché; washes the image out.
- **Lens flares (incl. anamorphic streak)** — bright source artifacts; the **anamorphic** flare is a horizontal (usually blue) streak from a cylindrical lens element. Energy, "epic sci-fi/action," futurism. Popularized by de Bont (1980s), trademarked by Bay, memed by Abrams (who later admitted going overboard). **Prompt cue:** `anamorphic lens flare, blue horizontal streak`. **Trap:** the canonical overuse example — Abrams-level flares obscure the image and read as parody.
- **Bokeh overlays** — out-of-focus light orbs composited in, sometimes with chromatic fringing. Romance, dream, festive, "premium lens" depth. **Prompt cue:** `bokeh overlay, soft defocused light orbs`. **Trap:** floating bokeh that ignores the scene's actual focus reads as a sticker.
- **Film grain / dust / scratches** — grain plus specks, hairs, and scratches of aged/damaged film. Age, decay, "old print/projector." **Prompt cue:** `old film texture, dust and scratches, damaged print`. **Trap:** dust/scratches that scream "fake-old" over crisp 4K and modern color.
- **Film burns** — warm orange/red blooms "burning" through frame (overexposed/end-of-reel), often as transitions. **Prompt cue:** `film burn transition, warm analog light burst`. **Trap:** a transition cliché; overuse makes every cut "look at my plugin."
- **Gate weave** — a subtle whole-frame wobble from film moving imperfectly through the gate; authentic "this is real film." **Trap:** too much is seasick; only convincing when subtle.
- **Chromatic aberration / RGB split** — color channels offset, fringing at edges; subtle = lens realism, strong = glitch. **Prompt cue:** `chromatic aberration, RGB split, color fringing`. **Trap:** overdone = eye-strain and "I just found an effect."
- **Vignette** — darkened (or lightened) frame edges; focus, mood, intimacy. **Trap:** heavy vignette is the oldest "instant moody" tell and crushes corner detail.
- **Datamosh / glitch** — intentional compression corruption (removing I-frames so motion vectors smear); surreal, edgy, digital-decay. Mainstreamed by Kanye (2009). **Prompt cue:** `datamosh, pixel melt, glitch transition, compression artifacts`. **Trap:** very of-its-moment; overuse = "edgy student film." Hard to control cleanly.
- **Scanlines / VHS tracking** — horizontal scanlines, tracking errors, color bleed, head-switching noise; 80s/90s nostalgia, analog horror, found-footage. **Prompt cue:** `VHS scanlines, tracking error, CRT, color bleed`. **Trap:** peak nostalgia cliché (*Stranger Things* era) — reads as costume, not content, when overdone.
- **HUD / UI / screen overlay** — sci-fi interface graphics, targeting reticles, data readouts, holographic panels composited over the frame. **Prompt cue:** `HUD overlay, sci-fi interface, targeting reticle, data readout`. **Trap:** the "Iron Man interface" cliché; HUDs so busy they're unreadable.
- **Hologram / scan** — translucent, scanline-flickering holographic projection or a "3D scan" build-up. **Prompt cue:** `hologram, translucent blue, scanline flicker, projection`. **Trap:** the default blue-translucent-glitch hologram everyone uses.
- **Redaction / censorship bars & blur** — black bars, pixelation, or blur over a face, plate, or word — for anonymity, comedy, or "classified" tension. **Prompt cue:** `redaction bars, pixelated censorship, blurred face`. **Trap:** a one-note gag; over-pixelation that hides too much.
- **Halftone / print-dot overlay** — comic/newsprint dot patterns over imagery; pop-art, editorial, retro-print. **Prompt cue:** `halftone dots, newsprint texture, Ben-Day dots`. **Trap:** the one-click "comic filter" with no design logic.
- **Particle / light FX** — dust motes, embers, floating particles, atmospheric haze, god-rays; depth, mood, "cinematic air." **Prompt cue:** `floating dust particles, atmospheric haze, god rays, light shafts`. **Trap:** unmotivated "atmosphere" = fog-machine/template overkill.

---

# 11. Notable references

A short, illustrative set of canonical works to anchor the vocabulary — the way the sibling docs point at notable design systems. These are reference points, not an exhaustive canon, and are named for what they *demonstrate*.

### Title sequences
- **Saul Bass** — *The Man with the Golden Arm* (1955, cut-out arm motif), *Vertigo*/*Psycho* (1958–60) — invented the title sequence as standalone, thematic art and the kinetic/cut-out vocabulary.
- **Kyle Cooper / Imaginary Forces** — *Se7en* (1995) main titles — the scratched, distressed, hand-made title that reset modern title design; Imaginary Forces' later *Mad Men*, *Stranger Things*-era work defines the prestige-TV opener.
- **Minimalist type-on-black** — the prestige-streaming default (stark type + sound design) — restraint as the statement.

### Grades & looks
- **Teal & orange** — *Transformers* (2007) as the aggressive popularizer of the DI-era blockbuster grade.
- **Bleach bypass** — *Saving Private Ryan* (1998) — desaturated, silver-retention war realism.
- **Neon / cyberpunk** — *Blade Runner 2049* (2017, Deakins) — the canonical magenta-cyan-haze reference.
- **Wes Anderson pastel symmetry** — *The Grand Budapest Hotel* (2014) — the total pastel-and-symmetry signature (now a meme template).
- **Saturated maximal color** — *Mad Max: Fury Road* (2015) — punched, hyper-saturated day/night palettes as a counter to the desaturated default.

### Broadcast & idents
- **Score bug** — the persistent sports scorebug (US debut 1994) and the ongoing per-league redesign cycle.
- **Channel idents** — the BBC/MTV ident tradition — the short branded interstitial as a design discipline.

*(Origins above are cross-checked against multiple sources; where authorship is genuinely disputed — e.g. the trailer "braaam" in the sibling doc — it is flagged rather than asserted.)*

---

# 12. Emerging & AI-era video

What's new in how video is made and how it looks — the AI-generation aesthetic, its tells, and the production shifts around it.

### The AI-generation aesthetic (and its tells)
Generative video has a recognizable default look — slightly dreamy, over-smooth, hyperreal-but-uncanny — and a set of artifacts ([§1.5](#15-generation-prompt-craft--the-ai-look-tells)): warping hands/faces, melting backgrounds, flicker, plastic skin, slow drift, gibberish text. **Reach for it** deliberately when the surreal/hyperreal *is* the aesthetic (dream sequences, abstract music visuals, impossible camera moves). **Trap:** letting the default look leak into work that wanted to read as real; the giveaway "AI sheen" of over-clean, slightly-floaty footage. The current craft response is to *break* it — add film grain, cut clips short, motivate the motion, grade for imperfection.

### Text-, image-, and source-to-video
The generation modes as a spectrum of control: **text-to-video** (most imaginative, least controllable), **image-to-video** (lock the look, prompt the motion), and **source-to-video** (turn a URL, doc, slide deck, or screenshots into a video — the explainer/marketing path). **Reach for** image-to-video when identity and look matter; source-to-video for templated, data-driven content. **Trap:** expecting text-to-video to hold a consistent character or brand across shots — that's image-to-video's job.

### The HTML-render path (vs. diffusion)
A distinct, non-diffusion approach worth knowing: **render motion graphics from code** — an agent writes HTML/CSS + GSAP/Lottie/Three.js, a headless browser captures it frame-by-frame, and it's stitched to video (the open-source HeyGen "HyperFrames" model; some hosted "Hyperframes" products pair this engine with diffusion generation). **Reach for it** for precise, on-brand, templated motion graphics, explainers, and data videos — where diffusion can't hold type, layout, or exact brand color. **Trap:** expecting it to produce photoreal or natural human motion — it renders markup, it doesn't generate pixels. *(Two distinct products share the "Hyperframes" name — the open-source HTML engine and a hosted generative studio; disambiguate before wiring up a pipeline.)*

### Virtual production & real-time
LED-volume virtual production and real-time engines (Unreal) collapsing the line between "shot" and "rendered" — in-camera VFX, live final-pixel backgrounds, real-time graphics. The growth edge of high-end production and broadcast GFX. **Trap:** the "volume look" — flat reflections and a slightly-fake background when the lighting and parallax aren't dialed.

### The authenticity backlash
The dominant counter-current: as generative and over-clean footage proliferate, audiences and brands swing toward grain, handheld, imperfect lighting, visible craft, and "shot, not generated" as a *value signal*. The reason film grain, stop-motion, and analog texture are all simultaneously trending. **Reach for it** to read as human and trustworthy. **Trap:** performing authenticity with a fake-grain overlay on otherwise glossy AI work — audiences increasingly spot it.

---

# 13. Current trends 2025-2026

A dated snapshot. Sources skew toward industry roundups (School of Motion, Envato, trade press) — directionally reliable, not peer-reviewed.

**IN / rising:** AI-assisted *hybrid* workflows (AI for grunt work — roto, captions, reframe, gen-fill — humans for taste; "good taste is the ceiling"); authenticity through imperfection (handheld, grain, raw); craft as luxury (cel, stop-motion, mixed-media, visible human touch); analog nostalgia (grain, tungsten, VHS, retro-futurism); anti-design/brutalism; bold/expressive/distorted type; Swiss/editorial restraint; 3D realism + real-time (Blender/Unreal); coded/procedural/generative motion; maximalism/collage; motion-as-UX (Rive/Lottie); platform-first / aspect-ratio-agnostic delivery (AI auto-reframe); the film-grain revival as a reaction to AI and over-clean digital.

**OUT / cooling:** the generic flat "corporate explainer" / Corporate-Memphis blob-people; whiteboard/doodle self-drawing explainers; peaked-2017 isometric icon-cities (as decoration); one-click glitch/VHS/liquid transition packs as filler; the default "TikTok auto-caption" karaoke style (now sameness); the default C4D "abstract gradient blob" reel-filler; the bar-chart-race gimmick; over-edited transition/shake montages; "flashy motion for its own sake."

**Late-cycle (still hot, nearing saturation):** Y2K/chrome/Frutiger Aero; teal-and-orange grading; the "Netflix look" (now in open backlash).

---

# 14. The default-look trap index

The visual keyword-collapse — what a tool (or a person) emits when given no direction. Name them to avoid them.

- **Teal-and-orange everything** — the global blockbuster grade slapped on without isolating skin vs. background.
- **The flat blue corporate explainer** — Corporate-Memphis blob-people, friendly VO, rounded icons. The archetypal generic/AI look.
- **Linear keyframes** — motion with no easing, anticipation, or follow-through. The unmistakable "untouched keyframes" tell.
- **Filter soup** — teal-orange + heavy grain + halation + light leaks + vignette + anamorphic flare all at once. The #1 amateur/AI tell.
- **The dreaded sepia filter** — brown wash for "the past" or "the desert." The single most mocked cinematic shortcut.
- **Abrams-level lens flare** — flares obscuring the image as a substitute for energy.
- **The default lower-third / generic logo sting** — a stock template with lens flares and a 3D swoosh that doesn't match the brand.
- **The generic karaoke caption** — the identical "TikTok default" word-by-word look on every clip.
- **The abstract gradient blob** — a C4D soft-body render with no message, as reel-filler.
- **Fake cinematic bars** — letterbox added to 16:9 as an "instant cinema" crutch.
- **The chrome-blob Y2K default** — liquid-metal type and metaballs as trend-chasing with no idea underneath.
- **The everything-boings overshoot** — spring/overshoot on every element until it reads unserious.
- **The AI sheen** — over-clean, slightly-floaty generated footage with no grain, no cuts, no motivation, reading as synthetic.

---

## Quick decision checklist

1. **Pick the frame's shape and feel first.** Aspect ratio and frame rate are authorial choices, not afterthoughts — decide 9:16-social vs. 2.39-cinema, 24p-film vs. 30p-video, before anything else.
2. **One camera move per shot** (and per generation prompt). Name it; put it last; keep it slow enough not to warp.
3. **Give motion principles.** Easing, anticipation, follow-through, a little overshoot — not linear keyframes.
4. **Name the look; don't describe the vibe.** Reach into the grading and texture catalogs for the actual token — "Kodak 2383, halation, 35mm grain," not "make it cinematic."
5. **One look, motivated.** Resist filter soup. Every signifier you stack costs credibility.
6. **Match the GFX register to the platform.** Broadcast density, streaming cleanliness, or social boldness — not the wrong one ported over.
7. **Legibility is a veto.** Captions and supers inside the safe area, clear of UI; grades that hold contrast.
8. **Designing for AI generation?** Lock look and identity with image-to-video and references; expect and *break* the AI tells with grain, short clips, and motivation.
9. **Run the trap index.** If the look matches a default on the list, that's the cue to make a real choice — and the sibling [`video-editing-taxonomy.md`](video-editing-taxonomy.md) is where you decide how it all cuts together.
