---
name: references/authoring/threejs
description: Three.js and LeaferThree module for 3D scene structure, rendering topics, and timeline guidance inside this repository.
---

## Use this module when

- The task involves `LeaferThree`, `scene_spec`, `three_timeline`, cameras, lights, materials, models, textures, shaders, or interaction.
- You need Three.js knowledge that must still land in the repository's `LeaferThree` contract instead of raw persistent `THREE.*` code.

## Direct rules

- Load `references/authoring/threejs/leaferthree-bridge` first when the output must fit this repository.
- After loading the bridge, treat every downstream Three.js topic module as reference material only. Final repository slide code must still fit the current `LeaferThree` persistence contract.
- Load `references/authoring/threejs/fundamentals` for core scene, camera, and renderer concepts.
- Load `references/authoring/threejs/geometry` for mesh geometry decisions.
- Load `references/authoring/threejs/materials` for material choices.
- Load `references/authoring/threejs/lighting` for lighting rigs.
- Load `references/authoring/threejs/textures` for texture handling.
- Load `references/authoring/threejs/animation` for `three_timeline` and animation strategy.
- Load `references/authoring/threejs/loaders` for model ingestion and external assets.
- Load `references/authoring/threejs/shaders` for shader guidance.
- Load `references/authoring/threejs/postprocessing` for post effects.
- Load `references/authoring/threejs/interaction` for camera or object interaction patterns.
