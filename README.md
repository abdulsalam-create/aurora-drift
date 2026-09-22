# Aurora Drift

**An immersive quiet.** A WebXR experience where you float in a twilight expanse: drifting stardust, flowing aurora curtains overhead, glowing lanterns bobbing on the air, and a reflective sea beneath. Bloom-lit and calm, it runs in a VR headset or in a plain browser tab.

**[▶ Open it](https://abdulsalam-create.github.io/aurora-drift/)** works in any browser; the _Enter VR_ button lights up on a WebXR headset.

## What it is
Not a data visualization. It is a mood: the version of XR people picture before they try it. The aim was a scene that is genuinely nice to look at, so the work went into light rather than geometry.

- **42,000 points of stardust** drifting on a flow field, each softly twinkling, additively blended so they read as light, not dots.
- **Five aurora curtains** rendered with layered fBm noise in a shader, waving and breathing at their own pace.
- **A reflective sea** that mirrors the sky gradient and the aurora, with a Fresnel grazing-angle sheen and pinpoint glints.
- **A gradient sky dome** with a warm horizon band and a scatter of fixed stars.
- **Floating lanterns** with additive halos, bobbing gently.
- **UnrealBloom** over the whole thing for the dreamy glow (in flat mode; XR renders direct to stay fast and correct per-eye).
- **Three skies** to switch between: Twilight, Deep Night, Dawn, with the colours eased from one to the next.
- **Generative ambient audio**: a slow, detuned oscillator pad with a drifting filter sweep, synthesised live, no audio files.

## Interaction
- **Browser:** drag/move the pointer to look around while the camera drifts on its own; click to send a burst of light.
- **VR:** press _Enter VR_. Your controllers become wands with a glowing tip; the trigger sends a burst of light, and holding it draws nearby stardust toward your hand.
- Comfort first: the viewpoint drifts slowly and never snaps, so it stays easy on the eyes.

## Running it
It is a single `index.html` with no build step. Open the file locally, or serve the folder:

```bash
python -m http.server 8000   # then open http://localhost:8000
```

Three.js and its addons load from a CDN via an import map. A WebXR headset (or the browser's WebXR emulator) is needed for VR; everything else works in a normal tab.

## How it is built
Plain [three.js](https://threejs.org) r160, no framework. Every glowing element is a custom `ShaderMaterial` with additive blending; the aurora, sky, and sea share one small GLSL noise/fBm routine. The render loop uses `setAnimationLoop` so the same scene serves both the flat camera (through an `EffectComposer` bloom chain) and the XR camera (rendered directly). One file, a few shaders, a lot of light.

## License
MIT
