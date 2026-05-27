---
name: references/authoring
description: Root navigation module for Canvotion authoring references. Use it to route into plan, visual, code, and threejs child modules.
---

## Role

- Stay responsible for the whole project by default, while honoring `focus_page` when the current request is about one page or one draft.
- Act as the root navigation layer only. This module should help you choose the next child module, not replace the runtime system instruction.

## Child Module Routing

- Use `references/authoring/plan` for outline design, storyboard planning, scene breakdown, and story structure.
- Use `references/authoring/visual` for scene composition, visual critique, refinement, and common visual failure patterns.
- Use `references/authoring/code` for Leafer implementation rules covering canvas/elements, layout/transform, visual style, animation/motion, media, assets, workspace publish, and preset routing.
- Use `references/authoring/threejs` for `LeaferThree`, `scene_spec`, `three_timeline`, cameras, lights, materials, model loaders, shaders, and interaction.

## Focused Routing Hints

- 当用户明确要求先做大纲/计划，或当前请求很简短、范围很宽而你判断需要先拆结构时，可以先进入 `references/authoring/plan`，再加载 `references/authoring/plan/outline`。是否进入大纲模式由你结合上下文自行判断。
- 当前焦点页续写或直接实现页面时，先加载 `references/authoring/code`，再按需要读取具体规则。
- 创建根画布、基础图元、容器、文本或安全图片引用时，读取 `references/authoring/code/canvas-and-elements`。
- 处理坐标、尺寸、缩放、旋转、镜像、锚点、层级或渲染边界时，读取 `references/authoring/code/layout-and-transform`。
- 处理颜色、渐变、描边、光影、遮罩、擦除、混合模式、透明背景留空或文字背景框时，读取 `references/authoring/code/visual-style`。
- 处理视频或多媒体页面、播放器缩略图、播放按钮或进度条表达时，读取 `references/authoring/code/video`。
- 处理入场/出场、关键帧、延迟、多步运动、轨迹路径、描边生长、数字滚动或打字机文字效果时，读取 `references/authoring/code/animation-and-motion`。
- 保存、验证、发布或续写现有 page 前，读取 `references/authoring/code/workspace-publish`。
- 如果任务需要使用用户提供的本地图片文件、已有项目 `delivery_url`、真实照片/插画/图标或图片资产，读取 `references/authoring/code/image-assets`；真正写入 Leafer `Image({ url })` 时，使用 `references/authoring/code/canvas-and-elements` 里的 `delivery_url` 合同。
- 如果任务需要 native Manim，读取 `references/authoring/code/manim`；如果需要旁白或按词触发动画，读取 `references/authoring/code/voiceover`；如果需要原生 Leafer 2.5D 翻转/页面倾斜/立方体面板，读取 `references/authoring/code/projection`。
- 如果当前 draft 强匹配已随镜像提供的 preset 页面，读取 `references/authoring/code/scripted`，再进入对应 preset 规则。
- 如果任务涉及 `LeaferThree` 或 3D 页面，先加载 `references/authoring/threejs`，再按需要读取具体规则。

## Three.js routing

- 当任务涉及 `LeaferThree`、`scene_spec`、`three_timeline`、Three.js 相机（例如 `PerspectiveCamera`）、几何体、材质、灯光、纹理、模型加载、shader、postprocessing、键控动画 keys 或交互时，先读取 `references/authoring/threejs`，再按需要继续读取具体规则。
- 如果任务是给当前项目页面生成或续写 3D 内容，先读取 `references/authoring/threejs/leaferthree-bridge`，再补充读取相关主题规则，例如 `references/authoring/threejs/fundamentals`、`references/authoring/threejs/lighting`、`references/authoring/threejs/animation`。

## Boundaries
- 绝对不得导入和使用skill没提到的任何模块或引入依赖。
- 这个 root module 只负责导航，不应该塞每轮都必须存在的 runtime 规则。
- 在真正使用某个专题合同前，先下钻到对应 child module 或 rule，再按其细则执行。
