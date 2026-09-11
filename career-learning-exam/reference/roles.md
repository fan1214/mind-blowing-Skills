# 常见岗位模块模板

Agent 识别到对应岗位时，可据此快速生成模块骨架，再按用户水平与时间微调。

**PLAN 阶段**：为每模块生成纲要 HTML（知识点明细 + 4–8 条真实学习链接）；`index.html` 用 `.module-outline` 展示摘要与 3 条精选链接。链接起点见 [learning-resources.md](learning-resources.md)。

**STUDY 阶段**：在纲要页上追加练习、误区与自检题。

## PHP 后端开发（programming）

| 模块 | 学完应能做什么 | 核心 |
|------|----------------|------|
| M1 PHP 基础 | 写变量、流程控制、函数与数组操作 | |
| M2 面向对象 | 定义类、继承、接口、命名空间与自动加载 | ★ |
| M3 Web 与 HTTP | 理解请求/响应、表单、Session/Cookie、REST 概念 | ★ |
| M4 数据库 | 用 PDO 做 CRUD、简单 JOIN、防 SQL 注入 | ★ |
| M5 框架入门 | 用 Laravel/Symfony 之一完成路由、控制器、视图 | |
| M6 部署与安全 | 配置 Nginx+PHP-FPM、环境变量、常见 OWASP 防护 | |

## 前端开发 React（programming）

| 模块 | 学完应能做什么 | 核心 |
|------|----------------|------|
| M1 HTML/CSS/JS | 语义化布局、Flex/Grid、ES6+ 基础 | |
| M2 React 基础 | 组件、Props、State、事件与列表渲染 | ★ |
| M3 Hooks 与状态 | useEffect、自定义 Hook、Context 或轻量状态库 | ★ |
| M4 路由与数据 | React Router、fetch/axios、Loading 与错误态 | ★ |
| M5 工程化 | Vite/CRA、组件拆分、简单测试 | |
| M6 性能与可访问性 | memo、懒加载、基础 a11y | |

## 数据分析（mixed）

| 模块 | 学完应能做什么 | 核心 |
|------|----------------|------|
| M1 Excel/表格 | 透视、常用函数、数据清洗 | |
| M2 SQL | SELECT/JOIN/GROUP BY、子查询 | ★ |
| M3 Python 基础 | pandas 读写的 DataFrame 操作 | ★ |
| M4 可视化 | 用 matplotlib/plotly 做常见图表 | |
| M5 统计基础 | 描述统计、假设检验概念 | ★ |
| M6 业务分析 | 从问题到指标、简单分析报告 | |

## 产品经理（mixed）

| 模块 | 学完应能做什么 | 核心 |
|------|----------------|------|
| M1 需求分析 | 用户故事、验收标准、优先级 | ★ |
| M2 原型与流程 | 画用户流程、低保真原型 | |
| M3 文档写作 | PRD 结构、非功能需求 | ★ |
| M4 数据与指标 | 北极星指标、漏斗、A/B 概念 | ★ |
| M5 协作沟通 | 与研发/design 协作、评审节奏 | |
| M6 上线与迭代 | 发布清单、复盘、版本规划 | |

## 通用规则

- 转行/就业：核心模块偏实战（M3–M5）
- 兴趣/hobby：可减少 M6 或合并模块为 4–5 个
- 有基础：诊断后可跳过 M1，权重转移到核心模块
