---
name: project-agent/code/scripted
description: Scripted preset module for bundled page patterns that should be routed directly instead of regenerated from scratch.
---

## Use this module when

- The current draft strongly matches a shipped preset pattern.
- The task is a known preset-style page and starting from scratch would be slower and less reliable.

## Direct rules

- Load `project-agent/code/scripted/free-fall-spring` for the falling block physics preset.
- Load `project-agent/code/scripted/quadric-surface-manim` for the quadric surface showcase preset.
- Load `project-agent/code/scripted/ball-follow-path` for the ball-on-path preset.
- Load `project-agent/code/scripted/typewriter-dialog` for short reply lines that appear like dialogue or typewriter subtitles.
