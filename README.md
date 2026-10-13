# Hexo 博客源码（全新重建）

全新、干净、可直接用的 Hexo 源码，不是旧 `source` 分支 Yilia 脚手架的像素级还原。

## 包含内容

- `_config.yml` — Hexo 核心配置（theme: fluid，url `https://timeisshort.github.io`，permalink `:year/:month/:day/:title/`，language `zh-CN`，timezone `Asia/Shanghai`，deploy 到 `master` 分支）
- `_config.fluid.yml` — Fluid 1.9.9 主题最小可用配置（导航、Banner、页脚、代码高亮、目录、搜索；评论关闭）
- `package.json` — Hexo 7.3.0 + hexo-deployer-git + 常用 generator/renderer，与 Fluid 1.9.9 兼容
- `scaffolds/` — post / page / draft 模板
- `source/_posts/` — 3 篇文章
  - `hello-world.md`（原文原样）
  - `two-skills-20260414.md`（由线上 HTML 还原，见文件顶部还原说明）
  - `2026-10-13-ai-requirement-orchestrator-claude-jev-codex.md`（用户提供原文，原样复制，未改正文）
- `source/about/index.md` — 沿用旧 `source` 分支的真实关于页（技术栈 / PandaHub / MiniMax Music Skill / 联系方式），重建时未覆盖，避免丢失真实信息
- `.gitignore` — node_modules / public / .deploy_git 等
- `themes/fluid/` — 主题本体**不在**本目录内（仅占位），需按下方步骤克隆

## ⚠️ source 分支现状警告（必读）

`TimeIsShort/TimeIsShort.github.io` 的 `source` 分支是旧脚手架：Hexo 8.1.1 + Yilia 主题、只有 `hello-world.md` 一篇、没有 Fluid 配置、没有 `two-skills` 文章。

**不要直接用旧 `source` 分支覆盖本重建源码，也不要把本重建源码不经确认直接推到 `source` 分支。** 推之前请先确认：是否用本重建源码替换 `source` 分支的旧 Yilia 内容（推荐），以及是否已备份旧 `source` 分支。

部署分支说明：`_config.yml` 的 deploy 目标是 `master` 分支（已生成静态站所在分支）。`hexo deploy` 会把 `public/` 推到 `master`，覆盖线上站。操作前请确认分支。

## 使用方法

```bash
# 1. 进入源码目录（本地克隆 source 分支后，或直接用本目录）
cd hexo-rebuild

# 2. 安装依赖
npm install

# 3. 克隆 Fluid 主题（1.9.9，与线上站一致）
# 注意：themes/fluid 目录目前只有占位文件，需先删除占位再克隆
rm -rf themes/fluid
git clone -b 1.9.9 https://github.com/fluid-dev/hexo-theme-fluid.git themes/fluid

# 4. 本地预览
npx hexo server
# 打开 http://localhost:4000 检查：首页、3 篇文章、归档/分类/标签、关于页、Banner、搜索

# 5. 部署到线上（确认无误后再执行）
npx hexo clean && npx hexo generate && npx hexo deploy
```

## 新文章发布流程

1. 在 `source/_posts/` 新建 `YYYY-MM-DD-标题-slug.md`，写好 front-matter（title / date / tags / categories）
2. 本地 `npx hexo server` 预览
3. `npx hexo clean && npx hexo generate && npx hexo deploy`

## 已知限制（见 VERIFY.md）

- Fluid 主题配置为最小可用 + 部分反推值，未逐项核对旧站的全部主题参数。
- `two-skills` 一文为 HTML 还原，音频播放器代码、1 个时长、文末完整 GitHub 链接未能还原，已在文件顶部标注。
- 本次验证未包含真实 Fluid 主题克隆后的完整生成（见 VERIFY.md）。
