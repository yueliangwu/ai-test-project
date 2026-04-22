# AI Test Project - AI智能软件测试平台

基于AI专家库的软件测试工作平台，覆盖测试全生命周期：需求分析 → 测试用例生成(Xmind) → 测试执行(Playwright CLI) → 测试报告生成(HTML)。

---

## 📁 项目结构

```
ai-test-project/
├── .trae/
│   ├── agents/                      # AI专家Agent (18个)
│   │   ├── agents-orchestrator/     # 智能编排者
│   │   ├── project-shepherd/        # 项目牧羊人
│   │   ├── project-manager/         # 项目管理
│   │   ├── technical-writer/         # 技术文档工程师
│   │   ├── code-reviewer/            # 代码审查专家
│   │   ├── senior-developer/         # 高级开发工程师
│   │   ├── api-tester/              # API测试专家
│   │   ├── accessibility-auditor/   # 无障碍测试专家
│   │   ├── embedded-qa-engineer/    # 嵌入式QA工程师
│   │   ├── evidence-collector/       # 证据收集专家
│   │   ├── performance-benchmarker/ # 性能基准测试专家
│   │   ├── reality-checker/          # 实际验证专家
│   │   ├── test-results-analyzer/   # 测试结果分析师
│   │   ├── tool-evaluator/          # 工具评估专家
│   │   ├── workflow-optimizer/       # 流程优化专家
│   │   ├── data-engineer/           # 数据工程师
│   │   ├── jira-workflow-steward/   # Jira工作流管理
│   │   └── devops-automator/         # DevOps自动化专家
│   │
│   └── skills/                      # 技能库
│       └── playwright-cli/           # UI自动化测试Skill
│
├── docs/                            # 测试文档（PRD/需求）
│
├── test-cases/                      # 测试用例库
│   └── {日期}-{需求名称}/           # 按项目和日期组织
│       ├── test-cases-xmind.md     # Xmind格式测试用例
│       └── 测试用例-Xmind.md        # 中文版本
│
├── reports/                          # 测试报告库
│   └── {日期}-{需求名称}/           # 按项目和日期组织
│       ├── html/                    # HTML格式报告
│       │   └── test-report.html     # 可用浏览器直接打开
│       ├── markdown/                # Markdown格式报告
│       │   └── test-report.md       # Markdown报告
│       └── screenshots/             # 测试截图
│
├── PROMPT-HISTORY.md                # 提示词历史记录 ⚠️
│
└── scripts/                         # 测试脚本
```

---

## 🎯 测试工作流

```
┌─────────────────────────────────────────────────────────────────────┐
│                        AI智能测试工作流                              │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  ① 需求分析          ② 测试用例            ③ 测试执行          ④ 报告输出    │
│     ↓                   ↓                    ↓                  ↓        │
│  project-manager   technical-writer     playwright-cli      test-results-  │
│                     +llm-testing-       +api-tester         analyzer       │
│                       expert             +performance-       +technical-   │
│                                            benchmarker         writer       │
│                                                                     │
│  输出:                    输出:               输出:               输出:         │
│  docs/                 test-cases/       reports/            reports/       │
│  需求文档               {date}-{name}/     {date}-{name}/     {date}-{name}/  │
│                        xmind.md          screenshots/        html/          │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 🚀 快速开始

### 1. 启动测试项目

```
请帮我测试 {系统名称}：

1. 需求文档路径: docs/{日期}-{需求名称}/PRD文档.md
2. 测试类型: {功能测试/UI测试/性能测试/API测试}
3. 测试地址: {被测系统URL}
4. 测试账号: {账号}
5. 测试密码: {密码}

执行流程：
1. 使用 project-manager 分析需求并创建测试任务清单
2. 使用 technical-writer + llm-testing-expert 生成Xmind格式测试用例
3. 使用 playwright-cli 执行UI自动化测试
4. 使用 test-results-analyzer + technical-writer 生成测试报告
5. 每个步骤完成后必须汇报进度和结果

输出要求：
- 测试用例: test-cases/{日期}-{需求名称}/test-cases-xmind.md
- 测试报告: reports/{日期}-{需求名称}/html/test-report.html
- 截图: reports/{日期}-{需求名称}/screenshots/
```

### 2. UI自动化测试 (Playwright CLI)

```bash
# 安装依赖
npm install
npx playwright install chromium --with-deps

# 基本命令
npx playwright open <URL>         # 打开浏览器
npx playwright snapshot           # 获取页面快照（元素引用）
npx playwright click <element>    # 点击元素
npx playwright fill <element> <text> # 填写表单
npx playwright screenshot          # 截图
npx playwright close              # 关闭浏览器
```

### 3. 测试用例生成 (Xmind格式)

测试用例使用Markdown格式，可被Xmind软件直接导入：

```markdown
# 保证金管理系统测试用例

## 一、商家后台测试

### 1.1 账户管理

#### 1.1.1 商家账户管理Tab
- 用例：账户余额展示 (P0)
- 用例：提现功能-正常状态 (P0)
- 用例：提现功能-受限状态 (P0)

---
**优先级说明**: P0=核心功能必须测试  P1=重要功能高优先级  P2=一般功能
```

**打开方式**：
- **Xmind软件**：文件 → 导入 → 选择Markdown文件
- **文本编辑器**：直接打开 `.md` 文件查看
- **VSCode**：按 `Ctrl+Shift+V` 预览

### 4. 测试报告 (HTML格式)

HTML报告可直接用浏览器打开，包含：
- 测试概览（通过率、覆盖率）
- 功能模块覆盖状态
- 缺陷列表
- 测试截图证据
- 结论与建议

---

## 📝 可用Agent速查表

| Agent | 职责 | 输入 | 输出 |
|-------|------|------|------|
| project-manager | 测试任务规划 | PRD文档 | 任务清单 |
| technical-writer | 测试用例/报告撰写 | 需求分析 | 文档 |
| llm-testing-expert | LLM测试策略设计 | 测试目标 | 测试方案 |
| playwright-cli | UI自动化测试 | URL+用例 | 截图+日志 |
| api-tester | API接口测试 | API文档 | 测试结果 |
| performance-benchmarker | 性能测试 | 性能要求 | 性能报告 |
| test-results-analyzer | 测试结果分析 | 测试数据 | 分析报告 |
| evidence-collector | 证据收集 | 测试过程 | 截图+日志 |
| agents-orchestrator | 多Agent协调 | 复杂任务 | 协作结果 |

---

## 📊 测试报告示例

### HTML报告预览

| 指标 | 数值 |
|------|------|
| 测试类型 | UI自动化测试 |
| 测试环境 | 预发布环境(pre) |
| 用例总数 | 45 |
| 通过率 | 73% |
| 覆盖率 | 38% |

### Xmind测试用例结构

| 模块 | 用例数 | 优先级 |
|------|--------|--------|
| 商家后台 - 账户管理 | 16 | P0/P1 |
| 商家后台 - 缴纳保证金 | 12 | P0/P1 |
| 运营平台 - 配置管理 | 12 | P0/P1 |
| 运营平台 - 商家保证金 | 8 | P0/P1 |
| 运营平台 - 违规管理 | 15 | P0/P1 |
| 运营平台 - 明细查询 | 8 | P0/P1 |

---

## 📦 全局Skill库 (可选)

项目还支持从全局Skill库拉取更多技能：

| Skill库 | 路径 | 说明 |
|---------|------|------|
| AI Expert Skills | `d:\AIproject\.trae\skills\ai-expert-skills\` | 30+AI编程专家技能 |
| Awesome Agent Skills | `d:\AIproject\.trae\skills\awesome-agent-skills\` | 社区精选技能目录 |

**可用的AI Expert Skills**：
- `llm-testing-expert` - 大语言模型测试专家
- `python-expert` - Python编程专家
- `github-master` - GitHub大师
- `software-architect` - 软件架构师

---

## 🔧 安装依赖

```bash
# 克隆项目后
cd ai-test-project

# 安装Node.js依赖（Playwright CLI需要）
npm install

# 安装Chromium浏览器
npx playwright install chromium --with-deps
```

---

## 📂 目录命名规范

| 目录 | 命名格式 | 示例 |
|------|----------|------|
| 测试用例 | `{日期}-{需求名称}` | `20260422-保证金管理` |
| 测试报告 | `{日期}-{需求名称}` | `20260422-保证金管理` |
| 需求文档 | `{日期}-{需求名称}` | `20260422-保证金管理` |

**日期格式**: `YYYYMMDD`

---

## 🚨 常见问题

**Q: Xmind文件如何打开？**
A: 使用Xmind软件（https://xmind.cn/），文件 → 导入 → 选择 `.md` 文件

**Q: HTML报告看不到截图？**
A: 确保HTML文件和截图都在 `reports/{日期}-{需求名称}/` 目录下，使用相对路径引用

**Q: 如何添加新的Skill？**
A: 使用 `npx skills add <owner/repo@skill> -g` 从skills.sh安装，或从AI Expert Skills目录复制

**Q: 提示词修改后如何更新记录？**
A: 修改提示词后，立即更新 `PROMPT-HISTORY.md`：
   - 新增提示词：添加新条目到时间线索引和详细记录
   - 修改提示词：在对应条目下添加修改记录
   - 任何Agent修改提示词后都有责任更新此文档

---

## 📋 提示词更新规范

> **⚠️ 重要：每次新增或修改提示词后必须更新 `PROMPT-HISTORY.md`**

| 操作类型 | 更新要求 |
|---------|---------|
| 新增提示词 | 在时间线索引和详细记录中添加新条目，序号延续 |
| 修改提示词 | 在对应条目下添加"**修改记录**"段落 |
| 删除提示词 | 不删除，标注"**已废弃**"，保留记录 |

**更新时机**: 每次创建新提示词或修改现有提示词后立即更新

---

## 🔐 配置管理

### 目录结构

```
config/
├── environments/
│   ├── dev.env              # 开发环境配置
│   ├── test.env             # 测试环境配置
│   ├── pre.env              # 预发布环境配置
│   ├── prod.env             # 生产环境配置
│   └── pre-accounts.yaml     # 预发布环境账号配置（本地使用）
├── accounts.yaml.example    # 账号配置模板
├── config.yaml.example      # 主配置模板
└── CONFIG-GUIDE.md         # 配置说明文档
```

### 敏感信息保护

✅ **已实现**:
- `config/environments/*.yaml` 包含账号密码，已加入 `.gitignore`
- `config/environments/*.env` 包含敏感信息，已加入 `.gitignore`
- `node_modules/` 依赖目录已忽略

### 快速配置

```bash
# 1. 复制配置模板
cp config/config.yaml.example config/config.yaml
cp config/accounts.yaml.example config/accounts.yaml

# 2. 配置测试账号
# 编辑 config/environments/pre-accounts.yaml
# 或设置环境变量: export ADMIN_PASSWORD=xxx

# 3. 修改 .gitignore（如需添加更多忽略规则）
# config/environments/pre-accounts.yaml 已被默认忽略
```

### 配置引用格式

在测试报告和脚本中使用配置引用：

| 类型 | 格式 | 示例 |
|------|------|------|
| URL | `${CONFIG.admin_platform.url}` | `${CONFIG.admin_platform.url}` |
| 用户名 | `${CONFIG.admin_platform.username}` | `${CONFIG.admin_platform.username}` |
| 密码 | `${CONFIG.admin_platform.password}` | `${CONFIG.admin_platform.password}` |

### 多环境切换

```bash
# 通过设置 ENVIRONMENT 环境变量切换
export ENVIRONMENT=pre  # 使用 pre.env 配置
export ENVIRONMENT=prod # 使用 prod.env 配置

# 或直接指定配置文件
npx playwright test --config=config/environments/pre.env
```

---

## 📋 后续规划

### 1、待实现接入飞书

- [ ] 飞书多维表格BUG管理
- [ ] 飞书消息通知（测试完成自动推送）
- [ ] BUG状态流转（创建 → 处理中 → 已解决 → 已关闭）
- [ ] 飞书群聊机器人通知

### 2、待实现邮件通知

- [ ] SMTP邮件配置
- [ ] 测试报告自动发送
- [ ] 定时任务邮件提醒

---

**项目创建时间**: 2026-04-22
**最后更新**: 2026-04-22
**维护者**: AI Testing Team
