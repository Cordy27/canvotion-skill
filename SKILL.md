---
name: canvotion
description: "Generate editable video projects and render them using code via the Canvotion CLI."
---

# Canvotion CLI Skill

## Role

- Use the Canvotion CLI to interact with Canvotion services.
- Execute only standard high-level CLI commands (e.g., `canvotion ...`).
- Do not attempt to call underlying API endpoints or internal system commands directly.
- For authoring guidelines, refer to the rule files under the `[project-agent](./project-agent)` directory (which contains guidelines for planning, visuals, coding, and 3D scenes).

## Setup

- Ensure the `canvotion` npm package is downloaded and installed:
  - Install globally: `npm install -g canvotion`
  - Or install locally in a project directory: `npm install canvotion` and run with `npx canvotion`
  - Always execute the CLI using the installed `canvotion` npm package command directly (e.g., canvotion [command] or npx canvotion [command]).
- Run `canvotion login` first to authenticate with the Canvotion service.
- The CLI credentials will be managed automatically. Do not ask the user for database or storage credentials.
- Automation environments can authenticate using `canvotion login --cli-token <token>` or by setting the `CANVOTION_CLI_TOKEN` environment variable.
- Run `canvotion capabilities --schema` before relying on specific command options or component contracts.

## Core Workflow

1. Bootstrap auth, project, and session:
   - `canvotion auth status`
   - `canvotion projects list`
   - `canvotion projects create --title "Demo" --template blank --start-session`
   - `canvotion projects use --project-id <project_id>`
   - `canvotion session start --project-id <project_id>`
   - `canvotion session status`
   - `canvotion session end`
2. Prepare or inspect workspace:
   - `canvotion workspace prepare --all`
   - `canvotion workspace list`
3. Read or update plan:
   - `canvotion plan read`
   - `canvotion plan write --stdin-json-file plan.json`
   - `canvotion plan publish`
4. Upload local images before writing canvas code:
   - `canvotion image upload --file ./cover.png --summary "cover image"`
   - Use the returned `delivery_url` in canvas code: `Image({ url: "<delivery_url>" })`.
5. Read, write, verify, and publish pages:
   - `canvotion page read --filename page-001.json`
   - `canvotion page write --filename page-001.json --stdin-file page.js`
   - `canvotion page verify --filename page-001.json`
   - `canvotion page publish --filename page-001.json --mode replace_focus`
   - `canvotion page ship --filename page-001.json --mode replace_focus --stdin-file page.js`
6. Export saved renders:
   - `canvotion render image --filename page-001.json [--time-seconds <seconds>] --output page-001.png`
   - `canvotion render video --scope slide --filename page-001.json`
   - `canvotion render video --scope slide --filename page-001.json --wait --timeout-seconds 120 --output page-001.mp4`
   - `canvotion render video --scope slide --filename page-001.json --format mov-alpha --wait --timeout-seconds 120 --output page-001.mov`
   - `canvotion render video --scope project --wait --output project.mp4`
   - `canvotion render video --scope project --format mov-alpha --wait --output project.mov`
   - `canvotion render status --task-id <task_id>`
   - `canvotion render download --task-id <task_id> --output project.mp4 [--resume] [--retries <n>]`
   - `canvotion render image` defaults to exporting the first frame; specify `--time-seconds <seconds>` to capture other timestamps.
   - `canvotion render download` keeps the `.part` file upon failure; use `--resume` to continue and `--retries` to specify retry attempts.
7. Diagnose:
   - `canvotion doctor`
   - `canvotion version`

## Canvas Contract

- Return a `Frame`.
- If you use `frame.add(...)` or `return frame`, declare it first with `const frame = new Frame({ width: 1920, height: 1080 });`. Do not rely on a global `frame`.
- `frame.add(...)` and `group.add(...)` accept only a constructed Leafer node or Leafer JSON with `tag`. Do not pass a plain config object such as `{ id, text, voice }`; for custom media like voiceovers, use constructors like `new LeaferVoiceover({ ... })`.
- Use supported constructors only: `Frame`, `Group`, `Box`, `Rect`, `Text`, `Line`, `Ellipse`, `Polygon`, `Image`, `Path`, `ManimAnimation`, `LeaferVideo`, `LeaferVoiceover`, `LeaferAudio`, `LeaferThree`, `LeaferProjection`, `LeaferProjectionFace`.
- Do not use `eval`, `Function`, `require`, dynamic `import`, `process`, `fetch`, or `XMLHttpRequest`.
- To use images, upload the local file via the CLI, and use the returned delivery_url in the canvas code. Local file paths must not appear in the final canvas code.
- Verify canvas content via the CLI verifier before publishing.

## Authoring Rule Tree

- Use `[project-agent/plan/10-outline.rule](./project-agent/plan/10-outline.rule)` for project outlines.
- Use `[project-agent/visual/](./project-agent/visual/)` rules for visual planning and refinement.
- Use `[project-agent/code/](./project-agent/code/)` rules for Frame/Leafer authoring, styles, animations, voiceovers, and asset references.
- Use `[project-agent/threejs/](./project-agent/threejs/)` rules when the canvas requires 3D scene configuration.

## Boundaries

- Render commands only export saved canvas or project data. Do not attempt to stream unsaved file content to render commands.
- Render dimensions must keep the canvas frame ratio (16:9). Pass `--width` and `--height` together.
- `render image` returns an image URL; `render video` returns a task ID and status URL by default, and only blocks/waits when `--wait` is specified.
- For transparent overlay video intended for Premiere Pro, Jianying, or After Effects, author subject-only alpha-safe scenes with no full-canvas background fills, opaque backdrops, or solid Frame fill, then request export with exactly `--format mov-alpha`.
- Image uploading supports standard file paths via `canvotion image upload --file`.
- For canvas publishing, only use continuation `none`.
- Do not attempt to use any private backend routes or internal system commands.
- Prefer `page ship` for a single operation; use `write -> verify -> publish` when iterative correction is needed.
