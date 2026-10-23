# Technical facts

Each bullet is a **Must (technical fact)** unless labelled otherwise. The builder's self-tests (`seeds/cut-and-build.md`) check the time facts before every render. FFmpeg facts were checked 2026-10-22 on 9.0.1 only; test each filter on your build.

## Time

- For a constant-speed source interval starting at `a`, output offset `u` and speed `r`, source instant `t` maps to `u + (t - a) / r`. Piecewise cuts, holds, overlaps, borrowed pictures and retimed media need their own mappings.
- Apply each speed factor once: 1.2× local under 1.25× global is 1.5×; never speed an exported faster clip again.
- Round cumulative boundaries to frames, not each duration, or drift accumulates. Verify audio endpoints and sync on its sample grid.
- **Hypothesis:** after cutting or retiming, revisit captions, speaker labels, reactions, scores, narration and sound, because removed speech can invalidate a score's reason, and moved events keep the wrong meaning.
- **Must (truthfulness):** distinguish demonstration values you authored from the product's real output.
- **Observed in the source production:** text alignment put some words after a pause at the preceding word's end; a waveform onset check improved them. A missing word's interpolated timestamp is an estimate.

## Audio retiming

- `atempo` keeps pitch; retime the picture separately by the same factor.
- One `atempo` accepts 0.5 to 100 but skips samples above 2: chain instances (`atempo=sqrt(3),atempo=sqrt(3)` for 3×), and chain below 0.5.
- `atempo` runs milliseconds long when speeding up and about 17 ms short at 0.5×; end each segment with `apad,atrim=end_sample=<computed count>`.

## Picture

- A borrowed picture (one clip's picture over another's sound) running past the next camera switch in its source shows the wrong shot.
- Interpolation across a camera switch blends two shots; hold the nearest real frame.
- **Observed in the source production:** about one frame in twelve of a 25 fps video-call recording was an exact repeat, so slowed motion stuttered.
- A conversion without a whole-number frame-rate ratio repeats or drops frames (`fps=30` doubles every fifth 25 fps frame). Interpolating to a common multiple (150 fps for 25 and 30) lets the builder sample any speed without repeats.
- **Observed in the source production:** an interpolator (RIFE v4.6) pulled frames of a slowed close-up toward the nearer real frame instead of the requested timestep. Measure placement by optical flow.
- A smooth motion metric does not prove a convincing face. **Hypothesis:** inspect interpolated faces or route them to the person.
- Grab a known frame by index (`select=eq(n\,N)`) or by seeking its timestamp; `-ss t` returns the first frame at or after `t`. In one test, the `fps` filter returned contact-sheet frames a second or more from their labels.

## Rendering and serving

- Writing into a render's inputs mid-render corrupts it (gate G3).
- Browser video seeks to unbuffered positions only if the server answers HTTP range requests (MDN, checked 2026-10-22). Python's `http.server` answered a range request with status 200 and the whole file (3.11 and 3.14, tested 2026-10-22); serve video from a handler that returns 206.

## Loudness

- Single-pass `loudnorm` varies gain, risking pumping. It applies one linear gain only given `measured_I`, `measured_LRA`, `measured_TP` and `measured_thresh` from a first pass, and reverts to dynamic mode if the target range is below the source's or true peak would exceed the target; limit peaks first.
- Dynamic `loudnorm` outputs 192 kHz unless you set `-ar` or `aresample`.
- Rebuild stems whenever clip lengths change, or they drift out of sync.

## No platform named

Use H.264 and AAC in MP4 (YouTube's recommended upload settings, checked 2026-10-22); `-pix_fmt yuv420p`, because libx264 wrote 4:4:4 from RGB input without it; and `-movflags +faststart`, so web playback starts early.

Take a platform's loudness target from the platform and measure the output. With none, record a target, its source and check date in `project.md`'s format section as an agent choice. One documented target: -18 LUFS for speech (AES TD1008, now AES77, for streaming; secondary sources checked 2026-10-22, AES text unverified).

## Parameters to record

Record each in the decision ledger with its reason, so later builds reuse it: frame and sample rates, `atempo` chains, repeat and camera-switch thresholds, interpolator and measured placement, loudness target, caption tolerance.
