# AI测试项目 - 优化提示词手册

## 📋 项目概述

AI测试项目是基于AI专家库的软件测试工作平台，覆盖测试全生命周期。
- **项目路径**: `d:\AIproject\ai-test-project\`
- **测试环境**: 预发布环境(pre)
- **测试工具**: Playwright CLI + Chrome DevTools MCP

---

## 🎯 测试工作流

```
需求分析 → 测试用例生成(Xmind) → 测试执行(Playwright CLI) → 测试报告生成(HTML)
    ↓              ↓                      ↓                      ↓
project-    technical-writer        playwright-cli       allure-report-generator
manager     +xmind-generator       +api-tester         +test-results-analyzer
```

---

## 🚀 启动测试的标准提示词

### 模板1：启动完整测试项目

```
请帮我测试 {系统名称}：

1. 需求文档路径: {PRD文档路径}
2. 测试类型: {功能测试/UI测试/性能测试/API测试}
3. 测试地址: {被测系统URL}
4. 测试账号: {账号}
5. 测试密码: {密码}

执行流程：
1. 使用 test-project-manager 分析需求并创建测试任务清单
2. 使用 xmind-generator 生成Xmind格式测试用例
3. 使用 playwright-cli 执行UI自动化测试
4. 使用 allure-report-generator 生成HTML格式测试报告
5. 每个步骤完成后必须汇报进度和结果

输出要求：
- 测试用例必须为Xmind格式 (Markdown)
- 测试报告必须同时生成 Markdown 和 HTML 两种格式
- 所有截图保存到 reports/ 目录
```

### 模板2：执行UI自动化测试

```
使用 Playwright CLI 执行UI自动化测试：

1. 打开浏览器并访问: {URL}
2. 登录系统（账号: {账号}, 密码: {密码}）
3. 执行以下测试步骤:
   - 步骤1: {操作描述}
   - 步骤2: {操作描述}
   - ...
4. 每个关键操作后截图保存
5. 记录测试结果和发现的问题

截图保存路径: d:\AIproject\ai-test-project\reports\
截图命名规范: {模块名}-{功能点}-{序号}.png
```

### 模板3：生成测试用例(Xmind格式)

```
请生成Xmind格式的测试用例：

1. 系统名称: {系统名称}
2. 功能模块:
   - 模块1: {模块描述}
   - 模块2: {模块描述}
3. 优先级要求:
   - P0: {核心功能}
   - P1: {重要功能}
   - P2: {一般功能}

格式要求：
- 使用Markdown格式，Xmind可直接导入
- 一级标题 (#) = 中心主题
- 二级标题 (##) = 一级分支
- 三级标题 (###) = 二级分支
- 四级标题 (####) = 三级分支

输出文件: d:\AIproject\ai-test-project\reports\test-cases-{模块名}-xmind.md
```

### 模板4：生成HTML测试报告

```
请生成HTML格式的测试报告：

1. 测试项目: {项目名称}
2. 测试日期: {日期}
3. 测试人员: {人员}
4. 测试数据:
   - 用例总数: {N}
   - 通过数: {N}
   - 失败数: {N}
   - 阻塞数: {N}
5. 缺陷列表: {列表}
6. 截图路径: {路径}

报告要求：
- 响应式HTML布局
- 专业美观的CSS样式
- 测试数据表格展示
- 缺陷统计可视化
- 可交互元素

输出文件: d:\AIproject\ai-test-project\reports\test-report-{模块名}-{日期}.html
```

---

## 📁 项目结构

```
ai-test-project/
├── .trae/
│   ├── agents/                    # AI专家Agent (20个)
│   │   ├── agents-orchestrator/   # 智能编排者
│   │   ├── test-orchestrator/     # 🆕 测试编排者
│   │   ├── test-project-manager/ # 🆕 测试项目经理
│   │   ├── technical-writer/     # 技术文档工程师
│   │   ├── code-reviewer/        # 代码审查
│   │   ├── senior-developer/     # 高级开发
│   │   ├── api-tester/           # API测试
│   │   ├── playwright-cli/        # UI自动化测试
│   │   ├── test-results-analyzer/# 测试结果分析
│   │   ├── evidence-collector/   # 证据收集
│   │   └── ... (其他Agent)
│   │
│   └── skills/                    # 技能库
│       ├── playwright-cli/        # UI自动化Skill
│       ├── xmind-generator/       # 🆕 Xmind生成Skill
│       └── allure-report-generator/# 🆕 HTML报告生成Skill
│
├── docs/                         # 测试文档
├── reports/                      # 测试报告
│   ├── test-cases-*-xmind.md    # Xmind格式测试用例
│   ├── test-report-*.md         # Markdown报告
│   └── test-report-*.html       # HTML报告
└── screenshots/                  # 测试截图
```

---

## 🛠️ 可用工具与命令

### Playwright CLI

```bash
# 安装
npm install -g playwright
npx playwright install chromium --with-deps

# 基本命令
npx playwright open <URL>         # 打开浏览器
npx playwright snapshot           # 获取页面快照
npx playwright click <element>    # 点击元素
npx playwright fill <element> <text> # 填写表单
npx playwright screenshot          # 截图
npx playwright close              # 关闭浏览器
```

### Xmind格式转换

```bash
# Markdown转Xmind
# Xmind支持直接导入Markdown文件
# 格式要求：
#   # = 中心主题
#   ## = 一级分支
#   ### = 二级分支
#   #### = 三级分支
```

### Allure Report

```bash
# 安装
npm install -g allure

# 生成报告
npx allure generate ./allure-results -o ./allure-report
npx allure open ./allure-report
```

---

## 📊 Agent职责速查表

| Agent | 职责 | 输入 | 输出 |
|-------|------|------|------|
| test-orchestrator | 测试工作流编排 | 测试需求 | 进度报告 |
| test-project-manager | 测试任务规划 | PRD文档 | 任务清单 |
| technical-writer | 测试用例编写 | 需求分析 | 详细用例 |
| xmind-generator | Xmind格式转换 | 测试用例 | Xmind.md |
| playwright-cli | UI自动化测试 | 用例+URL | 截图+结果 |
| api-tester | API测试 | API文档 | 测试结果 |
| test-results-analyzer | 结果分析 | 测试数据 | 分析报告 |
| allure-report-generator | HTML报告 | 测试数据 | HTML报告 |
| evidence-collector | 证据收集 | 测试过程 | 截图+日志 |

---

## 📝 测试用例Xmind格式模板

```markdown
# {系统名称}测试用例

## 一、{模块名称}

### 1.1 {子模块名称}

#### 1.1.1 {功能点}
- 用例：账户余额展示 (P0)
- 用例：余额显示/隐藏切换 (P1)
- 用例：提现功能-正常状态 (P0)
- 用例：提现功能-受限状态 (P0)

#### 1.1.2 {功能点}
- 用例：缴纳保证金入口 (P0)
- 用例：网银转账-填写金额 (P0)
- 用例：网银转账-上传凭证 (P1)

## 二、{模块名称}

### 2.1 {子模块名称}

#### 2.1.1 {功能点}
- 用例：配置列表展示 (P0)
- 用例：添加配置 (P0)
- 用例：编辑配置 (P1)
- 用例：删除配置 (P1)

---
**生成时间**: {timestamp}
**用例总数**: {count}
**优先级**: P0=核心 P1=重要 P2=一般
```

---

## 📄 测试报告HTML模板

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{项目名称} - 测试报告</title>
    <style>
        :root {
            --primary: #2c3e50;
            --success: #27ae60;
            --danger: #e74c3c;
            --warning: #f39c12;
            --info: #3498db;
            --light: #ecf0f1;
            --dark: #2c3e50;
        }
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            margin: 0;
            padding: 20px;
            background: #f5f6fa;
            color: #2c3e50;
        }
        .container { max-width: 1200px; margin: 0 auto; }
        .header {
            background: linear-gradient(135deg, var(--primary), var(--info));
            color: white;
            padding: 30px;
            border-radius: 12px;
            margin-bottom: 30px;
        }
        .header h1 { margin: 0 0 10px; font-size: 28px; }
        .header p { margin: 0; opacity: 0.9; }
        .metrics {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        .metric-card {
            background: white;
            padding: 25px;
            border-radius: 12px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.08);
            text-align: center;
        }
        .metric-card .number {
            font-size: 42px;
            font-weight: bold;
            margin-bottom: 5px;
        }
        .metric-card .label {
            color: #7f8c8d;
            font-size: 14px;
        }
        .metric-card.passed .number { color: var(--success); }
        .metric-card.failed .number { color: var(--danger); }
        .metric-card.blocked .number { color: var(--warning); }
        .card {
            background: white;
            border-radius: 12px;
            padding: 25px;
            margin-bottom: 20px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.08);
        }
        .card h2 {
            margin: 0 0 20px;
            padding-bottom: 15px;
            border-bottom: 2px solid var(--light);
            color: var(--primary);
        }
        table {
            width: 100%;
            border-collapse: collapse;
        }
        th, td {
            padding: 12px 15px;
            text-align: left;
            border-bottom: 1px solid var(--light);
        }
        th {
            background: var(--primary);
            color: white;
            font-weight: 600;
        }
        tr:hover { background: #f8f9fa; }
        .badge {
            display: inline-block;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
        }
        .badge-p0 { background: #e74c3c; color: white; }
        .badge-p1 { background: #f39c12; color: white; }
        .badge-p2 { background: #3498db; color: white; }
        .badge-passed { background: #27ae60; color: white; }
        .badge-failed { background: #e74c3c; color: white; }
        .badge-blocked { background: #f39c12; color: white; }
        .screenshot-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
        }
        .screenshot-item {
            background: var(--light);
            border-radius: 8px;
            padding: 10px;
        }
        .screenshot-item img {
            width: 100%;
            border-radius: 6px;
        }
        .screenshot-item .desc {
            margin-top: 10px;
            font-size: 14px;
            color: #7f8c8d;
        }
        .conclusion {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 30px;
            border-radius: 12px;
        }
        .conclusion h2 { margin-top: 0; }
        .footer {
            text-align: center;
            margin-top: 40px;
            color: #7f8c8d;
            font-size: 14px;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>{项目名称} - 测试报告</h1>
            <p>测试日期: {日期} | 测试人员: {人员} | 测试环境: {环境}</p>
        </div>

        <div class="metrics">
            <div class="metric-card">
                <div class="number">{总数}</div>
                <div class="label">用例总数</div>
            </div>
            <div class="metric-card passed">
                <div class="number">{通过数}</div>
                <div class="label">通过</div>
            </div>
            <div class="metric-card failed">
                <div class="number">{失败数}</div>
                <div class="label">失败</div>
            </div>
            <div class="metric-card blocked">
                <div class="number">{阻塞数}</div>
                <div class="label">阻塞</div>
            </div>
        </div>

        <div class="card">
            <h2>功能模块覆盖</h2>
            <table>
                <thead>
                    <tr>
                        <th>模块</th>
                        <th>状态</th>
                        <th>覆盖率</th>
                        <th>通过率</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>商家后台-账户管理</td>
                        <td><span class="badge badge-passed">已完成</span></td>
                        <td>25%</td>
                        <td>100%</td>
                    </tr>
                    <tr>
                        <td>运营平台-配置管理</td>
                        <td><span class="badge badge-passed">已完成</span></td>
                        <td>100%</td>
                        <td>100%</td>
                    </tr>
                </tbody>
            </table>
        </div>

        <div class="card">
            <h2>缺陷列表</h2>
            <table>
                <thead>
                    <tr>
                        <th>缺陷ID</th>
                        <th>描述</th>
                        <th>严重程度</th>
                        <th>状态</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>BUG-001</td>
                        <td>商家账号未开通资金账户</td>
                        <td><span class="badge badge-p0">P0</span></td>
                        <td><span class="badge badge-blocked">开放</span></td>
                    </tr>
                </tbody>
            </table>
        </div>

        <div class="card">
            <h2>测试截图</h2>
            <div class="screenshot-grid">
                <div class="screenshot-item">
                    <img src="screenshots/admin-bond-config.png" alt="配置管理">
                    <div class="desc">图1: 保证金配置管理</div>
                </div>
                <div class="screenshot-item">
                    <img src="screenshots/admin-bond-detail.png" alt="明细查询">
                    <div class="desc">图2: 保证金明细查询</div>
                </div>
            </div>
        </div>

        <div class="card conclusion">
            <h2>测试结论</h2>
            <p>{结论内容}</p>
            <h3>建议</h3>
            <ol>
                <li>补充测试数据</li>
                <li>完善商家账号权限</li>
                <li>继续完善UI自动化</li>
            </ol>
        </div>

        <div class="footer">
            <p>报告生成时间: {timestamp}</p>
            <p>报告版本: V1.0 | AI Testing Agent</p>
        </div>
    </div>
</body>
</html>
```

---

## ✅ 检查清单

启动测试前请确认：

- [ ] PRD文档路径正确
- [ ] 测试环境可访问
- [ ] 测试账号可用
- [ ] 截图保存目录存在
- [ ] Playwright CLI已安装

---

**文档版本**: V1.1
**更新日期**: 2026-04-22
**维护者**: AI Testing Team
