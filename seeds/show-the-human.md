# Show the human

Show the person every draft, still, stitch, board link and text artifact only through `tools/show`, which writes a check-in packet (`packets/<draft-id>.md`) and puts the exact file it names in front of them. This seed also makes the review surface, the live board, the restatement and the catch-up packet. These artifacts aim each round of the person's judgment at the right file and question, and make answering cheap.

## The check-in packet

`tools/show` refuses to run without the packet's audit-status field (G1): the audit report id for the file's hash, or "not audited: no checks run on this file". Unless G9 was skipped with a recorded reason, it also refuses until every verbatim-inbox entry since the last packet links to a directive id or is marked "no directive" (G9, `seeds/gates.md`). A text artifact such as the treatment also goes out in a packet, with its audit status stated.

`tools/show` opens the file when `project.json` says the person is at the machine, with the command `environment.md` records for its kind, and otherwise sends it to their chosen channel, or with none to a dated `drafts/` folder. It reuses an open tab or window and prints the path and application used.

Fields, in order: draft id; file, with the draft id in its filename; file hash; audit status; ledger diff since the person last looked; directives addressed and deferred; the message.

The message opens with one line per directive acted on, stating your reading in scope terms, for example "Removed narrator captions during the debate; kept the debaters' captions." The person reads the message, not the packet fields, so a misreading visible only in the ledger diff goes unseen; the full diff stays in the packet file. `SKILL.md` (Talking to the person) states the rules for every message. A packet's message adds which material is recorded and which generated, what changed and which version carries each fix, and one status line for work still running.

**Must (truthfulness):** the file opened or sent is the exact file the packet names. Give every render a new filename carrying its draft id; some players reshow a stale copy when a path is reopened.

**Must (explicit requirement):** when the person has declined involvement, a packet carries no questions or options (`SKILL.md`, The person). Unless they asked to see progress, nothing is shown until `deliver/`: drafts go to `drafts/` with their audit reports for your own record, and the decision ledger entry replaces the packet message.

## The review surface

Make the cheapest surface that keeps what the question depends on: a quote-level arrangement list for order; a bare stitch for flow; a short exact preview, compiled by script from the cut file, for one stretch; a low-resolution draft for overall shape; a contact sheet for framing; a comparison page with embedded images for choosing treatments; the beat table for timing against on-screen events. The status block shows the last full render's duration beside these surfaces, and a full render for a directive about words, order or a single join needs a recorded reason (G10). Keep a current draft available while slow work runs, stand-ins labelled. When an editor preview or a board might lag the export, send a short compiled sample of the export.

## The live board

**Hypothesis:** a live board pays when interface work produces many small visual changes the person reviews between builds; it needs a page the person can open (`environment.md`). The page shows labelled stills of key screens and interface states beside a newest-first feed of each build's time, changed source files and before-and-after stills, and refreshes in place with progress and errors. Its watcher waits for edits to settle, never overlaps builds, pauses during full renders, keeps the last good board when a build fails, and takes frames from the composition's timeline data so stills follow timing edits. On each build it runs layout checks (text overflow and line count per element, element bounds against the frame, and duplicated components where the composition can report them) and shows failures beside the stills. The packet that links the board names the checks the stills received. Stop the watcher and its server when the interface work ends.

**Must (truthfulness):** the board states on the page that it shows no motion or sound.

## Pushed drafts and catch-up

**Hypothesis.** Labelled drafts pushed as work proceeds let an intermittent person steer without anyone waiting, because they react to whatever is newest. In the source production the person, away for stretches, asked for every draft to reach their channel. The right cadence is not established. It fails when drafts outpace the person's reading and bury a decision-changing one; then send only drafts that change a decision.

When the person returns after an absence, send a catch-up packet first: what was finished; what you decided without them, each runner-up recoverable; what needs them now, as numbered options; the current draft.

## The restatement

**Hypothesis:** before acting on feedback whose cause is unclear, write a restatement into the directive's ledger entry (the observation in the person's terms; its level: purpose, premise, wording or frame; rival remedies that test different diagnoses; and what a sweep for the same defect found), because variations on one remedy share its diagnosis and fail together. Write one for any feedback about look, feel, tone or a whole section, and for every helper brief that carries feedback (`seeds/helpers.md`), not only when feedback seems ambiguous, because your judgment that feedback is clear is the judgment that failed. In the source production a complaint that components looked shapeless became several styling treatments built on one wrong reading. Rival remedies were not tried there, so their value is not established. It fails as busywork when the remedy is plain, or as escalation when the person asked for an exact frame fix; then make that fix.

Treat the person's examples as illustrations of a goal, and read a framing request for its intent: asking to centre a face may also mean showing all of it. When you remove something, show its replacement. Record every directive's scope (layer, section, version), even when it looks clear, so the scope line in the next message exposes a misreading early.

**Hypothesis: confirm what the person watched.** Before diagnosing a complaint about a file, confirm which file they watched and at what playback settings, because a stale copy or a player setting mimics a file defect. In the source production, where the person watched drafts in a desktop player, one left at half speed was read as a voice defect. How often playback is the cause is not established. It fails as ritual when the defect is plainly in the file; then measure the file.
