# Audit

The audit report (`audit/<draft-id>.md`) is a finishing editor's quality-control pass on the export: it finds defects before the person does and lists what is still wrong.

**Must (truthfulness):** every packet states the audit status of the exact file shown: the audit report id for its hash; "checked, not interpreted: raw outputs in `audit/<draft-id>/`"; or "not audited: no checks run on this file" (G1).

**Hypothesis: audit each showing, sized to the change (G1a).** Scoping keeps an audit cheap enough for every showing; in the source production, clipped words and an already-reported stray frame reached the person while audits depended on memory. How much scoping misses is not established. It fails on a hidden dependency, such as a cut removing a moment a later caption cites; check the dependents the assembly script lists. When auditing would delay a quick structural reaction, show the rough draft marked not audited.

## Check outputs and regressions

`tools/check <draft> <change>`, where change is first full draft, cut, mix, text or picture, writes that change's raw check output to `audit/<draft-id>/`, stamped with the file hash: for a cut, the words diff, edge levels, `scdet` and `freezedetect` (`d=0.1`) around changed joins, and metadata; for a mix, loudness; for a first full draft, everything. Edge levels classify the level track by speaker either side of each join (0.4 s in one test), flagging sound from a speaker or clip the assembly does not place there. `tools/show` refuses a media draft whose hash has no outputs in `audit/`, unless the ledger records that the change touched no cut.

**Hypothesis: a fixed defect needs a standing check,** because a scoped audit never revisits it. Each defect the person reports becomes a row in `audit/regressions.md`: the moment, anchored to a phrase or, without words, to a clip id, and the check that detects it. `tools/check` re-runs every row whose anchor is still in the cut, and `tools/show` refuses a draft lacking a result for any such row.

## The audit report

The report interprets and cites the raw outputs. It records the draft id, hash and the draft compared against, normally the last one shown; what changed and its dependents; each check run or skipped and why; each regression row's result; defects fixed and left, with timestamps; and a self-critique: proposal against result, the worst block, what to cut, the treatment's whole-film dimensions if any, and anything added unasked. A fix gets a new draft id: re-hash, re-run `tools/check` and compare against the draft it fixes.

**Must (truthfulness):** the report states what was checked and how, and what was not verified and why, in the evidence terms below. Label test artifacts, such as "audio replaced, not lip-synced".

## Candidate checks

- **Words:** diff the export's re-transcription against the assembly script, dropping non-speech tags such as [Music] from both; the recogniser misses quiet partial words.
- **Joins:** mid-word cuts, missing pauses, jumps within one speaker; transcript silence is not audio silence.
- **Frames near joins:** stray frames of the other speaker, borrowed picture past a camera switch, zoom jumps, freezes, duplicates (`mpdecimate`); grab contact-sheet frames per `reference/technical-facts.md` (Picture).
- **File:** dead air (`silencedetect`), rotation, duration, rates.
- **Pacing graphs** find candidates, not edits. **Must (truthfulness):** present no graph you have not read; write on each its question and conclusion.
- **Stills:** wraps, off-brand fonts, captions over names, stale or illegible text. For each interface still, run the checks under the ranked defects in `reference/ui-design.md` and record each hit with its rank.
- **Personal data. Must (privacy):** scan sampled frames of every span used for emails, keys, tokens, names and notifications, starting from `footage/privacy.md`; blur, crop or cut each.
- **Mix:** the mix report's loudness, true peak and clipping.

## What each form of evidence establishes

Timeline inspection shows intended data, not the export. Probes, recognition and loudness show media properties and candidate defects, not natural speech. A contact sheet shows sampled appearance, not motion or sound. Audio correlation matches soundtracks, not lips. Continuous review shows one file's experience, not viewer acceptance. A human response covers that version only. A send receipt shows delivery, not viewing.

**Must (truthfulness):** if you cannot hear, say so and claim no listening pass. With narration, music or cut speech, send the person the timestamps of every join and cue measurement could not clear (a level track clears bleed and dead air, not clicks or tone), or list them as unverified if the person asked for no discussion. A model's own listening is an instrument with false positives, never the person's. An honest report can read: "I inspected frames and measured the audio; I could not hear playback."

**Must (truthfulness):** an earlier session's or helper's statement that something was or was not done (listened to, checked, indexed) is its claim, not evidence; check the artifact, or report the statement as theirs.

## The independent review

**Hypothesis.** A fresh-context reader covers part of the person's coherence checking, most when the person is absent. It receives only the goal, the assembly script before the first stitch, and later the export (or, without video input, the re-transcription, a timecoded contact sheet and on-screen text). `review/<draft-id>.md` says what it took the film to be about, where it lost the thread and what it could not judge. How much it catches is not established; automated reviewers in the source production cited moments past the file's end, so check every timestamp.

Without a helper, a fresh model call given only these files counts as the G11 reader, logged through `tools/spend` and gated as `project.md`'s budget says; otherwise use your own cold read, reported as sharing your context (`environment.md`). If nothing can run, write `review/<draft-id>.md` as "not run" with the reason, record G11 as skipped in the ledger, and list it as unverified.

## Delivery

`tools/deliver` assembles `deliver/`: the export, `thumbnail.png`, `contact-sheet.png` (timecoded), `truth-note.md`, `unverified.md`, `spend-total.md`, `rebuild.md` and `drafts/`; give the person its path. The truth note reports the truth list (`seeds/project-file.md`), generated people and voices, material "supplied by the person, presumed cleared, not confirmed", redactions, departures from the real product and fallbacks that cost quality.

**Must (truthfulness):** `deliver/` is not final until `truth-note.md` and `unverified.md` are present, plus `spend-total.md` whenever `spend.jsonl` has entries (G6).

**Hypothesis:** `rebuild.md` lets a later agent reproduce the film without this session; omit it only with a reason in the decision ledger.

**Must (permission):** send or publish only through the channel and scope the person authorized.
