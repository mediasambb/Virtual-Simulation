# Virtual Simulation | 虚拟仿真实验项目

- 💡用 Trae SOLO 做了个大学物理仿真实验，打开就能跑
- 🚀零代码搭建 3D 分子物理仿真？Trae SOLO 真的可以做到
- 📌从想法到可运行的物理仿真，我只写了几段提示词

<br />

> 1. 基于 Trae SOLO 开发的“高等教育-虚拟仿真实验项目”**，架构设计具有**天然的可扩展性\*\*，可快速复用到化学、生物、数学、天文、编程等多个领域。
> 2. 适用于“沉浸式教学、学术研究模拟、可视化建模、微观宏观虚拟、即时反馈编程学习“等领域。
> 3. 适用于“六大主题领域扩展“主题，如:
>
> - 物理领域：光电效应仿真实验、双缝干涉可视化、洛伦兹力粒子运动、简谐振动与波、电磁场三维可视化；
> - 化学领域：化学键与分子结构；
> - 生物领域：蛋白质折叠过程可视化；
> - 数学领域：函数图像与导数可视化、太阳系行星运动仿真；
> - 编程领域：算法可视化（排序/搜索/树结构）；

## 1️⃣项目介绍

📌 用 Trae SOLO 做物理仿真之前 VS 之后
之前的我 😩

- 🚀想做分子物理仿真，要搭 Webpack + Three.js + React
  写碰撞检测、状态机、物理公式转换，至少一周
  3D 模型手动建，相机调试调半天
  最后做出来效果一般，学生还是看不懂
  用 Trae SOLO 之后🚀&#x20;
- 1️⃣单文件 HTML，双击直接跑，零配置
  告诉 AI "实现光子共振吸收"，它自动写出完整的物理闭环
  8 种分子、银色手电筒、电磁波谱，提示词描述就生成
  一天搞定，还能实时改参数，课堂直接演示📺

💡 核心创新
完整物理闭环：不是动画演示，是真的物理仿真👨‍🚀

- ☀️光子发射 → 🤲碰撞检测 → 📊频率匹配 → ⚖️共振吸收 → 🆚阻尼振动 → 💡光子发射
- 💻科学计数法显示：全部频率用标准物理格式（5.50×10¹ Hz），符合教学规范
- 0️⃣零依赖：单文件 HTML，双击运行，无需服务器

[\[项目截图\](](https://math-oss.nanyuecloud.com/xd-rag/vr3_png/1.png)[https://private-user-images.githubusercontent.com/209410688/592268944-a39b8926-2374-4ed2-951f-5c721db2108a.png](https://private-user-images.githubusercontent.com/209410688/592268944-a39b8926-2374-4ed2-951f-5c721db2108a.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Nzg3MzY0MjksIm5iZiI6MTc3ODczNjEyOSwicGF0aCI6Ii8yMDk0MTA2ODgvNTkyMjY4OTQ0LWEzOWI4OTI2LTIzNzQtNGVkMi05NTFmLTVjNzIxZGIyMTA4YS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwNTE0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDUxNFQwNTIyMDlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1kNGEzYjFhNTEyZTA2NTQ4NGYzZGQ2ODVlZGNkNzFlY2MwYzI3NWY5MjFmMTIwMGExOTI5YzdjOGM3YzMxNmMyJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZyZXNwb25zZS1jb250ZW50LXR5cGU9aW1hZ2UlMkZwbmcifQ.GrCkSDz20aG32Lj5MY_MPnl8BYl1uMIRqF7vC9ucEbA)[)](https://math-oss.nanyuecloud.com/xd-rag/vr3_png/1.png)

## 项目结构

```
Virtual-Simulation/
├── 分子与光/
│   ├── molecule_and_light.html
│   ├── 分子与光_skill.md
│   ├── 分子与光手册.md
│   ├── Code_Wiki_虚拟仿真.md
│   ├── 项目总结.md
│   └── Skill辅助文档/
│       ├── 材料整理.md
│       ├── 检查清单.md
│       ├── 提示词库.md
│       ├── 文案模板.md
│       ── Skill可扩展性分析.md
├── LICENSE
└── README.md
```

## 快速开始

### 方式 1：直接打开

双击 `分子与光/molecule_and_light.html`，浏览器即可运行

### 方式 2：本地服务器

```bash
cd 分子与光
python3 -m http.server 8080
# 浏览器访问: http://localhost:8080/molecule_and_light.html
```

## 技术栈

| 技术          | 版本       | 来源  | 用途      |
| ----------- | -------- | --- | ------- |
| Three.js    | r134     | CDN | 3D 渲染引擎 |
| TailwindCSS | v3.4     | CDN | UI 样式框架 |
| KaTeX       | v0.16.11 | CDN | 数学公式渲染  |
| JavaScript  | ES6+     | 原生  | 物理仿真逻辑  |

> **致谢**：本项目基于开源框架 [AetherViz Master](https://github.com/andyhuo520/aetherviz-master) 开发，感谢原作者 Andy Huo 的贡献。

## 核心功能

- **8 种分子 3D 建模**：CO、NO₂、N₂、O₃、O₂、CO₂、CH、H₂O
- **光子共振吸收**：入射频率匹配分子固有频率时触发吸收
- **完整物理闭环**：发射 → 碰撞 → 吸收 → 振动 → 再发射
- **科学计数法显示**：所有频率以 Hz 格式呈现（如 5.50×10¹⁴ Hz）
- **银色手电筒 3D 模型**：频率关联的彩色光子发射源
- **阻尼谐振子**：分子振动衰减模拟真实物理行为
- **频率-颜色映射**：可见光谱 RGB 实时计算
- **单文件零依赖**：728 行 HTML，双击即可运行

## 2️⃣分子与光 — 虚拟仿真实验手册

## 实验激活链接

```
http://localhost:8080/分子与光/molecule_and_light.html
```

## 实验简介

本实验是大学物理虚拟仿真项目，演示分子与光的共振吸收和发射现象。当入射光的频率等于分子的固有频率时，光子被分子吸收，分子发生剧烈振动；振动衰减后，分子发射出与入射光频率相同的光子。

[https://private-user-images.githubusercontent.com/209410688/592268940-9c5d5f62-a7ee-40ed-8e25-c15e3529e2c3.png](https://private-user-images.githubusercontent.com/209410688/592268940-9c5d5f62-a7ee-40ed-8e25-c15e3529e2c3.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Nzg3MzY2OTQsIm5iZiI6MTc3ODczNjM5NCwicGF0aCI6Ii8yMDk0MTA2ODgvNTkyMjY4OTQwLTljNWQ1ZjYyLWE3ZWUtNDBlZC04ZTI1LWMxNWUzNTI5ZTJjMy5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwNTE0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDUxNFQwNTI2MzRaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1jZGY5NmFhOTU5YTQ3ZTNjZWQ0NGVkNzcyM2M5Y2MyYjQ1MTM3ZThhNmJhYjAzZmEwZjU1OTdhYTllYzU5NWY1JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZyZXNwb25zZS1jb250ZW50LXR5cGU9aW1hZ2UlMkZwbmcifQ.JNNx0NlX1XBmjFL0wMrzvMmn2NJ8AasrhQLRxXIwa3M)

## 功能清单

### 一、光波频率控制

[https://private-user-images.githubusercontent.com/209410688/592268941-cc754162-6fdb-4752-b8dd-1ba338693208.png](https://private-user-images.githubusercontent.com/209410688/592268941-cc754162-6fdb-4752-b8dd-1ba338693208.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Nzg3MzY2OTQsIm5iZiI6MTc3ODczNjM5NCwicGF0aCI6Ii8yMDk0MTA2ODgvNTkyMjY4OTQxLWNjNzU0MTYyLTZmZGItNDc1Mi1iOGRkLTFiYTMzODY5MzIwOC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwNTE0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDUxNFQwNTI2MzRaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT03MmU1ZWFhMWU5ODI1NDk5YWQ4NzVmN2IxZmM5ZGEzOWY2NDBiOGM3ZWJkMzM0YzYzNWVkNGY1YzYzNzdmYTU3JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZyZXNwb25zZS1jb250ZW50LXR5cGU9aW1hZ2UlMkZwbmcifQ.goyqEobkIbMkIFqVu9xtYgpO1efUqQjNSVPOsyazt5k)

| 按钮  | 频率       | 功能说明             |
| :-- | :------- | :--------------- |
| CO  | 64 THz   | 设置入射光频率为一氧化碳固有频率 |
| N₂  | 70 THz   | 设置入射光频率为氮气固有频率   |
| O₂  | 47 THz   | 设置入射光频率为氧气固有频率   |
| CO₂ | 20 THz   | 设置入射光频率为二氧化碳固有频率 |
| CH₄ | 91 THz   | 设置入射光频率为甲烷固有频率   |
| H₂O | 550 THz  | 设置入射光频率为水分子固有频率  |
| NO₂ | 48 THz   | 设置入射光频率为二氧化氮固有频率 |
| O₃  | 31.5 THz | 设置入射光频率为臭氧固有频率   |

频率滑块范围：**0 \~ 900 THz**（连续可调，步进 1 THz）

[https://private-user-images.githubusercontent.com/209410688/592268943-b0116dfb-07a5-4038-8985-06f82fe9d402.png](https://private-user-images.githubusercontent.com/209410688/592268943-b0116dfb-07a5-4038-8985-06f82fe9d402.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Nzg3MzY5MzcsIm5iZiI6MTc3ODczNjYzNywicGF0aCI6Ii8yMDk0MTA2ODgvNTkyMjY4OTQzLWIwMTE2ZGZiLTA3YTUtNDAzOC04OTg1LTA2ZjgyZmU5ZDQwMi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwNTE0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDUxNFQwNTMwMzdaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1iOWZhMWMxOTJmOTc0ZWU0MGE5NDliNTE2NzBjZDk2ZjdiMzlhOWY1ZWJmNGQyNTBjMGQ3NmE0NmI2NjZiNDFlJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZyZXNwb25zZS1jb250ZW50LXR5cGU9aW1hZ2UlMkZwbmcifQ.wRqYVMdsDS65EvmS_R4jDiQE3xrEzHQd4RTwmTfsxvU)

### 二、分子选择

[https://private-user-images.githubusercontent.com/209410688/592268941-cc754162-6fdb-4752-b8dd-1ba338693208.png](https://private-user-images.githubusercontent.com/209410688/592268941-cc754162-6fdb-4752-b8dd-1ba338693208.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Nzg3MzY2OTQsIm5iZiI6MTc3ODczNjM5NCwicGF0aCI6Ii8yMDk0MTA2ODgvNTkyMjY4OTQxLWNjNzU0MTYyLTZmZGItNDc1Mi1iOGRkLTFiYTMzODY5MzIwOC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwNTE0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDUxNFQwNTI2MzRaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT03MmU1ZWFhMWU5ODI1NDk5YWQ4NzVmN2IxZmM5ZGEzOWY2NDBiOGM3ZWJkMzM0YzYzNWVkNGY1YzYzNzdmYTU3JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZyZXNwb25zZS1jb250ZW50LXR5cGU9aW1hZ2UlMkZwbmcifQ.goyqEobkIbMkIFqVu9xtYgpO1efUqQjNSVPOsyazt5k)

| 分子   | 化学式 | 固有频率      | 吸收波段   |
| :--- | :-- | :-------- | :----- |
| 一氧化碳 | CO  | 64.0 THz  | 远红外    |
| 氮气   | N₂  | 70.0 THz  | 远红外    |
| 氧气   | O₂  | 47.0 THz  | 远红外    |
| 二氧化碳 | CO₂ | 20.0 THz  | 远红外    |
| 甲烷   | CH₄ | 91.0 THz  | 远红外    |
| 水    | H₂O | 550.0 THz | 远红外    |
| 二氧化氮 | NO₂ | 48.0 THz  | 远红外    |
| 臭氧   | O₃  | 31.5 THz  | 远红外/微波 |

### 三、实验操作按钮

[https://private-user-images.githubusercontent.com/209410688/592268941-cc754162-6fdb-4752-b8dd-1ba338693208.png](https://private-user-images.githubusercontent.com/209410688/592268941-cc754162-6fdb-4752-b8dd-1ba338693208.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Nzg3MzY2OTQsIm5iZiI6MTc3ODczNjM5NCwicGF0aCI6Ii8yMDk0MTA2ODgvNTkyMjY4OTQxLWNjNzU0MTYyLTZmZGItNDc1Mi1iOGRkLTFiYTMzODY5MzIwOC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwNTE0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDUxNFQwNTI2MzRaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT03MmU1ZWFhMWU5ODI1NDk5YWQ4NzVmN2IxZmM5ZGEzOWY2NDBiOGM3ZWJkMzM0YzYzNWVkNGY1YzYzNzdmYTU3JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZyZXNwb25zZS1jb250ZW50LXR5cGU9aW1hZ2UlMkZwbmcifQ.goyqEobkIbMkIFqVu9xtYgpO1efUqQjNSVPOsyazt5k)

| 按钮    | 功能                  |
| :---- | :------------------ |
| 发射光子  | 从光源发射一个光子           |
| 重置    | 重置实验到初始状态           |
| 随机频率  | 随机设置频率并自动发射光子       |
| 随机分子  | 随机选择一个分子            |
| 连续发射  | 开启/关闭连续发射模式         |
| 正常/慢速 | 切换播放速度（1.0x / 0.3x） |
| 暂停/播放 | 暂停/恢复动画             |
| 单步    | 单帧推进动画              |
| 显示光谱  | 显示电磁波谱图             |

### 四、实验预期效果

1. **频率匹配时**（|f入射 - f固有| ≤ 共振容差）：

- 光子被分子吸收（缩小消失动画，约0.35秒）
- 分子开始剧烈振动（阻尼振荡，约2.8秒）
- 振动结束后分子发射同频率光子

[https://private-user-images.githubusercontent.com/209410688/592268940-9c5d5f62-a7ee-40ed-8e25-c15e3529e2c3.png](https://private-user-images.githubusercontent.com/209410688/592268940-9c5d5f62-a7ee-40ed-8e25-c15e3529e2c3.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Nzg3MzY2OTQsIm5iZiI6MTc3ODczNjM5NCwicGF0aCI6Ii8yMDk0MTA2ODgvNTkyMjY4OTQwLTljNWQ1ZjYyLWE3ZWUtNDBlZC04ZTI1LWMxNWUzNTI5ZTJjMy5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwNTE0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDUxNFQwNTI2MzRaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1jZGY5NmFhOTU5YTQ3ZTNjZWQ0NGVkNzcyM2M5Y2MyYjQ1MTM3ZThhNmJhYjAzZmEwZjU1OTdhYTllYzU5NWY1JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZyZXNwb25zZS1jb250ZW50LXR5cGU9aW1hZ2UlMkZwbmcifQ.JNNx0NlX1XBmjFL0wMrzvMmn2NJ8AasrhQLRxXIwa3M)

1. **频率不匹配时**：
   - 光子穿过分子，继续传播
   - Toast提示"光子穿过分子，未共振"

[https://private-user-images.githubusercontent.com/209410688/592268937-ee68509f-431d-4a80-942b-df44d0171a5d.png](https://private-user-images.githubusercontent.com/209410688/592268937-ee68509f-431d-4a80-942b-df44d0171a5d.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Nzg3MzY2OTQsIm5iZiI6MTc3ODczNjM5NCwicGF0aCI6Ii8yMDk0MTA2ODgvNTkyMjY4OTM3LWVlNjg1MDlmLTQzMWQtNGE4MC05NDJiLWRmNDRkMDE3MWE1ZC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwNTE0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDUxNFQwNTI2MzRaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT04MTAyNGU2MTg2ZjUzYTRmZGM1ZmRlNTIwZGFmYjFjMDUyYzkwZGY4ZWI2NzA1MGU1ZDQ1MjAxY2Y0YWI1NWM5JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZyZXNwb25zZS1jb250ZW50LXR5cGU9aW1hZ2UlMkZwbmcifQ.irQymWId9Y6g9GBnals2u4jyDA71wck846YSMyD0aNk)

### 五、技术栈

- Three.js r134（3D渲染）
- TailwindCSS v3.4（样式框架）
- KaTeX 0.16.11（公式渲染）

### 六、文件结构

```
Code仿真项目/
└── 分子与光/
    ├── molecule_and_light.html    # 实验主文件
    └── 分子与光手册.md             # 本手册
```

### 七、相机初始配置（提示词模板参数）

```
┌─────────────────────────────────────────────────────────────┐
│  相机初始状态配置 【可调】                                     │
─────────────────────────────────────────────────────────────┤
│                                                             │
│  相机位置 (x, y, z):                                        │
│    · x: 【5】   → 从右侧观察，能看到光源(左侧)和分子(中心)     │
│    · y: 【3】   → 俯视角度，能看到分子三维结构                 │
│    · z: 【6】   → 适中距离，确保光源和分子均在视野内            │
│                                                             │
│  相机目标点 (controls.target):                              │
│    · (0, 0, 0) → 聚焦分子中心                                │
│                                                             │
│  相机参数:                                                   │
│    · FOV: 【55】°                                           │
│    · 最小距离: 【3】(防止穿模)                                │
│    · 最大距离: 【20】(防止过远)                               │
│    · 阻尼系数: 【0.08】                                      │
│    · 最大俯仰角: Math.PI * 0.85 (防止翻转)                   │
│                                                             │
│  初始观察效果:                                               │
│    · 光源位于画面左侧可见                                    │
│    · 分子位于画面中央清晰可见                                 │
│    · 光束路径虚线从左向右延伸                                │
│    · 俯视角度可观察分子三维结构                              │
│                                                             │
│  适配不同比例窗口:                                           │
│    · 窗口 resize 时自动更新 camera.aspect                     │
│    · camera.updateProjectionMatrix() 重新计算投影            │
│    · renderer.setSize() 重新设置渲染尺寸                      │
│    · 初始位置 (5,3,6) 确保横屏/竖屏均能观察到光源和分子        │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**相机位置说明**：

- `(5, 3, 6)` 的位置使相机从**右上方**观察场景
- 光源位于 `x = -6.5`，分子位于 `x = 0`
- 相机在 `x = 5` 处，能同时看到左侧的光源和中心的分子
- `y = 3` 提供适度俯视角度，能观察分子三维结构
- `z = 6` 提供合适的观察距离
- 不同参数配置提供：不同观察角度

[https://private-user-images.githubusercontent.com/209410688/592268938-b8b50c5b-1af7-4e8c-961f-baa2ae411835.png](https://private-user-images.githubusercontent.com/209410688/592268938-b8b50c5b-1af7-4e8c-961f-baa2ae411835.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Nzg3MzY5MzcsIm5iZiI6MTc3ODczNjYzNywicGF0aCI6Ii8yMDk0MTA2ODgvNTkyMjY4OTM4LWI4YjUwYzViLTFhZjctNGU4Yy05NjFmLWJhYTJhZTQxMTgzNS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwNTE0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDUxNFQwNTMwMzdaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0xYWU1N2YzNmJkNGZmOTlhMzUwMjZhOGQ1YWEzYTkyYWE4MmI3NmNkNjA3NDM2ZDNmNjc1MDc1Mzc2NWE3MmJmJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZyZXNwb25zZS1jb250ZW50LXR5cGU9aW1hZ2UlMkZwbmcifQ.JD012ztnGfONWo0-fuSwsQuzh6ctJCKECTVBHvf_1To)

- 不同参数配置提供：分子缩放倍率

[https://private-user-images.githubusercontent.com/209410688/592268939-8e955aee-df1e-4261-abc5-a7c509fd3138.png](https://private-user-images.githubusercontent.com/209410688/592268939-8e955aee-df1e-4261-abc5-a7c509fd3138.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Nzg3MzY5MzcsIm5iZiI6MTc3ODczNjYzNywicGF0aCI6Ii8yMDk0MTA2ODgvNTkyMjY4OTM5LThlOTU1YWVlLWRmMWUtNDI2MS1hYmM1LWE3YzUwOWZkMzEzOC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwNTE0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDUxNFQwNTMwMzdaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1jMDMzOThjYTdhNDM4NDQxMzRlM2U4ZDQ5Njg3MWJjZjQ4YTNmMjgzM2I3NzIyNzM3ZDg5OWZlYmU0OTg1YThlJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZyZXNwb25zZS1jb250ZW50LXR5cGU9aW1hZ2UlMkZwbmcifQ.943kgZSMrOkoUvm60lvqL_BhJRQLJwGDbTRQ1OUXNMQ)

- 不同参数配置提供：分子不同观察高度/缩放倍率

[https://private-user-images.githubusercontent.com/209410688/592268936-315fee97-613b-4cad-b7b7-fd592484c55f.png](https://private-user-images.githubusercontent.com/209410688/592268936-315fee97-613b-4cad-b7b7-fd592484c55f.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Nzg3MzY5MzcsIm5iZiI6MTc3ODczNjYzNywicGF0aCI6Ii8yMDk0MTA2ODgvNTkyMjY4OTM2LTMxNWZlZTk3LTYxM2ItNGNhZC1iN2I3LWZkNTkyNDg0YzU1Zi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwNTE0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDUxNFQwNTMwMzdaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT03M2YwYjkyNTA2ZGNhMTQyZDI5MDM3MTlmMjIzY2Q2NGVmZTFmZDU1YWZhNGVjMjdmMTg1ODkyMWVlMzM2NTQ3JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZyZXNwb25zZS1jb250ZW50LXR5cGU9aW1hZ2UlMkZwbmcifQ.YyEH9oiQAODNhvH2A5UofTP91DSKOVwOFt32zcsLXVA)

### 八、更新日志

| 版本   | 日期         | 更新内容                               |
| :--- | :--------- | :--------------------------------- |
| v1.0 | 2026-05-12 | 初始版本，H₂O分子共振吸收实验                   |
| v2.0 | 2026-05-12 | 新增8种分子选择、光谱显示、慢速播放                 |
| v3.0 | 2026-05-12 | 扩展频率范围0-900 THz，新增远红外/中红外/近红外波段    |
| v4.0 | 2026-05-12 | 光波频率按钮改为分子频率按钮，核心公式文字改为白色，优化相机初始位置 |

<br />

## 开源协议

本项目采用 MIT 协议开源，详见 [LICENSE](LICENSE) 文件。

<br />

# 3️⃣Skill 可扩展性分析 — 多主题领域支持

## 结论：完全支持多主题领域扩展

本项目虽然当前聚焦**物理**领域的"分子与光"仿真实验，但其架构设计具有**天然的可扩展性**，可快速复用到化学、生物、数学、天文、编程等多个领域。

***

## 架构扩展性分析

### 核心扩展点

| 扩展维度      | 扩展方式                   | 修改位置                                   |
| :-------- | :--------------------- | :------------------------------------- |
| **数据模型**  | 修改 MOLECULES 对象为对应领域数据 | `const MOLECULES`                      |
| **3D 场景** | 替换 Three.js 几何体和材质     | `buildMolecule()` / `init()`           |
| **物理逻辑**  | 修改物理仿真规则               | `updatePhotons()` / `updateMolecule()` |
| **UI 布局** | 调整控制面板结构和样式            | HTML 结构 + CSS                          |
| **配色主题**  | 修改 `:root` CSS 变量      | `:root` 定义                             |
| **交互逻辑**  | 增减控件和事件处理              | `setupUI()` + 事件函数                     |

***

## 六大主题领域扩展示例

### 1. 物理领域（已完成）

**当前实现**：分子与光

- 8 种分子 3D 建模
- 光子共振吸收仿真
- 频率-颜色映射
- 银色手电筒光源

**可扩展子主题**：

- 光电效应仿真实验
- 双缝干涉可视化
- 洛伦兹力粒子运动
- 简谐振动与波
- 电磁场三维可视化

***

### 2. 化学领域

**推荐主题**：化学键与分子结构

```javascript
// 扩展数据结构示例
const MOLECULES = {
  H2O: {
    name: '水分子',
    formula: 'H₂O',
    bondType: '极性共价键',
    bondAngle: '104.5°',
    polarity: '极性',
    hybridization: 'sp³',
    atoms: [...],
    bonds: [...],
    electronPairs: {bonding: 2, lone: 2}  // 电子对分布
  },
  // 可扩展：NH₃, CH₄, CO₂, SO₂, C₂H₄, C₂H₂ 等
};
```

**UI 交互设计**：

| 控件    | 功能                 |
| :---- | :----------------- |
| 分子选择  | 选择不同分子结构           |
| 键角滑块  | 调节键角观察结构变化         |
| 电子云切换 | 显示/隐藏电子云密度         |
| 杂化方式  | 切换 sp/sp²/sp³ 杂化显示 |
| 极性指示  | 偶极矩方向箭头            |

***

### 3. 生物领域

**推荐主题**：蛋白质折叠过程可视化

```javascript
// 扩展数据结构示例
const PROTEINS = {
  insulin: {
    name: '胰岛素',
    chain: 'A链(21aa) + B链(30aa)',
    structure: 'α螺旋 + β折叠',
    disulfideBonds: [
      {from: {chain:'A', pos:6}, to: {chain:'A', pos:11}},
      {from: {chain:'A', pos:7}, to: {chain:'B', pos:7}},
      {from: {chain:'A', pos:20}, to: {chain:'B', pos:19}}
    ],
    // 氨基酸序列
    sequenceA: 'GIVEQCCASVCSLYQLENYCN',
    sequenceB: 'FVNQHLCGSHLVEALYLVCGERGFFYTPKT'
  }
};
```

**UI 交互设计**：

| 控件     | 功能                 |
| :----- | :----------------- |
| 蛋白质选择  | 选择不同蛋白质            |
| 折叠动画   | 播放从线性到三维折叠过程       |
| 二级结构高亮 | 标记 α 螺旋、β 折叠、无规则卷曲 |
| 二硫键显示  | 显示二硫键连接            |
| 突变模拟   | 模拟氨基酸突变对结构的影响      |

***

### 4. 数学领域

**推荐主题**：函数图像与导数可视化

```javascript
// 扩展数据结构示例
const FUNCTIONS = {
  polynomial: {
    name: '多项式函数',
    formula: 'f(x) = ax³ + bx² + cx + d',
    derivative: "f'(x) = 3ax² + 2bx + c",
    parameters: {a: 1, b: -3, c: 2, d: -1},
    range: {xMin: -5, xMax: 5},
    criticalPoints: [{x: 0.42, y: -0.15, type: 'local_max'}]
  },
  trigonometric: {
    name: '三角函数',
    formula: 'f(x) = A·sin(ωx + φ)',
    parameters: {A: 2, ω: 1, φ: 0}
  }
};
```

**UI 交互设计**：

| 控件   | 功能                   |
| :--- | :------------------- |
| 函数选择 | 选择函数类型               |
| 参数滑块 | 调节 a, b, c, d 观察图像变化 |
| 导数显示 | 叠加显示一阶/二阶导数          |
| 极值标记 | 自动标记极大/极小值点          |
| 切线工具 | 点击任意点显示该点切线          |

***

### 5. 天文领域

**推荐主题**：太阳系行星运动仿真

```javascript
// 扩展数据结构示例
const CELESTIAL_BODIES = {
  solarSystem: {
    name: '太阳系',
    star: {name: '太阳', radius: 696340, color: '#FDB813', mass: '1.989×10³⁰ kg'},
    planets: [
      {name: '水星', distance: 0.39, period: 0.24, radius: 2440, color: '#8C7E6D', eccentricity: 0.2056},
      {name: '金星', distance: 0.72, period: 0.62, radius: 6052, color: '#E8CDA0', eccentricity: 0.0068},
      {name: '地球', distance: 1.00, period: 1.00, radius: 6371, color: '#4B7BE5', eccentricity: 0.0167},
      // ... 更多行星
    ],
    gravity: {G: 6.674e-11, units: 'N·m²/kg²'}
  }
};
```

**UI 交互设计**：

| 控件   | 功能         |
| :--- | :--------- |
| 视角切换 | 俯视/侧视/行星跟随 |
| 时间缩放 | 调节时间流速     |
| 轨道显示 | 显示/隐藏行星轨道  |
| 数据面板 | 显示行星实时数据   |
| 彗星模拟 | 添加彗星观察椭圆轨道 |

***

### 6. 编程领域

**推荐主题**：算法可视化（排序/搜索/树结构）

```javascript
// 扩展数据结构示例
const ALGORITHMS = {
  sorting: {
    name: '排序算法',
    algorithms: [
      {name: '冒泡排序', complexity: 'O(n²)', stable: true, inPlace: true},
      {name: '快速排序', complexity: 'O(n log n)', stable: false, inPlace: true},
      {name: '归并排序', complexity: 'O(n log n)', stable: true, inPlace: false},
      {name: '堆排序', complexity: 'O(n log n)', stable: false, inPlace: true}
    ],
    array: [38, 27, 43, 3, 9, 82, 10],
    steps: [] // 记录每一步操作
  },
  tree: {
    name: '二叉搜索树',
    nodes: [{value: 8, left: 3, right: 10}, {value: 3, left: 1, right: 6}],
    operations: ['插入', '删除', '查找', '遍历']
  }
};
```

**UI 交互设计**：

| 控件    | 功能           |
| :---- | :----------- |
| 算法选择  | 选择不同算法       |
| 速度控制  | 调节动画速度       |
| 数组生成  | 随机/自定义数组     |
| 步骤高亮  | 高亮当前比较的元素    |
| 复杂度对比 | 并列显示不同算法执行过程 |

***

## 通用 UI 主题系统

所有主题可共享统一的 UI 框架，通过 CSS 变量切换主题：

```css
:root {
  /* 物理主题（当前） */
  --bg: #C8D8E8;
  --accent-cyan: #22D3EE;
  --accent-amber: #FBBF24;
  --nav-bg: rgba(15,23,42,0.88);
  
  /* 化学主题（可扩展） */
  --chem-bg: #E8E0D8;
  --chem-accent: #FF6B6B;
  --chem-secondary: #4ECDC4;
  
  /* 生物主题（可扩展） */
  --bio-bg: #D8E8D8;
  --bio-accent: #2ECC71;
  --bio-secondary: #E74C3C;
  
  /* 数学主题（可扩展） */
  --math-bg: #E0E0E0;
  --math-accent: #9B59B6;
  --math-secondary: #3498DB;
}
```

***

## 扩展路线图

| 阶段      | 目标           | 预计工作量 |
| :------ | :----------- | :---- |
| Phase 1 | 物理：分子与光（已完成） | 已完成   |
| Phase 2 | 化学：分子结构与化学键  | 3-5 天 |
| Phase 3 | 生物：蛋白质折叠可视化  | 5-7 天 |
| Phase 4 | 数学：函数与导数可视化  | 3-5 天 |
| Phase 5 | 天文：太阳系运动仿真   | 3-5 天 |
| Phase 6 | 编程：算法可视化平台   | 5-7 天 |

***

## 核心竞争力

1. **统一技术栈**：所有主题共享 Three.js + TailwindCSS 技术栈，降低维护成本
2. **模块化设计**：数据模型、3D 渲染、UI 布局分离，主题切换只需修改数据层
3. **零依赖架构**：每个主题都是独立 HTML 文件，可单独部署和分享
4. **AI 辅助开发**：通过提示词可快速生成新主题的基础代码，大幅缩短开发周期

***

*文档版本: 1.0 | 最后更新: 2026-05-13*
