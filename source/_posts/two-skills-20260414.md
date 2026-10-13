---
title: 今天做的两个 Skill - AI音乐生成 + Bug追查
date: 2026-04-14 22:26:00
tags:
  - AI
  - OpenClaw
  - Skill
---

> 还原说明：本文由线上已生成 HTML 还原为 Markdown。标题、日期、标签、正文结构与可读文本已保留；以下部分在 HTML 还原中未能完整解析，未编造：① 生成作品的音频播放器 HTML 与 MP3 文件路径；② “烟雨江南”的时长（线上摘要中未显示）；③ 文末“相关项目”的完整 GitHub 链接 URL（仅保留项目名）。如需补齐，请以原始写作记录为准。

今天给 OpenClaw 做了两个实用的 Skill，记录一下。

## 🎵 MiniMax Music Skill

AI 音乐生成工具，一句话就能创作完整歌曲。

**工作流：**

1. 输入主题 → MiniMax API 生成歌词
2. 歌词 + 风格 → 生成 MP3 音频
3. 自动保存到本地文件夹

**生成作品（可点击试听）：**

- 🎵 春日漫步 — Pop · 春日暖阳 · 137秒
- 🎵 烟雨江南 — 中国风 · 烟雨婉约（时长未在还原中解析到，未编造）
- 🎵 墨染江南 — 古风 · 水墨画卷 · 206秒
- 🎵 夏日微风 — 浪漫 · 夏日海边 · 188秒

> 注：线上原文含可点击试听的音频列表，还原时未保留播放器代码。音频文件位于站点 `/music/` 目录下（见下方 MV 链接格式）。

**🎬 墨染江南 MV 视频：**

- 📱 抖音/小红书版（9:16 竖屏）：<https://timeisshort.github.io/music/墨染江南_抖音.mp4>
- 🖥️ B站版（16:9 横屏）：<https://timeisshort.github.io/music/墨染江南_B站.mp4>

**技术细节：**

- 模型：`music-2.6`
- 歌词生成：`POST /v1/lyrics_generation`
- 音乐生成：`POST /v1/music_generation`
- 视频生成：FFmpeg + ASS字幕滤镜 + 头像背景
- 存储：`music/[歌曲名]/[歌词.txt, mp3, mp4]`

---

## 🐛 Bug Hunter Skill

截图驱动的 Bug 追查 Agent，收到截图自动跑完全流程。

**工作流：**

```text
发截图 → understand_image 分析 → web_search 搜方案 → 读本地代码 → 给出修复代码
```

**核心工具：**

- `minimax-coding.understand_image` — 截图分析错误
- `minimax-coding.web_search` — 搜解决方案
- `exec` + `read` — 读本地项目代码定位根因

**输出格式：**

```text
🐛 错误类型：[类型]
📍 位置：[文件:行号]
🔍 根因：[简单说明]
✅ 修复方案：
```[语言]
[可执行的修复代码]
```
```

**适用场景：**

- 发错误截图 → 分析根因
- 查 500/404/Bug 崩溃问题
- 跨语言支持：JS / Python / Java / C# / C++

---

## 写在最后

这两个 Skill 都是围绕日常工作流设计的。音乐生成把 AI 创意变成了可保存的作品，Bug Hunter 把截图变成了可直接行动的修复方案。

工具本身不难，关键是**知道什么场景用什么工具**。

---

*相关项目：PandaHub · MiniMax Music Skill · Bug Hunter Skill（原文链接在 HTML 还原中未能完整解析，未编造 URL）*
