# Master Video Editing Taxonomy

> Part of a frontier/craft reference set for steering AI video tools, editors, and creators past the default. Default reach: cut on every word, zoom-transition everything, pace it like a corporate explainer. Use the **trap** on each entry to avoid the cliché.

A working reference for the editor's craft — the timeline grammar that turns clips (shot or AI-generated) into something that holds attention and means something. Covers: **editing foundations & theory**, **cut types & transitions**, **pacing & rhythm**, **montage & sequence forms**, **editing by genre & format** (advertising, cinematic, short-form — plus music video, documentary, corporate, sports, news), **b-roll & screen division**, **time & speed manipulation**, **sound & the cut**, **the edit-workflow stages**, **assembling AI-generated footage**, and a **trap index** of default-edit clichés. Each entry: what it is, where it came from, its defining effect, when to reach for it, and the trap to avoid.

This is the *timeline* half of a pair. Its sibling — [`motion-graphics-taxonomy.md`](motion-graphics-taxonomy.md) — covers the *visual-language* half: camera grammar for generation prompts, motion-graphics styles, titles, broadcast graphics, color grading, format, and compositing looks. When a topic is the look of a frame rather than the join between two frames, it lives there.

Compiled June 2026. Trend-sensitive entries (short-form conventions, AI-tool workflow) are dated; foundational grammar is timeless. Disputed origins and soft terminology are flagged inline rather than asserted.

---

## How to use this doc

- **Editing is subtraction before it is addition.** The first job is what to *remove* and where to *join* — not what effect to add. A cut is a decision about attention, not a transition to decorate.
- **Theory → grammar → pacing is a stack.** Decide the register (invisible continuity vs. collision montage), then the cut vocabulary that serves it, then the rhythm. Choose top-down; a fast jump-cut grammar inside a slow-cinema register reads as confusion, not contrast.
- **Match the cut to the goal.** A brand film and a direct-response ad use opposite pacing. Cutting a brand film like a performance ad leaves no room to feel; cutting a DR ad like a brand film buries the ask. Pick the pace the objective demands — this is the single most common altitude error.
- **Every cut should be motivated.** The audience should cut *with* you because something — a look, a sound, a movement, a question — pulled them. An unmotivated cut is the tell of an editor cutting to a clock instead of to the content.
- **Retention is the short-form veto; clarity is the narrative veto.** On social, if a choice costs the first three seconds it loses, full stop. In narrative, if a cut breaks who-is-where it loses, however slick. Different masters, different non-negotiables.
- **Feeding this to an AI editor or sequencing generated clips?** The grammar here is the instruction set — "J-cut into the next scene," "cut on the beat," "hold the reaction two beats." The promptable *visual* vocabulary (camera moves, looks, formats) lives in the sibling doc; [§10](#10-assembling-ai-generated-footage) is the bridge for assembling Higgsfield/Hyperframes/Veo/Kling output into something that doesn't read as a reel of disconnected gens.

---

## Table of contents

- [How to use this doc](#how-to-use-this-doc)
- [1. Editing foundations & theory](#1-editing-foundations--theory)
  - [1.1 The two grammars: continuity vs montage](#11-the-two-grammars-continuity-vs-montage)
  - [1.2 Montage theory](#12-montage-theory)
  - [1.3 The editor's decision rules](#13-the-editors-decision-rules)
  - [1.4 Spatial & continuity rules](#14-spatial--continuity-rules)
- [2. Cut types & transitions](#2-cut-types--transitions)
  - [2.1 Cuts](#21-cuts)
  - [2.2 Dissolves & opticals](#22-dissolves--opticals)
  - [2.3 Cut & transition quick reference](#23-cut--transition-quick-reference)
- [3. Pacing & rhythm](#3-pacing--rhythm)
- [4. Montage & sequence forms](#4-montage--sequence-forms)
- [5. Editing by genre & format](#5-editing-by-genre--format)
  - [5.1 Advertising & commercial](#51-advertising--commercial)
  - [5.2 Cinematic & narrative](#52-cinematic--narrative)
  - [5.3 Short-form & social](#53-short-form--social)
  - [5.4 Music video](#54-music-video)
  - [5.5 Documentary](#55-documentary)
  - [5.6 Corporate & explainer](#56-corporate--explainer)
  - [5.7 Sports & highlight](#57-sports--highlight)
  - [5.8 News & broadcast package](#58-news--broadcast-package)
  - [5.9 Genre anatomy quick reference](#59-genre-anatomy-quick-reference)
- [6. B-roll, layering & screen division](#6-b-roll-layering--screen-division)
- [7. Time & speed manipulation](#7-time--speed-manipulation)
- [8. Sound & the cut](#8-sound--the-cut)
- [9. The edit-workflow stages](#9-the-edit-workflow-stages)
- [10. Assembling AI-generated footage](#10-assembling-ai-generated-footage)
- [11. The default-edit trap index](#11-the-default-edit-trap-index)
- [Quick decision checklist](#quick-decision-checklist)

---

# 1. Editing foundations & theory

The grammar under every cut. You can break all of it on purpose — but only the rules you can name.

## 1.1 The two grammars: continuity vs montage

### Continuity (classical / "invisible") editing
The rule-system that stitches shots into a seamless, legible flow so the audience reads space, time, and action without noticing the cuts. Codified in the Hollywood studio system (1910s–30s) and still the dominant grammar of narrative film, dialogue, and most commercial work. Built on the master/coverage workflow: establishing shot → mediums → close-ups, assembled so each join serves clarity. The cut is meant to disappear. **Trap:** mechanical, "TV-flat" coverage — cutting by rote (wide, single, single, wide) instead of for emotion. Invisible ≠ inert; the goal is unnoticed, not lifeless.

### Discontinuity / collision editing
The opposite premise: meaning is *created by the collision* between shots, not contained within them, and the cut is *foregrounded* for style or argument (jump cuts, graphic collisions, jarring tonal shifts). Roots in Soviet montage (below); native to music videos, trailers, essayistic work, and most modern social editing. **Trap:** collision for its own sake reads as noise; a discontinuous grammar still needs an internal logic (rhythm, theme, escalation) or it's just jitter. Modern work freely mixes both grammars — the error is mixing them *without intent*.

### The master/coverage model
The shooting-and-cutting system continuity rests on: a **master** (wide shot of the whole scene) plus **coverage** (mediums, singles, over-the-shoulders, inserts, reactions) so the editor can assemble any rhythm in post. The editor's raw material and the reason "we'll fix it in the edit" is sometimes true. **Trap:** thin coverage (no reactions, no inserts, no cutaways) traps the editor into the master and the obvious cut; the edit can only be as good as the coverage allows.

## 1.2 Montage theory

### Soviet montage — Eisenstein's five methods
Sergei Eisenstein's theory (1920s USSR) that editing generates meaning through juxtaposition, in five ascending types. **Metric** — cuts on a fixed frame count regardless of content; shortening the interval mechanically accelerates the pulse. **Rhythmic** — cut points driven by movement *within* the frame and the pacing it implies (the Odessa Steps boots in *Battleship Potemkin*, 1925). **Tonal** — cuts driven by the emotional tone of the image (light, shape, mood). **Overtonal** — a synthesis of metric + rhythmic + tonal acting at once, the most complex sensory effect. **Intellectual** — juxtaposing two unrelated shots to produce a third, abstract idea (workers cut against cattle slaughter in *Strike*, 1925). **Reach for it** in music videos, trailers, concept ad-spots, and essay films where idea or feeling outranks spatial realism. **Trap:** intellectual montage reads as heavy-handed agitprop when the linked images are too on-the-nose; metric cutting goes soulless when length ignores content.

### The Kuleshov effect
Lev Kuleshov's experiment (Moscow, c. 1921–1923) showing viewers derive more meaning from the *interaction of two sequential shots* than from either alone: the same neutral face, intercut with soup, a coffin, or a woman, reads as hunger, grief, or desire. Foundational proof that meaning is assembled in the viewer's mind, not the frame. **Reach for it** in reaction-driven scenes, suspense, and ads (cut "neutral person → product → smile" and the audience infers satisfaction you never showed). **Trap:** relying on it over a genuinely empty performance with weak flanking shots — the inference doesn't fire on its own. *(Sources date the experiment to 1921 and 1923; "early 1920s" is safe.)*

### The montage sequence (the "Hollywood montage")
The compressed passage — training, falling in love, passage of time, travel — that condenses a long span into a music-led beat, usually dissolve- or rhythm-cut. Descends from Soviet montage but domesticated into a narrative shorthand. **Reach for it** to skip dramatized "dead time" and show transformation economically. **Trap:** the training-montage cliché; using montage to *substitute* for a story beat you didn't earn rather than to compress one you did.

## 1.3 The editor's decision rules

### Walter Murch — the Rule of Six
From *In the Blink of an Eye* (1995): a priority ranking for what makes a cut "right," with Murch's own weights — **Emotion 51%** (does the cut preserve what the audience should feel? "preserve at all costs"), **Story 23%** (does it advance the narrative?), **Rhythm 10%** (is it the right *moment*?), **Eye-trace 7%** (does it respect where the viewer's eye is?), **2D plane / the screen 5%** (does it honor the 180° axis?), **3D space of action 4%** (true physical continuity). The top beats the bottom: sacrifice spatial continuity, eye-trace, even the 180 rule *if* the cut lands emotionally. **Trap:** the amateur inversion — fixating on technical continuity (items 5–6) while violating emotion and story (1–2). *(The full percentages are Murch's book-canonical figures; some secondary sources quote only "emotion > 50%.")*

### Murch — "Blink theory"
The idea (Murch credits the seed to director John Huston) that a blink is mental punctuation — we blink to separate thoughts — and a cut is the film equivalent. The natural cut point is often exactly where the viewer, or the on-screen actor, would blink: at the end of a thought. **Reach for it** to find the "felt" cut in dialogue and performance; if it feels like the moment you'd blink, it usually cuts clean. **Trap:** treating it as frame-science. It's a heuristic for *thought boundaries*, not a metronome.

### Motivated vs. unmotivated cuts
A **motivated** cut is pulled by something on screen or track — a look offscreen, a sound, a movement, a line, a question the audience now wants answered. An **unmotivated** cut happens because the editor felt it had been a while. The single most useful self-check: *why does this cut happen here?* If the only answer is "pacing," the cut is unmotivated. **Reach for** the motivation: cut on a glance (eyeline), on a movement (match-on-action), on a sound (sound bridge), or on a beat. **Trap:** a whole edit of unmotivated cuts — technically fine, emotionally arbitrary, the timeline equivalent of a metronome.

### Cut on motion, look, or sound
The three reliable triggers that make a cut feel inevitable rather than imposed. **On motion:** cut while something moves and the eye is busy (the most invisible). **On a look:** a character glances and we cut to what they see. **On a sound:** a sound starts or stops across the cut. **Trap:** cutting on a *static* frame with no trigger — the "dead" cut that the audience notices because nothing carried them across it.

## 1.4 Spatial & continuity rules

### The 180-degree rule
Keep the camera on one side of an imaginary "axis of action" between subjects so screen direction stays consistent shot to shot. The safety code of spatial legibility. **Trap:** "crossing the line" disorients the viewer — which is exactly why it's used *deliberately* to signal chaos, a turning point, or a character's unraveling. Accidental crossings just read as a mistake.

### The 30-degree rule
Between two shots of the same subject, change the camera angle by at least 30° (and/or the shot size). Prevents the cut from reading as a glitchy jump. **Trap:** ignoring it manufactures an accidental jump cut; obeying it slavishly produces robotic, evenly-spaced coverage.

### Screen direction & the line
The broader principle the 180 rule protects: a character moving left-to-right should keep moving left-to-right across cuts; two people talking should each hold their side of the frame. Chases, conversations, and geography all depend on consistent screen direction. **Trap:** a flipped shot or a crossed line silently reverses direction and the audience feels two characters "swap places" or a runner suddenly double back.

### Eyeline match
A shot of a character looking, cut to what they see — tied to the 180 rule for direction. **Trap:** mismatched eyelines (the look pointing the wrong way) silently break the spatial illusion; the audience feels "off" without knowing why.

### Shot / reverse-shot
Alternating singles across the axis — the spine of dialogue coverage. **Trap:** robotic A-B-A-B ping-pong with no reaction beats; cutting on every line-end instead of holding on the face that carries the scene.

### Match-on-action (cut-on-action)
Cut mid-movement — a door opening, a punch, sitting down — so the action carries across two framings and reads as continuous. The most *invisible* cut there is. **Reach for it** as the default way to hide a cut inside motion. **Trap:** mismatched action or screen position across the splice produces a visible "jump in the move" — worse than not cutting on action at all.

---

# 2. Cut types & transitions

The grammar. A cut is the basic unit; everything else is a softened or decorated cut. Format below: what it is / its effect / origin where notable / the trap.

## 2.1 Cuts

### Hard cut (straight cut)
Instant change from shot A to B, no transition — the default, invisible building block of all editing. **Trap:** none inherently; it's the baseline. The real tell is the *opposite* — reaching for a soft transition where a hard cut was the honest choice.

### Standard / continuity cut
A hard cut placed to obey continuity (match-on-action, eyeline, 180) so it reads as seamless. **Trap:** lifeless if cut by formula rather than for the emotional beat.

### J-cut (audio lead)
The audio of the *next* shot starts before its picture — you hear B over the tail of A. Named for the timeline shape. Pulls the viewer forward, smooths scene changes, and is natural in conversation. **Reach for it** to ease into a new scene or, in short-form, to hook with the next line's audio over the current frame. **Trap:** overuse makes every transition feel soft and mushy; a mistimed lead reads as an error.

### L-cut (split edit)
Picture cuts to B but the audio of A continues underneath — the workhorse of dialogue editing, letting a line carry over a listener's reaction. (J- and L-cuts are collectively *split edits*.) **Trap:** holding the outgoing audio too long muddies whose scene it is.

### Match cut
A cut between two shots linked by composition, subject, or motion, creating a seamless or symbolic bridge across time and space (the bone → satellite in *2001*). **Reach for it** for elegance and thematic linkage. **Trap:** the "clever" match that distracts from the story; it works precisely because it's rare, so one per piece, not one per scene.

### Graphic match / form cut
A match cut specifically on shape, color, or composition — a circle resolving to the moon to a plate. ("Form cut" is the form-specific variant; the terms are used loosely.) **Trap:** becomes a "look what I did" gimmick when it isn't carrying meaning.

### Axial cut (concentric cut)
A cut straight along the lens axis to a tighter (or wider) framing of the *same* subject from the *same* angle — the camera appears to jump closer in a straight line. A deliberate emphasis device (Kurosawa, and a staple of suspense punctuation). **Reach for it** to snap focus onto a face or object, or to mimic a "step-in" of attention. **Trap:** without the >30° angle change it's a controlled jump cut — only works *because* it breaks the rule on purpose; use it as a punch, not a habit.

### Jump cut
Two shots of the *same* subject with a small jump in time or position — the image visibly "jumps." Méliès used it as a trick (1890s); Godard's *Breathless* (1960) turned it into a style (it began as a way to trim an over-long take). Cues time compression, energy, unease, "raw/authentic." **Reach for it** to compress a talking head or inject restlessness. **Trap:** the single most overused move in modern social and talking-head content — applied without reason it just signals amateur vlog pacing.

### Smash cut
An abrupt cut between tonally opposite scenes — calm to chaos, loud to silence — with no transition. Cues shock, comedy, or a jolt; often a hard-out on a held beat. **Trap:** loses all impact past a couple of uses in one piece.

### Contrast / concept cut
A cut that joins two shots for *meaning* through their difference — rich vs. poor, war vs. dinner, the intellectual-montage idea applied locally (the cut from a thrown bone to a spacecraft is also this). **Reach for it** in essays, ads, and montage to make an argument the shots don't state. **Trap:** too on-the-nose and it preaches; the comparison should reward the viewer for getting it, not spell it out.

### Cutaway
A cut from the main action to a related secondary shot (a reaction, a detail) and back. Hides time edits, adds information, and covers continuity gaps. **Trap:** the "random B-roll" cutaway that adds nothing and breaks rhythm.

### Insert
A close-up of a detail *within* the scene — a watch, a phone screen, hands. Directs attention and plants story information. **Trap:** inserting things the audience doesn't need ("on-the-nose" emphasis).

### Reaction cut (cut on the look)
A cut to a listener or onlooker's face at the moment a line or event lands — the Kuleshov effect in working form, and often the most important cut in a scene. **Reach for it** to tell the audience how to feel, to land a joke, or to build suspense by showing who's watching. **Trap:** missing the reaction entirely (staying on the speaker), or holding it so long the energy drains.

### Cross-cut / parallel editing
Alternating between two or more lines of action in different locations, implied simultaneous — building tension, scale, or thematic comparison ("will they make it in time"). Central to Griffith and to Nolan (*Inception*, *Dunkirk*). **Trap:** intercutting threads of unequal tension kills momentum; the "ticking clock" feels cheap when the timelines don't actually sync.

### Flash cut / subliminal cut
A single frame or a handful of frames inserted as a near-subliminal flash — a memory, a threat, a glimpse of what's coming. Horror and thriller punctuation (and a music-video staple). **Reach for it** for a jolt, a fractured memory, an intrusive thought. **Trap:** so fast the audience only registers irritation, not the image; over-flashing turns dread into a strobe.

### Invisible / hidden cut
A cut deliberately masked — by a whip-pan blur, a body or object wiping frame, a tilt to a featureless surface, or a digital morph — to fake a continuous take. Hitchcock's *Rope* (1948); *Birdman* (2014) and *1917* (2019). **Reach for it** to build unbroken tension or the illusion of a oner. **Trap:** if the audience spots the seam the trick collapses — and chasing oners can straitjacket performance and coverage.

### Whip-pan transition
A fast camera pan blurs the image; the cut is hidden in the blur to jump location or time. Kinetic, cause-and-effect, good for flashbacks. **Trap:** the travel-vlog cliché when sprayed across every transition.

## 2.2 Dissolves & opticals

### Dissolve / crossfade
One shot fades into the next, overlapping (typically ~1–2 seconds). Cues passage of time, dreaminess, soft connection, and is the classic glue of montage. **Trap:** the default "soft transition" that screams 1990s slideshow or wedding video when overused; reach for a hard cut unless the dissolve is doing real work.

### Match dissolve
A dissolve between two *compositionally aligned* shots so one morphs into the other — a graphic match executed as a dissolve rather than a cut (a place across seasons, a face across decades). **Trap:** muddy if the two compositions don't truly register. *(Not rigidly standardized as a term — treat it as a dissolve-plus-graphic-match hybrid.)*

### Fade in / fade out
A shot resolves to or from black (or white). A full stop — opens or closes a story or chapter. **Trap:** fading between scenes that should hard-cut drops the pacing to a crawl.

### Flash / whiteout / wash
A quick flash to white (or a color) bridging two shots — a camera-flash motivation, a burst of energy, a memory or transition. **Reach for it** for a punchy, music-video or trailer transition, or to motivate a time/place jump. **Trap:** the "every cut is a white flash" trailer cliché; eye-fatiguing in sequence.

### Defocus / morph transition
Rack the outgoing shot out of focus and the incoming shot in (or digitally morph one into the other) to hide the cut. Dreamy, subjective, a soft scene change. **Trap:** the soft-focus-everything wedding look; a morph that draws attention to itself.

### Wipe
One shot pushes another off-screen along a line or shape (including clock and iris wipes). The signature of *Star Wars* (homage to 1930s serials) — overt, playful, retro chapter-break. **Trap:** dated and cheesy outside a deliberately stylized piece.

### Iris
A circular mask opens or closes on a subject — a silent-era technique that isolates a subject with "old-timey" punctuation. **Trap:** pure nostalgia gimmick; breaks immersion in any realist piece.

### Zoom / blur / "digital" transition
A fast digital push or directional blur that carries one shot into the next — the social-edit transition vocabulary (whip-zoom, spin, shake, luma-wipe). **Reach for it** sparingly for energy on a beat. **Trap:** the over-edited CapCut-transition-on-every-cut look that the 2026 social algorithm reportedly de-prioritizes; clean cuts and "invisible" transitions now read more premium.

## 2.3 Cut & transition quick reference

| Move | Core effect | Reach for it when | The trap |
|---|---|---|---|
| Hard cut | Invisible, neutral join | The default — almost always | Replacing it with a soft transition out of habit |
| J-cut (audio lead) | Pulls the viewer forward | Easing into a scene; audio hook | Mushy "everything is soft" pacing |
| L-cut (audio tail) | Carries voice over reaction | Dialogue, reactions | Holding outgoing audio till it muddies |
| Match-on-action | Most invisible cut | Hiding a cut inside movement | Mismatched action across the splice |
| Match cut / graphic match | Elegant, thematic bridge | One signature link per piece | Clever-for-clever's-sake |
| Axial cut | Snap emphasis on a subject | A punch of attention | Used as a habit, not a punch |
| Jump cut | Energy, compression, raw | Talking heads, restlessness | The default social over-cut |
| Smash cut | Shock, comedy, jolt | A tonal collision, once | Overuse drains all impact |
| Reaction cut | Tells the audience how to feel | The beat lands on a face | Missing the reaction; holding too long |
| Cross-cut | Tension, simultaneity, scale | Two synced lines of action | Threads of unequal tension |
| Flash / subliminal cut | A jolt, a fractured glimpse | Horror, memory, music video | A strobe of irritation |
| Invisible / hidden cut | Faked continuous take | Unbroken dread or a oner | A visible seam kills the trick |
| Dissolve | Time passing, soft connection | Montage glue, gentle change | The 1990s-slideshow tell |
| Fade in/out | A full stop | Opening/closing a chapter | Fading where you should cut |
| Flash / whiteout | Punchy energy bridge | Trailers, beats, time jumps | Every-cut-a-flash fatigue |
| Wipe / iris | Overt, retro punctuation | A deliberately stylized piece | Dated and cheesy elsewhere |
| Zoom/blur "digital" | Social energy on a beat | Sparingly, on a hit | CapCut-transition-on-every-cut |

---

# 3. Pacing & rhythm

Pace is the editor's main dial. The number that captures it is **average shot length (ASL)** — runtime divided by shot count — and the looks below are points along it.

### Average shot length (ASL) as a dial
A measurable proxy for cutting pace. Verified era benchmarks: classical Hollywood (1930s–50s) ran ~8–11s; the 1970s ~5–8s for drama; from the 1980s double-digit ASLs "virtually disappear" and *Top Gun*-era films hit 3–4s; modern mainstream ("intensified continuity") sits ~4–6s, and contemporary action routinely under 2s. At the far end, slow cinema runs the other way — Tarkovsky ~60–70s, Béla Tarr ~191s average. **Use it deliberately:** sub-2s = adrenaline and overwhelm; 8s+ = dread, contemplation, realism. Action sequences should cut faster than the dialogue around them by design. **Trap:** a uniform ASL across a whole piece — pace should breathe, not idle in one gear.

### Intensified continuity
David Bordwell's term for the modern mainstream style: classical continuity *intensified* — shorter ASL, tighter framings, a more restless camera, wider focal-length extremes — while keeping action coherent. The water most contemporary editing swims in. **Trap:** intensification tipping into illegibility (see chaos cinema, [§5.2](#52-cinematic--narrative)).

### The tempo map (scene vs. sequence pacing)
Pace is layered: the overall *piece* has an arc, each *sequence* has its own curve, and individual *scenes* run faster or slower than their neighbors. A good edit modulates all three — a tense sequence of short shots framed by slower scenes that let it land. **Reach for it** by mapping the whole runtime as a tempo curve before fine-cutting. **Trap:** flattening the map — every scene at the same energy, so nothing reads as a peak.

### Rapid / accelerated cutting
Progressively shorter shots to spike intensity — a metric-montage idea. **Reach for it** at climaxes, fights, panic, hype. **Trap:** disorientation and lost geography; cutting fast to *hide* that the action wasn't well staged.

### Overlapping & staggering action
Letting picture and sound, or action and reaction, *overlap* across a cut rather than lining up on it — the sound starting early, the reaction landing late, two beats interleaved. The texture that separates a breathing edit from a mechanical one. **Reach for it** to avoid the "everything changes on the cut" stutter. **Trap:** lining up every element on the same frame, so the edit pulses like a machine.

### Long take / oner / sequence shot
A single uninterrupted shot; a *sequence shot* covers a whole scene in one take. Cues real-time tension, immersion, virtuosic flow, and showcases performance. **Reach for it** to build unbroken dread or awe (or fake it with invisible cuts). **Trap:** spectacle for its own sake — sacrificing the *best* performance or angle to preserve the take.

### Slow cinema
Deliberately long ASLs, "dead time," minimal cutting (Tarkovsky, Tarr, Akerman, Hou). The viewer stops waiting for plot and starts observing; duration becomes the subject. **Trap:** tedium without rigorous composition and sound to fill the duration.

### Cutting on the beat
Placing cuts on musical beats — downbeats for punch, off-beats for a looser, experimental feel. The spine of music video, trailers, and social montage. **Trap:** *robotic* beat-cutting; slavishly cutting every beat flattens the edit. The pros deliberately hold *through* frantic passages for contrast.

### Build / release (tension curves)
Shaping pace as a wave — accelerate cutting and layer sound to build, then release (a held wide, silence, a slow shot) so the audience can breathe before the next build. **Reach for it** in suspense, action, trailers, any climax. **Trap:** all-build-no-release is numbing; you can't feel a peak with no valley.

---

# 4. Montage & sequence forms

Named structures longer than a cut but shorter than the whole piece — the shapes a sequence can take.

### Passage-of-time montage
The compressed span — seasons turning, a city waking, a project being built — usually music-led and dissolve- or rhythm-cut. **Trap:** the doc/explainer "slideshow" version where nothing is actually compressed, just listed.

### Training / getting-ready montage
The transformation shorthand: reps, failures, incremental progress to a music build. **Trap:** the most parodied montage there is; modern use should sample its energy ironically or earn it, not play it straight.

### Supercut
Many short clips sharing one trait (a repeated word, a gesture, a product in use) cut into a single rapid run. **Reach for it** for proof-by-volume, comedy, or a brand "ways to use it" beat. **Trap:** monotony — a supercut needs internal escalation or variation or it's a list.

### Walk-and-talk
A continuous tracking shot (or stitched coverage) of characters moving through a space while talking — momentum and exposition at once. **Trap:** motion with no purpose; the energy is borrowed from the movement, not the scene, so it papers over flat dialogue.

### In medias res / cold open
Opening *in the middle of the action*, before any setup, then catching the audience up. Standard in TV, trailers, and increasingly short-form. **Reach for it** to win attention before spending any of it on context. **Trap:** an in-media-res open with no actual hook is just a confusing start; the moment has to intrigue.

### Flashback / flashforward
Cutting out of the present timeline to the past (flashback) or future (flashforward) — often signaled by a grade shift, a transition, or a sound cue, then returned from. **Reach for it** to reveal backstory at the moment it lands hardest, or to tease a destination. **Trap:** the over-signaled "ripple-dissolve-and-harp" flashback; flashbacks that explain what the present scene already showed.

### The reveal / twist edit
Withholding a piece of information and then cutting to recontextualize everything — the pull-back that shows the real situation, the insert that changes the meaning. **Reach for it** for the gut-punch, the gag, the rug-pull. **Trap:** a reveal the audience saw coming three cuts earlier; over-withholding until the audience disengages.

### Bookend / circular structure
Opening and closing on the same image, line, or location so the piece feels whole — often with the meaning changed by everything between. **Reach for it** in brand films, short docs, and narrative shorts that want a sense of completion. **Trap:** a bookend that adds symmetry but no payoff — the return has to *mean* something different.

### Anthology / vignette
Discrete self-contained mini-segments strung together by a theme rather than a continuous plot — "five stories," "a day in the life," a montage of vignettes. **Reach for it** in brand anthems, portmanteau pieces, and theme-led social. **Trap:** vignettes of uneven strength; no escalation, so the piece plateaus.

### Time loop / seamless loop
A structure that returns the end to the beginning — for a narrative loop (Groundhog-Day logic) or a literal seamless social loop that triggers involuntary rewatch. **Reach for it** on punchy short-form and "wait for it" clips. **Trap:** a loop that doesn't actually match at the seam; a narrative loop with no variation each pass.

### Recap ("previously on") & the post-credits stinger
Two episodic devices: the **recap** front-loads the beats the audience needs (fast, punchy, music-led); the **post-credits stinger** is a final beat *after* the credits — a tease, a gag, a button. **Reach for** the recap to re-onboard a returning audience; the stinger to reward the patient. **Trap:** a recap that spoils the episode's own surprises; a stinger that undercuts the ending's tone.

---

# 5. Editing by genre & format

The same grammar, tuned to a job. This is where "advertising vs cinematic vs short-form" actually lives — each has its own pacing contract, structure, and clichés.

## 5.1 Advertising & commercial

### Spot lengths & structure (:60 / :30 / :15 / :06)
Each length is a *purpose-built* video, not a trim of the longer one. The **:30** carries a full mini-arc — hook → problem/desire → product as solution → money shot → brand + CTA. The **:15** lands one value prop and one outcome. The **:06** bumper (YouTube, non-skippable) carries one idea: product hero → quick benefit → logo + tagline. Modern reality is a *family* cut from one shoot — :30 hero, :15s, :06 bumpers, square and vertical, captioned/sound-off versions, alternate CTAs per audience. **Trap:** cutting a :15 down from a :30 instead of building it; trying to tell a story in :06 instead of landing one image plus the brand.

### The hook (first 2–3 seconds)
The opening must interrupt the scroll — motion-driven, branded early, legible sound-off. On paid social a weak first three seconds wastes the whole budget. **Trap:** slow logo intros and "establishing" the brand before earning attention.

### Problem-Agitate-Solve (PAS)
The performance-ad spine: name the problem, twist the knife (agitate the pain), then present the product as relief — fast cuts, on-screen text, a clear turn at the "solve." **Reach for it** in direct-response and UGC ads. **Trap:** agitating so long it's miserable to watch; a "solve" that doesn't visibly deliver on the problem.

### The money shot / hero product reveal
The beauty/payoff shot — the clean pack shot or hero angle the whole spot drives toward. A tight reveal arc runs hook (abstract/silhouette) → explore (detail beats) → reframe (second hero angle) → payoff (clean pack shot + brand line). **Trap:** burying the hero reveal too late, or over-glamorizing it into generic-stock blandness.

### Match-frame product reveal
A match cut into the product — an object or motion in one shot resolving precisely onto the product in the next, so the reveal feels inevitable. **Trap:** forced matches that prioritize slickness over the product reading clearly.

### The demo & the before/after
Two workhorses of product advertising. The **demo** shows the product *working* in real time (the infomercial's engine); the **before/after** cuts the problem-state hard against the solved-state for instant proof. **Reach for them** when the product's value is visual and demonstrable. **Trap:** a demo too slow or staged to believe; a before/after so exaggerated it reads as fake.

### Testimonial / talking-head & social-proof montage
A real person to camera, cut for credibility — tightened with jump cuts or cutaways (B-roll, product in use) to hide pauses and lift the pace. The **social-proof montage** strings many short testimonials (or reviews/screenshots) into a rapid run of "everyone loves this." **Trap:** over-polished testimonials read as fake; a proof montage of obviously-scripted clips.

### UGC-style ad edit
Mimics organic native content — real person, raw phone-camera look, native in-app text overlays, phone audio, fast 2–3s cuts, trending sounds — built specifically *not* to look like an ad. The dominant performance format on TikTok/Reels (2025–26). Sub-types: the **unboxing**, the **"get ready with me"** product weave, the **founder VSL** (founder-to-camera video sales letter), the **listicle ad** ("3 reasons…"). **Trap:** production polish that breaks the native illusion; missing captions for sound-off; a hook that looks like an ad in frame one.

### Direct-response / DRTV pacing
Reverse-engineered from unit economics: aggressive hook → clear problem/solution → fast pacing → demonstrate the product in use → CTA, often repeated. The digital descendant of the infomercial. **Trap:** so CTA-heavy it kills watch-through; no emotional or utility payoff before the ask.

### Brand film vs performance ad
Two opposite pacing contracts. **Brand film:** longer, slower ASL, narrative and emotional, soft or absent CTA — built for affinity. **Performance ad:** fast, hook-first, problem/solution, hard CTA — built for a measurable action. **Trap:** mismatching the cut to the goal — the most common and most expensive editing error in advertising.

## 5.2 Cinematic & narrative

### Continuity / invisible editing
The narrative default ([§1.1](#11-the-two-grammars-continuity-vs-montage)) — cuts serve clarity and emotion and stay hidden. **Trap:** mechanical coverage; cutting for technical correctness instead of the felt beat.

### Trailer grammar
A genre with its own structure: often a four-act build — cold-open/teaser before the logo → establish world and character → raise stakes (around the one-minute mark) → climax and crescendo in the final thirty seconds — with rising tempo via layered percussion, risers, and impacts. Signature devices: the **"braaam"** (the massive low-brass blast popularized by the *Inception* campaign — authorship genuinely disputed among Mike Zarin, Hans Zimmer, and Zack Hemsey), the **drop / hard-out** (music and picture cut to dead silence at the peak, then one last image or title), and the **button / stinger** (a final beat *after* the title — one more joke or scare). **Trap:** giving away the whole film; formula-by-numbers braaam-and-flutter-cut sameness; a button that undercuts the tone.

### Teaser
Short (often under 1:30), mood- and concept-led, withholding plot — versus the full trailer's three-act reveal. **Trap:** a teaser that teases nothing — atmosphere with no question planted.

### Action editing — coherent vs chaos
Two poles. **Intensified continuity** keeps fast cutting and a mobile camera while preserving legible geography — you always know who is where, facing where. **"Chaos cinema"** (Matthias Stork's polemical 2011 term, not a neutral category) is the degenerate extreme: sub-second cuts, shaky cam, no master geography — sensory overload standing in for clarity. **Reach for** coherent geography; reserve deliberate chaos for subjective disorientation. **Trap:** cutting fast and shaky to *manufacture* excitement or hide poorly-staged stunts — the audience feels noise, not thrill.

### Dialogue scene editing
Shot/reverse-shot governed by the 180 and eyeline rules, but **reaction-driven** — the cut to the *listener* often matters more than the speaker, and L/J-cuts overlap voice and reaction for naturalism. **Reach for** the face the audience most needs to read; hold after a line lands. **Trap:** mechanical A-B ping-pong; missing the reaction beat that actually carries the scene.

### Suspense / horror editing
Tension lives in anticipation, not the monster — editing controls *what the audience knows and when*. Dread scenes often use few cuts and long takes (you know something's coming, not when); the payoff is the sharp reveal cut, sometimes paired with a sudden cut of *sound*. **Trap:** the cheap telegraphed jump-scare with a loud noise doing all the work; over-cutting a scare and killing the slow burn the genre depends on.

### Dream / fantasy / subjective edit
Breaking continuity on purpose to signal a non-real headspace — dissolves, defocus, slowed or reversed motion, mismatched eyelines, a grade shift. **Reach for it** for dreams, hallucinations, memory, intoxication. **Trap:** the cliché "ripple dissolve + harp"; subjectivity so heavy the audience loses the thread of what's real.

## 5.3 Short-form & social

> Currency note (mid-2026): the macro-shift is *away* from heavy effects and transitions toward retention-first, "platform-native authentic" editing. Word-by-word captions, fast hooks, and beat-sync are now baseline, not differentiators. Over-produced transition montages and dense text-listicles read as 2023–24 dated. AI-assisted editing (auto-captions, auto-reframe, silence removal, auto-clipping) is standard workflow. Specific stats below are vendor/marketing-sourced and directional.

### The 1–3 second hook
Front-load the single most compelling promise, visual, or line into the opening — big readable text, immediate motion, the payoff shown or stated with no runway. Non-negotiable on every short-form video; 2026 guidance pushes the decisive window toward 0.5s. Common hook types: the **bold claim** ("I quit my job over this"), the **visual hook** (something striking in frame one), the **question hook** ("why does nobody…"), the **negative/warning hook** ("stop doing X"), the **open-loop hook** ("wait for the end"), the **in-media-res hook** (drop into the action). **Trap:** logos, "hey guys welcome back," slow establishing shots; an open-loop hook whose payoff never comes.

### Pattern interrupt
A deliberate violation of expectation — a hard cut, whip-pan, snap-zoom, sound drop — to reset attention, roughly every 3–5 seconds. **Trap:** interrupts with no purpose become nausea; the 2026 correction explicitly warns against interrupt-spam.

### Retention-graph editing
Editing by reading the platform's audience-retention curve and patching the dips (a cut, a zoom, a reveal, a B-roll). **Trap:** a live, contested philosophy — MrBeast has publicly argued to *stop* manipulative "retention-style editing" in favor of genuine story. Cargo-culting micro-spikes without narrative now reads as hollow. The *technique* is current; the *doctrine* is openly debated.

### The "but / therefore" beat structure
Borrowed from the South Park (Parker/Stone) rule: connect beats with "but" (tension) or "therefore" (consequence), never "and then" (flat continuation). The fix for a story-time or case-study short that feels like a flat timeline. **Trap:** "and then… and then…" listing with no cause-and-effect momentum.

### Jump-cut talking head (the "YouTuber cut")
Cutting out pauses, filler, mistakes, and breaths so only forward-moving speech remains — cut on the breath for smoothness. The base layer of vlogs, tutorials, and explainers; now heavily automated (Descript, OpusClip, FireCut). **Trap:** cutting *too* tight makes speech robotic; identical framing across cuts looks cheap — mask it with a punch-in or B-roll.

### Punch-in / digital zoom on cut
A slight digital zoom (or alternating zoom levels) at each jump cut — disguises the cut and adds variety to a static talking head. **Trap:** over-zoomed, jittery, or every-single-cut punch-ins feel mechanical.

### Captions as an edit decision
With most feed viewing sound-off, captions are a primary engagement driver, not an afterthought. The dominant 2025–26 style is **word-by-word / "karaoke"** — each word highlights as spoken via a color shift, reading rhythm matched to speech. The **bold-outline** look (thick black stroke, ~5–8 words per line, lower-middle third inside the safe area) is the legibility baseline. *(Caption visual styling — fonts, the "Hormozi" look, animation — lives in the sibling doc's title section; here the point is that caption timing is part of the cut.)* **Trap:** captions placed where the platform UI covers them; mistimed highlights; the identical auto-style on every clip now reading as sameness.

### Beat-sync & the transition trends
Cutting hits, text, and effects to the beat. Current named transitions: **whip-pan** (same-direction motion blur between clips), **snap-zoom**, **invisible/outfit-change** (hide the cut behind a passing object, a hand over lens, or a match-on-motion), and **velocity/speed-ramp** edits (fast→slow→fast ramped to audio, smoothed with Twixtor in the After Effects "edit" subculture). **Trap:** spin/3D and shake transitions are cooling — the over-edited look the 2026 algorithm reportedly de-prioritizes. Clean "invisible" transitions are favored over flashy ones.

### Seamless loop
The final frame connects to the first so replay has no visible boundary — triggering involuntary rewatch (a completion signal platforms weight heavily). **Reach for it** on punchy, satisfying, "wait for it" clips. **Trap:** forced loops that don't actually match.

### Format-native grammar
The moves that only exist because of the feed: **direct address** (eye-contact, second-person, conversational), **text-on-screen storytelling** (the narrative carried by sequential on-screen text over a vibe clip), **green-screen reaction** (creator keyed over the media they're reacting to), **duet/stitch**, and **satisfying/ASMR pacing** (slower, sound-forward, deliberately *holding* shots — the one place "no dead air" is wrong). **Trap:** wall-of-text listicles (now dated); low-effort "react to everything"; loud music killing an ASMR piece.

### Short-form genres (each with its native cut)
Tutorial/how-to (front-load the result, tight step cuts), listicle (countdown headers — the *dense* version is cooling), story-time (direct address + but/therefore + open loop, often multi-part), day-in-the-life/vlog (rapid montage, time-stamp text), product/UGC ad (native, un-ad-like), meme edit (trend audio + template, decays fast), street interview (punchy answer first, name/question supers), edutainment (counterintuitive-fact hook + tight pacing). **Trap (general):** burying the best soundbite; being late to a trend; a slow setup before the payoff.

## 5.4 Music video
Rhythm-led — cut on or around the beat (downbeats punch, off-beats experiment), with genre-matched grammar: EDM/rock leans on jump cuts, whip-pans, strobe and match cuts; ballads on cross-dissolves, fades, and longer takes. The craft is balancing rhythm, lyric, and image — and sometimes *holding long* through frantic music for contrast. **Trap:** mindless beat-cutting with no relation to the lyric or the image.

## 5.5 Documentary
Two poles plus a signature device. **Vérité / observational** (direct cinema, fly-on-the-wall): minimal intervention, long observational takes, cut to preserve real time and "truth." **Essayistic / expository:** voice-of-God VO over B-roll, argument-driven, archival-heavy. **The Ken Burns effect:** slow pan-and-zoom across still photographs to give motion to stills — popularized by Ken Burns, named when Apple built it into iPhoto/iMovie. **Trap:** shapeless vérité footage with no editorial spine; the mechanical "doc slideshow" Ken-Burns-on-every-photo; VO that narrates what's already on screen.

## 5.6 Corporate & explainer
Continuity-clean, brisk, often VO- or motion-graphics-led, with lower-thirds and screen recordings — optimized for clarity over art. **Trap:** stock-footage blandness and pacing too slow for an impatient audience; the "explainer" pace that assumes more patience than anyone has.

## 5.7 Sports & highlight
Energy-led — cut to the *peak* of each play, nat-sound and music driven, escalating, with replays and slow-mo reserved for the climax beats. **Trap:** cutting away from the decisive moment; uniform pacing with no build toward the payoff.

## 5.8 News & broadcast package
The anchored-package structure: strong open (nat-sound or a compelling soundbite/SOT) → VO over B-roll for context → SOT for human perspective → VO → SOT → close + sign-off, often with a reporter stand-up; runs ~1:15–2:00. Core rules: VO must *not* narrate what's already on screen; SOTs carry *feeling*, not facts the reporter could state. **Trap:** "wallpaper" B-roll that doesn't match the VO; SOTs spent on dry information.

## 5.9 Genre anatomy quick reference

| Format | Typical length | Spine / structure | Pacing | The cut's job | The trap |
|---|---|---|---|---|---|
| Brand film | 60–120s+ | Story arc, soft/no CTA | Slow-ish, breathing | Build affinity, hold mood | Cutting it like a DR ad |
| Performance ad | 6–30s | Hook → PAS → CTA | Fast, hook-first | Drive an action | Buried CTA; no payoff before the ask |
| UGC ad | 15–45s | Native talking head + demo | Fast 2–3s cuts | Not look like an ad | Polish breaking the illusion |
| Trailer | 60–150s | 3–4 act build → drop → button | Rising tempo | Sell the promise, withhold | Braaam-and-flutter sameness |
| Dialogue scene | — | Shot/reverse, reaction-driven | Set by performance | Read the right face | A-B ping-pong, missed reactions |
| Action scene | — | Coherent intensified continuity | Sub-2s, escalating | Keep geography legible | Chaos-cinema noise |
| Short-form social | 7–60s | Hook → retain → payoff/loop | Cut every ~1.5–2s | Win the first 3s, hold | Slow intro; over-editing |
| Music video | song length | Beat-led, genre grammar | Cut on/around the beat | Marry rhythm, lyric, image | Robotic beat-cutting |
| Documentary | — | Vérité or essayistic | Observational or argument | Preserve truth / build a case | Shapeless footage; VO narrating the picture |
| News package | 75–120s | Open → VO/SOT alternation → sign-off | Brisk, even | Inform without redundancy | Wallpaper B-roll; SOTs on facts |

---

# 6. B-roll, layering & screen division

### B-roll (overlay)
Supplementary footage cut over the main audio/VO to illustrate, add information, and hide cuts in the A-roll. **Reach for it** to cover a jump cut, show what's being described, or vary a static talking head. **Trap:** generic stock B-roll that doesn't match the words; B-roll for its own sake that breaks rhythm.

### Cutaway & insert
(See [§2.1](#21-cuts).) Cutaway = a related secondary shot away from the main action; insert = a detail *within* the scene. The two main tools for controlling attention and hiding time edits. **Trap:** cutaways that add nothing; inserts the audience didn't need.

### Picture-in-picture (PiP)
A second image inset over the main frame — reaction cam, screen + face, source + commentary. Native to reactions, tutorials, and gaming. **Trap:** the inset covering the thing it's commenting on; a PiP that's decorative rather than informative.

### Split screen / multi-box
The frame divided into two or more simultaneous images — for parallel action, comparison, conversation across distance, or density (the *24* multi-box, the music-video grid). **Trap:** more boxes than the eye can read; splitting the screen when a cut would carry the comparison better.

### Overlay graphics & layering
Text, callouts, and motion graphics composited over footage as part of the edit (the *styling* of these lives in the sibling doc; the *timing* — when each appears and clears — is an edit decision). **Trap:** layers that arrive and leave on no rhythm, fighting the cut instead of riding it.

---

# 7. Time & speed manipulation

### Slow motion
Footage captured at a high frame rate (60/120/240+ fps) and played at 24/30 for smooth slow motion — drama, beauty, impact, the hero moment. **Trap:** slow-mo overuse drains pacing and energy; it needs enough light/shutter or it strobes. *(Frame-rate-as-look is detailed in the sibling doc; here it's a timeline tool.)*

### Speed ramp / time remap
Dynamic speed changes within a shot — fast→slow→fast — ramped to audio hits; smoothed with optical-flow tools (Twixtor) in high-craft edits. The engine of action, sports, dance, and hype edits. **Trap:** jarring ramps with no motion blur; ramping for its own sake.

### Fast motion / timelapse / hyperlapse
Speeding footage up: **timelapse** (many stills/long span, static camera), **hyperlapse** (timelapse with the camera physically moving between frames). Passage of time, scale, energy, "epic transition." **Trap:** the establishing-shot crutch; an unstabilized hyperlapse is a jittery mess.

### Freeze frame
Holding a single frame — to punctuate, label a character, or stop time for narration. **Trap:** the dated "record-scratch, freeze, 'yep, that's me'" cold-open; freezing on a frame that isn't worth the stop.

### Reverse
Playing footage backward — for surrealism, a reveal, or a satisfying "un-doing." **Trap:** a novelty that wears off instantly; obvious reversed motion (hair, smoke, gravity) that reads as a gimmick rather than an effect.

### Stutter / strobe / step-print
Repeating or dropping frames for a stuttered, pulsing, or hand-cranked feel — common on beats in music and hype edits. **Trap:** eye-fatiguing when sustained; a texture, not a base layer.

### Frame interpolation
Generating in-between frames to smooth slow-motion or raise frame rate after the fact. **Trap:** interpolation artifacts (warping edges, ghosting) on fast or complex motion — the smoothness isn't free.

---

# 8. Sound & the cut

Sound is half the edit even when it isn't the subject. The cut and the audio are decided together; these are the audio-side moves that *are* editing decisions. *(Full sound design — mix, foley, score — is out of this doc's scope.)*

### Cutting to music / the beat
(See [§3](#3-pacing--rhythm).) The track is a pacing grid: downbeats for punch, drops for the biggest picture moment, the build for accelerating cuts. **Trap:** robotic every-beat cutting; ignoring the track entirely so picture and sound feel unrelated.

### Sound bridge
Audio that carries *across* a picture cut — the next scene's sound starting early (J-cut) or the previous scene's continuing (L-cut) — to smooth or to comment. The connective tissue of scene transitions. **Trap:** a bridge with no reason; smoothing a cut that *should* be abrupt.

### Needle drop
A deliberate, often unexpected music cue dropped onto a moment for tone or irony. **Reach for it** for energy, a hard tonal shift, or a trailer/montage lift. **Trap:** the "licensed song doing the emotional work the edit didn't earn."

### Silence as an edit
Cutting the sound out — full silence after a wall of noise — as the loudest move available. The release in a build/release curve; the held beat before a reveal. **Trap:** silence with nothing riding on it; using it so often it stops landing.

### The radio edit (dialogue first)
A dialogue-editing method: cut the *audio* of a scene first, eyes closed, until it sounds right as pure radio — then lay picture over it. Forces the cut to serve the performance and the listen, not the pretty frame. **Reach for it** in interview, talking-head, and dialogue work. **Trap:** cutting to picture first and bending the audio to fit — the scene looks right and sounds wrong.

### Audio-led hook (short-form)
Opening on the next line's audio over the first frame (a J-cut as a hook) so the *sound* grabs before the picture does. **Trap:** a mistimed lead that reads as a glitch; an audio hook that over-promises what the video delivers.

---

# 9. The edit-workflow stages

The path from raw footage to finished cut. Useful as a literal workflow and as the right altitude to instruct an AI editor — "give me a stringout of the selects," "this is a rough cut, ignore color," "we're at picture lock."

### Selects / stringout
The first pass: pull the usable takes and best moments ("selects") and lay them end-to-end in script or logical order (a "stringout"). No shaping yet — just everything worth keeping, in a row. **Reach for it** to see what you actually have before you cut. **Trap:** skipping it and cutting straight from the bin — you edit blind and miss the best material.

### Paper edit
Planning the cut *on paper* (or in a doc) from transcripts and logs before touching the timeline — common in documentary and interview work. **Reach for it** when the structure lives in what people *said*. **Trap:** over-committing to a paper structure that the footage won't actually support.

### Assembly
The first timeline pass: every scene in order, roughly the right takes, far too long. The skeleton. **Trap:** polishing the assembly — it's meant to be loose and overlong; refining it early wastes work you'll cut anyway.

### Rough cut
The assembly shaped into something that plays — scenes trimmed, the arc legible, pacing roughed in, but not fine. Where the story is *found*. **Trap:** judging a rough cut on polish (color, sound, graphics) instead of structure; showing it to stakeholders who can't see past the temp look.

### Fine cut
Frame-accurate refinement — every cut motivated, every trim tightened, rhythm dialed, reactions placed. The craft pass. **Trap:** fine-cutting before the structure is locked — polishing scenes that will get cut.

### Picture lock
The edit is frozen so downstream work (color grade, sound mix, VFX, graphics, titles) can begin against a stable cut. **Trap:** "lock" that keeps changing — every re-cut after lock ripples into conform, sound, and color and burns budget.

### Online / conform & finishing
Relinking the locked edit to full-resolution media, color grading, sound mixing, adding final graphics and titles, and exporting to delivery specs. The finish. **Trap:** discovering at conform that the edit used the wrong media, mismatched frame rates, or unlicensed assets — finishing surfaces every shortcut taken upstream.

### Multicam
Editing synchronized footage from multiple cameras of the same event by cutting between angles live or in post — concerts, interviews, events, podcasts. **Trap:** cutting angles on a metronome rather than on motivation; ignoring continuity (eyelines, screen direction) between cameras.

### Versioning & deliverables
The modern finish is rarely one file: a master plus cutdowns (:30/:15/:06), aspect-ratio variants (16:9 / 9:16 / 1:1 / 4:5), captioned and clean versions, and platform-spec exports. **Reach for it** by planning the family up front and protecting framing for every ratio. **Trap:** treating cutdowns and reframes as an afterthought — blind crops decapitate subjects and rushed :15s lose the hook.

---

# 10. Assembling AI-generated footage

The new craft: most AI video tools (Higgsfield, Hyperframes, Veo, Kling, Runway, Seedance, Hailuo) generate *clips* — 2–15 seconds each, one clean camera move apiece. Turning a folder of gens into something that holds together is an *editing* problem, and the grammar in this doc is the solution. The promptable look of each clip lives in [`motion-graphics-taxonomy.md`](motion-graphics-taxonomy.md); this section is how you cut them together.

### Shot-list before you generate
Decide the edit first — the sequence of shots, their sizes, and the cuts between them — then prompt each clip to fill a slot. Generating clips and editing-to-discover wastes credits and yields a reel of disconnected "best shots." **Reach for** a classic coverage logic (establishing → medium → close → reaction) so the gens cut together like real coverage. **Trap:** prompting twenty hero shots and no connective tissue — no inserts, no reactions, nothing to cut *to*.

### Continuity across clips
AI clips drift — identity, lighting, color, and background can shift shot to shot. Lock what you can at generation (a character/consistency reference, a fixed start frame, the same aspect and grade) and *fix the rest in the edit*: a unifying color grade across all clips, match-on-action and cutaways to hide mismatches, and a consistent caption/graphics layer to bind them. **Trap:** trusting raw gens to match; cutting two clips of "the same" person whose face subtly changed across the join.

### Cut to hide the AI tell
The artifacts — warping hands and faces, melting backgrounds behind orbits and pull-outs, slow identity drift, flicker — usually appear at the *ends* of clips and on complex motion. Cut *away* from them: trim before the warp, hide a morph inside a whip-pan or a match-on-action, keep shots short enough that drift never accumulates, and cover suspect frames with B-roll or a graphic. A faster ASL is a feature here, not just a style. **Trap:** holding a generated shot long enough for the model's drift to become visible; ending a clip on the frame where the hands fall apart.

### Use start/end frames as edit points
Image-to-video with a fixed **start frame** (and optional **end frame**) is a continuity tool: end clip A on a frame, start clip B on the same frame, and the join is a built-in match cut. Keyframe-interpolation tools (Pikaframes, Luma keyframes, Veo first/last) let you author the in-and-out of a shot to land on a clean cut point. **Trap:** big gaps between supplied frames produce morphing; the interpolation is only as clean as the endpoints you give it.

### Pace and caption for the platform
The destination dictates the cut: vertical 9:16 and a sub-second hook for social, a slower ASL and breathing room for a brand film, captions and safe-area-aware text for sound-off feeds. Most tools expose **reframe / auto-aspect** to retarget one master to 9:16 / 1:1 / 4:5 — but plan framing for every ratio up front rather than blind-cropping (which decapitates subjects and breaks composition). **Trap:** generating 16:9 hero clips and crop-to-vertical at the end; letting auto-reframe wreck the framing you generated.

### Let the edit carry meaning the clips can't
Individual gens are isolated moments; the *cut* is where Kuleshov ([§1.2](#12-montage-theory)) does the work — sequence a neutral generated face, a generated object, and a generated reaction and the audience infers a story no single clip contains. The model makes images; the edit makes meaning. **Trap:** expecting each clip to "say" something on its own and stacking spectacle, instead of letting juxtaposition and rhythm do what they've always done.

---

# 11. The default-edit trap index

The editing equivalent of a keyword-collapse: the canned moves an editor (or an AI tool given no direction) emits by default. Name them to avoid them.

- **The cut-on-every-word talking head** — relentless jump cuts with no breath, no reaction, no B-roll. Reads as "raw social default," not as a choice.
- **Zoom-transition everything** — a punch/whip/spin transition on every cut. Energy as a substitute for rhythm; the over-edited look 2026 actively penalizes.
- **The corporate-explainer pace** — even, mid-tempo, dissolve-glued, stock-B-roll, VO-over-everything. Clarity with no pulse.
- **The braaam-and-flutter trailer** — the *Inception* horn, rising flutter-cuts, a drop, a button — run by the numbers. Instantly dated and parodied.
- **Beat-cut robotically** — a cut on literally every beat, with no holds and no relation to image or lyric. Mechanical, not musical.
- **The training-montage / passage-of-time slideshow** — montage standing in for a beat you didn't earn, or "passage of time" that compresses nothing.
- **Chaos-cinema action** — sub-second shaky cuts manufacturing excitement and hiding un-staged action. Noise, not thrill.
- **Soft-transition-itis** — dissolves and fades between scenes that should hard-cut. The 1990s-slideshow tell.
- **The record-scratch freeze-frame cold open** — "yep, that's me, you're probably wondering how I got here." Dead on arrival.
- **The ripple-dissolve flashback** — every memory signposted with a wavy dissolve and a harp. The audience got it without the costume.
- **Unmotivated cutting** — cuts that happen on a clock, not a trigger. Technically clean, emotionally arbitrary.
- **Overlay/filter soup on AI clips** — masking generation drift with stacked grain, glitch, and shake instead of cutting away from it. The cut is the fix, not the plugin.
- **The reel of disconnected gens** — AI hero shots with no coverage, no continuity grade, no connective tissue. Spectacle with no edit.

---

## Quick decision checklist

1. **Register first.** Invisible continuity or foregrounded collision? Everything below inherits this.
2. **Match pace to goal.** Brand vs performance, dread vs hype, observe vs sell — set the ASL the objective demands, not a default.
3. **Earn the first three seconds** (short-form) or **protect who-is-where** (narrative). Know which veto you're under.
4. **Motivate every cut.** If the only reason is "it had been a while," find a real trigger — a look, a move, a sound, a beat — or don't cut.
5. **Cut for emotion and story before continuity** (Murch). If a technically "wrong" cut feels right, it's right.
6. **Build and release.** Shape pace as a wave; give every peak a valley.
7. **Hard-cut by default.** Reach for a soft transition only when it's doing real work.
8. **Sound and picture together.** Decide the J/L, the bridge, the needle drop, and the silence as part of the cut; radio-edit dialogue first.
9. **Know your stage.** Selects → assembly → rough → fine → lock → finish. Don't polish what isn't structured.
10. **Assembling AI footage?** Shot-list first, grade to unify, cut away from the tell, let juxtaposition carry meaning.
11. **Run the trap index.** If the edit matches a default on the list, that's the signal to make an actual choice.
