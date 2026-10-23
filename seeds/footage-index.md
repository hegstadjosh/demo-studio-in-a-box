# Footage index

Before the assembly script, turn any recording to be cut by what happens in it (speech, screen activity, sound or picture events) into files in `footage/` that let you and the person find any moment without opening the source; one clip trimmed at known times needs none. Offer the clip library unasked through `tools/show` as a text list of labels, speakers, intervals and words, which needs no audit report.

Index what `project.md` lists, reusing existing labels, transcripts and selections:
- `proxy.mp4`, keyframed at least every 0.5 s so seeks are fast; `audio16k.wav`, 16 kHz mono;
- `transcript.json`, word-timed, from the recogniser `environment.md` records, tags such as [Music] flagged non-speech; with no recogniser, index from levels and frames and mark clips and the truth list "not transcribed";
- `speakers.json`, from whatever cue the recording offers, checked against sampled frames (lacking a reliable cue, label from frames and turn-taking and list those spans as unconfirmed in the truth list), and `lines.md`, numbered lines with each word's speaker;
- `levels.csv`, fine enough (10 ms worked) to find silences and correct the onsets of words alignment misplaces at pauses;
- `thumbs.png`, a strip, and `overview.png`, a timecoded sheet, frames grabbed per `reference/technical-facts.md` (Picture), one tile checked against a known event;
- `clips.json`, `structure.md`, `privacy.md` and, for a long source, `indexed-spans.md`.

**Hypothesis: split lines on pauses, turns and sentences,** so a person can point at each line; in the source production's two-person call, a line ended at a gap over 0.8 s, a speaker change across 0.15 s, a sentence end or 16 words. Other material is untested. Overlapping speech can merge turns, so split on every speaker change, and sound without words on level changes and silences.

## The clip library

**Hypothesis: one library over the whole source, labelled by what happens,** because people select faster from meaning than from transcript; in the source production it backed every draft. Each clip has a label, its words without non-speech tags, source interval and setup (what a viewer must know for it to land); a clip may be a partial turn or hold sub-clips. Whether your labels match the person's sense of a moment is untested; the person's labels replace yours, recorded as theirs. A label restating the transcript sends the person back to raw text; relabel it.

**Hypothesis: anchor clips by first and last phrases,** because phrases survive re-transcription where timestamps drift; without words, anchor by source time and a nearby level or scene event. Cut at word boundaries, padding (0.12 s before, 0.2 s after in the source) only into the clip's own speaker or silence, because padding into a neighbour imports its sound; there, cut at the level track's boundary. A repeated phrase can match the wrong instance, so give each clip an earliest start; fail the build on a missing anchor or a sub-clip outside its clip.

**Hypothesis:** the structure map, `footage/structure.md`, shows shape as labelled sections and sub-sections, each with what it does and how well it holds, without quoted transcript, which pulls the reader into lines; in the source production the person asked for it.

## Screen recordings

**Hypothesis: a product film needs a screen recording's visible state changes.** Find them with `scdet` and `freezedetect` (lower `d` below its 2 s default for short idle spans; checked 2026-10-22), read a frame per scene by vision or OCR, label clips by visible event, and mark idle spans as speed-up or cut candidates. Untested. It fails on a narrated walkthrough, whose value is the speech; index the speech.

## Musts

- **Must (technical fact):** speech recognition misses quiet and overlapping speech; a word absent from the transcript may be in the audio.
- **Must (truthfulness):** a clip's text is the transcript's words, untidied.
- **Must (privacy):** scan sampled frames for emails, keys, tokens, names and notifications, and list each span showing them in `footage/privacy.md` for blurring, cropping or cutting.
