# iPhone PWA Mobile Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Make the Paris itinerary site iPhone-friendly as a lightweight installable PWA with mobile travel navigation.

**Architecture:** Preserve the current single-file React app. Add small static PWA assets beside `paris.html`, then enhance the existing `App` component with mobile quick actions and iPhone-safe bottom navigation.

**Tech Stack:** HTML, Tailwind CDN, React 18 UMD, Babel Standalone, Leaflet CDN, Web App Manifest, Service Worker.

---

### Task 1: Add PWA Assets

**Files:**
- Create: `manifest.webmanifest`
- Create: `service-worker.js`
- Create: `icons/paris-icon.svg`

- [x] Create `manifest.webmanifest` with the app name, start URL, standalone display, blue theme color, and SVG icon.
- [x] Create `service-worker.js` that caches the local app shell files and ignores failed CDN/runtime requests.
- [x] Create `icons/paris-icon.svg` as a simple Paris-themed app icon.

### Task 2: Add iPhone Metadata And Registration

**Files:**
- Modify: `paris.html`
- Modify: `paris.txt`

- [x] Add manifest, theme color, Apple mobile web app, Apple title, Apple status bar, and Apple touch icon tags.
- [x] Add a safe service worker registration script that only runs on HTTP localhost or HTTPS.
- [x] Keep `file://` preview quiet by not attempting service worker registration there.

### Task 3: Add Travel Mode Mobile UI

**Files:**
- Modify: `paris.html`
- Modify: `paris.txt`

- [x] Add CSS helpers for `safe-area-inset-bottom`.
- [x] Add an `activeDayData` derived value in `App`.
- [x] Add a mobile-only active-day quick panel below the header tabs.
- [x] Add mobile-only bottom navigation buttons for Today, Itinerary, Tickets, Food, and Map.
- [x] Ensure bottom navigation calls existing state setters and the existing global map modal.

### Task 4: Document And Verify

**Files:**
- Modify: `summary.md`

- [x] Add a 2026-05-09 PWA/mobile conversion note.
- [x] Verify `paris.html` and `paris.txt` are identical.
- [x] Search for expected PWA strings.
- [x] Reload the page in the in-app browser.
- [x] Check desktop DOM visibility and console errors; mobile-only UI was verified by source/CSS because the in-app browser viewport is desktop-sized.
