# Assembly

Write `assembly.md` in the project folder: candidate cuts as speaker-labelled scripts, a join table for each, rival orderings and a structure decision. Render a bare stitch of the leading ordering before any interface, polish or mix depends on the order.

An order costs minutes to change in a script or stitch, and drafts once polish sits on it. Gate G10 (`seeds/gates.md`) reads the structure decision, and the independent reader for gate G11 (`seeds/audit.md`) reads this file. Make it for any film that cuts recorded speech or orders scenes, not for one clip trimmed at known times. The standard is a professional paper edit: every line has a job, every join is explainable, and a stranger believes the cut was said as heard.

## What `assembly.md` contains

For each candidate cut:

1. **Script.** Speaker-labelled lines quoted verbatim, each with its clip name and source interval. **Must (truthfulness):** mark each line existing or newly generated.
2. **Join table.** Per join: previous line, next line, why it follows, what it sets up or pays off, mechanism (straight cut, overlap, cutaway, hold), edge words checked. A first row records what the viewer knows at the first cut.
3. **Beat jobs**: setup, claim, rebuttal, reveal, payoff, transition, or whatever each beat does.
4. **Rival orderings**, more than one, each with its reason, noting where they differ in tone, which text cannot settle.
5. **Unfamiliar-viewer read.** Read each proposed sequence as an unfamiliar viewer would:
   - Does each answer respond to what the audience just heard?
   - Have pronouns, a topic change, an interruption, or a punchline lost their setup?
   - Are we repeating the same assertion, or moving the exchange forward?
   - Does the ending resolve or deliberately hold the moment, rather than simply stop?
6. **Bare stitches** of the leading ordering and of any rival that differs in tone: low resolution, no interface, named by ordering id, made with FFmpeg cuts of the script's source intervals or with the builder's rough mode (`seeds/cut-and-build.md`). A bare stitch built from FFmpeg cuts with no retiming needs no builder self-tests; any retimed build goes through the builder. Retain source handles so the person can restore or trim the moment.
7. **Beat table**, for films with on-screen events: rows in time order, with separate columns for time, spoken line, narration, on-screen text or graphic, picture and sound cue.
8. **Outtakes**, for a reel: label, why it is funny, the setup it needs, a source interval that includes that setup, and any brand or consent concern.
9. **Structure decision**: the chosen ordering, who chose it, the runner-up kept recoverable, and the stitch it was judged on.

Verify by re-reading each ordering against item 5 and playing every join of the stitch, checking the level track at each cut edge for energy mid-word. Every stitch and text arrangement goes out through `tools/show` with its join-table rows, its unfamiliar-viewer read and an audit report sized to the stitch; G10 (`seeds/gates.md`) checks the rows and the read.

## Hypotheses, by the part they shape

**Structure before polish (items 6 and 9).** Show a plain stitch when the dispute is about words or order, because a finished interface and a long render delay that decision. The source production's largest avoidable losses came from structure decided after polish; bare stitches worked once the person answered quickly. Untested with a person who answers slowly. It fails when the effect depends on finish, such as a sound treatment; then build the one finished sample that judgment needs.

**A sequence for a quick responder (items 4 and 6).** Try quote-level arrangements, then numbered options, then the edit room, then a render. Abbreviated quotes let the person judge order without watching, numbered options take one-word replies, and an agreed arrangement settles the order before a render is spent on it; in the source production, renders cut without one were rejected. Untested with a person who answers slowly, where each round trip stalls; then send the arrangement and its stitch together.

**After a rejected ordering (item 4).** When the person rejects an ordering, the next reply carries new numbered orderings rather than a request for direction: choosing costs the person one word, composing costs many messages, and in the source production the person dictated the order line by line when no alternatives were offered. How many to offer is not established. It fails when the objection is to a line, not its place, because reordering repeats the defect; write a restatement of the objection instead (`seeds/show-the-human.md`). It does not apply to a dictated order (see Musts).

**Why it follows (item 2).** Judge spliced dialogue as speech: grammar, tone, delivery, continuity of props, wardrobe and position, and whether setups resolve. A logical but ungrammatical join exposes the cut, and a voice swap cannot repair corny words or broken logic. This held for the source production's video-call argument; not established for scripted or multi-camera dialogue. It fails for deliberately discontinuous montage, where the viewer expects jumps; judge those joins by rhythm and contrast.

**Edge words (item 2).** Words that lean on what came before ("but", "and", "well", "so") make a cut audible, because the viewer hears a link to a sentence that is gone; propose a trim. This held for the source production's conversational English; not established for other languages. It fails when the dependency is the joke; then keep the sentence the word leans on.

**Shortening (item 3).** To lose time, cut duplicates of a beat's job, speed idle screen time, or drop a whole beat, in no fixed order, and record which. A setup looks expendable alone, but removing it leaves the payoff unexplained; a shortened highlights cut in the source production became incomprehensible this way. Speeding screen time in which nothing changes removes waiting, not information. Which candidate costs least is not established. Cutting fails for a deliberate fast-cut sizzle, where recognition matters more than logic; speeding fails where the viewer must read the screen.

**Picture and speech (item 2, mechanism).** A conversation need not cut sound and picture at the same instant. Let a reply begin on the listener, or hold the listener through a revealing phrase; a reaction can cover a discontinuity within one person's speech and often makes a splice feel natural. Keep speaker captions tied to the voice. Choose among mechanisms and inspect each: straight cuts for stray frames and clipped words, coverage for reused reactions and misleading mouth movement, offsets for real overlap, shortened pauses for sudden motion and a lost comic beat. Punch-ins and morph bridges gave uneven results on the source production's video-call footage; not established on footage with better resolution or more angles. A punch-in fails when it enlarges compression artefacts; check a still at full size.

**Pauses and pace (items 2 and 6).** Distinguish waiting, thinking, disbelief, turn-taking, a laugh and a punchline's landing; keep an intentional eye roll or revealing silence while tightening nearby setup. A low word rate may mark a valuable reaction, so derive no universal gap, word rate or filler rule from one clip. Not established beyond conversational footage. It fails when context becomes a reason to keep every pause; in the source production a pacing chart was drawn, not read, and the slowest block stayed. Fix the worst block first.

**One global speed (item 6).** One speed change across the main conversation keeps the speakers' relative rhythm and removes many small decisions. In the source production a uniform speed-up, outtakes excepted, was applied before the draft the person liked most; whether the speed-up caused the preference is not established. It fails when one speaker is already rushed; then tighten that speaker's pauses. Inspect articulation and tone after any speed change.

**Beat table (item 7).** One time axis for speech, narration and on-screen events lets the person judge, without a render, whether a label lands on the words it comments on. Generate it from the timing data the composition reads, so table and render agree. The source production adopted it at the person's request; not established for films with few on-screen events. It goes stale when beats are hand-tuned outside that data; regenerate it after every build.

### Conversation and comedy

**Deadpan (items 1, 3 and 5).** Deadpan depends on the speaker not seeming to know the line is funny: a line that states the joke becomes an announcement, and cutting the sentence before the admission often makes it a slip. In the unfamiliar-viewer read, ask whether a supposedly serious character announces the joke so plainly that it stops being funny. This held for the source production's recorded argument; not established for scripted comedy. A slip needs an expectation the viewer holds, so it reads as noise before the viewer knows who is speaking and what is at stake; in a self-aware or presenter-led format the effect can invert.

**Outtakes (item 8).** A list of amusing moments is not necessarily a coherent reel. An outtake needs the exchange it interrupts, because a slip is funny against an expectation, so it may take more filler and setup than the main cut; a montage of stripped clips was rejected in the source production in favour of a few in full context. Not established for formats whose viewers already know the speakers. It fails when the reel's slot is too short for any setup; then the outtake may not belong.

## Musts

- **Must (explicit requirement):** build an order the person dictates exactly as dictated and record it in the directive ledger; never substitute another order for it. **Hypothesis:** a rival shown beside the dictated order can surface a better structure the person had not seen; it fails when the person dictated the order to end a discussion, so offer a rival only when it fixes a defect you can name, such as a lost setup.
- **Must (explicit requirement):** a cut runs to the duration, or within the range, the person stated; Shortening lists ways to get there.
- **Must (truthfulness):** the structure decision names the person as its source only on their word. Name labels identify the person actually shown. Never conceal a missing speaking shot by presenting unrelated mouth movement as a matching performance.
- **Must (technical fact):** apply each speed factor exactly once (`reference/technical-facts.md`).
