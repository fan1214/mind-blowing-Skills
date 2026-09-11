# HTML 产物规范

用户可见的交付物**必须是独立 HTML 文件**，排版清晰、可在浏览器直接打开。Agent 状态用 JSON，Rubric 用 Markdown（不对用户展示）。

## 工作区目录

首次 PLAN 时创建：

```
.cursor/learning/{goal-slug}/
├── state.json              # Agent 状态（阶段、模块、考试 ID 等）
├── index.html              # 学习路径总览（PLAN）
├── assets/style.css        # 从 skill 的 assets/style.css 复制
├── modules/
│   └── m1-slug.html        # 模块详情（STUDY）
├── exams/
│   ├── exam-{id}.html      # 试卷（用户可见，无答案）
│   └── exam-{id}-rubric.md # Rubric + 参考答案（仅 Agent 阅卷用）
└── results/
    └── result-{id}.html    # 成绩报告（GRADE）
```

goal-slug 示例：`php-backend`。模块文件名：`m2-oop.html`。

## state.json 格式

```json
{
  "goal": "php-backend",
  "title": "PHP 后端开发",
  "phase": "PLAN",
  "job_type": "programming",
  "modules": ["M1", "M2", "M3", "M4", "M5", "M6"],
  "core": ["M2", "M3", "M4"],
  "exam_mode": "full",
  "attempt": 0,
  "modules_generated": true,
  "modules_studied": ["M1"],
  "updated": "2026-09-10"
}
```

恢复上下文：优先读 `state.json`，其次 `@` 用户引用的 HTML。

## HTML 页面骨架

每个 HTML 文件使用同一套结构。**SaaS 文档风**：Inter + Noto Sans SC 字体，样式仅来自 `assets/style.css`，禁止 inline style。

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>{页面标题} · {目标名称}</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Noto+Sans+SC:wght@400;500;600;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="{相对路径}/assets/style.css">
</head>
<body>
  <main>
    <!-- index / exam / result 用 .hero；modules 页用 .meta + h1 -->
    <!-- 正文 -->
    <nav class="footer-nav">
      <a href="../index.html">← 返回学习路径</a>
    </nav>
  </main>
</body>
</html>
```

相对路径：`index.html` 用 `assets/style.css`；`modules/` 下用 `../assets/style.css`；`exams/`、`results/` 同理。

### index.html Hero 区块（PLAN 必须）

```html
<header class="hero">
  <p class="meta"><span class="badge">学习路径</span> 预计 {N} 周</p>
  <h1>{目标名称}</h1>
  <p class="hero-desc">{一句话能力目标，≤ 40 字}</p>
  <div class="stats">
    <div class="stat"><span class="stat-num">{N}</span><span class="stat-label">模块</span></div>
    <div class="stat"><span class="stat-num">{N}</span><span class="stat-label">核心</span></div>
    <div class="stat"><span class="stat-num">{N}h</span><span class="stat-label">预计学时</span></div>
  </div>
</header>
```

模块总览表用 `.table-wrap` 包裹：`<div class="table-wrap"><table>...</table></div>`。

## 各阶段 HTML 要求

### index.html（PLAN）

- **`.hero` 区块**：badge、标题、`.hero-desc`、`.stats` 三栏统计（模块数 / 核心数 / 预计学时）
- 能力目标列表
- 模块总览表（`.table-wrap` 包裹；模块 ID、名称、学完应能做什么、预计学时、是否核心 ★）
- **每模块 `.module-outline` 卡片**：
  - **`.module-header`**：`.module-id`（如 M2）+ `h3` 标题 + 核心 badge
  - 3 条可测量学习目标（缩写）
  - **精选 3 条**学习链接（完整 URL，带类型 badge）
  - 「查看完整模块 →」链到 `modules/m{x}-*.html`
- 里程碑时间线
- 下一步提示（直接学模块 / 深化 Mx / 开始考试）
- 免责声明（`.note`，非官方认证）

### modules/m{x}-*.html（PLAN 纲要 + STUDY 深化）

**PLAN 阶段必须生成**（纲要页）：

- 模块概览（学时、前置、核心 badge）
- 学习目标 3–5 条
- 知识点明细 3–6 小节（每节要点列表；编程类配短代码示例）
- **`.resource-table` 资源表**（4–8 条真实链接，含类型/名称/说明/打开链接）
- 建议学习顺序（有序列表）
- 本节小结 + 链回 index.html

**STUDY 深化时追加**：

- 常见误区（`.card`）
- 练习任务 1–2 个（`.card`，含验收标准）
- 自检题 3 道（`.question`，无标准答案）

资源链接规范见 [learning-resources.md](learning-resources.md)。

模块页最小骨架：

```html
<p class="meta"><span class="badge">模块</span> M2 · 面向对象</p>
<h1>面向对象</h1>
<section class="module-outline">
  <p class="outline-meta"><span class="badge core">核心</span> 预计 10h · 前置 M1</p>
</section>
<h2>学习目标</h2>
<ul>...</ul>
<h2>知识点明细</h2>
<h3>2.1 类与对象</h3>
<ul>...</ul>
<h2>推荐学习资源</h2>
<div class="table-wrap">
  <table class="resource-table">...</table>
</div>
<h2>建议学习顺序</h2>
<ol class="learning-path">...</ol>
```

### exams/exam-{id}.html（EXAM）

- **`.hero` 区块**：badge「结业考试」、试卷标题、`.hero-desc`（模式、及格线、时长建议）
- 考试说明（ID、模式、及格线、时长建议；可并入 hero-desc）
- 每题 `.question` 区块：
  - 题头：Qn、模块、难度、分值、题型 badge
  - 题干（代码用 `<pre><code>`）
  - 选择题：`.options` 列表
  - 简答/代码题：`<textarea class="answer-area" placeholder="在此作答…">`（供用户本地记录，提交时在对话中粘贴）
- 页脚提示：「在 Cursor 对话中按 Q1: 答案 格式提交，完成后说 提交阅卷」
- **禁止**出现答案、Rubric、解析

### results/result-{id}.html（GRADE）

- **`.score-hero` 区块**：`.score-value`（大号分数）、`.score-total`（/ 100）、结论 badge（pass / fail）
- 模块得分表（`.table-wrap` 包裹）+ `.score-bar` 进度条
- 逐题得分与解析（含错题要点）
- 未通过：复习清单 + 补考说明
- 通过：后续进阶建议

## 创建与打开

1. 首次 PLAN：创建目录、复制 `assets/style.css`、写 `state.json` 与 `index.html`
2. 每次生成 HTML 后更新 `state.json` 的 `phase` 与 `updated`
3. 告知用户 HTML 绝对路径，并尝试在 Windows 用 `start "" "{path}"` 打开浏览器（失败则仅给路径）

## 对话中的回复

- 正文简短摘要（3–5 句）+ HTML 文件路径
- 不要在大段对话里重复 HTML 全文
- 末尾仍附 `learning-state` HTML 注释块（与 state.json 同步），便于无文件时的降级恢复

```html
<!-- learning-state
goal: php-backend
phase: EXAM
...
-->
```
