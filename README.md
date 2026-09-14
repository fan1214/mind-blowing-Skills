# mind-blowing-Skills

面向 [Cursor](https://cursor.com) 的 Agent Skills 集合。每个 Skill 为 Agent 提供结构化指令，使其在特定场景下按统一规范产出高质量结果。

当前包含 **career-learning-exam** —— 根据职业或技能目标，生成 HTML 学习路径、模块课件、结业试卷与成绩报告，并支持补考与进度持久化。

## 特性

- **四阶段状态机**：`PLAN` → `STUDY` → `EXAM` → `GRADE`，每轮只做一件事，流程清晰
- **HTML 交付物**：学习路径、模块详情、试卷、成绩报告均为独立 HTML，浏览器直接打开
- **真实学习链接**：每模块 4–8 条可点击资源（官方文档、教程、练习等），禁止占位符
- **Rubric 阅卷**：试卷与评分标准分离，支持整卷与闯关两种考试模式
- **进度持久化**：`.cursor/learning/{goal-slug}/state.json` 记录阶段、模块与考试状态

## 快速开始

### 1. 安装 Skill

将本仓库克隆或复制到 Cursor Skills 目录：

```bash
git clone git@github.com:fan1214/mind-blowing-Skills.git
```

**方式 A — 项目级**（仅当前项目可用）：

```text
<你的项目>/.cursor/skills/career-learning-exam/
```

**方式 B — 全局**（所有项目可用）：

```text
~/.cursor/skills/career-learning-exam/
```

将 `career-learning-exam/` 整个目录复制到上述路径之一即可。

### 2. 在 Cursor 中使用

在 Agent 对话中描述你的学习目标，例如：

```text
我想做 PHP 后端开发，零基础，大概 2 个月。
```

Agent 会识别 Skill 并进入 `PLAN` 阶段，生成学习路径 HTML 与工作区。后续可继续：

| 你说 | Agent 阶段 | 产出 |
|------|-----------|------|
| 展开 M2 / 深化 M2 | STUDY | 模块练习、误区、自检题 |
| 开始考试 / 出题 | EXAM | 试卷 HTML（无答案） |
| 提交答案 / 阅卷 | GRADE | 成绩报告 HTML |

也可 `@` 引用 `.cursor/learning/{goal-slug}/` 下的文件，从上次进度继续。

### 3. 查看产物

首次 PLAN 完成后，工作区结构如下：

```text
.cursor/learning/{goal-slug}/
├── state.json              # Agent 状态（阶段、模块、考试 ID）
├── index.html              # 学习路径总览
├── assets/style.css        # 样式表
├── modules/
│   └── m1-*.html           # 各模块纲要 / 深化页
├── exams/
│   ├── exam-{id}.html      # 试卷（用户可见）
│   └── exam-{id}-rubric.md # 评分标准（仅 Agent 阅卷用）
└── results/
    └── result-{id}.html    # 成绩报告
```

用浏览器打开 `index.html` 即可开始学习。

## 项目结构

```text
mind-blowing-Skills/
├── README.md
├── LICENSE
└── career-learning-exam/
    ├── README.md                       # Skill 使用说明（给人看）
    ├── SKILL.md                        # Skill 主指令（Agent 读取）
    ├── examples.md                     # 完整流程示例（PHP 后端）
    ├── demo/preview.html               # SaaS 样式预览
    ├── assets/
    │   └── style.css                   # 学习工作区共享样式
    └── reference/
        ├── html-guide.md               # HTML 产物规范
        ├── learning-resources.md       # 学习链接与模块明细规范
        ├── roles.md                    # 常见岗位模块模板
        └── rubric-examples.md          # Rubric 评分示例
```

## 适用场景

| 适合 | 不适合 |
|------|--------|
| 系统学习某职业或技能 | 单次知识点问答 |
| 要学习计划、学习路径 | 从需求文档生成测试用例 |
| 学完要求出题、考试、测评 | 只要资源推荐、不要路径与考试 |
| 提交答案要求判定是否通过 | |

## 支持的岗位类型

Skill 内置常见岗位模块模板（见 `reference/roles.md`），包括：

- **programming**：PHP 后端、前端 React 等
- **mixed**：数据分析、产品经理等
- **theory**：会计、法务等理论岗

不确定时按 `mixed` 处理，Agent 会根据目标自动选择模块骨架与考试配比。

## 考试规则摘要

- 总题 15–25 道，满分 100，覆盖所有模块
- **通过条件**：总分 ≥ 80，每个核心模块 ≥ 60%，无大题（≥ 8 分）得 0 分
- **考试模式**：`full`（一次出全卷）或 `gate`（闯关，每模块 ≥ 80% 解锁下一模块）
- 最多 2 次补考

## 开发说明

本仓库按 [Cursor Agent Skills](https://cursor.com/docs/context/skills) 规范组织。新增 Skill 时：

1. 在仓库根目录创建 `{skill-name}/` 目录
2. 编写 `SKILL.md`（含 YAML frontmatter：`name`、`description`）
3. 按需添加 `reference/`、`assets/`、`examples.md` 等辅助文件

`description` 字段决定 Agent 何时自动选用该 Skill，请写清楚触发场景。

## 许可证

[MIT License](LICENSE) · Copyright (c) 2026 fan1214
