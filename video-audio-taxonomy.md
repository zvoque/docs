# Master Video Audio Taxonomy

> Part of a frontier/craft reference set for steering AI video tools, editors, and creators past the default. Default reach: drop a trending track under the whole thing at one flat level, no ducking, no design, mixed on studio headphones for a phone-speaker audience. Use the **trap** on each entry to avoid the cliché.

A working reference for the sound half of video — **voiceover**, **music**, **sound design**, **the mix**, **sync**, and **licensing**. Each entry: what it is, when to reach for it, and the trap to avoid; with a **prompt cue** where it helps you direct an AI voice or music tool.

This is the audio layer of a video reference set. Its siblings: [`video-editing-taxonomy.md`](video-editing-taxonomy.md) (the cut — where "cut to the beat" and J/L sound-cuts also live), [`video-preproduction-taxonomy.md`](video-preproduction-taxonomy.md) (the script & VO timing math), [`motion-graphics-taxonomy.md`](motion-graphics-taxonomy.md) (the visual language), [`ai-video-generation-playbook.md`](ai-video-generation-playbook.md), and [`code-rendered-video-playbook.md`](code-rendered-video-playbook.md).

Compiled June 2026. AI voice and music tools move fast and are flagged as time-sensitive; mix standards (LUFS) and sound-design craft are stable. AI-music ownership is genuinely unsettled and flagged inline rather than asserted.

---

## How to use this doc

- **Audio is half the picture, and the half people leave on default.** A competent mix on mediocre footage reads as professional; a bad mix on beautiful footage reads as amateur. It's the cheapest large quality gain available.
- **Layer, don't pile.** Voice → music → SFX is a hierarchy, not a stack at one level. The voice is on top, the music sits *under* it (ducked), SFX punctuate around them. Every layer at full level is mud.
- **Mix for the phone and the mute button.** Most social video plays on a tiny mono speaker, in a noisy room, often muted with captions. Sub-bass, stereo tricks, and whispered dynamics vanish there. Design the meaning to survive sound-off; let audio enhance, not carry.
- **Name the sound; don't hum the vibe.** AI voice and music tools resolve named direction — `[whispers]`, "112 BPM melancholic indie, instrumental," "announcer hype read" — far better than adjectives. The vocabulary here is the prompt.
- **Sync is decided after picture lock.** Spotting (where music and SFX go) and hit-points are placed against a *locked* cut; doing it earlier means re-doing it every re-edit.

---

## Table of contents

- [How to use this doc](#how-to-use-this-doc)
- [1. Voiceover](#1-voiceover)
- [2. Music](#2-music)
- [3. Sound design](#3-sound-design)
- [4. The mix](#4-the-mix)
- [5. Sync](#5-sync)
- [6. Licensing](#6-licensing)
- [7. The default-audio trap index](#7-the-default-audio-trap-index)
- [Quick decision checklist](#quick-decision-checklist)

---

# 1. Voiceover

The spoken core. In the AI era the read is generated and *directed* — which means the direction vocabulary is the prompt.

## AI TTS / voice tools

### ElevenLabs (and the expressive-TTS field)
The current leader in expressive AI text-to-speech — wide emotional range, 70+ languages, voice cloning, and inline performance control. Peers worth knowing: **Cartesia** (low-latency, real-time agents), **Hume** (emotion-first), **WellSaid Labs** (corporate-narration polish), **Murf / Play.ht / Speechify** (creator tools), and the enterprise SSML-first stacks (**Azure Neural TTS, Amazon Polly, Google Cloud TTS, OpenAI TTS**). **Reach for** the expressive models when emotional nuance matters; the enterprise stacks when you need SLAs and deterministic SSML control. **Trap:** the newest, most expressive models are the *least* deterministic — the same input drifts between generations, and "most natural" claims shift monthly. For long-form production pipelines a stabler older model often beats the flashiest new one; verify language coverage and commercial/cloning terms per vendor.

### Audio tags & performance control
Inline bracketed directions an expressive model interprets — emotion `[sad] [happily] [angry]`, delivery `[whispers] [shouts] [rushed] [drawn out] [pause]`, non-verbals `[laughs] [sighs] [clears throat]`, even accents `[British accent]`. **Reach for** them to direct a performance without re-recording. **Prompt cue:** embed tags inline at the exact word: `[whispers] it's already inside the house.` **Trap:** tags are probabilistic, not switches — they can be ignored, fire on the wrong word, or leak as artifacts; over-tagging destabilizes the whole read. Tag support is model-specific.

### Voice cloning (instant vs. professional)
**Instant clone** from a short sample — fast, lower fidelity, good for quick consistency. **Professional clone** trained on 30 min–3 hr of clean audio — high fidelity, a brand/talent's signature voice. **Reach for** instant for speed, professional for a signature voice at top quality. **Trap (legal):** cloning a real person's voice without consent violates law and platform policy — full stop. And the newest expressive models aren't always optimized for professional clones yet, so cloned quality can regress on the latest model.

### Pronunciation control (SSML, phonemes, dictionaries)
Three levers for getting tricky words right: **SSML** (`<break>`, `<emphasis>`, `<prosody>`, `<say-as>` — best on the enterprise stacks), **phoneme tags** (IPA/CMU to force exact pronunciation), and **pronunciation dictionaries** (map a word to a phoneme or an alias). **Reach for** these for names, brands, and jargon — the #1 failure point in e-learning and long-form. **Trap:** support is partial and model-specific (phoneme tags are often English-only and model-gated; dictionary files are case-sensitive). Newer expressive models often prefer natural-language tags over SSML — verify before relying on either.

## Voice direction vocabulary

The terms that translate "make it good" into something a human or a model can act on.

- **Tone / attitude** — the emotional color and stance (warm, authoritative, playful, sincere, snarky). The first thing you specify. **Trap:** "tone" and "style" get used interchangeably with no shared meaning — pin it to a reference clip, not an adjective.
- **Pace / tempo** — delivery speed, often expressed as WPM to hit a runtime. **Trap:** AI pacing is hard to control precisely; budget time for re-gens or post time-stretching.
- **Energy / intensity** — how much lift the performance carries. **Trap:** sustained high energy clips and fatigues; low energy dies on phone speakers.
- **Pitch** — highness/lowness and inflection range; lower = authority, higher/varied = friendliness/excitement. **Trap:** pushing pitch in post sounds artificial; AI voices have a baked-in range.
- **Read styles** — the working menu: **announcer** (broadcast hype — dated outside hard-sell; clients often ask for "non-announcery"), **conversational** (natural, the modern default), **hype / hard-sell** (urgent, abrasive at length), **ASMR** (intimate, close-mic — unforgiving of noise), **documentary** (measured, credible — tips into monotone without a subtle arc). **Prompt cue:** name the style explicitly — `conversational, warm, like talking to a friend`.
- **Terms of art** — **billboard** (lift a key word while staying in tone), **beat** (a tiny pause for a thought), **arc** (the emotional through-line), **pickup** (re-record a small section to match). **Trap:** AI tools don't natively understand "billboard this" — translate to emphasis tags.

## VO types
**Narration** (a guiding voice over explainers/docs/brand films — clarity is non-negotiable over long runtimes), **character** (performed personas — AI range still limited), **e-learning** (steady, clear, jargon-heavy — use a pronunciation dictionary), **IVR/telephony** (narrowband 8 kHz — mix for intelligibility), **dubbing** (lip/timing-constrained localization — AI lip-sync remains weak). **Trap:** matching the wrong VO type to the content — an announcer read on an intimate brand film, a conversational read on a hard-sell promo.

## Scratch / temp VO
A placeholder read (the editor's own, or a quick AI gen) cut against before the final is recorded — now usually AI TTS because it's instant. **Reach for it** to lock timing and structure early. **Trap:** **"temp love"** — the team falls for the scratch read's specific cadence and the final feels wrong; and a scratch made with a cloned/real voice can accidentally ship. Clear or replace it before delivery.

---

# 2. Music

The emotional engine and the pacing grid. Increasingly generated — which makes the prompt recipe a core skill.

## AI music generation
**Suno** (leading text-to-song — vocals + instrumental, structure, genre) and **Udio** (competing, strong audio fidelity) lead; peers include **Stable Audio, Google Lyria/MusicFX, AIVA, Soundraw, Mubert, Beatoven**. **Reach for** them for original, on-brief beds and songs fast. **Prompt cue (the reliable recipe):** *Mood + Genre/Era + Key Instruments + Vocal Type + Production/Mix Tone + Tempo (BPM)* — e.g. `melancholic 2000s indie rock, electric guitar + warm synth pads, male lead, nostalgic, wide cinematic mix, 112 BPM`. Generators weight early words most heavily (put the primary genre first) and **always specify BPM** (it stabilizes rhythm and predictability); use structure tags `[Verse] [Chorus] [Drop] [Outro]`, and explicitly request `instrumental` for beds. **Trap:** ownership is murky (see [§6](#6-licensing)); free-tier output is non-commercial; outputs sound generic without a disciplined prompt; and **Spotify/Apple now require AI-disclosure flagging at upload**. *(Flag: Suno settled with Warner and Udio with Universal in 2025–26; both are rolling out label-licensed models that change behavior and terms — verify current status.)*

## Stock / library music
Browsing pre-cleared, licensable tracks by genre/mood/BPM/energy. **Reach for it** when you need cleared, predictable music without generation risk. **Trap:** over-used "trending" tracks make content feel templated; filter by energy and runtime, not just genre.

## Tempo, energy & structure
- **BPM / tempo** — the grid your edit cuts against; fast cuts ↔ high BPM, slow emotional ↔ low BPM. **Trap:** mismatched BPM vs. edit rhythm makes a piece feel "off" even when nothing is technically wrong.
- **Energy** — perceived intensity, often independent of BPM (a high-BPM track can feel low-energy). Map the music arc to the story arc. **Trap:** judging by the tempo number instead of the feel.
- **Genre → emotion mapping** — genre as emotional shorthand: lo-fi → calm/nostalgic; trap → swagger/tension; ambient/piano → intimate/sad; orchestral hybrid → epic/heroic; synthwave → retro; corporate pop → optimistic/clean. **Trap:** genre clichés date fast and carry unintended cultural baggage.
- **The bed** — a continuous, low-intensity layer *under* VO to set tone without competing. **Reach for it** on explainers, podcasts, corporate, vlogs. **Trap:** a bed with melodic or vocal hooks fights the voice — pick sparse, sustained material and duck it.
- **Stems / multitrack** — the song split into component tracks (drums, bass, vocals, melody). **Reach for it** to remix to picture — drop the drums for a quiet beat, mute vocals under VO, rebuild to the edit. **Trap:** not all libraries/tools provide stems (or only at higher tiers); without them you can't surgically duck or rearrange.
- **Build / drop (trailer & hype structure)** — **build** = rising tension (risers, accelerating percussion, layering); **drop** = release where full music hits, usually on a cut. The trailer arc: quiet/atmospheric → momentum → climax, often with a **stop-down** (sudden silence before the final hit) as a natural cut point. **Reach for it** for trailers, promos, hype reels, launches. **Trap:** the drop must land *on* the picture beat — a few frames off reads as amateur; over-building with no payoff frustrates.

---

# 3. Sound design

The layers under (and around) voice and music. The difference between "has audio" and "sounds designed."

## The layer taxonomy
Professional sessions organize as **DX** (dialogue/VO) · **MX** (music) · **SFX** (hard effects) · **FLY** (Foley) · **AMB** (ambience/atmos) · **RT** (room tone) · **Design** (stylized elements).

- **Dialogue / VO (DX)** — the spoken core; everything serves it. **Trap:** if dialogue isn't intelligible, the mix has failed regardless of polish.
- **Music (MX)** — score and source music; sets tone and pace. **Trap:** the easiest layer to overuse — wall-to-wall music flattens dynamics and buries dialogue.
- **SFX / hard effects** — synced literal sounds tied to on-screen events (doors, engines, impacts), library or designed. **Trap:** library SFX that don't match the on-screen object or space break immersion.
- **Foley** — *performed* human/prop detail recorded to picture: **feet** (matched to surface/shoe/weight), **cloth** (body presence), **props/moves** (object handling). **Reach for it** for grounded, character-level realism. **Trap:** surface/material mismatch (wrong shoe on wrong floor) and wrong perspective (close Foley on a wide shot) destroy believability.
- **Ambience / atmos** — environmental beds (traffic, birds, wind, crowd, room HVAC) that establish place. **Trap:** a scene with no ambience sounds "dead"/vacuum-sealed.
- **Room tone** — the unique "silence" of a specific location, captured ~30–60s on set, used to fill gaps under dialogue edits so cuts don't drop to digital black. **Trap:** forgetting to capture it — audible holes between takes where tone is missing.

## Design elements (the stylized, non-literal toolkit)
- **Riser / uplifter** — a long sound rising in pitch/intensity to build tension before a reveal, cut, or drop. **Trap:** generic risers are a cliché; time the peak to the exact cut.
- **Downer / reverse-riser** — a descending sweep to release or transition down. **Trap:** overuse drains energy.
- **Impact / boom / hit** — a heavy percussive accent on a key frame (title cards, logo stings, punches). **Trap:** too many = fatigue and loudness-limiter pumping.
- **Whoosh / swoosh / transition** — a movement sound for objects, camera moves, and graphic transitions. **Trap:** a whoosh on every transition reads as cheap; vary length and character.
- **Stinger** — a short musical/sonic sweetener punctuating a reveal or punchline. **Trap:** a stinger in the wrong key clashes with the score.
- **Drone** — a sustained, evolving tonal bed for tension/unease (suspense, sci-fi). **Trap:** static drones get boring (add slow filter movement) and mud up the low-mids.
- **Sub-drop / sub-boom** — a deep sub-bass hit for weight and shock. **Trap:** inaudible on phone speakers and laptops — never the *only* accent; it can also wreck loudness/true-peak.
- **The "braaam"** — the loud, low brass blast popularized by *Inception*-era trailers. **Reach for it** for epic/ominous hits. **Trap:** now heavily parodied — sparingly and intentionally.

## The role of silence
Deliberate absence of sound as a design choice — the brain notices *removal* more than presence. Strip ambience/music just before a scare, reveal, or emotional climax (*A Quiet Place*) so the next sound lands hard. **Reach for it** to maximize an impact or build dread. **Trap:** on sound-off social, true silence reads as "audio is broken"; and dead silence after loud content exposes the dynamic jump — manage with captions and visual cues.

---

# 4. The mix

Balancing the layers so the result is clear, consistent, and survives a phone.

## Level hierarchy
The canonical priority: **VO/dialogue on top → music underneath → SFX punctuating around them.** **Reach for it** as the default starting balance for any spoken-word piece. **Trap:** mixing each element to sound good *solo* instead of in context — balance is relational, set it in the full mix.

## Ducking / sidechain compression
Automatically lowering the music whenever VO is present (a compressor keyed to the voice, or NLE/DAW auto-ducking), then restoring it. **Reach for it** to keep music energy while guaranteeing the voice stays clear — podcasts, explainers, ads, livestreams. **Trap:** aggressive ducking "pumps" audibly (too-fast attack/release, too-deep dip); too gentle and the voice still fights the bed. Tune attack/release/threshold/depth — and for music with strong transients, also pick sparser material.

## Loudness standards (LUFS)
LUFS = integrated program loudness (LKFS is the broadcast-equivalent term, same scale). The verified 2025–26 targets:

| Target | Use |
|---|---|
| **−14 LUFS** | Streaming default — YouTube, Spotify, Apple Music, Amazon, Tidal. Platforms normalize *to* this. |
| **−16 LUFS** | Podcasts (Apple standard, ±1 dB); spoken-word. |
| **−23 LUFS (EBU R128)** | EU/rest-of-world broadcast. |
| **−24 LUFS (ATSC A/85)** | US broadcast/TV. |
| **≈ −14 LUFS, tolerant of hotter (−12 to −10)** | TikTok/Reels/Shorts — feeds run loud. *(Approximate and moving — verify per platform.)* |

**Reach for** the target that matches your *deliverable spec exactly* — broadcast QC rejects out-of-spec loudness. **Trap:** mastering hotter than −14 for streaming just gets turned down, losing dynamic range for no loudness gain; delivering a −23 broadcast mix to YouTube sounds weak. *(Platform numbers change and vendors publish conflicting values — treat social targets as approximate.)*

## Peaks, headroom & dynamics
- **True peak / dBTP** — the real peak including inter-sample peaks that appear after lossy transcode. Use a true-peak limiter on every master. **Trap:** a mix hitting 0 dBFS clips *after* the platform re-encodes it.
- **Headroom / ceiling** — leave margin: **−1 dBTP** common, **−1.5 dBTP** safer before lossy transcode. **Trap:** a −0.1 ceiling invites post-codec clipping; −3+ needlessly sacrifices level.
- **Dynamic range** — wide for cinematic/headphone contexts, narrow (compressed) for noisy/social/mobile listening. **Trap:** film-style wide dynamics on social means viewers crank for dialogue then get blasted by music — and most just scroll away.

## Mix for phone speakers / sound-off
Assume tiny mono speakers, no sub-bass, noisy rooms, and a large muted-with-captions audience. Keep critical info **mono-compatible** (stereo-only effects vanish when collapsed to mono), don't rely on sub-bass or whispered dynamics, compress more for consistency, and carry meaning visually so the piece works silent. **Reach for** this on all social/short-form. **Trap:** approving a mix only on studio monitors or headphones; stereo-width tricks and low-end punch that disappear or distort on a phone; assuming anyone hears the audio at all.

---

# 5. Sync

Marrying sound to picture. Several of these are shared with the edit — cross-referenced to [`video-editing-taxonomy.md`](video-editing-taxonomy.md).

- **Cutting to the beat** — placing edit points on the music's rhythmic grid (downbeats, accents). **Reach for it** for montages, hype reels, music-driven social, trailers. **Trap:** cutting *every* beat is exhausting and mechanical — cut on selected accents; an edit a few frames off the beat feels worse than not cutting to it at all.
- **Hit point** — a specific frame where a musical accent (brass stab, drum hit) lands on an on-screen action (punch, door slam, logo). **Reach for it** to emphasize precise dramatic or comedic moments. **Trap:** too many = busy; missing the frame by a hair kills the effect.
- **Mickey-mousing** — scoring/SFX that mimics on-screen movement beat-for-beat (tiptoe = staccato notes per step). **Reach for it** in animation, comedy, kids' and playful brand work. **Trap:** in serious/realistic content it reads as cartoonish and undercuts tension.
- **Spotting** — the process (after picture *lock*) of deciding where music and SFX go, marking each cue's in/out. **Reach for it** as the planning step before you score or design. **Trap:** spotting against an *unlocked* edit wastes work — every re-cut shifts your sync points.
- **J-cut & L-cut (sound leading/trailing)** — **J-cut:** the next scene's audio starts before its picture (sound leads). **L-cut:** the current scene's audio continues over the next picture (sound trails). **Reach for them** to smooth transitions and overlap dialogue. **Trap:** hard A/V cuts that slam together feel abrupt; no J/L overlaps makes dialogue scenes robotic.
- **Sync sound & frame-rate discipline** — audio recorded with picture, matched to action/lip movement. **Trap:** drift over long takes, and sample-rate or frame-rate mismatches (23.976 vs 24) cause creeping desync — lock rates across the pipeline.
- **Tempo-matched edits** — choosing or conforming music BPM to the footage's natural rhythm (or vice versa). **Trap:** a great track at the wrong tempo will never "sit" — time-stretch, change track, or re-cut.

---

# 6. Licensing

The rights layer — and, for AI-generated audio, the genuinely unsettled part.

## License types
- **Royalty-free (RF)** — pay once or subscribe, use unlimited, no per-use royalties. **Reach for it** for high-volume content where predictable cost matters. **Trap:** "royalty-free" ≠ "free" and ≠ "no rules" — usage scope (web vs. broadcast vs. paid ads), territory, and per-project limits still apply; subscription RF often means tracks become **unlicensed if you cancel**.
- **Sync license** — permission to synchronize a *composition* with visual media. **Trap:** covers the composition only — you also need the master.
- **Master (master-use) license** — permission to use a specific *recording*. **Trap:** using a famous track legally usually requires **both** sync and master, often from different rights holders (publisher vs. label) — slow and expensive.
- **Production music library** — pre-cleared catalogs written for media, licensed quickly. **Reach for it** to skip the dual sync/master clearance. **Trap:** per-use pricing on some libraries scales with reach/territory — confirm coverage for paid ads, broadcast, and your region.

## AI-generated music — ownership (flagged: high uncertainty)
**Unsettled and risky.** Key facts (2025–26): purely AI-generated works generally **cannot be registered for U.S. copyright** (no human authorship) — only human-authored elements qualify. A tool's "commercial-use rights" on a paid plan is a license to *use*, not proof you *own or can defend* it; free-tier output is typically non-commercial. **Trap (critical):** "you own your songs" marketing ≠ enforceable copyright — you may be able to *use* an AI track but **cannot stop others from using a near-identical one** and can't reliably register or defend it. Label settlements (Warner/Suno, Universal/Udio) mean terms and training data are **actively changing** — today's TOS may differ next quarter. And **Spotify/Apple now enforce AI-disclosure flagging at upload** — a compliance step, not optional. Verify each tool's current terms before any commercial release.

## Major libraries (positioning)
- **Epidemic Sound** — subscription RF, pre-cleared for YouTube Content ID, strong search. **Reach for it** for creators wanting zero Content-ID hassle. **Trap:** tracks become unlicensed if you unsubscribe; heavy use → ubiquity.
- **Artlist** — subscription RF for filmmakers/commercial, broadcast/ad licenses. **Reach for it** for ads, film, broadcast-grade deliverables. **Trap:** confirm the tier covers broadcast/paid social.
- **Musicbed** — premium-feeling brand/film catalog, also project-based licensing. **Trap:** premium pricing; check subscription vs. single-project for commercial spots.
- **Others** — Soundstripe, PremiumBeat, Storyblocks, Marmoset, APM/UPM (broadcast/pro). **Trap:** subscription vs. needle-drop vs. blanket models differ fundamentally — match to your distribution.

## Content-ID risk
YouTube's automated rights-matching can claim, demonetize, or block a video if it detects "owned" audio. **Reach for** pre-cleared/whitelisted libraries and register your channel where required. **Trap:** even legitimately licensed music — and **AI-generated tracks** — can get false Content-ID claims because someone else uploaded the same or similar audio; AI tracks are especially exposed since a generator can output near-identical music to others. Keep your license receipts.

---

# 7. The default-audio trap index

What "didn't think about audio" sounds like.

- **The flat-level drop** — one trending track under the whole video at a single level, no ducking, burying the voice.
- **No ducking** — music and VO fighting at the same level; the words get lost.
- **Wall-to-wall music** — score under every second, flattening all dynamics and killing the impact of any one cue.
- **Mixed for headphones, played on a phone** — sub-bass, stereo width, and whispered dynamics that vanish on the device 90% of viewers use.
- **Audio-only meaning** — the punchline, stat, or CTA exists only in the sound, invisible to the muted majority.
- **The off-beat drop** — a music drop a few frames off the cut, reading as amateur.
- **Riser/whoosh/braaam on everything** — design elements as reflexes, not punctuation; fatigue and cliché.
- **No room tone** — audible holes between dialogue edits where the location's "silence" wasn't captured.
- **Loudness ignored** — delivering off-spec LUFS, getting normalized down to a weak, quiet mix.
- **AI-music "I own this"** — assuming a generated track is yours to defend, undisclosed, and Content-ID-safe. It usually isn't.

---

## Quick decision checklist

1. **Set the hierarchy first.** VO on top, music ducked underneath, SFX punctuating. Never one flat level.
2. **Pick music by BPM and energy, not just genre** — and match the track's arc to the story's build/release.
3. **Direct the read by name** — tone, pace, energy, read style, with tags at the exact word; budget for re-gens.
4. **Design with intent** — risers, impacts, whooshes, and silence as punctuation, not reflexes; capture/lay room tone.
5. **Duck the music under the voice.** Tune attack/release so it doesn't pump.
6. **Mix for the phone and the mute button** — mono-compatible, compressed for consistency, meaning carried visually.
7. **Hit your LUFS spec** for the deliverable (−14 streaming, −16 podcast, −23/−24 broadcast); true-peak ceiling −1 dBTP.
8. **Spot and sync after picture lock** — hit-points on the beat, J/L overlaps, locked sample/frame rates.
9. **Clear the rights** — license scope, AI-disclosure flags, Content-ID safety; keep receipts. Treat AI-music ownership as unsettled.
