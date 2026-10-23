# Edit room

**Edit room.** Build a small local web editor that you and the person share over the cut file, which the builder renders from (`seeds/cut-and-build.md`), and record the editor's tests in `edit-room/verification.md`.

The person directs by pointing (put this after that, trim here, show this reaction under that line); you make the same change in the cut file, and the open page shows it without a reload. Build the page when a person will direct cuts of recorded footage; otherwise the clip library and scripted previews usually serve, unless the editor would speed your own iteration. **Hypothesis:** an editor the person already uses may serve; it fails when that editor cannot read your edits and the person must re-enter each. Vet any third-party tool before installing it.

The page edits the cut file's named drafts and each item's source, in and out points, speed, gain, zoom and borrowed picture, as `seeds/cut-and-build.md` defines them; add missing fields there. It reads the footage index's clip library, word-timed transcript with speakers, and proxy, whose audio gives the waveforms. Without words, skip the transcript features.

The bar: someone who has used a professional editor finds no basic operation missing, and the page plays what the export will contain or offers an exact rendered sample of what it cannot play.

## The editor's first build

**Operations every non-linear editor has:** a clip library panel over `footage/clips.json`, one line per clip that expands to its sub-clips, with the person's labels and renames, and drag into the cut; trim, split at the playhead, reorder, delete, undo; a draggable playhead; separate picture and sound tracks that draw borrowed pictures, overlaps, freezes and speed changes; per-item speed, gain and zoom; a timeline zoom out to the whole cut, with a playback-rate control beside it; playback that stops at the cut's end and passes each cut with no audible gap or overshoot.

**Operations for cutting by transcript in a file the agent also edits:** a transcript panel that adds a line or a run of lines as one item, with drag into the cut; transcript cards on cut items that update on trim; speaker-coloured waveforms with word labels when zoomed in; a cut list with named drafts (new, duplicate, rename); "update clip", which writes an item's new bounds back to its library clip, distinct from "save as new", which adds a library clip; a status line showing when the page picked up an agent edit.

**Hypothesis:** building the first list at once spares the person discovering each gap mid-edit; in the source production, a person cutting a recorded video-call argument and answering within minutes found them one by one. Build from the second list what this project's cutting method needs. Not established for multi-camera or music-led material. It fails when the cut waits behind editor polish; build the first list and let use reveal the rest.

**Hypothesis: two players for playback.** In the source production, seeking one player at each cut produced gaps and played 0.1 to 0.4 seconds past clip ends, so the person asked to cut words the render lacked; a second player parked at the next item's in point fixed both. Swap once the item's last frame has finished its display time, which `requestVideoFrameCallback` reports; in one test, polling the current time swapped up to half a frame early. Untested in other browsers. Swaps lag on sources with long keyframe intervals; play the proxy.

## Each edit's check

The server tells the page of your edit (a pushed file watch works), and the page keeps the person's place: same playhead, the frame the new cut puts there, playback continuing. With two writers on one file, refuse a page save from a stale copy, and do not let the person's undo silently revert your edit; clear or rebase the undo history and say which.

The server runs the builder's join checks on every cut-file change, whoever made it, so no check depends on memory; the page shows each result, which the builder also logs (`seeds/cut-and-build.md`). The packet that first shows the edit room (G7) gives the page's local address, what the page cannot show, and the checks each later edit receives: these join checks, not the full audit.

## When the editor falls short

Settle what the editor cannot express, such as an overlap, with an exact rendered sample, not an editor rebuild, and say whether preview or sample represents the change. If the environment inventory says the person cannot open your local pages, build the degraded form: the same cut file and builder, rendered previews per draft, and a timecoded notes file the person edits and you apply to the cut file.

## Verify

Write `edit-room/verification.md` as a table: behaviour, how tested, result (passed, failed or not verified), and a hash of the page, server and builder as tested.

**Hypothesis: test each behaviour that misled the source production and that this project relies on:** overshoot at discontinuous cuts, speed, a borrowed picture, an agent edit during playback, and preview against export. Script them with browser automation driving the page's controls, on copies of the cut file and clip library, because the tests edit the files the person cuts in. Compare the player's time at each cut with the cut file, and preview with export frames at equal timeline times, judging a match by which neighbouring export frame the preview frame most resembles, not by a fixed difference, since browser and FFmpeg colour conversion can differ by more than a frame of motion. Check both sides of each cut and the exported join. Route smoothness and audible gaps to the person with timestamps, or record them as not verified.

Launch test browsers muted (`seeds/environment.md`); a muted run is not a sound check. Playwright's bundled Chromium lacks some proprietary codecs (checked 2026-10-22); test with installed Chrome (`channel: 'chrome'`) or Edge, or a VP9 proxy. With no browser automation, record the scripted checks as not run and compile exact previews with FFmpeg.

## Musts

- **Must (truthfulness):** do not call the editor ready before `edit-room/verification.md` exists (G7). While the page plays a part it cannot show as exported, the viewer says so.
- **Must (truthfulness):** do not tell the person an edit is in before you have read its join-check result in `edit-room/edit-log.md`; report a failed or missing check.
- **Must (technical fact):** browser video seeks to unbuffered positions only when the server answers HTTP range requests (`reference/technical-facts.md`).
- **Must (permission):** bind the server to the local machine; a tunnel or port forward that exposes the footage, or an install outside the project folder, needs the person's approval.
