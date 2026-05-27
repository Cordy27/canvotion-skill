  # 🎨 Canvotion-Skill (Canvas + Motion)

<div align="center">
  <img src="https://img.shields.io/badge/CLI-Canvotion-007FFF?style=flat-square&logo=npm" alt="NPM CLI">
  <img src="https://img.shields.io/badge/2D_Engine-LeaferJS-32cd79?style=flat-square&logo=javascript" alt="LeaferJS">
  <img src="https://img.shields.io/badge/3D_Engine-Three.js-000000?style=flat-square&logo=three.js" alt="Three.js">
  <img src="https://img.shields.io/badge/AI_Agent-Prompt_Engineering-6366f1?style=flat-square" alt="AI Agent">
</div>

<br>

**Canvotion-Skill** 是一个专为 AI Agent 打造的高级视觉与视频工程指令库。

通过结合 **Canvotion CLI** 与经过调优的 System Rules，它能赋予大语言模型制作图形与动画的能力。只需输入自然语言，即可在 Web 环境中自动编写、验证并渲染出商业发布会级别的 2D 动态影像 (LeaferJS) 与 3D 交互场景 (Three.js)。

---

## 🎞️ 效果展示

> 💡 **Tip:** 以下动画由 AI Agent 根据本项目的 Rule 规则，输出纯 JavaScript 代码并在浏览器中渲染生成。

<table align="center" style="border: none;">
  <tr>
    <td width="50%" align="center" style="border: none;">
      <video src="https://github.com/user-attachments/assets/47be7b20-40e3-43d9-b650-faeeefc657e1" width="100%" controls autoplay loop muted></video>
      <br>
    </td>
    <td width="50%" align="center" style="border: none;">
      <video src="https://github.com/user-attachments/assets/3f61c581-3d14-4f30-b998-414d71e3c147" width="100%" controls autoplay loop muted></video>
      <br>
    </td>
  </tr>
</table>

<table align="center" style="border: none;">
  <tr>
    <td width="50%" align="center" style="border: none;">
      <video src="https://github.com/user-attachments/assets/fdc81706-c939-46cb-a4e6-7b3a6ee17225" width="100%" controls autoplay loop muted></video>
      <br>
    </td>
    <td width="50%" align="center" style="border: none;">
      <video src="https://github.com/user-attachments/assets/fd646082-e985-42b9-8620-6d872c7419b5" width="100%" controls autoplay loop muted></video>
      <br>
    </td>
  </tr>
</table>


---

## 🌟 核心特性

* 🛠️ **全链路 CLI 驱动**：配套 `canvotion` npm 命令行工具，提供从工作区搭建、代码编写、安全校验到视频/透明通道导出的全自动化 API。
* 📐 **2D/3D 双引擎**：
  * **2D 视觉 (LeaferJS)**：严格的空间纪律、非线性极速缓动、SVG 轨迹运动、拟真光影。
  * **3D 世界 (Three.js)**：从基础网格构建，到高级物理材质、光照系统与 Shader 后处理。
* 🎙️ **多模态时间轴**：内建声画同步逻辑，支持 `Voiceover` 旁白触发、媒体播放（视频/图片资产）以及 Manim 数学动画的无缝嵌入。

---

## 📁 核心架构

Canvotion-Skill 将大模型的认知过程拆解为 4 个层级的 `Rules`：

```text
canvotion-skill/
├── manifest.json              # ⚙️ 技能元数据与 Schema 版本配置
├── SKILL.md                   # 🔌 Canvotion CLI 核心交互约定与系统边界
└── references/
    └── authoring/             # 🧠 喂给 LLM 的 authoring reference tree
        ├── plan/              # 📝 视频结构大纲与脚本规划
        ├── visual/            # 👁️ 视觉排版、自我审查与美学纠错
        ├── code/              # 💻 2D 图元、样式、动画、媒体、旁白与资源管理
        └── threejs/           # 🧊 3D 场景、材质、光照、着色器与后期处理
```

## 🚀 快速开始

### 1. 环境准备
你需要安装 Node.js 并全局安装 Canvotion CLI：

```bash
npm install -g canvotion
```
### 2. 身份认证与项目创建
登录 Canvotion 服务并初始化一个空白工作区：

```Bash
canvotion login
canvotion projects create --title "My First AI Video" --template blank --start-session
canvotion session start --project-id <your_project_id>
```
### 3. Agent 驱动流
将本仓库 SKILL.md 及 references/authoring/ 下相关的 .rule 注入给你的 AI Agent 系统提示词中，Agent 即可学会如何使用 CLI 读写代码并发布：

```Bash
# Agent 生成并覆盖写入画布代码
canvotion page write --filename page-001.json --stdin-file page.js

# Agent 执行严格的语法与视觉规范审查
canvotion page verify --filename page-001.json
```
### 4. 一键渲染与视频导出
代码发布后，通过 CLI 直接唤起云端引擎渲染出片：

```Bash
# 渲染为带 Alpha 透明通道的 MOV 视频（方便导入 PR/AE/剪映）
canvotion render video --scope slide --filename page-001.json --format mov-alpha --wait --output final.mov
```


## 🤝 参与贡献
我们欢迎任何形式的贡献！
如果你发现了会导致渲染报错的幻觉代码，请在 Issues 中提交。
如果你调试出了更惊艳的 2D/3D 视觉配方（如：高级 Shader、水波纹模拟、拟真设备框），欢迎将它们整理为新的 .rule 或 scripted 模板提交 PR。

## 📜 许可证
本项目基于 MIT License 开源。
