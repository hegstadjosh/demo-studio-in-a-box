# Media index

The kinds of media a short film can contain, and the ways each is made. This file names no providers on purpose: the field changes faster than a skill is revised. When the treatment calls for a kind, follow the sourcing rule in `SKILL.md` (First moves): research the current state of the art for making and editing that kind, check what the person already uses, then offer options or choose.

Four ways to make any kind. **Recorded:** captured from the world or a screen. **Coded:** drawn from data and tokens by a program. **Licensed:** stock or library material under a licence that covers this use. **Generated:** produced by a model, hosted or local, usually paid.

| Kind | What it is in a film | Usual ways | What to check before using it |
|---|---|---|---|
| Moving picture | B-roll, scenes, transitions, motion graphics, product footage | Recorded; coded (composition tools, browser capture); licensed stock; generated video from text, image or video | Resolution and frame rate match the master; generated motion holds up at full size; licence covers commercial use |
| Still image | Illustration, portrait, background, product render, storyboard frame | Recorded; coded; licensed; generated from text or reference | Consistency across frames; the truth list records whether it depicts a real thing |
| Interface | Screens of the product the film is about | Recorded from the live product; coded depiction from brand tokens and component code (`seeds/coded-scenes.md`) | Every depicted feature exists (truthfulness) |
| Voice | Narration, character lines, dubbed speech | Recorded; free stand-in synthesis; generated voice with per-word timing; cloned voice (consent, G5) | Word timings for captions; consent for any real person's voice |
| Talking head | A face that visibly speaks approved audio | Recorded; generated from a portrait and audio; lip-sync of existing footage | Consent and rights (G5); splices cleanly into the cut |
| Music | Bed, sting, theme | Licensed library; local synthesis; generated from a text prompt or reference | Licence and attribution; loudness target (`reference/technical-facts.md`) |
| Sound effect | Hits, whooshes, interface sounds, ambience | Licensed library; local synthesis; generated from a description | Level against the voice; nothing masks a word |
| On-screen text | Titles, captions, labels, lower thirds | Coded (`drawtext`, `subtitles`, composition tools) | Readable at phone size; never covers a name or logo |
| Transcript and timing data | Word times, speaker map, scene changes | Local recognition; hosted recognition; diarization | Checked against sampled frames; privacy scan (`seeds/footage-index.md`) |
| Edited picture | Speed change, slow motion, stabilization, upscaling, background removal | FFmpeg filters; frame interpolation; generative editing (inpainting, extension, object removal) | The edit is declared in the truth note when it changes what the viewer takes as real |

**Hypothesis:** keeping the kinds and the checks here, and the providers in the dated environment table or in fresh research, means the skill ages well where it can and is rechecked where it cannot. Not established over time; this index was written on 2026-10-23.
