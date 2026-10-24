# short-video

short-video is a skill: a folder of Markdown files that an AI agent reads to carry a short video (a promo, an explainer, a product demo, an edited conversation) from a brief to a delivered export. A person directs occasionally or not at all.

## Origin

The package was distilled from one multi-day production of promotional films for a debate app, heavily directed by its author, and from an analysis of the direction he had to give. That direction repeatedly recovered decisions the agent had lost, caught defects in drafts it had not checked and redirected polish spent before the structure was settled. The package therefore carries gates, scripts that refuse a step until its prerequisite exists, and a decision ledger that keeps choices in a file rather than the agent's memory.

## What has been tested

A fresh agent built from two seeds on synthetic footage, reading only `SKILL.md` and the seeds under test.

- **Edit room.** The agent built a working local editor that passed 35 of 36 checks. The remaining check, audible gaps at cuts, needs a listener and was not verified.
- **Footage index and audit.** Both seeds ran end to end. The audit caught a real defect: the footage-index seed's padding rule had placed fractions of a second of the other speaker at four joins.

The findings were applied to the seeds but not re-tested. The other seeds were only read. No full production trial has been run with this package yet.

## Install

Copy the `short-video` folder, with `SKILL.md` at its top, into your agent's skills folder:

- Claude Code: `~/.claude/skills/short-video/`, or `.claude/skills/short-video/` in a project.
- Codex: `~/.agents/skills/short-video/`, or `.agents/skills/short-video/` in a repository.

Any other agent can be pointed at the folder and told to read `SKILL.md` first; the files use relative paths and no harness-specific syntax.

## Use

Give the agent the brief and material, and say how involved you want to be. `SKILL.md` is the entry point: it records your availability, chooses the seeds the job needs from `seeds/`, and installs the gates.

- **An engaged person** gets an early, cheap artifact (numbered premises, an arrangement of quotes or a rough stitch) with the intake questions, then each draft with a packet naming the exact file and its audit status. A person who will direct cuts gets a local edit room.
- **An absent person** says so, for example "make the best film you can, no discussion." The agent then asks nothing, records each choice with its runner-up, uses a fresh-context reviewer, and delivers the export with a truth note and a list of what it could not verify.

## local.md

An owner may add a private file, `local.md`, beside `SKILL.md` with standing instructions for every film, such as review channel, spending limits and permissions. The agent reads it first and treats each entry as the owner's instruction. `local.example.md` shows the form; `local.md` itself is not shipped.

## Licence

No licence has been chosen yet.
