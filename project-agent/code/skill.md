---
name: project-agent/code
description: 包含官方 Leafer 基础实现模块，以及独立的项目专属媒体、资产、发布和预设路由。
---

## 触发本模块的场景

- 任务需要生成实际的幻灯片代码、进行工作区编辑、执行验证或发布决策时。
- 当你需要基础 Leafer 代码约定、定位规则、视觉样式规则、动画和运动规则，或任何一个项目专属的交付规则时。

## 核心 Leafer 规则

以下四个官方 Leafer 规则是普通元素编写的主要知识库。当讨论相同的画布、布局、样式或动画主题时，请优先使用它们，而不是其他旧的重叠表述。

- 当需要创建根 `Frame`、基础 Leafer 元素、文本、容器，或安全地使用 `Image({ url })` 时，请加载 `project-agent/code/canvas-and-elements`。
- 当需要精确定位元素、声明尺寸、应用变换、控制锚点/原点、组合组件层级或渲染边界时，请加载 `project-agent/code/layout-and-transform`。
- 当需要定义填充、描边、渐变、阴影、遮罩、橡皮擦、混合模式、透明度、透明背景留空或文本背景框时，请加载 `project-agent/code/visual-style`。
- 当需要视频或多媒体页面、播放器式缩略图、播放按钮和进度条表达时，请加载 `project-agent/code/video`。
- 当需要编写 `animation`、生命周期关键帧、延迟、运动路径、描边生长、数字滚动、打字机文本效果、续写动画追加，或 `triggerAtWord` 时，请加载 `project-agent/code/animation-and-motion`。

## 独立项目专属规则

- 当需要原生 `ManimAnimation` / `manim_code` 集成时，请加载 `project-agent/code/manim`。
- 当任务需要使用原生 Leafer 元素制作卡片翻转、PPT 页面倾斜、立方体面板或简单的摄像机推拉效果时，请加载 `project-agent/code/projection`。
- 当需要 `LeaferVoiceover`、旁白时间轴控制、TTS 创作字段或由单词触发的动画计时机制时，请加载 `project-agent/code/voiceover`。
- 当任务使用用户提供的本地图片文件、已有项目 `delivery_url`、项目资产上传、图标系统、解释性图片或自定义象形图时，请加载 `project-agent/code/image-assets`。
- 在执行任何将保存工作区文件、验证、发布或续写现有幻灯片操作的代码编写步骤之前，请加载 `project-agent/code/workspace-publish`。
- 当需要使用已交付的预设风格路由（例如自由落体、二次曲面、小球沿路径跟随，或打字机回复场景）时，请加载 `project-agent/code/scripted`。
