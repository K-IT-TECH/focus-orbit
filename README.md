![FocusOrbit banner](./banner.svg)

# FocusOrbit

[**Open live app →**](https://k-it-tech.github.io/focus-orbit/)

An energy-aware task board with a focus timer and session log.

**Status:** Working local-first web app. Responsive, dependency-free, and published on GitHub Pages. No backend or account system.

## Why build it?

Make a focus tool that adapts to energy instead of showing only a generic to-do list.

**Design:** Forest-black surfaces, lime details and a circular timer.

**Practice:** Time-based state, local persistence and task filtering.

## Working features

- Add tasks with an energy level and an estimated duration.
- Filter tasks to match your current energy.
- Run, pause and reset a deadline-based focus timer.
- Mark tasks complete and save a log when the timer finishes.
- Download and restore versioned JSON backups, with validation before replacement.
- Use the app offline after the first successful online visit (HTTPS or localhost).

## Run it

1. Clone or download this repository.
2. Open the repository folder in VS Code using **File → Open Folder**.
3. Double-click `index.html` in File Explorer to launch it in a current browser.

There is no dependency installation, API key, paid service or build step. All assets are local. If your browser restricts storage or clipboard access on `file://`, use a local static server. If Python is already installed on Windows, open a terminal in this folder and run:

```powershell
py -m http.server 5500 --bind 127.0.0.1
```

Then visit `http://localhost:5500`. Keep using the same browser and address to keep the same saved data. Changing ports, browsers or origins creates a separate storage area.

## A quick demo

Add a low-energy task → filter by Low → finish a short timer session.

## File guide

| File | Purpose |
|---|---|
| `index.html` | Document shell and local script/style references |
| `meta.js` | App name, tagline, description and initials |
| `styles.css` | Theme variables, responsive components and app layout |
| `common.js` | Storage, safe text escaping, dialogs, downloads and shared UI |
| `app.js` | App state, sample data, rendering and event handlers |
| `data-tools.js` | Versioned backup, validation, restore and offline status |
| `sw.js` / `manifest.webmanifest` | Scoped offline cache and web app metadata |
| `banner.svg` / `favicon.svg` | Editable vector branding |
| `ROADMAP.md` | Three follow-up tasks and a build prompt |
| `MY_CHANGES.md` | A place to record your own work |
| `.nojekyll` | Allows straightforward static publishing on GitHub Pages |

Every folder is self-contained. It does not depend on another starter folder.

## Make it your own

1. Change the name/tagline in `meta.js` and the accent colors at the top of `styles.css`.
2. Replace demo content in the `seed` object in `app.js`.
3. Implement one item from `ROADMAP.md` and record the change in `MY_CHANGES.md`.
4. Replace this section with your own problem statement, screenshots and development notes.

## Deployment

GitHub Pages serves this repository's `main` branch from `/(root)`. All assets use relative paths, so the app works from its repository subpath. No API keys or build commands are required.

For future releases, update the cache version in `sw.js` when changing the offline shell. The service worker only caches this app's files and only clears older caches with this app's prefix.

## Scope and data

The timer uses a wall-clock deadline so a delayed browser interval does not accumulate drift. Returning after a closed or sleeping tab logs a finished session once. It does not run an OS notification service; changing your system clock can change the timer. Task estimates are separate from the timer and must be set manually.

Sample data is fictional. Changes stay in `localStorage` in this browser, are not encrypted, and do not sync across devices. Clearing browser data removes them. Multiple tabs do not coordinate edits. Use **Your data → Download backup** to export a version 1 JSON snapshot, then choose that file under **Restore** on another device. Restore validates the app name, version, fields, ranges and record references, previews the record count, and asks before replacing local data. Back up your current data first. Focus timers restore paused. Files larger than 2 MB are rejected. **Reset demo** replaces the saved data after confirmation. Browser data is separate from the source files you upload to GitHub.

## Next steps

1. Add an editable weekly focus target.
2. Add optional audio with a user gesture and permission handling.
3. Add a calendar view and sync across devices.

## Validation

See `CHECKS.md` for completed checks and the short manual checklist. Native keyboard controls, form labels, visible focus styles and responsive CSS are included. Check the manual checklist when you customize the app or test it on a new browser.
