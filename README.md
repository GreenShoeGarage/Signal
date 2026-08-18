# SIGNAL v0.1.0

SIGNAL is a local-first visual gesture and gaze automation workbench.

**Core abstraction:** CAMERA → LANDMARKS → OBSERVATIONS → EVENTS → RULES → ACTIONS.

This v0.1.0 build implements a functional browser application with:

- camera start/stop and device selection
- local video preview with hand/face landmark overlays
- MediaPipe Tasks Vision integration for hand gestures and face landmarks
- semantic enter/hold/exit gesture events
- hand-motion history with swipe and depth-motion events
- approximate webcam gaze, blink/double-blink/long-blink events, and 3×3 gaze zones
- local gaze calibration samples
- live observations and event stream
- visual rule editor with confidence, hold, cooldown, enable/disable, and trace output
- SIMULATE vs LIVE execution modes
- internal actions plus opt-in webhook actions
- Action Lab, Tool Builder, variables, Test Lab event injection, and developer API workspace
- trajectory-based **Teach Gesture** workflow (no server-side training)
- local autosave, Fresh Start, JSON import/export, tool export, dark/light mode, Easy/Advanced mode

## Run

Serve the folder from `localhost` or HTTPS; camera access is normally restricted to secure contexts.

Examples:

```bash
python3 -m http.server 8080
```

Then open `http://localhost:8080/`.

## Vision dependency

The application itself is one HTML file, but v0.1.0 loads Google MediaPipe Tasks Vision, WASM, and the gesture/face model assets from their public CDN/model endpoints at runtime. **Camera frames are not uploaded**; inference occurs in the browser after those assets load. Test Lab, rule editing, project storage, and event injection continue to work if those model assets cannot load.

For a fully offline deployment, download and vendor the MediaPipe Tasks Vision JS/WASM package and model files, then change `MP_JS`, `MP_WASM`, `GESTURE_MODEL`, and `FACE_MODEL` near the top of the module script in `index.html` to local paths.

## Browser boundaries

A normal web page cannot synthesize arbitrary OS keyboard input, silently send SMS, or bypass cross-origin/network security policy. SIGNAL therefore uses explicit browser actions and configurable connectors. Webhook actions are simulated unless the application is placed in **LIVE** mode, and any remote endpoint must allow the browser request.

## Safety

SIGNAL is a prototyping environment. Ordinary webcam gesture recognition must not be used as the only safety control for hazardous or safety-critical machinery. Use independent engineered safety systems for consequential physical control.

## User scripts in v0.1.0

The Developer script editor exposes a small documented `signal` API, but v0.1.0 does **not** yet provide a hardened security sandbox for arbitrary JavaScript. Only run scripts you trust. A sandboxed worker/iframe execution host is a planned hardening step.
