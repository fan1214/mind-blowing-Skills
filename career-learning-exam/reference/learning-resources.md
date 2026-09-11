# 模块学习资源与链接规范

每个模块的 HTML **必须**包含可点击的真实学习链接，禁止占位符（如 `example.com`、`TODO`、`链接待补充`）。

## 链接质量要求

| 优先级 | 类型 | 示例来源 |
|--------|------|----------|
| 1 | 官方文档 | MDN、PHP.net、React.dev、Laravel.com、MySQL Docs、Python.org |
| 2 | 权威教程 | freeCodeCamp、Microsoft Learn、Google Developers、W3Schools（入门） |
| 3 | 优质中文 | 菜鸟教程、廖雪峰、Runoob、B 站官方/高赞系列（附 BV 号或完整 URL） |
| 4 | 实战练习 | LeetCode、Exercism、HackerRank、Kaggle Learn、官方 Quickstart |
| 5 | 深度阅读 | OWASP、12factor、Martin Fowler 文章、官方 Blog |

### 必做

- 每模块 **至少 4 条、至多 8 条** 链接，覆盖 ≥2 种资源类型
- 每条链接含：**标题**、**URL**、**类型 badge**、**一句话说明**（学什么、约多久）
- 优先 HTTPS；同一模块内避免重复域名堆砌
- 用户水平/语言偏好明确时，优先匹配（如零基础 → 入门视频；中文用户 → 中英各至少 1 条）
- 不确定链接是否有效时，**用 WebSearch 检索**后再写入；勿凭记忆编造 URL

### 禁止

- 虚假、过期、需付费且无说明的链接
- 仅写「Google 一下」「自行搜索」代替具体 URL
- 盗版、破解站、侵权资源

## 每模块明细结构（纲要页与完整页共用）

生成 `modules/m{x}-*.html` 时按以下顺序组织：

### 1. 模块概览

- 预计学时（如 6–10 小时）
- 前置模块（无则写「无」）
- 核心/选修 badge

### 2. 学习目标（3–5 条，可测量）

动词开头，如「能写出…」「能解释…」「能独立完成…」。

### 3. 知识点明细

按 **3–6 个小节**（`<h3>`）展开，每节：

- 2–5 个要点（`<ul>`）
- 关键术语首次出现加粗
- 编程类模块：每 1–2 节配一个 **10 行以内** 的代码示例（`<pre><code>`）

### 4. 推荐学习资源（核心）

使用 `.resource-table` 表格，列：**类型 | 名称 | 说明 | 链接**

```html
<table class="resource-table">
  <thead>
    <tr><th>类型</th><th>名称</th><th>说明</th><th>链接</th></tr>
  </thead>
  <tbody>
    <tr>
      <td><span class="badge res-official">官方</span></td>
      <td>PHP 手册 — 语言参考</td>
      <td>语法与内置函数权威说明，可按章节阅读</td>
      <td><a href="https://www.php.net/manual/zh/" target="_blank" rel="noopener">打开</a></td>
    </tr>
  </tbody>
</table>
```

类型 badge 取值：

| class | 显示 | 用途 |
|-------|------|------|
| `res-official` | 官方 | 官方文档、规范 |
| `res-video` | 视频 | 课程、系列视频 |
| `res-doc` | 文档 | 第三方教程、电子书章节 |
| `res-lab` | 练习 | 动手实验、题库 |
| `res-read` | 阅读 | 文章、最佳实践 |

### 5. 建议学习顺序

 numbered list：先读什么 → 再做什么练习 → 最后验收什么能力。

### 6. 本节小结

3–5 句回顾 + 链回 `index.html`。

### STUDY 展开时额外追加（用户说「展开 Mx」或「深化 Mx」）

- **常见误区**（`.card` 2–4 条）
- **练习任务**（1–2 个 `.card`，含验收标准）
- **自检题** 3 道（无标准答案，`.question` 区块）

## 按 job_type 的链接策略

| job_type | 链接侧重 |
|----------|----------|
| `programming` | 官方文档 + 交互练习 + 1 个完整 Quickstart |
| `theory` | 教材章节/权威 PDF + 案例解读 + 法规/标准原文（如适用） |
| `mixed` | 概念文档 + 工具官方指南 + 1 个端到端案例 |

## 各岗位模块资源起点

Agent 可从此处起步，**仍须核对 URL 有效**并按用户目标替换。

### PHP 后端

| 模块 | 推荐链接起点 |
|------|--------------|
| M1 基础 | https://www.php.net/manual/zh/langref.php · https://www.w3schools.com/php/ |
| M2 OOP | https://www.php.net/manual/zh/language.oop5.php · https://phptherightway.com/ |
| M3 Web/HTTP | https://developer.mozilla.org/zh-CN/docs/Web/HTTP · https://www.php.net/manual/zh/features.session.php |
| M4 数据库 | https://www.php.net/manual/zh/book.pdo.php · https://dev.mysql.com/doc/ |
| M5 框架 | https://laravel.com/docs · https://symfony.com/doc/current/index.html |
| M6 部署安全 | https://owasp.org/www-project-top-ten/ · https://www.nginx.com/resources/wiki/start/ |

### 前端 React

| 模块 | 推荐链接起点 |
|------|--------------|
| M1 基础 | https://developer.mozilla.org/zh-CN/docs/Web · https://javascript.info/ |
| M2 React | https://react.dev/learn · https://zh-hans.react.dev/ |
| M3 Hooks | https://react.dev/reference/react · https://react.dev/learn/reusing-logic-with-custom-hooks |
| M4 路由数据 | https://reactrouter.com/en/main · https://axios-http.com/docs/intro |
| M5 工程化 | https://vitejs.dev/guide/ · https://vitest.dev/guide/ |
| M6 性能 a11y | https://web.dev/performance/ · https://developer.mozilla.org/zh-CN/docs/Web/Accessibility |

### 数据分析

| 模块 | 推荐链接起点 |
|------|--------------|
| M1 Excel | https://support.microsoft.com/excel · https://pandas.pydata.org/docs/user_guide/index.html#io-tools-text-csv-hdf5-excel-json |
| M2 SQL | https://sqlbolt.com/ · https://www.postgresql.org/docs/current/tutorial.html |
| M3 Python | https://pandas.pydata.org/docs/getting_started/ · https://jupyter.org/try-jupyter/lab/ |
| M4 可视化 | https://matplotlib.org/stable/tutorials/index.html · https://plotly.com/python/ |
| M5 统计 | https://www.khanacademy.org/math/statistics-probability · https://scipy-lectures.org/ |
| M6 业务分析 | https://www.kaggle.com/learn · https://amplitude.com/blog/north-star-metric |

### 产品经理

| 模块 | 推荐链接起点 |
|------|--------------|
| M1 需求 | https://www.atlassian.com/agile/project-management/user-stories · https://www.nngroup.com/articles/ux-user-stories/ |
| M2 原型 | https://www.figma.com/resource-library/ · https://www.nngroup.com/articles/task-analysis/ |
| M3 文档 | https://www.atlassian.com/agile/product-management/requirements · https://coda.io/@atlassian/prd-template |
| M4 指标 | https://amplitude.com/blog/north-star-metric · https://www.optimizely.com/optimization-glossary/ab-testing/ |
| M5 协作 | https://www.atlassian.com/team-playbook · https://basecamp.com/shapeup |
| M6 迭代 | https://www.atlassian.com/incident-management/postmortem · https://www.productplan.com/glossary/product-roadmap/ |

## index.html 中的模块摘要

PLAN 阶段在总览表之外，为每个模块增加 **`.module-outline` 卡片**，内含：

- 模块 ID + 名称
- 3 条学习目标（缩写版）
- **精选 3 条** 最重要链接（完整 URL）
- 「查看完整模块 →」链到 `modules/m{x}-*.html`

完整资源表放在模块 HTML 中，避免 index 过长。
