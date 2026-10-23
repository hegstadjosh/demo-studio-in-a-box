# Coded scenes

Build the film's coded parts (product interfaces, title cards, scoreboards, captions, the shell recorded clips play inside) as a composition project on the route `environment.md` chose, with on-screen text, timing and cues kept as data. Beside it, write `brand.json`, stills in `stills/<draft-id>/`, and a truth-list entry in `project.md` for every depicted feature and generated element. A plain trim needs none of this.

The person directs by naming what a viewer should see; you edit the data and rebuild (**hypothesis**, `seeds/cut-and-build.md`: a patched render cannot say which edit it reflects). **Must (technical fact):** never write scene data while a render reads it (G3).

**Quality bar.** Each interface passes for a real page of a professional product: clear hierarchy, containment, type, spacing, contrast and deliberate component detail. The data maps narration lines to on-screen words, marks hand overrides of computed beat times, keeps caption layers separate, and marks each element recorded, designed or generated.

## Timing

**Hypothesis.** Time scenes from the narration's measured line lengths, starting with a free stand-in voice, so picture and captions are timed before any paid voice exists and a new take needs only splitting and a re-render. The production this package comes from (the source production) timed a narrated promo this way. It is untested where music or picture leads. It fails where a joke needs a pause speech length cannot supply; set that beat by hand and mark the override so retiming keeps it.

## Brand tokens

Before drawing any interface, put the wordmark, fonts, colours, navigation and real copy in `brand.json`, each with its source, and have every scene and helper read it. Take them from the live product; when only a recording is supplied, it is the source of truth for features and brand: sample logo, colours and copy from its frames, and search the web for the product name only to confirm. **Hypothesis:** a shared file stops each scene guessing; the source production's agent drew wrong fonts and invented copy because it had not read the live site. When sources disagree, ask the person which governs; with no discussion, prefer what the recording shows and record the conflict in the truth list.

**Must (truthfulness):** settle whether each picture is a recording, a designed depiction or a proposed experience. Check every depicted feature, and anything the film invites the viewer to try, against what the product really does; record the result in the truth list, or name the check only the product's owner can make. Explain invented examples in the truth note in `deliver/`.

## Interfaces designed for the story

**Hypothesis:** a viewer who loses track of a basic fact (who is speaking, which round, which product) spends attention recovering it instead of following the scene, so keeping that answer on screen frees attention; a persistent matchup bar did this for a debate in the source production. It fails where the film withholds the answer on purpose, as in a reveal, because the label spoils the payoff.

**Hypothesis:** design each screen from what the scene must show, with the tokens and the product's component code as material; a designed depiction can be polished without being a screenshot. In the source production, a screenshot fallback after a rejected design was also rejected, and better design worked. It fails when the brief requires the real product exactly; then match it.

**Hypothesis:** frames compared against real apps of the same kind, for content fidelity, component scale, density and finish, expose the defects a generated interface tends to have: a generic look, floating panels without containment, duplicated widgets, too many accent colours. Borrowing a familiar convention for an element (overlay captions, score pop-ups, broadcast title cards) may let viewers read it faster. In the source production these checks came from one director's critiques of rejected designs. It fails when the film needs a distinctive look; then a borrowed convention reads as a template.

**Style directions.** When the person criticizes the look, write the restatement (`seeds/show-the-human.md`), then have competing helpers, each given a different premise, or sequential fresh passes render the same key states into `design/<direction>/` from a goal-level brief ("make this read as a professional product page"). **Hypothesis:** in the source production that brief produced the accepted redesign where piecemeal fixes had not, and the person chose among stills quickly. Identical briefs return one look.

## Format changes and caption layers

**Hypothesis:** a viewer on a phone judges a portrait product film as the product on a phone, so a framed landscape interface reads as small and unfinished; in the source production the person directed this change. Redesign navigation, main content and primary actions for the phone rather than enlarging a border around the landscape film, and keep a third-party moment, such as an invite shared in a familiar messaging thread, recognizable. Where the product has a mobile form, depict it. Where it has none, a mobile depiction is a proposed experience and goes in the truth list; a framed or cropped landscape view may be the honest choice. Keep the soundtrack if the picture fits; verify readability and timing.

Track which caption layer a request concerns (recorded speakers, narrator, other clip speech, interface text) and when: removing narrator captions during a debate leaves the debaters' captions. If a caption covers something important, move that layer; deleting it changes what the film says. Check each layer for words per screen, line grouping, contrast, timing against speech and safe-area placement, including over a reaction shot or split screen. Mark in the truth list whether a caption is a film overlay or a depicted product feature, since a viewer may take an overlay for something the product does.

## Screen recordings

**Hypothesis.** Desktop text shown full frame is too small to read on a phone, so reframe a screen recording toward the part that matters: find the active region from differences between consecutive frames or from the cursor position, then crop or zoom with easing (FFmpeg `crop` or `zoompan`), keeping every value in the cut file (`seeds/cut-and-build.md`). A portrait frame holds one region where landscape holds two, so plan which region each moment needs. This comes from common screen-demo practice, not from the source production; how tightly to frame is not established. It fails when a zoom outruns the eye or crops away the context that says where the action is; ease slower or widen. The audit report records whether on-screen text is legible on the target screen.

## Stills of key states

For every draft, render key states and transition midpoints from the actual render into `stills/<draft-id>/` for the audit report (G1) and the live board. Look for captions over names or logos, unintended wraps, duplicated widgets, stale text from the previous beat, off-brand fonts, an empty card mid-click, a face labelled as someone speaking offscreen, and a background that changes while a modal still covers it. Judge each interface still against `reference/ui-design.md`, the interface direction the person gave during the source production, such as containing all text, building from real components in the product's brand and never wrapping by accident, and name the rule behind each finding. A still shows a visible defect, not how motion feels.

## Generated pictures and speaking faces

**Must (permission):** generate a real person's likeness or voice only with consent recorded (G5); make every paid call through `tools/spend` (G2).

**Hypothesis.** Propose each generated element in one line before making it: in the source production generated media cost the most and survived the least, and a proposal answered within minutes beat an unwanted render. How long to wait is not established; when no reply is coming, the proposal only delays the work, so generate within the budget and record the choice in the decision ledger. Cost questions within the budget: `seeds/sound-and-voice.md`.

**Hypothesis:** for speaking faces, a service that renders a clip from an image and finished audio gives a fixed, reviewable take, where recording a live streaming avatar depends on the network during capture; in the source production the live route lost frames and sync. Locking the voice first, one clip per line, and naming background, lighting and camera in the prompt kept clips consistent there. Not established across services. It fails when the service drifts in identity or setting within a clip, which prompt words suggesting a place (an orator, a hall, a library) can invite; check a contact sheet of every raw clip.

**Must (technical fact):** matching audio does not prove visible lip-sync; inspect word beginnings and endings, pauses and the return to rest, and the whole face for identity, lighting and crop.

**Must (truthfulness):** present real recorded speech and people as real, never present generated people or voices as recorded, and list each generated person and voice in the truth note.

**Must (permission):** add on-screen labels where platform rules or law require them.

**Hypothesis.** Beyond those labels, disclose in the truth note and the offered post description, because on-screen footnotes made a marketing film read as amateur in the source production. This fails when viewers could take a generated figure or voice for a recording, which the truthfulness Must forbids; then label it on screen.
