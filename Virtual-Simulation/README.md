# Virtual-Simulation — 虚拟仿真实验项目

> 基于 Trae SOLO 开发的大学物理虚拟仿真实验项目，用于 SOLO 技能创作赛

## 项目简介

本项目是 **SOLO 技能创作赛**参赛作品，实现了大学物理"分子与光"虚拟仿真实验。学生无需实验室设备，打开浏览器即可观察光子与分子共振吸收/发射的完整物理过程。

## 项目结构

```
Virtual-Simulation/
├── 分子与光/                          # 仿真实验项目
│   ├── molecule_and_light.html        # 主实验文件（728行，自包含）
│   ├── 分子与光_skill.md              # Skill 技能文档（10大模块参数）
│   ├── 分子与光手册.md                # 用户手册
│   ├── Code_Wiki_虚拟仿真.md          # 代码 Wiki
│   ├── 项目总结.md                    # 项目总结
│   └── Skill参赛作品/                 # 参赛材料
│       ├── 参赛材料整理.md            # 完整参赛材料
│       ├── 参赛检查清单.md            # 提交前必查项
│       ├── 提示词库.md                # 7大类开发提示词
│       ├── 社媒发布模板.md            # 社媒发布模板
│       └── Skill可扩展性分析.md       # 6大领域扩展分析
├── LICENSE                            # MIT License
└── README.md                          # 本文件
```

## 快速开始

### 方式1：直接打开
```bash
# 双击 molecule_and_light.html 在浏览器中打开
```

### 方式2：本地服务器
```bash
cd Virtual-Simulation/分子与光
python3 -m http.server 8080
# 访问 http://localhost:8080/molecule_and_light.html
```

## 技术栈

| 组件 | 技术 | 版本 | 来源 |
|------|------|------|------|
| 3D 引擎 | Three.js | r134 | CDN |
| UI 框架 | Tailwind CSS | v3.4+ | CDN |
| 公式渲染 | KaTeX | 0.16.11 | CDN |
| 架构 | 单文件 HTML | 自包含 | — |

> **致谢**：本项目基于开源框架 [AetherViz Master](https://github.com/andyhuo520/aetherviz-master) 开发，感谢原作者 Andy Huo 的贡献。

## 核心功能

- **8种分子模型**：CO/N₂/O₂/CO₂/CH₄/H₂O/NO₂/O₃
- **光子共振吸收**：频率匹配时吸收→振动→发射完整闭环
- **频率颜色映射**：0~9.0×10¹⁴ Hz 科学计数法显示
- **银色手电筒光源**：频率颜色联动
- **电磁波谱覆盖层**：分子位置标记
- **零依赖架构**：单文件 HTML，双击即可运行

## 参赛信息

- **赛事**：Trae SOLO 技能创作赛
- **赛道**：Skill 创作
- **领域**：开发辅助 / 无限创意
- **版本**：v6.0
- **完成日期**：2026-05-13

## 许可证

MIT License
