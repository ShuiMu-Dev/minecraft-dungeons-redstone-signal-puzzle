# 红石信号解谜 / Redstone Signal Puzzle

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=6b4038&height=200&section=header&text=Redstone%20Signal%20Puzzle&fontSize=50&fontColor=fcf6ed&animation=fadeIn&fontAlignY=38&desc=红石信号解谜&descAlignY=60&descSize=22" width="100%"/>

<a href="#">
  <img src="https://readme-typing-svg.demolab.com?font=Noto+Sans+SC&weight=500&size=20&duration=3000&pause=800&color=FF6A4A&center=true&vCenter=true&width=600&lines=%E6%88%91%E7%9A%84%E4%B8%96%E7%95%8C%EF%BC%9A%E5%9C%B0%E4%B8%8B%E5%9F%8E+%7C+%E6%BD%AE%E6%B9%BF%E6%B4%9E%E7%A9%B4;Minecraft+Dungeons+%7C+Soggy+Cave;%E5%8D%95%E6%96%87%E4%BB%B6+%C2%B7+%E9%9B%B6%E4%BE%9D%E8%B5%96+%C2%B7+%E8%B7%A8%E5%B9%B3%E5%8F%B0;Single+File+%C2%B7+Zero+Dep+%C2%B7+Cross-Platform" alt="Typing SVG" />
</a>

[![License: MIT](https://img.shields.io/badge/License-MIT-2ea44f?style=for-the-badge)](LICENSE)
[![Single File](https://img.shields.io/badge/Single--File-HTML-E34F26?style=for-the-badge&logo=html5&logoColor=white)](#)
[![Minecraft Dungeons](https://img.shields.io/badge/Inspiration-Minecraft%20Dungeons-6b4038?style=for-the-badge)](#)
[![Language](https://img.shields.io/badge/Language-中文%20%7C%20English-blue?style=for-the-badge)](#)

一个单文件、零依赖的网页版红石信号解谜小游戏。灵感来源于《我的世界：地下城》“潮湿洞穴”关卡中的活塞机关。

A single-file, zero-dependency web-based Redstone signal puzzle. Inspired by the piston mechanisms in the "Soggy Cave" level of Minecraft Dungeons.

</div>

---

## 目录 / Table of Contents

<div align="center">

| 章节 / Section | 快速跳转 / Jump |
|:---:|:---:|
| 项目简介 / Introduction | [前往](#项目简介--introduction) |
| 功能特点 / Features | [前往](#功能特点--features) |
| 快速开始 / Quick Start | [前往](#快速开始--quick-start) |
| 玩法与原理 / Gameplay & Rules | [前往](#玩法与原理--gameplay--rules) |
| 技术要点 / Tech Highlights | [前往](#技术要点--tech-highlights) |
| 已知限制 / Limitations | [前往](#已知限制--known-limitations) |

</div>

---

## 项目简介 / Introduction

这是一款还原《我的世界：地下城》红石活塞机关的网页解谜游戏。玩家需要观察红石方块的升降状态，通过点击不同的按钮，利用“信号传递”和“方块平移”的机制，让红石信号成功传导至终点。

This is a web-based puzzle game that recreates the Redstone piston mechanisms from Minecraft Dungeons. Players must observe the raised/lowered states of Redstone blocks and click various buttons, utilizing "signal propagation" and "block shifting" mechanics to guide the Redstone signal to the target.

游戏内置了由易到难的多道关卡，且提供**中英双语**、**日间/夜间模式自适应**以及**移动端响应式布局**。

The game features multiple levels of increasing difficulty, and supports **English/Chinese**, **auto-adaptive light/dark themes**, and a **mobile-responsive layout**.

---

## 功能特点 / Features

- **原汁原味**：高度还原“潮湿洞穴”的机关逻辑与视觉反馈。
- **沉浸体验**：红石升起时的发光效果、下落时的重力回弹动画。
- **自动生成**：每关起始状态由 BFS 算法随机生成，保证绝对有解且每次开局不同。
- **智能提示**：卡关时点击“答案”，系统将通过 BFS 寻路算法给出当前状态的最短通关步骤。
- **双语切换**：一键切换中文与英文，所有 UI 和弹窗文案均已精准本地化。
- **零依赖**：纯原生 HTML + CSS + JS，单文件双击即用。

<br/>

- **Authentic**: Highly recreates the mechanism logic and visual feedback of "Soggy Cave".
- **Immersive**: Glowing effects when Redstone rises, and gravity-rebound animations when it lowers.
- **Auto-Generated**: The initial state of each level is randomly generated via a BFS algorithm, ensuring it's always solvable and unique every time.
- **Smart Hints**: When stuck, click "Answer", and the system will use BFS pathfinding to provide the shortest solution for the current state.
- **Bilingual**: Toggle between Chinese and English with one click; all UI and modal texts are accurately localized.
- **Zero Dependencies**: Pure vanilla HTML + CSS + JS. Double-click a single file to play.

---

## 快速开始 / Quick Start

### 方式 1：直接打开（最简单）/ Option 1: Open directly (simplest)

1. 下载 `index.html` 文件。
2. 双击用任意现代浏览器打开即可开始游戏。

1. Download the `index.html` file.
2. Double-click to open in any modern browser and start playing.

### 方式 2：部署到 GitHub Pages / Option 2: Deploy to GitHub Pages

1. 将代码推送到 GitHub 仓库。
2. 仓库 **Settings → Pages**。
3. Source 选择 `main` 分支与 `/root` 目录。
4. 保存后访问：`https://<你的用户名>.github.io/<仓库名>/`

1. Push the code to your GitHub repository.
2. Go to **Settings → Pages**.
3. Select the `main` branch and `/root` directory.
4. Save and visit: `https://<your-username>.github.io/<repo-name>/`

---

## 玩法与原理 / Gameplay & Rules

### 核心机制 / Core Mechanics

- **信号源 (Source)**：最左侧，常亮，是传递信号的起始点。
- **红石方块 (Redstone Blocks)**：中间可交互的方块。只有「升起 (Raised)」且左侧有信号时才会亮起。
- **目标灯 (Target)**：最右侧。亮起即代表通关。
- **断点 (Gap)**：如果信号传播途中遇到一个落下的方块，信号中断，后面的方块全部熄灭。

<br/>

- **Source**: Far left, always on, the starting point of the signal.
- **Redstone Blocks**: Interactive blocks in the middle. They only light up if they are "Raised" and the block to their left has power.
- **Target**: Far right. Lights up to indicate victory.
- **Gap**: If the signal encounters a lowered block, it breaks, and all subsequent blocks turn off.

### 操作按钮 / Buttons

部分按钮控制方块的**升降**（激活），部分按钮控制方块的**左右平移**。移出边界的方块会从另一端绕回（Wrap around）。

Some buttons control the **raising/lowering** (activation) of blocks, while others control the **left/right shifting**. Blocks that fall off one edge wrap around to the other side.

---

## 技术要点 / Tech Highlights

- **算法支持**：内置 BFS（广度优先搜索）算法。不仅用于验证随机初始状态是否有解，还用于计算“答案”中的最短操作路径。
- **动画曲线**：使用 `cubic-bezier(.34, 1.3, .5, 1)` 实现红石下落时轻微的“触底回弹”物理感。
- **双语状态保持**：切换语言时，若当前处于游戏或弹窗状态，游戏进度不会重置，且弹窗文案会实时重绘。
- **移动端适配**：通过 CSS 变量 `--cell-w` 和 `--cell-h`，配合媒体查询，在窄屏幕下自动缩小棋盘，确保不溢出。

<br/>

- **Algorithm**: Built-in BFS (Breadth-First Search). Used not only to validate if a random initial state is solvable but also to calculate the shortest path for the "Answer" hint.
- **Animation Curves**: Uses `cubic-bezier(.34, 1.3, .5, 1)` to simulate the physical "bounce" of Redstone hitting the bottom when lowered.
- **State Preservation on Language Switch**: Switching languages mid-game or during a modal won't reset progress, and modal texts update instantly.
- **Mobile Adaptation**: Uses CSS variables `--cell-w` and `--cell-h` with media queries to auto-shrink the board on narrow screens, preventing overflow.

---

## 已知限制 / Known Limitations

- 游戏核心逻辑提取自游戏关卡机制，但为了解谜体验做了一定程度的算法简化。
- 关卡数量有限，目前包含基础教学（3格）与进阶难度（5格）两部分。

<br/>

- The core logic is extracted from the game's level mechanics, but simplified for a better puzzle experience.
- Limited number of levels. Currently includes a basic tutorial (3 blocks) and an advanced level (5 blocks)
