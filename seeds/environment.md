# Environment

**Environment inventory.** Write `environment.md` in the project folder: what this machine, agent and account can do. Later seeds choose routes from it, so gaps show up there, not as a failed command mid-seed. Check each capability before the first seed that depends on it. The bar is a production engineer's setup sheet: what will run, on what, and what the film loses where something will not.

## What `environment.md` contains

1. Per capability: present or absent, version, date checked, chosen route.
2. Per absence: the fallback and its cost to the film, such as "no slow motion; holds instead".
3. One line per seed the inventory changes, such as "edit room: degraded form".
4. Per artifact kind (video, audio, HTML page, image): the command, tested once, that opens it in front of the person; `tools/show` uses it. Audio must open in a player that plays it, not a music library.
5. Per install: where it went, on what permission.

## Tools

The named routes are examples checked 2026-10-22 against current documentation unless marked unverified; they are not a list to keep. Before committing to a paid or generative route, run the sourcing rule in `SKILL.md` (research the current state of the art, check what the person already uses, then offer or choose); `reference/media-index.md` lists the media kinds. FFmpeg facts were checked only on 9.0.1; test each filter on your build. Re-read licences before commercial delivery.

| Capability | Check | Routes | If absent |
|---|---|---|---|
| FFmpeg and ffprobe | Versions; `ffmpeg -filters` lists `loudnorm`, `ebur128`, `atempo`, `scdet`, `freezedetect`, `drawtext` (needs libfreetype, libharfbuzz), `subtitles` (needs libass) | Package manager; static builds linked from ffmpeg.org when a filter is missing; the imageio-ffmpeg wheel, without ffprobe | Stop media work and tell the person; text artifacts can proceed |
| Python 3 with numpy; Node.js | Versions | Package managers; uv installs Python under the user's home without administrator rights | Write tools in whichever exists |
| Speech recognition with word timestamps | Transcribe a one-minute sample | mlx-whisper (Apple Silicon); faster-whisper (CPU or CUDA, `word_timestamps=True`); whisper.cpp (`-ml 1`); hosted services (paid; unverified) | The platform's transcript; coarser cut points |
| Text on screen | Read one frame of the recording | Your own vision; Tesseract (Apache-2.0; apt `tesseract-ocr`, needing root; Homebrew `tesseract`; UB Mannheim's Windows installer) | FFmpeg scene changes and idle spans; the person labels a contact sheet |
| Speaker map | Sampled frames against transcript turns | A layout cue (active-speaker tile, background colour); pyannote's community-1 (CC-BY-4.0; gated by a Hugging Face token); hosted diarization (paid) | Frames and turn-taking; the person confirms spans |
| Frame interpolation | A Vulkan or CUDA GPU; one interpolated pair | rife-ncnn-vulkan (MIT; macOS, Ubuntu, Windows); FFmpeg `minterpolate`, uneven in the source production | Hold, cutaway or speed change; the truth note states the loss |
| Coded composition | Render one frame | FFmpeg `drawtext` or `subtitles`; Motion Canvas (MIT); Revideo (MIT); HTML captured frame by frame; Remotion (free for individuals, non-profits and companies of up to three employees; otherwise paid) | The simplest route the scenes allow; record its licence |
| Headless browser | One screenshot | Playwright; `chrome --headless --screenshot URL` | Editor verification not run (G7); previews compiled with FFmpeg; screenshots from the person |
| Server with range requests | Seek a served test video | A short script with a range handler (`reference/technical-facts.md`) | None needed |
| The person opens your local pages | The person opens a test URL | Same machine; an approved tunnel or port forward; harness preview | Degraded edit room: previews and a cut list the person edits; boards as images |
| Free stand-in voice | Synthesize one line | macOS `say`; Windows `System.Speech`; Piper (GPL-3.0; each voice's licence on its model card); Kokoro (Apache-2.0 weights) | Durations from word counts at a measured speech rate |
| Real voice, images, talking heads, lip-sync | A key from an environment variable or a file the person named, or a local model and GPU | Hosted services (paid; ElevenLabs' `with-timestamps` gives per-character times; others unverified); local models on a GPU | The best free voice or none; illustration, licensed stock, text, or a still with captions; the truth note names the paid step |
| Music and effects | Fetch one track with `curl` | Mixkit (commercial use, no attribution, no sign-up; check its licence page for exclusions); Kevin MacLeod at incompetech.com (CC BY 4.0; the site generates the credit); both serve direct MP3 links; local synthesis (Python WAV, SoX `synth`); Apple Loops on Macs (inside a composition, not as loops); generative services (paid; unverified) | Synthesized effects, a quiet bed, or no music (`seeds/sound-and-voice.md`) |
| Web search | The harness's tool | Harness search; a search API | Sources from the person; research notes say none ran |

**No root and no licence answer.** On a fresh Linux machine, Playwright's browsers, headless Chrome and Remotion need system libraries, which Playwright's `install-deps` installs as root. Without that permission, use `drawtext` or `subtitles` for cards and captions if your build lists them (a Homebrew 9.0.1 build had neither); Motion Canvas or Revideo only if their browser runs without new libraries; Remotion only with the person's licence answer in `local.md`.

## Agent capabilities

| Capability | Check | If present | If absent |
|---|---|---|---|
| Viewing images | Read your own contact sheet | Audit frames and designs by eye | Frame-difference and scene-change measures; the person judges visuals; audit reports say "not visually inspected" |
| Helpers | Documentation or a test spawn | File-scoped helpers, competing designs, the independent reader | Independent reader: a new session or fresh model call given only the goal, assembly script and export; else your own cold read, reported as sharing your context |
| Model billing | How the launching account bills | `tools/spend` logs your and helpers' calls on it; G2 gates them only if the person counts helper cost (`seeds/project-file.md`, section 6) | None needed |

## Hypotheses

**Time a one-minute sample before a long transcription or interpolation job.** Speed varies widely between a GPU or Apple Silicon route and a CPU-only one, and the rate decides model size and route. The source production ran on one fast machine, so this method is untested. Time the second run, since the first includes model download, and time it under the planned concurrency, since parallel interpolation jobs saturated the source machine.

**Install project-locally without asking.** A virtual environment or `node_modules` inside the project folder changes nothing outside it, so it is ordinary production work; the source production installed its recogniser and composition tool this way. This fails when the person or `local.md` restricts installs; then ask.

**Launch test browsers muted** (`--mute-audio`, media elements `muted`). Sound from a source the person cannot find alarms them; a hidden test browser did this in the source production. Its value when the person is away is unknown. It fails when a test must be heard; then warn the person first.

## Musts

- **Must (truthfulness):** record a capability as present only after exercising it here.
- **Must (permission):** ask the person before any system-wide install or anything needing administrator rights, and before building on a route whose licence may not cover their use, such as Remotion for a company above its free tier.

The listening Must is in `seeds/audit.md`; the credentials Must, in `SKILL.md`.
