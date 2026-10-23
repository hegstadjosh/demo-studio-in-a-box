# Cut and build

**Cut and build.** Keep every edit decision for recorded footage in the cut file, `cut.json`, and write a builder, the script that renders from it. Every preview and export comes from the cut file through the builder, with or without an edit room (`seeds/edit-room.md`).

**Hypothesis: every film that cuts or retimes recorded footage renders from a cut file through the builder, and the builder reads only the cut file and source media.** A draft made this way says which edits it contains, because its build records the draft id and the cut file's hash, and any draft can be rebuilt after a later change. A patched render cannot say which edit it reflects. In the source production, which went through many drafts, patch scripts over frozen renders replaced the builder late on, and fixes went missing from the preferred draft. Not established for a film of a few plain trims, where the cut file is short and the builder can be a list of FFmpeg cuts. It fails when a one-off repair is genuinely cheaper than extending the builder and gets applied to a render instead; record the repair in the cut file as data, so the next build reproduces it.

## The cut file

`cut.json` holds the named drafts and which one is current. Each item carries its source file, in and out points in source time, label, speed, gain, borrowed picture, freeze or hold, overlap lead, and a generated-line flag. Name source time and timeline time separately everywhere, because speed, holds and overlaps make them diverge; where the cut plays inside a composition, name composition time too, because the composition offsets the cut and every caption and cue keyed to it must move with it. Design the schema yourself.

Reframing values live in the cut file too: zoom for any item, and for screen recordings the crop, zoom and pan keyframes (`seeds/coded-scenes.md`, Screen recordings). Key them to source time, so a trim or retime moves each keyframe with the moment it frames, and the builder reproduces the framing on every build.

**Hypothesis: a new draft per batch of your edits,** named with the time and the change, because the person compares versions and an in-place edit destroys the one they were comparing against. This held while the person directed in the editor. It fails when every tweak spawns a draft and the selector buries the comparison; group edits by the person's request.

## The builder

The builder turns one draft into frame-exact clips plus composition data: frames per segment, the source-time map, captions with word starts, per-frame voice level, and the reframing applied through the same source-time map. Rough mode renders a bare stitch. A per-clip cache keyed by a hash of everything shaping a clip's output rebuilds only what changed. Process only the spans the cut uses; before interpolating, drop exact repeated frames, and never interpolate across a camera switch. Each build records the draft id and the cut file's hash.

**Self-tests.** The builder runs these before every render of a build that retimes footage, cuts recorded speech or shows captions, and fails on a mismatch; the audit report cites the results. They check the time facts in `reference/technical-facts.md`, whose violation caused repeated rework in the source production. A build of plain trims needs only an ffprobe duration check.
1. **Round trip:** map sample instants in every segment from source to output time and back; each returns within half a frame.
2. **Speed composition:** each clip's effective speed is the product of its factors, and a clip exported at speed carries a flag that blocks a second retime.
3. **Cumulative rounding:** per-segment frame and sample counts sum to the rounded cumulative boundaries.
4. **Caption alignment (hypothesis):** re-transcribing the export with word timestamps catches captions that drift after retiming; list caption words outside your recorded tolerance. Skip it when no retiming touched captioned speech, with the reason in the decision ledger.

## What each build reports

**Hypothesis: the builder runs the join checks on every cut-file change.** The checks are the sound level at the edges of each changed join, where a word cut mid-syllable leaves energy, and recogniser words in a short window around each changed join compared with the clip text, which reveal a clipped, leftover or doubled word. A cheap check on each change catches these mechanical defects before the person hears them. In the source production, the clipped and leftover words the person caught while directing the main cut in the editor were defects of this kind; the check itself was not run there. How reliably a recogniser reads so short a window is not established. It fails when edits arrive faster than the checks run and a result describes a superseded cut; match each result to the current hash. The builder writes each result to a status file, shown on the edit room's page when one exists, and appends it, with the draft id and the cut file's hash, to `edit-room/edit-log.md`.

The builder also prints, and records with the build, the clips and transcript lines added or removed relative to the last draft the person saw (the last shown draft in `project.json`). `tools/show` copies that list into the packet, so an addition the person did not ask for, such as a line an older draft's data restored, is visible before they watch.

## Musts

- **Must (technical fact):** writing into a file a running render reads corrupts the render; the builder renders from a copy of its draft, through `tools/render`, which holds the render lock (G3).
