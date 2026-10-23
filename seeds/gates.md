# Gates

**Hypothesis: a refusing script holds where a written rule does not.** Write the gate scripts below in the project's `tools/` folder and perform the steps they gate only through them, because a check inside a command the agent must run fires at the right moment without being remembered, while a written rule guards a step only as long as the agent remembers it, which lost context erases; the status block each script prints restores what lost context removed. In the source production, which ran over several days with a person who answered quickly, the edit room kept doing its job while a written rule to audit every changed join did not keep clipped words from reaching the person. Gate scripts as a whole were not tried there, and nothing establishes that an agent keeps using scripts it wrote itself. The method fails when the agent calls FFmpeg, opens a file or pays a service directly. The signs are a draft the person saw with no packet, a packet without an audit status or hash, or a service bill above the `spend.jsonl` total. Then tighten the path: let only `tools/show` open files for the person, or, with the person's permission, add a harness hook that blocks direct media commands or sends.

List in `project.md` the gates installed and the reason for any left out.

## The scripts

Use whatever language the environment has. Keep the machine-read state in `project.json` (or YAML front matter in `project.md`): forest line, budget, directives with status and draft id, holds, current draft, last shown draft, and whether the person is at the machine. Keep prose beside it. Every gate script first prints the status block from that file and `spend.jsonl`, adding the count of unlinked inbox entries, the `helpers.md` register (`seeds/helpers.md`) and the last full render's duration beside the cheaper surfaces available (edit room, preview script, bare stitch); `tools/status` prints only the block.

- `tools/show` handles everything the person sees. It opens the file when `project.json` says the person is at the machine and sends it to the person's chosen channel otherwise, reuses an open tab or window, and prints the path and the application it used. It snapshots `project.json` at each showing, so the ledger diff is a file comparison, and writes the packet skeleton `packets/<draft-id>.md`: draft id, file, file hash, audit status, ledger diff, directives addressed. You add the message (`seeds/show-the-human.md`). Writing to `drafts/` for your own record is not a showing.
- `tools/check <draft> <change>` runs the checks for that change type (`seeds/audit.md`) and re-runs every row of `audit/regressions.md` whose anchor is still in the cut. It writes their raw output to `audit/<draft-id>/`, stamped with the file hash; the audit report interprets those outputs.
- `tools/render` holds a lock file from the moment it starts building inputs until the render ends, and records each render's duration. Every script that writes files a render reads (clips, audio stems, images, composition data) waits until the lock clears.
- `tools/spend` wraps each paid call and appends service, purpose and cost to `spend.jsonl`. `tools/deliver` marks `deliver/` final.
- `tools/note` appends every message from the person, with its time, to the verbatim inbox `messages.md` before you reply. Where the harness has a prompt-submit hook and the person permits it, the hook can do this instead.
- `tools/brief` refuses a helper brief missing a field listed in `seeds/helpers.md`.

Where the harness supports a session-start or after-compaction hook and the person permits it, add one that runs `tools/status` (G8).

A refusal names what is missing, for which file, and the seed that makes it: "Refused: draft-07.mp4 (hash 3f9a1c) has no tools/check output. Run tools/check draft-07 (seeds/audit.md) or record a skip reason." A gate is quiet when its condition holds; one that blocks without saying why, or passes without checking, does harm.

## Requirement gates

Each condition is a Must of the class shown and holds whenever the step happens.

| Gate | Script | Before | Requires | Class |
|---|---|---|---|---|
| G1 show | show | Showing anything to the person | A packet naming the exact file and hash shown and its audit status: the audit report id, or "not audited: no checks run on this file". A packet that cites a check with no raw output for the shown hash is refused | truthfulness |
| G2 spend | spend | Any call to a third-party paid service (transcription, voice, music, image or video generation) | Estimated cost plus ledger total within the budget; zero if nothing was authorized | permission |
| G3 render lock | render and every input writer | Writing a file a running render reads | No render running | technical fact |
| G4 hold | render | Starting or resuming a held render | The person's release, recorded in the directive ledger | explicit requirement |
| G5 consent and rights | spend, render | Generating a real person's likeness or voice; rendering a deliverable with generated likeness or voice, or third-party material the person did not supply | Consent or rights status in the truth list | permission |
| G6 delivery | deliver | Marking `deliver/` final | Truth note, spend total, unverified list | truthfulness |
| G7 editor ready | show | Telling the person the edit room is ready | `edit-room/verification.md` | truthfulness |

## Hypothesis gates

Weigh these. Skip one with a reason in the decision ledger, or when the person explicitly says to.

| Gate | Script | Before | Requires | Reason |
|---|---|---|---|---|
| G1a audit before showing | show | Showing a media draft whose hash has no `audit/` outputs, unless the ledger records that the change touched no cut | `tools/check` outputs for the shown hash, including a result for every live `audit/regressions.md` row, and `audit/<draft-id>.md` interpreting them | The G1a hypothesis below the table |
| G8 status re-entry | all | Every run | Status block printed; with permission, a session-start or after-compaction hook | Restores state when work is built or shown, which is when lost context did damage |
| G9 directives accounted | show | Showing | Every `messages.md` entry since the last packet links to a directive-ledger id or is marked "no directive", and every open directive is addressed by this draft or deferred with a reason | An instruction that never reached the ledger cannot be checked; the verbatim inbox captures it before your judgment filters it |
| G10 structure first | show, render | Showing a stitch or text arrangement; full-resolution renders, interface polish builds, sound mixes | For a showing: a join-table row in `assembly.md` for every join in the shown ordering (matched by clip names in the cut file), each with "why it follows", and an unfamiliar-viewer read for that ordering id. Before polish: a structure decision naming at least two ordering ids and the existing stitch file it was judged on, accepted by the person or recorded as your choice with the runner-up. A full-resolution render for a directive about words, order or a single join needs a reason in the decision ledger | Structure settled before polish (`SKILL.md`), judged on the cheapest surface that shows it |
| G11 independent reader | show, render, deliver | The first stitch shown, where helpers exist; full-resolution render of a new assembly; final delivery | `review/<draft-id>.md` from a fresh-context reader given only the goal, the assembly script and, later, the export | A fresh reader may catch coherence failures the author's context hides; how much is not established (`seeds/audit.md`) |

**Hypothesis (G1a):** an audit report sized to the change, written before a showing, catches defects before the person spends attention on them; in the source production clipped words reached the person when audits depended on memory. How much an audit adds to a rough draft shown only to judge order is not established. It fails when audit time delays a quick structural reaction; then show the rough draft marked not audited, and audit the first draft the person will judge for finish. G1 still refuses any packet that omits audit status.

**Must (permission):** install a harness hook or change harness configuration only with the person's permission.

## How many to install

Install requirement gates G1 to G7 in every project; each stays quiet until its step occurs, so G7 never fires without an edit room. The level (the levels table in `SKILL.md`) chooses only among hypothesis gates G1a and G8 to G11. A requirement gate's condition is never overridden; only its mechanism may differ.

## Check the scripts

Confirm that `tools/show` refuses a packet with no audit status, refuses a media draft until `tools/check` outputs exist for its hash and again after a re-render changes the hash, and refuses while an inbox entry is unlinked; that `tools/check` re-runs a regression row, `tools/note` appends a timed entry and `tools/brief` refuses an incomplete brief; and that `tools/status` in a new session matches `project.json`. Record the check's date beside the gates list in `project.md`.
