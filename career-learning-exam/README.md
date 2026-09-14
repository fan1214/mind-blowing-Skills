# career-learning-exam

Cursor Agent Skill：根据**职业或技能目标**生成 HTML 学习路径、带真实链接的模块课件、结业试卷与成绩报告；支持补考与 `state.json` 进度持久化。

> Agent 执行细则见 [SKILL.md](./SKILL.md)。本文面向**安装、使用与目录说明**。

## 能做什么

| 能力 | 说明 |
|------|------|
| 学习路径 | PLAN 阶段生成 `index.html` + 各模块纲要页 |
| 模块深化 | STUDY 阶段追加练习、误区、自检题 |
| 结业考试 | EXAM 阶段 HTML 试卷 + Agent 专用 Rubric |
| 阅卷报告 | GRADE 阶段 HTML 成绩与复习建议 |
| 样式 | SaaS 文档风，accent `#0070F3`，内容区最大宽度 1200px |

## 安装

将本目录**整份复制**到 Cursor Skills 路径之一：

| 范围 | 路径 |
|------|------|
| 全局（推荐） | `~/.cursor/skills/career-learning-exam/` |
| 仅当前项目 | `<项目>/.cursor/skills/career-learning-exam/` |

Windows 全局示例：

```text
C:\Users\<用户名>\.cursor\skills\career-learning-exam\
```

安装后新开 Agent 对话即可触发；未生效时重启 Cursor 或新开会话。

## 怎么用

在 Agent 里用自然语言描述目标，例如：

```text
我想做 FDE 工程师，有 Python 基础，3 个月。
```

### 常用指令

| 你说 | 阶段 | 产出 |
|------|------|------|
| （首次描述学习目标） | PLAN | `index.html` + `modules/m*.html` |
| 展开 M3 / 深化 M3 | STUDY | 该模块练习与自检题 |
| 开始考试 / 补考 | EXAM | `exams/exam-*.html` |
| Q1:A … 提交阅卷 | GRADE | `results/result-*.html` |

从上次进度继续：在对话中 `@` 引用 `.cursor/learning/{goal-slug}/` 下的 HTML 或 `state.json`。

### 学习产物位置

生成内容在**当前打开的项目**内，不在 Skill 目录里：

```text
.cursor/learning/{goal-slug}/
├── state.json
├── index.html
├── assets/style.css          # 从本 skill 的 assets/style.css 复制
├── modules/
├── exams/
└── results/
```

**建议**在项目根 `.gitignore` 中加入 `.cursor/learning/`，避免个人学习文件进仓库。

## 样式预览

本地打开演示页查看 SaaS 组件效果：

```text
career-learning-exam/demo/preview.html
```

更新 Skill 后，已有 learning 工作区需**手动覆盖** `assets/style.css`，或重新 PLAN。

## 目录结构

```text
career-learning-exam/
├── README.md                 # 本文件（给人看）
├── SKILL.md                  # Agent 主指令（给模型看）
├── examples.md               # 完整流程示例
├── demo/
│   └── preview.html          # 样式预览
├── assets/
│   └── style.css             # 学习工作区样式源文件
└── reference/
    ├── html-guide.md         # HTML 结构与各阶段要求
    ├── learning-resources.md # 链接与模块明细规范
    ├── roles.md              # 常见岗位模块模板
    └── rubric-examples.md    # 阅卷 Rubric 示例
```

## 考试规则（摘要）

- 15–25 题，满分 100；核心模块题量 ≥ 40%
- **通过**：总分 ≥ 80，各核心模块 ≥ 60%，无 ≥8 分大题得 0 分
- 模式：`full`（整卷）或 `gate`（闯关）；最多 2 次补考
- 试卷 HTML **不含答案**；Rubric 仅在 `exams/*-rubric.md`

## 适用 / 不适用

| 适合 | 不适合 |
|------|--------|
| 系统学某岗位或技能 | 单次知识点问答 |
| 要路径 + 链接 + 结业考 | 只要资源列表、不要考试 |
| 能力测评与补考 | 从 PRD 生成软件测试用例 |

## 维护 Skill

- 改行为：编辑 `SKILL.md` 与 `reference/*`
- 改外观：编辑 `assets/style.css`，并同步到已安装的 `~/.cursor/skills/career-learning-exam/`
- 改触发条件：调整 `SKILL.md` frontmatter 中的 `description`

## 许可

与仓库一致：[MIT License](../LICENSE)
