# NeuroQuest Static Course Site

This repository is the GitHub Pages version of NeuroQuest. It is a static learning site: students can open the modules, view slides, play aligned narration, and use the embedded GIF/video/YouTube media without needing Django, a database, or a local launcher.

## GitHub Pages Setup

1. Put `index.html` and the `assets/` folder at the repository root.
2. In GitHub, open **Settings > Pages**.
3. Set **Source** to **GitHub Actions**.
4. Push to `main`, or run the **Deploy GitHub Pages** workflow manually.
5. Wait for GitHub Pages to publish the site.

The expected published URL is usually:

```text
https://cortical-analysis-lab.github.io/NeuroQuest/
```

## What This Version Includes

- Static NeuroQuest module player
- Slide PNGs
- Aligned narration audio
- Transcript/cue data
- GIF overlays
- Local non-YouTube video overlays
- YouTube embed links
- Mascot images and interface assets

## What This Version Does Not Include

- Student login
- Saved quiz scores
- Topic Reflection recording/submission
- Instructor review dashboard
- Django database features

Those features live in the full Django version under `09_Neuro_Quest_Platform` in the local project workspace.

## Large File Notes

This static site contains large audio, GIF, video, and slide image files. Keep individual files under GitHub's 100 MB file limit. If a future media file is larger than that, compress it before committing or move it to external hosting and update the relevant asset path.

The local workspace may contain extra uncleaned narration files used as source/archive material. They are not required for this static deploy unless referenced by `index.html` or `assets/audio/course-modules.js`.

## Quick Local Preview

Because this is static HTML, it can usually be opened directly in a browser. For a closer GitHub Pages-style test, run a simple static server from the repository root:

```powershell
python -m http.server 8000
```

Then open:

```text
http://localhost:8000/
```
