# AI Test Project - Config Schema
# 配置文件格式说明（不包含实际数据）

# ============================================
# 环境配置文件格式 (config/environments/{env}.env)
# ============================================
# ENVIRONMENT=dev|test|pre|prod
# BASE_URL=https://xxx.com
# DEBUG=true|false
# REPORT_PATH=./reports

# ============================================
# 账号配置文件格式 (config/accounts.yaml)
# ============================================
# 系统名称:
#   username: "账号"
#   password: "密码"    # 建议使用环境变量引用
#   role: "角色说明"

# ============================================
# 主配置文件格式 (config/config.yaml)
# ============================================
# environment: dev|test|pre|prod
# timeout: 30000
# retry: 3
# screenshot_dir: ./reports/screenshots
# report_format: html|markdown|all

# ============================================
# 使用示例
# ============================================
# 1. 复制配置模板
#    cp config/config.yaml.example config/config.yaml
#    cp config/accounts.yaml.example config/accounts.yaml
#
# 2. 配置账号信息（填入真实数据）
#    编辑 config/accounts.yaml
#
# 3. 设置环境变量
#    在 accounts.yaml 中使用 ${ENV_VAR} 引用环境变量
#
# 4. 运行测试
#    测试将自动读取配置并执行