# Facebook 360 VR

Web prototype for 360° immersive viewing in the browser, translating social VR interaction patterns into a lightweight, deployable experience without native platform dependencies.

## Live Demo

[View the immersive prototype](https://ramona-dsouza.github.io/Facebook-360-VR/)

---

## Overview

Maps platform-native VR behaviors, spatial context, orientation, in-scene UI, onto open web architecture. Single-page app: equirectangular 360° background plus a React-driven UI layer, packaged and served with standard web tooling.

---

## Concept

**Translation** of VR interaction and presentation into a browser-only environment. 
Priorities:

- **Spatial navigation and orientation** — sense of place and view direction within the 360° scene.
- **Interaction feedback** — focus/input semantics (focus-in, focus-out) aligned with VR-style interaction on conventional devices.
- **Interface clarity** — in-scene panels and typography that read clearly against immersive backgrounds.

Goal: immersive experiences as first-class web assets, with UX consistency and clear technical boundaries over visual effects alone.

---

## Technical Architecture

**Runtime:** React 360 (React + React Native–style APIs for 360/VR on the web). **Entry:** static HTML loads the client bundle; `React360.init()` receives app bundle path, mount node, and `assetRoot`. **App bundle:** root component `ramonavr360` (View/Text panel, styled greeting) registered with `AppRegistry` and mounted to the default surface. **Client bundle:** creates instance, compositor, and surfaces; sets background via `compositor.setBackground(getAssetURL('360_world.jpg'))`; resolves assets from `static_assets/`. **Surfaces:** default surface = UI layer; compositor = panorama background (no app-level 3D setup). **Assets:** `static_assets/`; `360_world.jpg` required.

Repo contains pre-built `index.bundle.js`, `client.bundle.js`, and `index.html` only—no build pipeline or source. Stack: Babel-transpiled JS, React 360 (bridge + WebGL-backed rendering).

---

## Interaction Model

- **Viewport:** Full-screen 360°; orientation (head or pointer) drives camera; framework exposes head-matrix listeners.
- **UI layer:** One floating panel on the default surface (2D overlay, e.g. 1000×600), centered greeting; `StyleSheet` for layout and typography.
- **Input:** Runtime supports focus/press events (`FOCUS_IN`, `FOCUS_OUT`, `FOCUS_IN_PRESS`, etc.) for future `VrButton` integration; prototype does not yet wire custom handlers.
- **Audio:** `VrSoundEffects` and audio modules available; unused in this demo.

---

## Setup

1. Clone or download the repo.
2. Create `static_assets/` in the project root; add `360_world.jpg` (equirectangular panorama).
3. Serve over HTTP from the project root (e.g. `npx serve .`). Avoid `file://`.
4. Open the root URL in a modern browser.

No `npm install`, pre-built bundles only. Use any static server.

---

## Purpose

Structured experiment in bringing VR-style presentation and interaction to the web: same mental model (immersive space, in-scene UI, orientation and focus), different delivery (static assets, HTTP, no app store or VR runtime). Showcases systems thinking, UX translation across platforms, constraint-driven architecture, and clear implementation for maintainability and extension. Portfolio evidence for immersive and spatial web design-to-implementation.
