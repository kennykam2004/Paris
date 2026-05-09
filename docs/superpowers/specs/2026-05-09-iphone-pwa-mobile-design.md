# iPhone PWA Mobile Design

## Goal

Turn the existing single-file Paris itinerary site into an iPhone-friendly travel web app that can be added to the Home Screen when hosted over HTTPS, while preserving the current itinerary data and desktop layout.

## Selected Approach

Use the recommended "Travel Mode PWA" approach:

- Keep `paris.html` as the main React entry point.
- Add iOS PWA metadata, web app manifest, service worker, and app icon files.
- Add a mobile-first quick entry panel for the active day.
- Add an iPhone-safe bottom navigation for Today, Itinerary, Tickets, Food, and Map.
- Avoid a build step, package manager, or full project split.

## iPhone Constraints

- On iPhone, install-like behavior depends on Safari's "Add to Home Screen".
- `file://` is fine for local preview but cannot provide a production-grade install/offline PWA experience.
- Service workers require HTTP localhost during development or HTTPS in production.
- Bottom navigation must respect `safe-area-inset-bottom`.

## Files

- `paris.html`: add PWA metadata, iOS metadata, mobile app controls, service worker registration, and bottom navigation.
- `paris.txt`: synchronized copy of `paris.html`.
- `manifest.webmanifest`: app name, theme, display mode, icons, and start URL.
- `service-worker.js`: lightweight cache for local app shell files.
- `icons/paris-icon.svg`: install icon source.
- `.gitignore`: ignore `.superpowers/` brainstorming artifacts if this folder is later placed under git.
- `summary.md`: record the PWA/mobile conversion.

## Acceptance Checks

- The page still loads from `file:///C:/Users/User/Desktop/Codex/Paris/paris.html`.
- The title and main tabs remain visible on desktop.
- Mobile viewport shows bottom navigation and a compact active-day panel.
- Day 1 still shows the updated 04:30 cross-border car plan.
- Browser console has no JavaScript errors from this page.
- `paris.html` and `paris.txt` remain identical after synchronization.
