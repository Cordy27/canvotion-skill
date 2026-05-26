---
name: project-agent/visual
description: Visual planning and critique module for scene composition, refinement, and common visual errors.
---

## Use this module when

- The request is about how a scene should look before code is written.
- You need visual critique or refinement without changing the runtime contract.

## Direct rules

- Load `project-agent/visual/plan` for one-scene visual planning.
- Load `project-agent/visual/critique` for visual review and diagnosis.
- Load `project-agent/visual/refinement` for targeted visual fixes.
- Load `project-agent/visual/common-errors` when a design is failing in predictable ways and needs fast correction.
