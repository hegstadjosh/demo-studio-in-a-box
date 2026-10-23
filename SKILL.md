---
name: demo-studio-in-a-box
description: Make, cut or revise short videos (promos, explainers, product demos, edited conversations) from a brief, footage, a product or code. Use when you carry the work from first look to delivered export, with a person directing occasionally or not at all.
---

# Demo Studio in a Box

Make a film its intended viewer can follow and wants to watch, starting from the audience, the purpose, the material and what the person has already chosen. This package was distilled from one multi-day production of promotional films for a debate app, directed by a person who answered quickly; the seeds call it the source production.

## How to read this package

**Must (class)** binds you. Its five classes: (explicit requirement), what the person asked for or forbade, within its scope; (permission), what the person has not authorized, you do not do; (technical fact), what holds regardless of taste; (truthfulness), your claims about your work, checks, perception and the film match what happened; (privacy), credentials and personal data.

**Hypothesis** marks everything else, including every method: its mechanism, the conditions it appeared to work under, what is not established, and how it fails. Weigh each hypothesis against the current goal and circumstances, and improve on it; record what you changed and why in the decision ledger in `project.md`. Musts and requirement gates are fixed; seeds and hypothesis gates are strong defaults, which you may skip or adjust with such an entry.

Examples in the seeds come from the source production. Generate premises and devices from this project's material, and mark any proposal that matches a seed example.

If `local.md` exists beside this file, read it before anything else. Its entries are the person's standing instructions: each carries the class (explicit requirement) or (permission) within its stated scope, overrides any hypothesis or seed default, and yields to a later instruction in the current project. `local.example.md` shows its form.

## First moves

Start the verbatim inbox, `messages.md` (`seeds/gates.md`), with the person's first message, so no instruction goes unrecorded. Look at the material, and inspect existing clips, drafts, timelines, assets and helper scripts before making replacements. Then write the short form of `project.md` (`seeds/project-file.md`) and the rows of `environment.md` (`seeds/environment.md`) the first artifact needs. Record in `project.md` the level (below) and the person's availability as they described it.

**Hypothesis:** the first artifact the person sees (a numbered premise list, a quote-level arrangement or a bare stitch) should arrive soon after that first look, because a reaction to something concrete answers questions an intake message cannot. Send the intake questions with it. Build `tools/show` before the first showing and `tools/spend` before the first paid call, and the remaining gate scripts before the first render. In the source production, questions that could have gone in an intake arrived later as corrections from a person who answered quickly. This sequencing is reasoned, not observed. It fails when the first artifact rests on a premise one answer would have overturned, such as whether the people shown consent; ask those blocking questions before making it.

## Seeds, in the order a project usually reaches them

An example sequence, not a pipeline:
1. In parallel: `seeds/footage-index.md` for recordings (footage index, clip library, structure map); brand tokens (`seeds/coded-scenes.md`) and research notes (`seeds/treatment.md`) for a product.
2. `seeds/treatment.md`: treatment and storyboard.
3. `seeds/assembly.md`: assembly script, bare stitch, structure decision; then the independent review (`seeds/audit.md`).
4. As needed: `seeds/cut-and-build.md` (cut file, builder) whenever recorded footage is cut or retimed; `seeds/edit-room.md` when a person directs cuts; `seeds/coded-scenes.md` (composition, stills); `seeds/sound-and-voice.md` (voice, cue sheet, music, mix report, master); `seeds/helpers.md` (briefs, helper register) when helpers take work.
5. Before every showing, a check-in packet stating the file's audit status (`seeds/show-the-human.md`), usually after an audit report (`seeds/audit.md`).
6. Revision in the seed where the problem lives, from a restatement when feedback is ambiguous.
7. Final audit and the delivery folder (`seeds/audit.md`).

`reference/technical-facts.md` holds timing, picture and loudness facts; the builder's self-tests that check them are in `seeds/cut-and-build.md`.

**Hypothesis: settle structure before polish**, because a bare stitch lets order be judged before finish is paid for. The source production's largest avoidable losses were polished drafts on an order later discarded. It fails when the effect depends on finish, as with a sound treatment; then finish only the sample that judgment needs (`seeds/assembly.md`).

## Levels

| Material and job | Seeds that usually matter (added to the first row) | Hypothesis gates that usually pay |
|---|---|---|
| A small change to an existing film or clip, such as a trim (read nothing else) | project-file (short form), environment (FFmpeg row), gates, audit checks for what changed, show-the-human | G1a, G8 |
| A long recording (demo, talk, stream) condensed to a short cut | footage-index (screen section), treatment (short form), assembly, cut-and-build, sound-and-voice (captions, music, levels), full audit | G1a, G10, G11 |
| A product or idea explained in coded scenes | treatment, assembly, coded-scenes, sound-and-voice | G1a, G8 to G11 |
| A recorded conversation edited into a film | treatment, footage-index, assembly, cut-and-build, sound-and-voice, and edit-room when a person directs cuts | G1a, G8 to G11 |
| Recordings combined with coded product scenes | all seeds, helpers, a live board | G1a, G8 to G11 |

A recording counts as footage when its clips may appear in the film; one used only as source for the script feeds the research notes.

## Gates

A gate is a condition a step must meet before it runs. Requirement gates hold whatever enforces them; install all seven in every project, since each stays quiet until its step occurs. **Hypothesis:** checking each condition inside a script you must run to perform the step holds where a written rule fails, because a check inside a command needs no memory; this has not been tried as a whole (`seeds/gates.md`), so watch for the failure signs listed there. It fails when you bypass a script by calling a media tool, opening a file or paying a service directly. A harness hook that blocks direct media commands or sends enforces a condition without your cooperation; add one only with the person's permission.
- Requirement gates enforce a Must: G1 show (every packet names the exact file and hash shown and states its audit status: the audit report id, or not audited); G2 spend; G3 render lock; G4 hold; G5 consent and rights; G6 delivery; G7 editor ready (the editor verification before you call the edit room ready).
- Hypothesis gates may be skipped with a recorded reason: G1a audit before showing; G8 status re-entry; G9 directives accounted, in every packet; G10 structure first, before polish; G11 independent reader, before a full render or delivery.

Every gate script prints the status block: the forest line (goal, premise and current stage in one line), open directives, current draft id, held renders and budget left.

## The person

Availability changes who decides, how often you show work, and which review surfaces are worth building; it does not change the Musts, the requirement gates or the artifacts that record decisions. Weigh what the person knows that you cannot find out (taste, consent, intent), the cost of interrupting them, and how reversible the choice is: money spent or a claim published cannot be undone by a later draft.

**Hypothesis: early cheap artifacts reveal preferences before expensive polish**, because a person can judge a premise list or a short exact preview in a word. This appeared useful when the person answered quickly, with check-ins after the treatment, the assembly and the first full draft while work continued; when it generalizes is not established. Rough drafts can obscure an idea whose effect depends on execution; show such an idea finished. For a person away for stretches, see the pushed drafts and catch-up packet in `seeds/show-the-human.md`.

- **Must (explicit requirement):** when the person has said not to involve them, for example by asking for the best film with no discussion, ask nothing; your messages then carry no questions or options. Choose by the goal, record each choice as yours with its runner-up, and let the independent review stand in for part of their coherence check.
- Spending, including whether your own model calls count, follows the budget Must in `seeds/project-file.md`.
- **Must (truthfulness):** never simulate the person's approval or present an imagined reaction as measured. Where consent, a product fact or rights stay unsettled, use a depiction that claims nothing unsupported, such as a labelled mockup, and flag it in the truth note. The truth list in `project.md` marks each element of the film recorded, authored or generated and each product claim verified or assumed; the truth note in `deliver/` reports it to whoever shares the film (`seeds/audit.md`).

**Hypothesis: stop when another pass is unlikely to change what the viewer gets** and you can name what you could not verify, because each further pass spends time and the person's attention. In the source production the person, not the agent, found the remaining defects; when another pass stops paying is not established. It fails through self-trust, when you stop at a draft you believe clean; the independent review guards against that.

## Talking to the person

These govern every message, not only check-in packets.

**Must (explicit requirement):** answer each question the person asked, because a question is a request for its answer. When asked for your view, give it; when asked what should go somewhere, propose something rather than asking back.

**Hypothesis:** a message that answers the person's questions in their order, leads with your recommendation, offers numbered options a word can answer, quotes any line it mentions with its neighbouring lines and speakers, says what you agree with when you agree, uses plain words and fits one phone screen lets a person decide at a glance without reopening files. In the source production the person directed many agents at once and asked for exactly this. Whether other people want the same form is not established. A person who wants the reasoning first finds the recommendation-first form abrupt; record their preference in `project.md` and follow it.

## Throughout

**Hypothesis:** build a promising idea before you can explain its value, yours or the person's, because some ideas show their value only once built; a topical real clip the person proposed reorganized the source film before either could say why. How often an agent finds such an idea unaided is not established. It fails as licence to chase novelty against a clear brief.

**Hypothesis: a request for a change is a request for the whole film to work after it.** A shorter cut still needs its setup, sound and interface finish, because the viewer judges the film, not the change; the source agent, asked for something shorter, dropped all three. It fails when it expands scope beyond the format in `project.md`.

## Helpers and the machine

**Hypothesis:** a helper keeps a decision only if its written brief carries it, so paste the ledger entries in force into every brief; one integrator owns the cut file and the build, so no two writers collide. `seeds/helpers.md` holds the full hypothesis and makes the brief and the helper register.

**Hypothesis:** stop each server, watcher and worker you started when its work ends, and list running ones in the status block, because forgotten processes hold memory and ports the person needs. It fails when the person still uses a page that a process serves; keep that process running until the person's work with the page ends.

- **Must (technical fact):** nothing writes into render inputs while a render runs (the render lock gate).
- **Must (privacy):** use credentials only from environment variables or files the person names; never search for, print or log keys.
