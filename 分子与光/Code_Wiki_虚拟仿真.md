# AetherViz Master — Code Wiki

> **项目名称**: AetherViz Master  
> **版本**: 5.0 (SVG + Three.js 融合版)  
> **许可证**: MIT  
> **核心使命**: 将任意教学主题瞬间转化为沉浸式 3D 交互教学网页  
> **项目类型**: AI Skill 定义项目（Claude Skill Prompt Template）

---

## 目录

1. [项目整体架构](#1-项目整体架构)
2. [项目目录结构](#2-项目目录结构)
3. [主要模块职责](#3-主要模块职责)
4. [关键类与函数说明](#4-关键类与函数说明)
5. [依赖关系](#5-依赖关系)
6. [项目运行方式](#6-项目运行方式)
7. [渲染模式与自动识别机制](#7-渲染模式与自动识别机制)
8. [配色与主题系统](#8-配色与主题系统)
9. [页面结构规范](#9-页面结构规范)
10. [教育功能规范](#10-教育功能规范)
11. [技术实现细节](#11-技术实现细节)
12. [更新日志](#12-更新日志)

---

## 1. 项目整体架构

### 1.1 架构概述

AetherViz Master 是一个 **AI Skill 驱动型项目**，其核心并非传统意义上的应用程序代码库，而是一套**结构化的 Prompt 模板与规范定义**。项目本身不包含可执行的业务代码，而是通过 [SKILL.md](file:///workspace/aetherviz-master/SKILL.md) 定义了一套完整的生成规范，指导 AI（如 Claude）根据用户输入的教学主题，自动生成一个**自包含的单文件 HTML 交互式教学网页**。

### 1.2 架构模式

```
┌──────────────────────────────────────────────────────────────────┐
│                      AetherViz Master 架构                       │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ┌─────────────┐     ┌──────────────────┐     ┌──────────────┐  │
│  │  用户输入    │ ──▶ │  AI Skill 引擎    │ ──▶ │  输出产物     │  │
│  │  (教学主题)  │     │  (SKILL.md 规范)  │     │  (HTML 文件)  │  │
│  └─────────────┘     └──────────────────┘     └──────────────┘  │
│                                                                  │
│  SKILL.md 规范包含:                                               │
│  ├── 配色方案定义 (CSS 变量体系)                                   │
│  ├── 技术栈与 CDN 依赖声明                                        │
│  ├── 渲染模式自动识别逻辑                                         │
│  ├── Three.js 3D 场景规范                                        │
│  ├── SVG + D3.js 2D 图表规范                                     │
│  ├── 混合渲染架构与坐标同步机制                                    │
│  ├── 页面结构布局规范                                             │
│  ├── UI 交互与动画规范                                            │
│  └── 教育功能规范                                                 │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

### 1.3 核心工作流

```
用户输入主题 → 学科自动识别 → 渲染方案检测 → 配色主题匹配 → HTML 生成 → 浏览器运行
     │              │               │                │
     │         物理/化学/       Three.js/        蓝色/橙红/
     │         生物/数学/       SVG/混合         翠绿/金黄/
     │         天文/编程                         深蓝/代码青
     ▼              ▼               ▼                ▼
  "牛顿第二定律" → 物理 → 混合模式 → 蓝色渐变 → 完整 HTML 输出
```

---

## 2. 项目目录结构

```
aetherviz-master/
├── README.md          # 项目说明文档（面向用户的使用指南）
├── LICENSE            # MIT 开源许可证
└── SKILL.md           # 核心 Skill 定义文件（AI 生成规范的完整定义）
```

### 文件说明

| 文件 | 职责 | 重要性 |
|------|------|--------|
| [SKILL.md](file:///workspace/aetherviz-master/SKILL.md) | AI Skill 核心定义文件，包含所有生成规范、配色方案、技术栈要求、渲染逻辑、页面结构等 | ⭐⭐⭐ 核心 |
| [README.md](file:///workspace/aetherviz-master/README.md) | 项目介绍、功能特性、快速开始、支持主题、技术栈、使用示例等 | ⭐⭐ 文档 |
| [LICENSE](file:///workspace/aetherviz-master/LICENSE) | MIT 许可证声明 | ⭐ 声明 |

> **注意**: 本项目不包含传统意义上的 `src/`、`dist/`、`package.json` 等目录或文件。项目的"源代码"本质上是 SKILL.md 中的 Prompt 规范，"产物"是由 AI 根据该规范动态生成的 HTML 文件。

---

## 3. 主要模块职责

虽然项目本身是 Prompt 模板而非传统代码库，但 SKILL.md 中定义了若干逻辑模块，这些模块在生成的 HTML 产物中对应具体的实现区域：

### 3.1 模块总览

| 模块 | 职责 | 对应规范章节 |
|------|------|-------------|
| **配色系统模块** | 定义 CSS 变量体系，包括主色调、背景渐变、强调色、学科主题色、玻璃拟态样式等 | 核心配色方案 |
| **渲染模式识别模块** | 根据主题关键词自动判断使用 Three.js 3D / SVG 2D / 混合渲染 | SVG + Three.js 混合渲染方案 |
| **3D 场景模块** | Three.js 场景初始化、灯光系统、材质模型、矢量可视化、粒子系统、轨迹线、物理模拟、交互增强、标签系统 | Three.js 教学模块要求 |
| **SVG 图表模块** | SVG Overlay 层创建、D3.js 数据驱动图表、函数图像、坐标系、流程图等 | SVG 适用场景 |
| **坐标同步模块** | 3D-2D 坐标实时转换与同步，响应式同步机制 | 混合渲染架构 / 响应式同步 |
| **页面布局模块** | 顶部导航栏、左侧边栏、中央主区域、控制面板、小测验面板的布局与交互 | 页面结构 |
| **教育功能模块** | 学习目标追踪、KaTeX 公式渲染、原理讲解、小测验、播放控制等 | 教育性要求 |

### 3.2 模块依赖关系图

```
┌─────────────────────────────────────────────────────┐
│                    页面布局模块                       │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐            │
│  │ 顶部导航  │ │ 左侧边栏  │ │ 控制面板  │            │
│  └──────────┘ └──────────┘ └──────────┘            │
│  ┌──────────┐ ┌──────────────────────────┐          │
│  │ 小测验面板│ │      中央主区域           │          │
│  └──────────┘ └──────────────────────────┘          │
│                      │                              │
│         ┌────────────┼────────────┐                 │
│         ▼            ▼            ▼                 │
│  ┌────────────┐ ┌─────────┐ ┌──────────┐           │
│  │ 3D场景模块  │ │坐标同步  │ │SVG图表模块│           │
│  └──────┬─────┘ └────┬────┘ └─────┬────┘           │
│         │            │            │                  │
│         └────────────┼────────────┘                  │
│                      ▼                              │
│            ┌──────────────────┐                      │
│            │ 渲染模式识别模块  │                      │
│            └────────┬─────────┘                      │
│                     ▼                               │
│            ┌──────────────────┐                      │
│            │   配色系统模块    │                      │
│            └──────────────────┘                      │
└─────────────────────────────────────────────────────┘
```

---

## 4. 关键类与函数说明

以下类与函数定义在 SKILL.md 规范中，在生成的 HTML 产物中由 AI 实现并使用：

### 4.1 渲染模式识别

#### `detectRenderMode(topic)`

- **定义位置**: [SKILL.md](file:///workspace/aetherviz-master/SKILL.md) — 渲染方案自动识别逻辑
- **功能**: 根据用户输入的主题关键词，自动判断应使用的渲染方案
- **参数**:
  - `topic` (string): 用户输入的教学主题文本
- **返回值**: `'three'` | `'svg'` | `'hybrid'`
- **识别逻辑**:

| 关键词类别 | 关键词列表 | 匹配结果 |
|-----------|-----------|---------|
| Three.js 关键词 | 运动、粒子、碰撞、旋转、天体、分子、机械、力、磁场、电场 | 纯 3D |
| SVG 关键词 | 函数、图像、曲线、图表、统计、证明、几何、坐标 | 纯 2D |
| 混合关键词 | 牛顿、运动定律、波动、振动、电磁、能量 | 混合模式 |

- **优先级**: 混合关键词 > (Three.js 关键词 && SVG 关键词) > SVG 关键词 > Three.js 关键词（默认）
- **实现代码**:

```javascript
function detectRenderMode(topic) {
    const threeKeywords = ['运动', '粒子', '碰撞', '旋转', '天体', '分子', '机械', '力', '磁场', '电场'];
    const svgKeywords = ['函数', '图像', '曲线', '图表', '统计', '证明', '几何', '坐标'];
    const hybridKeywords = ['牛顿', '运动定律', '波动', '振动', '电磁', '能量'];

    const hasThree = threeKeywords.some(k => topic.includes(k));
    const hasSVG = svgKeywords.some(k => topic.includes(k));
    const hasHybrid = hybridKeywords.some(k => topic.includes(k));

    if (hasHybrid || (hasThree && hasSVG)) return 'hybrid';
    if (hasSVG) return 'svg';
    return 'three';
}
```

### 4.2 坐标同步

#### `syncSVGto3D()`

- **定义位置**: [SKILL.md](file:///workspace/aetherviz-master/SKILL.md) — 混合渲染架构
- **功能**: 将 Three.js 3D 坐标投影到 SVG 2D 屏幕坐标，实现 3D-2D 标注位置同步
- **实现代码**:

```javascript
function syncSVGto3D() {
    const vector = new THREE.Vector3(x, y, z);
    vector.project(camera);

    const sx = (vector.x * 0.5 + 0.5) * width;
    const sy = (-(vector.y * 0.5) + 0.5) * height;

    return { x: sx, y: sy };
}
```

- **核心原理**: 使用 Three.js 的 `Vector3.project(camera)` 方法将 3D 世界坐标转换为 NDC（归一化设备坐标），再映射到屏幕像素坐标
- **调用时机**: 每帧渲染循环中、3D 相机移动时、窗口 resize 时

### 4.3 Three.js 场景核心类

以下类由 Three.js r134 提供，在生成的 HTML 中按规范配置使用：

| 类名 | 用途 | 规范配置 |
|------|------|---------|
| `THREE.Scene` | 3D 场景容器 | — |
| `THREE.PerspectiveCamera` | 透视相机 | `fov: 60, near: 0.1, far: 1000` |
| `THREE.WebGLRenderer` | WebGL 渲染器 | `antialias: true, shadowMap.enabled: true, alpha: true` |
| `THREE.HemisphereLight` | 半球环境光 | 天空色 + 地面色 |
| `THREE.DirectionalLight` | 方向光（主光源） | `castShadow: true` |
| `THREE.MeshStandardMaterial` | PBR 标准材质 | 金属度、粗糙度可调 |
| `THREE.MeshPhongMaterial` | Phong 光照材质 | 简化场景使用 |
| `THREE.ArrowHelper` | 矢量箭头可视化 | 力(红)、速度(蓝)、加速度(绿) |
| `THREE.Points` + `BufferGeometry` | 粒子系统 | 支持实时更新 position/color attribute |
| `THREE.Line` + `BufferAttribute` | 轨迹线 | 固定长度缓冲区，每帧 shift + push |
| `THREE.Raycaster` | 射线检测 | 鼠标点击 3D 物体交互 |
| `THREE.Sprite` + `CanvasTexture` | 3D 标签 | 使用 projectVector 同步 |
| `THREE.Clock` | 时间管理 | deltaTime 用于物理模拟 |
| `OrbitControls` | 轨道控制器 | 内联简化版，支持 enableDamping / touch / zoom 限制 |

### 4.4 物理模拟函数

- **积分方法**: Verlet 积分 或 Euler 方法（内联实现）
- **时间步进**: 使用 `THREE.Clock` 的 `deltaTime`
- **应用场景**: 牛顿运动定律、碰撞检测、粒子运动等

### 4.5 SVG 图表构建函数（D3.js）

| SVG 元素 | 用途 | 典型场景 |
|----------|------|---------|
| `<path>` | 函数曲线绘制 | 三角函数波形 |
| `<line>` | 坐标轴与网格线 | X/Y 轴 |
| `<rect>`, `<circle>` | 数据图表元素 | 柱状图、散点图 |
| `<marker>` | 标注箭头 | 指示方向 |
| `<g>` + `<text>` | 图例分组 | 颜色图例 |
| `<rect>` + `<path>` | 流程图 | 步骤流程 |
| `<text>` | 刻度标注 | 坐标刻度数字 |

---

## 5. 依赖关系

### 5.1 外部依赖（CDN 引入）

所有外部依赖均通过 CDN 引入，无需本地安装。生成的 HTML 文件为零依赖自包含文件。

| 依赖 | 版本 | CDN 地址 | 用途 | 是否必需 |
|------|------|---------|------|---------|
| **Three.js** | r134 | `https://cdnjs.cloudflare.com/ajax/libs/three.js/r134/three.min.js` | 3D 渲染引擎 | ✅ 必需 |
| **OrbitControls** | 内联简化版 | 内联于 HTML 中 | 3D 场景轨道控制（旋转/缩放/平移） | ✅ 必需 |
| **Tailwind CSS** | v3.4+ | `https://cdn.tailwindcss.com` | UI 样式框架 | ✅ 必需 |
| **KaTeX CSS** | 0.16.11 | `https://cdn.jsdelivr.net/npm/katex@0.16.11/dist/katex.min.css` | 数学公式样式 | ✅ 必需 |
| **KaTeX JS** | 0.16.11 | `https://cdn.jsdelivr.net/npm/katex@0.16.11/dist/katex.min.js` | 数学公式渲染引擎 | ✅ 必需 |
| **KaTeX Auto-render** | 0.16.11 | `https://cdn.jsdelivr.net/npm/katex@0.16.11/dist/contrib/auto-render.min.js` | 自动公式渲染 | ✅ 必需 |
| **D3.js** | v7 | `https://d3js.org/d3.v7.min.js` | 数据驱动 SVG 图表 | ⚡ 可选 |
| **Inter 字体** | — | 系统字体回退 | UI 字体 | ✅ 必需（系统回退） |

### 5.2 依赖关系图

```
生成的 HTML 文件
├── Three.js r134 ─────────── 3D 场景渲染
│   └── OrbitControls (内联) ── 场景交互控制
├── Tailwind CSS v3.4+ ────── UI 布局与样式
├── KaTeX 0.16.11 ─────────── 数学公式渲染
│   ├── katex.min.css ──────── 公式样式
│   ├── katex.min.js ───────── 公式引擎
│   └── auto-render.min.js ─── 自动渲染
├── D3.js v7 (可选) ────────── SVG 数据驱动图表
└── 字体: Inter + 系统回退 ──── 文字渲染
```

### 5.3 浏览器要求

- 现代浏览器：Chrome / Edge / Firefox / Safari
- 必须支持 WebGL
- 支持触控设备（触摸旋转、双指缩放）

---

## 6. 项目运行方式

### 6.1 作为 Claude Skill 使用（主要方式）

AetherViz Master 的核心使用方式是作为 **Claude Code 的 Skill** 运行：

```bash
# 1. 启动 Claude Code
claude

# 2. 输入主题（Skill 自动激活）
/aetherviz-master

# 3. 输入任意教学主题
牛顿第二定律
# 或
光合作用
# 或
勾股定理
```

系统将根据 SKILL.md 中定义的规范，自动生成完整的 HTML 文件。

### 6.2 本地静态服务（查看生成产物）

生成的 HTML 文件可通过任意静态服务器在浏览器中运行：

```bash
# 方式 1: Python
python -m http.server 8080

# 方式 2: Node.js
npx serve .

# 方式 3: PHP
php -S localhost:8080
```

访问 `http://localhost:8080` 即可查看交互式教学页面。

### 6.3 直接打开

由于生成的 HTML 文件是零依赖自包含文件，也可以直接双击用浏览器打开（但部分 CDN 资源需要网络连接）。

---

## 7. 渲染模式与自动识别机制

### 7.1 三种渲染模式

| 模式 | 适用场景 | 技术实现 | 示例主题 |
|------|---------|---------|---------|
| **Three.js 纯 3D** | 需要空间感、立体结构的主题 | WebGL 渲染器 + 3D 场景 | 分子结构、机械运动、天体运动、粒子碰撞 |
| **SVG 2D** | 2D 图表、函数图像、几何证明 | SVG Overlay + D3.js | 函数曲线、统计图、勾股定理、三角函数 |
| **混合模式** | 既有 3D 对象又有数据图表 | Three.js 底层 + SVG 顶层 + 坐标同步 | 牛顿定律、波动振动、电磁场、能量转换 |

### 7.2 混合渲染架构

```
┌─────────────────────────────────────────┐
│          SVG Overlay (顶层)              │  ← 透明背景, pointer-events:none
│  函数图像 / 坐标轴 / 标注 / 图表         │
├─────────────────────────────────────────┤
│          Three.js 3D 场景 (底层)         │  ← WebGL 渲染, alpha:true
│  3D 模型 / 粒子 / 矢量箭头 / 轨迹        │
└─────────────────────────────────────────┘
              ↕ 坐标同步 (projectVector)
```

### 7.3 响应式同步机制

| 触发源 | 同步行为 |
|--------|---------|
| 滑块控制 | 同时更新 Three.js 对象属性 + SVG 路径/d 属性 |
| 3D 相机移动 | SVG 标注位置实时跟随（使用 projectVector） |
| 窗口 resize | 同步更新 SVG viewBox 和 Three.js renderer |

---

## 8. 配色与主题系统

### 8.1 学科主题色映射

| 学科 | 渐变色 | CSS 变量 |
|------|--------|---------|
| 物理 | 蓝色渐变 `#3B82F6 → #0EA5E9` | `--theme-physics` |
| 化学 | 橙红渐变 `#F59E0B → #EF4444` | `--theme-chemistry` |
| 生物 | 翠绿渐变 `#10B981 → #22D3EE` | `--theme-biology` |
| 数学 | 金黄渐变 `#F59E0B → #EAB308` | `--theme-math` |
| 天文 | 深蓝渐变 `#1E40AF → #3B82F6` | `--theme-astronomy` |
| 编程 | 代码青渐变 `#22C55E → #14B8A6` | `--theme-programming` |

### 8.2 核心设计系统

- **主色调**: 青绿到天蓝渐变 (`#14B8A6 → #06B6D4 → #22D3EE`)
- **背景**: 深海科技感 (`#0F172A → #164E63 → #155E75`)
- **强调色**: 霓虹质感 — Cyan / Emerald / Amber / Rose / Orange
- **玻璃拟态**: 半透明背景 + 模糊边框 + 阴影
- **文字**: 主色 `#F8FAFC` / 次色 `#CBD5E1` / 弱色 `#94A3B8`

### 8.3 矢量颜色约定

| 物理量 | 颜色 | 色值 |
|--------|------|------|
| 力 | 红色 | `#EF4444` |
| 速度 | 蓝色 | `#3B82F6` |
| 加速度 | 绿色 | `#22C55E` |

---

## 9. 页面结构规范

生成的 HTML 页面遵循以下固定布局结构：

```
┌──────────────────────────────────────────────────────────┐
│  顶部导航栏                                               │
│  [主题名称(中英文)]                    [重置][随机][全屏][关于] │
├──────────────┬───────────────────────────────────────────┤
│  左侧边栏     │  中央主区域                                 │
│  (30%,可折叠) │                                           │
│              │  ┌─────────────────────────────────────┐  │
│  □ 学习目标   │  │                                     │  │
│              │  │     Three.js 3D 画布 / SVG 图表       │  │
│  核心公式     │  │     (全响应式)                        │  │
│  (KaTeX)     │  │                                     │  │
│              │  └─────────────────────────────────────┘  │
│  原理讲解     │                                           │
│              │  ┌─────────────────┐ ┌─────────────────┐  │
│  为什么重要   │  │  控制面板        │ │  小测验面板      │  │
│  真实应用     │  │  (玻璃拟态)      │ │  (可折叠)        │  │
│  扩展阅读     │  │  滑块/播放控制   │ │  360px/380px    │  │
│              │  └─────────────────┘ └─────────────────┘  │
└──────────────┴───────────────────────────────────────────┘
```

### 9.1 各区域详细规范

| 区域 | 宽度 | 关键特性 |
|------|------|---------|
| 顶部导航栏 | 100% | 背景 `--nav-bg`，底部边框 `--nav-border`，右侧功能按钮 |
| 左侧边栏 | 30%，可折叠 | 学习目标(复选框)、KaTeX 公式、原理讲解、应用与扩展 |
| 中央主区域 | 70% | Three.js 3D 画布，背景 `--bg-gradient`，全响应式 |
| 控制面板 | — | 玻璃拟态风格，实时滑块 + 数值显示，KaTeX 计算结果，播放/暂停/单步/速度 |
| 小测验面板 | 360px 宽，380px 高 | 可折叠设计，展开/收起动画 `transition: all 0.3s ease`，收起后显示右下角悬浮按钮 |

---

## 10. 教育功能规范

### 10.1 功能清单

| 功能 | 描述 | 实现方式 |
|------|------|---------|
| 学习目标 | 3-4 条可勾选追踪的学习目标 | HTML 复选框 |
| 数学公式 | 多行对齐的数学公式实时渲染 | KaTeX auto-render |
| 原理讲解 | 生动比喻，高中-大学水平文字 | 侧边栏文本区域 |
| 小测验 | 可折叠测验面板，带隐藏/展开切换 | DOM + CSS transition |
| 播放控制 | 播放/暂停/单步/速度倍率 | JavaScript 动画控制 |
| 重置 | 恢复到初始状态 | 按钮触发 |
| 随机实验 | 随机参数组合实验 | 按钮触发 |
| 语言适配 | 自动检测中文/英文主题 | 关键词检测 |

### 10.2 交互反馈

- 滑块移动 → 3D 物体变化 + 矢量箭头同步伸缩 + SVG HUD 更新
- 点击 3D 物体 → 高亮 + 侧边栏弹出公式推导
- 触控设备 → 触摸旋转、双指缩放、长按物体显示提示
- Toast 提示 + 高亮解释 + 3D 高光

---

## 11. 技术实现细节

### 11.1 Three.js 场景初始化规范

```javascript
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(60, width / height, 0.1, 1000);
const renderer = new THREE.WebGLRenderer({
    antialias: true,
    shadowMap: { enabled: true },
    alpha: true
});
```

### 11.2 SVG Overlay 创建规范

```javascript
const svgContainer = document.createElement('div');
svgContainer.style.cssText = 'position:absolute;top:0;left:0;width:100%;height:100%;pointer-events:none;';
document.getElementById('canvas-container').appendChild(svgContainer);

const svg = d3.select(svgContainer).append('svg')
    .attr('width', '100%')
    .attr('height', '100%');
```

### 11.3 OrbitControls 内联规范

- 必须内联完整简化版代码（不通过 CDN 引入）
- 必须包含 `enableDamping` 支持
- 必须支持 touch 操作
- 必须支持 zoom 限制

### 11.4 物理模拟规范

- 使用 Verlet 积分或 Euler 方法
- 使用 `THREE.Clock.deltaTime` 作为时间步长
- 粒子系统通过 `BufferGeometry` + `PointsMaterial` 实现
- 轨迹线使用固定长度缓冲区，每帧 shift 并 push 新点

### 11.5 输出规则

1. **只能**输出一个完整的 HTML 文件
2. 从 `<!DOCTYPE html>` 开始，到 `</html>` 结束
3. **绝不添加任何解释、说明、markdown、代码块**
4. HTML 必须**零依赖外部文件**（CDN 资源除外）
5. 可直接保存为 `lesson.html` 并用浏览器打开
6. 支持手机触控

---

## 12. 更新日志

| 版本 | 日期 | 变更内容 |
|------|------|---------|
| v5.0 | 2026-02-22 | 新增 SVG + Three.js 混合渲染；新增渲染方案自动识别；新增 D3.js 支持；优化坐标同步机制 |
| v4.0 | 2026-02-22 | 优化面板布局；小测验面板可折叠；新增右下角悬浮按钮 |

---

## 附录：支持的主题领域

| 学科 | 示例主题 |
|------|---------|
| 物理 | 牛顿第二定律、匀速运动/匀变速运动、电磁感应、相对论时间膨胀、量子隧穿效应 |
| 化学 | 光合作用、酸碱中和、氧化还原反应、分子结构 |
| 生物 | DNA 复制、细胞呼吸、有丝分裂、遗传规律 |
| 数学 | 勾股定理、三角函数、正弦函数图像、概率分布 |
| 天文 | 行星运动定律、宇宙膨胀、黑洞、日食月食 |
| 编程 | 算法复杂度、数据结构、排序算法、设计模式 |

---

*本文档由 AetherViz Master Code Wiki 生成器自动创建*
