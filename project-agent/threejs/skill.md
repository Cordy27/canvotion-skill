---
name: project-agent/threejs
description: Three.js and LeaferThree module for 3D scene structure, rendering topics, and timeline guidance inside this repository.
---

## Use this module when

- The task involves `LeaferThree`, `scene_spec`, `three_timeline`, cameras, lights, materials, models, textures, shaders, or interaction.
- You need Three.js knowledge that must still land in the repository's `LeaferThree` contract instead of raw persistent `THREE.*` code.

## Direct rules

- Load `project-agent/threejs/leaferthree-bridge` first when the output must fit this repository.
- After loading the bridge, treat every downstream Three.js topic module as reference material only. Final repository slide code must still fit the current `LeaferThree` persistence contract.
- Load `project-agent/threejs/fundamentals` for core scene, camera, and renderer concepts.
- Load `project-agent/threejs/geometry` for mesh geometry decisions.
- Load `project-agent/threejs/materials` for material choices.
- Load `project-agent/threejs/lighting` for lighting rigs.
- Load `project-agent/threejs/textures` for texture handling.
- Load `project-agent/threejs/animation` for `three_timeline` and animation strategy.
- Load `project-agent/threejs/loaders` for model ingestion and external assets.
- Load `project-agent/threejs/shaders` for shader guidance.
- Load `project-agent/threejs/postprocessing` for post effects.
- Load `project-agent/threejs/interaction` for camera or object interaction patterns.
