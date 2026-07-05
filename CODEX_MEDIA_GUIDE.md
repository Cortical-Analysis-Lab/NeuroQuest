# Codex Media Guide for NeuroQuest

This file is for future Codex/Codespaces sessions. It explains how the static GitHub Pages version is structured and how to keep media working smoothly.

## Core Rule

The GitHub Pages version is static. Do not add Django-only behavior, database calls, login/session logic, or local launcher scripts here. Keep student-facing playback inside `index.html` and static assets under `assets/`.

## Folder Structure

```text
index.html
assets/
  audio/
    course-modules.js
    *.m4a
    *-transcript.js
    *.transcript.json
    *.vtt
  slides/
    <module>/
      <module>-slide-##.png
  media/
    media-overlays.js
    <module>/
      *.gif
      *.mp4
      *.m4a
  mascot/
    *.png
```

## Audio Alignment

- The active module cue file is `assets/audio/course-modules.js`.
- Module audio paths are defined by each module's `audioOut` value.
- Current active cleaned audio references include:
  - `tools-clean.m4a`
  - `neuropsych-clean.m4a`
  - `language-clean.m4a`
  - `technology-clean.m4a`
- Anatomy and Aging use the direct audio references in `index.html`.
- The local workspace may retain uncleaned/source narration files such as `tools.m4a`, `neuropsych.m4a`, `language.m4a`, and `technology.m4a`. Do not add them to the deploy unless the static app references them.
- Do not reintroduce narration phrases such as "pause for media", "Section Pause", or spoken YouTube/video durations into active audio/transcripts.
- If audio is edited, update cue times and transcript timings together.

## Slide Assets

- Slide images live in `assets/slides/<module>/`.
- Keep filenames stable because the player constructs slide paths from module IDs and slide numbers.
- Export slides at a consistent 16:9 aspect ratio.
- Do not replace animated GIF/video content with frozen slide screenshots only. If the source slide had animated media, preserve it through `assets/media/` overlays.

## GIFs and Local Videos

- Media overlay placement is controlled by `assets/media/media-overlays.js`.
- Overlay coordinates should preserve the source PowerPoint placement as percentages of the slide stage.
- GIFs should stay as `.gif` files so they animate in the browser.
- Local videos should be committed under `assets/media/<module>/`.
- Local/non-YouTube videos should play muted and loop during narration unless a module intentionally specifies otherwise.

## YouTube Videos

- YouTube media should remain URL-based and should not be uploaded to the repository.
- The working pattern is click-to-play in the slide stage.
- Keep embed URLs simple. Avoid adding complex YouTube API/player-control behavior unless it is tested carefully in GitHub Pages.
- Narration should pause when the active cue lands on a YouTube slide. The student advances manually after the video, then narration resumes from the next cue.

## Updating From the Local Workspace

When preparing a new GitHub Pages deploy from the full local project:

1. Sync `09_Neuro_Quest_Platform/static/neuroquest/` into `08_Choose_Your_Own_Neuro_Adventure/`.
2. Copy `08_Choose_Your_Own_Neuro_Adventure/` into the GitHub Pages repo root.
3. Keep `.nojekyll`, `.gitattributes`, `README.md`, and this guide at the repo root.
4. Omit unreferenced source/archive narration files unless `index.html` or `assets/audio/course-modules.js` points to them.

## GitHub Pages Constraints

- Keep each file under 100 MB.
- Use relative paths only, such as `assets/audio/...`, not local Windows paths.
- Include `.nojekyll` at the repository root so GitHub Pages serves asset folders without Jekyll processing.
- Large media pushes are easier from GitHub Desktop or command-line Git than from browser upload.

## Validation Checklist

Before committing media changes:

1. Confirm every referenced audio/media/slide file exists.
2. Confirm no active file references local Windows paths.
3. Confirm `index.html` JavaScript still parses.
4. Confirm `course-modules.js` and `media-overlays.js` parse.
5. Check that no single file exceeds 100 MB.
6. Preview at a local static URL, not only by opening the file directly, because browser media behavior can differ.

Useful PowerShell checks:

```powershell
Get-ChildItem -Recurse -File | Sort-Object Length -Descending | Select-Object -First 20 FullName,@{Name='MB';Expression={[math]::Round($_.Length/1MB,2)}}
```

```powershell
node -e "const fs=require('fs'),vm=require('vm'); const html=fs.readFileSync('index.html','utf8'); [...html.matchAll(/<script>([\\s\\S]*?)<\\/script>/g)].forEach((m,i)=>new vm.Script(m[1],{filename:'index.html:inline-'+(i+1)})); new vm.Script(fs.readFileSync('assets/audio/course-modules.js','utf8'),{filename:'course-modules.js'}); new vm.Script(fs.readFileSync('assets/media/media-overlays.js','utf8'),{filename:'media-overlays.js'}); console.log('static JS ok');"
```
