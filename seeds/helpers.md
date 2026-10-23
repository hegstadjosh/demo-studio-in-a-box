# Helpers

**Hypothesis:** a helper given a written brief containing the ledger entries in force does file-scoped work without undoing decisions, because a helper that never received a decision cannot keep it. In the source production, where the person sent many small notes and helpers took tool fixes while one agent kept the conversation, a helper lost decisions it never received, and two concurrent writers doubled a render's music. How much judgment a helper can take is not established. It fails when two helpers write the same file, because each writes from its own stale read; one integrator owns the cut file and the build, and helpers return their changes to it. Match model strength to the judgment the task needs, and count token cost when it is billed (`seeds/project-file.md`).

This seed makes the helper briefs in `briefs/`, the helper register `helpers.md` and the brief check `tools/brief`. It applies when the Helpers row of `environment.md` records helpers (subagents or parallel sessions) or sequential fresh-context sessions. A sequential session reads only its brief, so for it the brief is the whole handover.

## The helper brief

Write one file per helper, `briefs/<helper>-<time>.md`, with these fields:

1. **Goal**: the outcome the work serves, in the terms of the goal in `project.md`.
2. **Owned files**: the files the helper may write; every other file is read-only to it.
3. **Restatement**: when the brief carries the person's feedback, the directive id whose ledger entry holds the restatement (`seeds/show-the-human.md`).
4. **Ledger entries in force**: every decision and directive entry that bears on the task, pasted in full.
5. **Asset register**: when the helper creates assets, the register from `project.md` section 4, pasted, to search before making an asset of a kind.
6. **Current draft id**: the draft the work applies to.
7. **Render status**: whether a render is running. A helper that writes files a render reads waits for the lock to clear (G3).
8. **What to return**: the files changed, what was checked and how, what was not verified, and where to write the report.

**Hypothesis:** a goal and a restatement keep a helper from filling a brief's gaps with the literal reading of the person's words. In the source production two helpers briefed with the person's literal words for a look returned the same rejected design. Whether the field prevents this is not established. It fails when the restatement itself misreads the person; the next check-in packet shows your reading so they can correct it.

**Hypothesis:** hand editor and tool fixes to a helper so you stay on the edit with the person, and give that helper the current draft id and render status, because a fix tested on another draft may fail on the one the person is watching, and a write during a render corrupts that render. It appeared useful in the source production while the person directed cuts; whether it pays when they review rarely is not established. It fails when a fix touches the cut file; then the helper returns the change and the integrator applies it.

## The brief check and the helper register

`tools/brief <file>` refuses a brief missing a field, naming it; the restatement and asset register fields are required when the brief says it carries feedback or creates assets. It fills the draft id from `project.json` and the render status from the render lock, so neither comes from memory. A passing brief adds its line to `helpers.md`: helper, brief file, directive ids served, draft id, start time, expected finish and status (running, returned, stopped). The status block prints the register (`seeds/gates.md`), so `tools/status` lists open briefs, marking any line past its expected finish. Update the status when the helper returns or stops.

## Running helpers

**Hypothesis:** stop a helper when a directive it serves is superseded, and mark its line stopped, because a helper keeps working on its brief as written, and its output can overwrite newer work. When a new directive enters the ledger, compare it with the register's directive ids. In the source production a helper kept running after the person wanted it stopped. Whether this comparison catches every case is not established. It fails when the helper's work still serves part of the new directive; then send an amended brief instead.

**Hypothesis:** pass the person's messages meant for a helper to that helper, and bring its answer back in your next reply, because the person may have no way to reach a helper you started. Mark each such message's inbox entry with the helper's name and, once answered, the reply, so an unanswered relay stays visible. In the source production a helper did not answer the person's direct prompts. Whether other harnesses let the person reach helpers is not established. It fails when relaying delays an answer the person needs now; answer from the helper's last report, say so, and relay the rest.

**Hypothesis:** record in the helper's line any finish time you give the person, and when it passes, tell them before they ask, with a new time and the cause, because a missed time the person discovers makes every later status suspect. In the source production an agent's stated finish time passed without word. How accurate an agent's estimates are is not established. It fails when the estimate rests on nothing measured; base it on a measured rate, such as the last full render's duration, or give none.
