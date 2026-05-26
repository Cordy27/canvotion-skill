---
name: project-agent/plan
description: Planning module for outlines, scene decomposition, and project-level structure decisions.
---

## Use this module when

- The user is asking for a plan, outline, scene ordering, or narrative structure.
- This is the first user request for a new animation or deck, and the user did not explicitly ask you to skip planning and implement directly.
- You need to decide how a multi-page idea should be broken into scenes before implementation.
- The request is unclear enough that implementation would require guessing product, audience, style, timing, or scene structure.

## Direct rules

- Load `project-agent/plan/outline` when you need the concrete outline contract for multi-step planning.
- For the first user requirement in a new animation/deck task, enter this module first and then load `project-agent/plan/outline`.
- If the requirement is unclear, ask concise clarification questions before writing a plan.
- Unless the user explicitly asks to implement directly, do not enter code-writing modules until the project outline/plan has been approved by the user.
- Project outlines are stored in the project-level `animation_outline` plan, not in chat text and not in a normal page. In the external CLI profile, use `canvotion plan write --stdin-json-file <plan.json>` and `canvotion plan publish`; do not create `page-001` as an outline table.
