# Sound and voice

Make the film's sound as files under `sound/`: a voice plan with a listening page, per-line voice files, a cue sheet, music candidates, stems, a mix report before and after each render, and a mastered export.

These files let the person direct sound by ear in short rounds and you find problems by measurement. Make them for any film with narration, music or mixed sources; a straight trim needs only the mix report and the master. The bar is a mix a professional editor would pass: speech always intelligible, no level jumps between lines or speakers, no clipped words, no drops to digital silence.

## Voice plan and listening page

Write `sound/voice-plan.md` first: the narration's job, as the treatment set it (`seeds/treatment.md`); each line's id, spoken words and mapped on-screen words; the stand-in and real-voice routes from `environment.md`, with cost; the voice service's features beyond text to speech and its remaining credit; consent status for any real person's voice.

To choose a voice, build `sound/auditions/index.html`, where a few candidates read one real line, and show it through `tools/show` so the person picks by ear. If the person has named a voice or no one will listen, record your choice and reason.

**Hypothesis: one take per speaker, split into lines.** One take of all a speaker's lines keeps pace and tone matched; compare takes by transcript, duration and level. Cut the chosen take into `sound/lines/<line-id>.wav` at the gaps, found from the voice service's character timestamps or the recogniser's word timestamps, keeping each last word's decay, with short fades and room tone, each line levelled to one loudness. Take room tone from a span the level track, recogniser and frames all show empty, and by ear when anyone can listen; a flat waveform or a closed mouth alone does not show a span is free of speech. In the source production this kept a narrator consistent across many redrafts while the person answered within minutes. Not established: whether it suits dialogue among several generated speakers. It fails when a new take changes durations and a line pushes into the next beat or onto an effect; re-check every line against its slot after each take.

**Hypothesis: spend within the budget without asking.** `tools/spend` (G2) already holds the person's decision about money, so a per-call question costs a message and decides nothing; the source production's director objected to such questions. How often to report the running total is not established. It fails when the person meant the budget as a cap, not a pre-approval; the intake question on budget settles which.

## Cue sheet and music candidates

Write `sound/cues.md` before building music: per section, the sound's job, its entry and exit (a cut or a word), and who speaks under it. Choose the job before an engine or loop: suspense, release, momentum, a clean handoff and an intentional silence differ, and a treatment can suit one line and fail as the next section's mood. List the treatment's genre-convention sounds as candidates.

**Hypothesis:** two or more candidates for a cue let the person choose by ear instead of describing a sound in words; one candidate suffices where the cue's job is plain and the person has accepted its kind before. For a short product demo, a quiet bed or no music may beat a weak synthesized bed; count both as candidates, judged by the measure below. Build each in `sound/music/<candidate>/`, rendered in context with the film's voice or its stand-in, with a `notes.md`: source, tempo, key, entry and exit, level under speech, licence, and who has heard it.

**Hypothesis: build music from measurable parameters.** Align bar lines, entries and exits to cuts, and keep the voice's frequency range clear by filtering or ducking; all checkable without hearing. In the source production, music under recorded speech hurt, and a drone that swelled on key words and dropped out before the punchline worked. Not established: whether measured fit predicts taste in other genres. It fails on mood, which measurement cannot judge; when no one can listen soon, pick the candidate that measures least intrusive under speech and best fits the cue's job, and say no one has heard it.

**Hypothesis: answer a sound complaint with the narrowest change.** Check the project file's methods that worked before removing a layer. In the source production, removing all music after one complaint about its mood lost the connective tissue it had supplied in earlier films. Not established: whether a narrow change suffices when the person cannot name the cause. When narrow fixes to one cue keep failing, the cue's job is wrong; rewrite its entry and build new candidates.

## Stems, mix report and master

Build stems (dialogue, narration, music, effects) on the picture's timeline in `sound/stems/`. Write `sound/mix-<draft-id>.md` before each render, predicted by summing the stems at the composition's gains, and after, measured on the export: per-section short-term loudness of speech, narration and music alone, then integrated loudness, true peak, clipped samples and dead air. Compare lines, speakers, and new narration against old; matching average level need not erase expressive contrast, and a final loudness target cannot fix one quiet line or restore a clipped word. The audit report cites the mix report (G1).

Master with FFmpeg into a new file named by draft id: measure with `loudnorm`; limit peaks so peak plus planned gain stays under the target true peak with a margin, since true peaks exceed sample peaks; then run a second pass with the measured values and `linear=true`, copying video and setting the sample rate. Confirm the second pass printed `"normalization_type" : "linear"`, and measure the master with `ebur128=peak=true`. The `loudnorm` and stem Musts are in `reference/technical-facts.md`.

## Musts

- **Must (technical fact):** a step change in gain clicks; ramp gain changes.
- **Must (permission):** clone or generate a real person's voice only with their recorded consent (G5). Use only sound whose licence permits the use, and record each licence.
- **Must (truthfulness):** label replacement or generated speech as such in every check-in packet and in the truth note; on-screen disclosure follows `seeds/coded-scenes.md`.
- **Must (truthfulness):** approval in words of a sound the person has not heard is not acceptance of the rendered result.

Claims about your own listening follow `seeds/audit.md`.
