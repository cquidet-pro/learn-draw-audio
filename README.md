# learn-draw-audio

Pre-generated narration clips for **[Learn 2 Draw](https://learn2drawkids.com)**'s
read-aloud feature — the drawing hints spoken in a warm human voice (ElevenLabs,
"Candy – Young and Sweet"). Hosted here as a **public repo served over the
[jsDelivr](https://www.jsdelivr.com) CDN**, so playback costs the main site
**zero Firebase egress**.

The app plays the matching clip for each step's hint and falls back to the
browser's built-in voice for anything without a clip.

## Structure

```
common/                 ← lines shared by every drawing
  all-done-press-space.mp3
  now-the-next-colour.mp3
  yay-all-done-press-for-a-surprise.mp3
<drawing-id>/           ← one folder per drawing (folder name = the drawing's id)
  <phrase-slug>.mp3
```

- Filenames are the spoken phrase, lowercased with non-letters turned into `-`
  (emoji dropped), e.g. `start-with-a-big-round-head.mp3`.
- A drawing that shares a step with another (e.g. `dog` vs `dog-7`) reuses the
  base drawing's file via the app's manifest rather than duplicating audio.

## Serving

Clips are fetched via jsDelivr:

```
https://cdn.jsdelivr.net/gh/cquidet-pro/learn-draw-audio@main/dog/start-with-a-big-round-head.mp3
```

Pin a tag (e.g. `@v1`) instead of `@main` for cache-stable production URLs.

## Format

MP3, 44.1 kHz, mono. Generated from the drawing hints in the Learn 2 Draw repo.
