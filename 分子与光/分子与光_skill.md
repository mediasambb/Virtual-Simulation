# 分子与光 — 虚拟仿真实验 Skill 文档

## 项目概述

「分子与光」是基于 AetherViz Master 框架开发的大学物理虚拟仿真实验，演示分子固有频率与光子共振吸收/发射的完整物理过程。

**最终版本**: v6.0 | **完成日期**: 2026-05-13

> **致谢**：本项目基于开源框架 [AetherViz Master](https://github.com/andyhuo520/aetherviz-master) 开发，感谢原作者 Andy Huo 的贡献。本项目在框架基础上独立实现了物理仿真逻辑、分子建模、UI 交互等核心功能。

---

## 技术架构

| 组件 | 技术 | 版本 | 来源 |
|------|------|------|------|
| 3D 引擎 | Three.js | r134 | CDN |
| 相机控制 | OrbitControls | 内联版 | CDN |
| UI 框架 | Tailwind CSS | v3.4+ | CDN |
| 公式渲染 | KaTeX | 0.16.11 | CDN |
| 架构模式 | 单文件 HTML | 自包含 (728行) | — |

**无本地构建依赖，直接浏览器打开即可运行。**

---

## 模块参数提示词

### 1. 分子数据模块 (MOLECULES)

**定义位置**: `const MOLECULES` (第 235-266 行)

**数据结构**:
```javascript
MOLECULES = {
  KEY: {
    name: '中文名',
    formula: '化学式',
    freq: 固有频率(THz),        // 内部使用 THz，显示转换为科学计数法 Hz
    band: '波段',
    atoms: [
      {el:'元素符号', r:半径, color:十六进制颜色, x,y,z:坐标},
      ...
    ],
    bonds: [[原子索引1, 原子索引2], ...]
  }
}
```

**8 个分子完整参数**:

| 键 | 名称 | 化学式 | f₀ (THz) | f₀ (Hz) | 波段 | 原子数 |
|----|------|--------|----------|---------|------|--------|
| CO | 一氧化碳 | CO | 64.0 | 6.4×10¹³ | 远红外 | 2 |
| N2 | 氮气 | N₂ | 70.0 | 7.0×10¹³ | 远红外 | 2 |
| O2 | 氧气 | O₂ | 47.0 | 4.7×10¹³ | 远红外 | 2 |
| CO2 | 二氧化碳 | CO₂ | 20.0 | 2.0×10¹³ | 远红外 | 3 |
| CH4 | 甲烷 | CH₄ | 91.0 | 9.1×10¹³ | 远红外 | 5 |
| H2O | 水 | H₂O | 550.0 | 5.5×10¹⁴ | 远红外 | 3 |
| NO2 | 二氧化氮 | NO₂ | 48.0 | 4.8×10¹³ | 远红外 | 3 |
| O3 | 臭氧 | O₃ | 31.5 | 3.15×10¹³ | 远红外/微波 | 3 |

**原子颜色编码**:
- 碳 C: `0x333333` (深灰)
- 氧 O: `0xcc3333` (红色)
- 氮 N: `0x3344cc` / `0x4444cc` (蓝色)
- 氢 H: `0xeeeeff` (浅白)

**原子半径参考**: C:0.38, N:0.36, O:0.35, H:0.25-0.28

**新增分子步骤**:
1. 在 `MOLECULES` 对象中添加新键值对
2. 定义 `name`, `formula`, `freq`(THz), `band`
3. 定义 `atoms[]` 数组（元素、半径、颜色、3D坐标）
4. 定义 `bonds[]` 数组（原子索引对）
5. 在 `MOLECULE_ORDER` 数组中添加新键
6. 在 HTML 中添加对应的按钮（光频选择 + 选择分子）

---

### 2. 相机配置模块 (Camera)

**初始化参数**:
```javascript
camera = new THREE.PerspectiveCamera(55, aspect, 0.1, 1000);
camera.position.set(5, 3, 6);      // 右上方角度，同时观察光源和分子
controls.target.set(0, 0, 0);       // 聚焦分子中心
controls.enableDamping = true;
controls.dampingFactor = 0.08;
controls.minDistance = 3;
controls.maxDistance = 20;
controls.maxPolarAngle = Math.PI * 0.85;
```

**设计要点**:
- 位置 (5,3,6): 右上方视角，确保光源(x=-6.5)和分子(x=0)同时可见
- FOV 55°: 标准广角
- 阻尼 0.08: 平滑跟随
- 最大仰角限制: 防止观察到底面

---

### 3. 光照配置模块 (Lighting)

```javascript
// 半球光 - 基础环境
new THREE.HemisphereLight(0x4488bb, 0x002244, 0.6);

// 方向光 - 主光源 + 阴影
const dir = new THREE.DirectionalLight(0xffffff, 0.8);
dir.position.set(5, 8, 5);
dir.castShadow = true;

// 环境光 - 暗部填充
new THREE.AmbientLight(0x223344, 0.3);
```

---

### 4. 光源设备模块 (Light Source - 银色手电筒)

**位置**: `CONFIG.lightSourceX = -6.5`

**结构组成**:
| 部件 | 几何体 | 材质参数 | 位置 |
|------|--------|---------|------|
| 主体 | `CylinderGeometry(.22,.28,.6,16)` | `color:0xC0C0C0, metalness:.9, roughness:.15` | x=-.1 |
| 灯头 | `ConeGeometry(.32,.3,16,1,true)` | 同主体材质 | x=.45 |
| 尾盖 | `CylinderGeometry(.24,.24,.08,16)` | `color:0x808080, metalness:.7` | x=-.44 |
| 防滑环 ×3 | `TorusGeometry(.23,.02,8,16)` | `color:0x909090, metalness:.8` | x=-.2~.04 |
| 镜片 | `CircleGeometry(.28,32)` | `color:0xFFFFFF, emissive:0x22D3EE, opacity:.6` | x=.58 |
| 发光体 | `PointLight(0x22D3EE, 1.5, 6)` | — | x=.6 |

**频率颜色联动**: `lightSourceMesh.material.color/emissive/lightSourceGlow.color` 随入射光频率动态变化

---

### 5. 光子物理模块 (Photon Physics)

**发射参数**:
```javascript
photonSpeed: 3.5,                    // 光子运动速度
absorptionThreshold: f₀ * 0.02,      // 吸收阈值（2% 容差）
emitInterval: 1.8,                   // 连续发射间隔（秒）
```

**光子生命周期**:
1. `traveling`: 从光源出发，向分子运动
2. `absorbing`: 碰撞后缩小消失（0.35s 过渡）
3. `emitted`: 分子发射的光子，从中心随机方向扩散

**碰撞检测**: 光子距分子中心 < 0.6 时触发频率匹配判断
- `|f_incident - f_natural| ≤ Δf_threshold` → 共振吸收
- 否则 → 光子穿透

**光子球体**: `SphereGeometry(.15,16,16)` + `MeshBasicMaterial` + `PointLight`

---

### 6. 分子振动模块 (Vibration)

**阻尼谐振公式**:
```
amplitude = A₀ × e^(-decay × t) × sin(frequency × t)
```

**参数**:
| 参数 | 值 | 说明 |
|------|-----|------|
| `vibrationDuration` | 2.8s | 振动持续时间 |
| `vibrationVisualFreq` | 10/8 Hz | 视觉振动频率（大分子降为8） |
| `vibrationAmplitude` | 0.35/0.25 | 振动幅度（大分子降为0.25） |
| `vibrationDecay` | 1.2 | 衰减系数 |

**视觉反馈**:
- 原子沿键方向振荡
- 自发光强度随振动幅度变化
- 绿色共振环 (resonanceRing) 闪烁
- 键长实时伸缩

**状态机**:
```
IDLE ──吸收──> ABSORBING ──(0.35s)──> VIBRATING ──(2.8s)──> EMITTING ─(0.3s)──> IDLE
```

---

### 7. 频率-颜色映射模块 (Color Mapping)

**转换链**: 频率(THz) → 波长(nm) → RGB → THREE.Color

**公式**: `λ(nm) = 299792.458 / f(THz)`

**可见光范围**: 380-780nm

**波段映射**:
| 波段 | 波长范围 | 颜色范围 |
|------|----------|----------|
| 紫 | 380-440 | 紫色→蓝色 |
| 蓝 | 440-490 | 蓝色→青 |
| 青绿 | 490-510 | 青色→绿色 |
| 绿 | 510-580 | 绿色→黄绿 |
| 黄橙 | 580-645 | 黄色→橙→红 |
| 红 | 645-780 | 红色 |
| 不可见红外 | >780 | 暗红色 factor=0.3 |
| 不可见紫外 | <380 | 紫色 factor=0.35 |

**科学计数法转换**:
```javascript
function formatFreqHz(fTHz) {
  const hz = fTHz * 1e12;
  let exp = Math.floor(Math.log10(hz));
  let mantissa = hz / Math.pow(10, exp);
  // 上标映射: ⁰¹²³⁴⁵⁶⁷⁸⁹
  return mantissa.toFixed(2) + '×10^' + exp + ' Hz';
}
```

---

### 8. UI 布局模块 (Control Panel)

**HTML 结构**:
```
── 导航栏 (nav, 44px) - 标题 + 全屏/关于按钮
├── 主区域 (main-area)
│   ├── 侧边栏 (sidebar, 300px) - 可折叠
│   │   ├── 知识原理
│   │   ├── 学习目标 (4项checkbox)
│   │   ├── 核心公式 (KaTeX渲染，白色)
│   │   └── 实时参数 (5行状态)
│   └── 3D场景 (scene-wrap)
├── 控制面板 (ctrl-area, 3行)
│   ├── 行1: [入射光频 56px] [滑块 320px] [数值 78px] [光频选择 52px] [8按钮×78px]
│   ├── 行2: [分子缩放 56px] [滑块 320px] [数值 78px] [选择分子 52px] [8按钮×78px]
│   └── 行3: [发射光子] [重置] [随机频率] [随机分子] [连续发射] [正常/慢速] [显示光谱]
└── 光谱弹层 (spectrum-overlay)
```

**按钮样式参数**:
```css
.btn-mol-freq, .btn-mol-sel {
  padding: 3px 4px;
  width: 78px;              /* 固定宽度，两行按钮完全一致 */
  font-size: 9px;
  text-align: center;
  overflow: hidden;
  text-overflow: ellipsis;
}

.ctrl-label { min-width: 60px; }     /* 滑块标签 */
.ctrl-label[inline] { min-width: 52px; }  /* 光频选择/选择分子标签 */
.ctrl-label[left] { min-width: 56px; }    /* 入射光频/分子缩放标签 */

input[type=range] { flex:0 0 320px; min-width:320px; }  /* 滑块固定宽度 */
.ctrl-value-inline { min-width:78px; margin-left:4px; } /* 数值显示 */
```

**按钮对齐**:
- 光频选择 8 个按钮 ↔ 选择分子 8 个按钮 → 固定宽 `78px`，逐一对齐
- 「光频选择」文字 ↔ 「选择分子」文字 → 标签宽 `min-width:52px`
- 入射光频滑块 ↔ 分子缩放滑块 → 固定宽 `320px`
- THz 数值 ↔ x 倍率数值 → 宽 `min-width:78px`

**响应式布局**:
```css
@media screen and (orientation:portrait) {
  .freq-btn-group, .mol-btn-group {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    justify-items: end;
  }
}
```

---

### 9. 场景装饰模块 (Scene)

```javascript
// 网格地面
grid = new THREE.GridHelper(20, 40, 0x1a3a4a, 0x0d2530);
grid.position.y = -1.5;
grid.material.opacity = 0.3;

// 光束虚线
beamLine = new THREE.Line(..., new THREE.LineDashedMaterial({
  color: 0x22D3EE, opacity: 0.15, dashSize: 0.2, gapSize: 0.15
}));

// 共振环（吸收时显示）
resonanceRing = new THREE.Mesh(new THREE.RingGeometry(1.4, 1.5, 64),
  new THREE.MeshBasicMaterial({color: 0x22C55E, opacity: 0, side: DoubleSide}));
```

**注意**: 背景星空粒子已移除（避免灰色像素块干扰）

---

### 10. 交互事件模块 (Events)

| 控件 | 事件 | 功能 |
|------|------|------|
| 频率滑块 | `input` | 实时更新入射光频率 |
| 分子缩放滑块 | `input` | 实时更新分子缩放倍率(0.5-3.0x) |
| 光频选择按钮 | `click` | 设置频率 + 高亮 + 自动发射 |
| 选择分子按钮 | `click` | 切换分子结构 + 更新参数 |
| 发射光子按钮 | `click` | 切换连续发射状态(发射光子↔暂停发射) |
| 重置按钮 | `click` | 清除所有光子，恢复初始状态 |
| 随机频率按钮 | `click` | 200-900 THz 随机频率 |
| 随机分子按钮 | `click` | 随机切换分子 |
| 连续发射开关 | `click` | 切换自动发射模式 |
| 速度单选 | `change` | 正常(1x) / 慢速(0.3x) |
| 显示光谱按钮 | `click` | 弹出电磁波谱覆盖层 |
| 键盘 Space | `keydown` | 发射单个光子 |
| 键盘 R | `keydown` | 重置实验 |
| 窗口 resize | `resize` | 自适应相机和渲染器 |

---

## 配置参数速查表

| 参数名 | 默认值 | 可调范围 | 说明 |
|--------|--------|----------|------|
| `CONFIG.moleculeNaturalFreq` | 550 THz | 20-550 | 当前分子固有频率 |
| `CONFIG.absorptionThreshold` | 12 THz | 动态(2%容差) | 共振吸收阈值 |
| `CONFIG.photonSpeed` | 3.5 | 1-10 | 光子运动速度 |
| `CONFIG.vibrationDuration` | 2.8s | 1-5 | 振动持续时间 |
| `CONFIG.vibrationAmplitude` | 0.35 | 0.1-0.5 | 振动幅度 |
| `CONFIG.vibrationDecay` | 1.2 | 0.5-3.0 | 衰减系数 |
| `CONFIG.lightSourceX` | -6.5 | -10~-3 | 光源X坐标 |
| `CONFIG.emitInterval` | 1.8s | 0.5-5 | 连续发射间隔 |
| `CONFIG.timeScale` | 1.0 | 0.1-3.0 | 时间缩放 |
| `camera.position` | (5,3,6) | 自定义 | 相机位置 |
| `controls.dampingFactor` | 0.08 | 0.01-0.2 | 控制阻尼 |

---

## 开发指南

### 新增分子
1. 在 `MOLECULES` 对象中添加新键值对
2. 定义 `name`, `formula`, `freq`(THz), `band`
3. 定义 `atoms[]` 数组（元素、半径、颜色、3D坐标）
4. 定义 `bonds[]` 数组（原子索引对）
5. 在 `MOLECULE_ORDER` 数组中添加新键
6. 在 HTML 中添加对应的按钮（光频选择 + 选择分子）

### 修改配色主题
编辑 `:root` CSS 变量:
```css
:root {
  --bg: #C8D8E8;          /* 背景色 */
  --accent-cyan: #22D3EE; /* 强调色 */
  --nav-bg: rgba(15,23,42,0.88); /* 导航栏 */
}
```

### 调整相机视角
修改 `camera.position.set(x, y, z)` 和 `controls.target.set(x, y, z)`

### 修改物理参数
直接编辑 `CONFIG` 对象中的参数值

---

## 文件结构

```
/workspace/Code仿真项目/分子与光/
├── molecule_and_light.html    # 主实验文件（728行，自包含）
├── 分子与光_skill.md           # Skill 技能文档（本文档）
├── 分子与光手册.md            # 用户手册
├── Code_Wiki_虚拟仿真.md       # 代码Wiki文档
└── README_汇总.md             # README更新副本

/workspace/aetherviz-master/
├── molecule_and_light.html    # 同步副本
└── README.md                  # 已更新至 v6.0
```

## 启动方式

```bash
cd /workspace/Code仿真项目/分子与光/
python3 -m http.server 8080
# 访问 http://localhost:8080/molecule_and_light.html
```

**或者直接双击 `molecule_and_light.html` 在浏览器中打开（无需服务器）。**

---

## 版本历史

| 版本 | 日期 | 更新内容 |
|------|------|----------|
| v1.0 | 2026-05-12 | 初始版本，基础仿真 |
| v2.0 | 2026-05-12 | 频率范围扩展至 0-900 THz |
| v3.0 | 2026-05-12 | 相机优化，公式白色显示 |
| v4.0 | 2026-05-12 | 光频按钮 + 银色手电筒 |
| v5.0 | 2026-05-13 | UI 重构，按钮对齐，暂停功能 |
| **v6.0** | **2026-05-13** | **科学计数法 Hz + 最终对齐 + 背景清理** |

---

*文档版本: 2.0 | 最后更新: 2026-05-13 | 对应项目版本: v6.0*
