# 完整流程示例：PHP 后端开发（HTML 产物）

## 工作区结构（PLAN 完成后）

```
.cursor/learning/php-backend/
├── state.json
├── index.html
├── assets/style.css
├── modules/
│   ├── m1-basics.html      # PLAN 即生成：知识点 + 资源链接
│   ├── m2-oop.html
│   └── ...（每模块一份纲要）
├── exams/
│   ├── exam-2026-09-10-001.html
│   └── exam-2026-09-10-001-rubric.md
└── results/
    └── result-2026-09-10-001.html
```

## 1. PLAN

**用户**：我想做 PHP 开发，零基础，2 个月。

**Agent**：
- 创建 workspace，复制 `style.css`
- 生成 `index.html`（6 模块总览 + 每模块 `.module-outline` 含 3 条精选链接）
- **为 M1–M6 各生成** `modules/m{x}-*.html`（知识点明细 + 完整资源表）
- 用 WebSearch 核实链接有效性
- 写 `state.json`（phase: PLAN, modules_generated: true）
- 回复摘要 + 路径，尝试打开浏览器

## 2. STUDY

**用户**：展开 M2

**Agent**：
- 读取 `modules/m2-oop.html`，追加常见误区、练习任务、3 道自检题
- 更新 `state.json`（phase: STUDY, modules_studied 含 M2）

## 3. EXAM

**用户**：开始考试

**Agent**：
- 生成 `exams/exam-2026-09-10-001.html`（20 题，含 textarea 作答区）
- 生成 `exams/exam-2026-09-10-001-rubric.md`（含 Rubric，不对用户展示）
- 更新 state（phase: EXAM, attempt: 1）

## 4. GRADE

**用户**：Q1:B … Q20:（代码）提交阅卷

**Agent**：
- 按 rubric 评分
- 生成 `results/result-2026-09-10-001.html`（模块条形图、逐题解析、未通过补考说明）
- 更新 state（phase: GRADE）

## index.html 片段示例

```html
<h2>学习模块</h2>
<table>
  <thead>
    <tr><th>模块</th><th>学完应能做什么</th><th>预计学时</th><th></th></tr>
  </thead>
  <tbody>
    <tr>
      <td>M1 PHP 基础</td>
      <td>写变量、流程控制与函数</td>
      <td>8h</td>
      <td></td>
    </tr>
    <tr>
      <td>M2 面向对象</td>
      <td>定义类、接口与命名空间</td>
      <td>10h</td>
      <td><span class="badge core">核心</span></td>
    </tr>
  </tbody>
</table>

<section class="module-outline" id="m2">
  <h3>M2 面向对象 <span class="badge core">核心</span></h3>
  <p class="outline-meta">预计 10 小时 · 前置：M1</p>
  <ul>
    <li>能定义类、属性、方法与访问修饰符</li>
    <li>能使用继承、接口与 trait 组织代码</li>
    <li>能配置 PSR-4 自动加载</li>
  </ul>
  <ul class="link-preview">
    <li><span class="badge res-official">官方</span>
      <a href="https://www.php.net/manual/zh/language.oop5.php" target="_blank" rel="noopener">PHP OOP 手册</a>
      — 类与对象权威参考</li>
    <li><span class="badge res-read">阅读</span>
      <a href="https://phptherightway.com/" target="_blank" rel="noopener">PHP The Right Way</a>
      — OOP 与最佳实践</li>
    <li><span class="badge res-lab">练习</span>
      <a href="https://www.php.net/manual/zh/language.oop5.php" target="_blank" rel="noopener">动手：实现 User 类</a>
      — 见模块页练习任务</li>
  </ul>
  <p class="module-link"><a href="modules/m2-oop.html">查看完整模块 →</a></p>
</section>
```

## modules/m2-oop.html 资源表示例

```html
<h2>推荐学习资源</h2>
<table class="resource-table">
  <thead>
    <tr><th>类型</th><th>名称</th><th>说明</th><th>链接</th></tr>
  </thead>
  <tbody>
    <tr>
      <td><span class="badge res-official">官方</span></td>
      <td>PHP 类与对象</td>
      <td>语法、继承、抽象类、接口；建议分 2 次读完</td>
      <td><a href="https://www.php.net/manual/zh/language.oop5.php" target="_blank" rel="noopener">打开</a></td>
    </tr>
    <tr>
      <td><span class="badge res-doc">文档</span></td>
      <td>PSR-4 自动加载</td>
      <td>理解命名空间与 Composer autoload 约定</td>
      <td><a href="https://www.php-fig.org/psr/psr-4/" target="_blank" rel="noopener">打开</a></td>
    </tr>
    <tr>
      <td><span class="badge res-video">视频</span></td>
      <td>freeCodeCamp PHP OOP</td>
      <td>英文视频，约 2h，适合跟练</td>
      <td><a href="https://www.youtube.com/watch?v=OK_JCtrrv-c" target="_blank" rel="noopener">打开</a></td>
    </tr>
    <tr>
      <td><span class="badge res-lab">练习</span></td>
      <td>Exercism PHP Track</td>
      <td>小型 OOP 练习题，带 mentor 反馈</td>
      <td><a href="https://exercism.org/tracks/php" target="_blank" rel="noopener">打开</a></td>
    </tr>
  </tbody>
</table>

<h2>建议学习顺序</h2>
<ol class="learning-path">
  <li>阅读 PHP 官方 OOP 章节「类的基础」与「继承」</li>
  <li>跟做 freeCodeCamp 视频中 User/Admin 类示例</li>
  <li>阅读 PSR-4，用 Composer 创建带命名空间的小项目</li>
  <li>在 Exercism 完成 2 道 OOP 题</li>
</ol>
```

## 与 teach Skill 的差异

| | career-learning-exam | teach |
|--|---------------------|-------|
| 产物 | 路径 + **带链接的模块明细** + 试卷 + 成绩 HTML | 多节 lesson HTML |
| 目标 | 岗位能力达标 + 结业考 | 深度掌握某主题 |
| 链接 | PLAN 即给出每模块 4–8 条真实 URL | 视主题而定 |
| 结业判定 | 有（Rubric + 及格线） | 无 |
| 状态 | state.json | MISSION.md + learning-records |
