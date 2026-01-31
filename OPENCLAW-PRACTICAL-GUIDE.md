# OpenClaw 实用指南

基于实际使用经验和真实功能整理

## 目录
1. [核心概念](#核心概念)
2. [初始化设置](#初始化设置)
3. [工作空间结构](#工作空间结构)
4. [常用工具和命令](#常用工具和命令)
5. [飞书集成](#飞书集成)
6. [项目管理](#项目管理)
7. [最佳实践](#最佳实践)
8. [故障排除](#故障排除)

## 核心概念

### 什么是 OpenClaw？
OpenClaw 是一个 AI 助手平台，提供：
- **多通道通信**：支持飞书、Telegram、WhatsApp、Discord 等
- **文件操作**：完整的文件读写编辑能力
- **代码执行**：安全的命令执行环境
- **浏览器控制**：自动化网页操作
- **节点管理**：分布式设备控制

### 工作模式
- **主会话**：直接与用户对话，可以访问完整记忆
- **子代理**：后台运行特定任务，完成后通知主会话
- **心跳检查**：定期主动检查任务状态

## 初始化设置

### 1. 基础安装
```bash
# 全局安装 OpenClaw
npm install -g openclaw

# 初始化配置
openclaw setup
openclaw onboard
```

### 2. 工作空间初始化
```bash
# 创建工作空间目录
mkdir -p ~/.openclaw/workspace
cd ~/.openclaw/workspace

# 初始化 Git 仓库（如果需要）
git init
```

### 3. 核心配置文件
工作空间包含以下核心文件：
- `AGENTS.md` - 工作空间指南和会话规则
- `SOUL.md` - AI 助手的个性和行为准则
- `USER.md` - 用户信息和偏好
- `IDENTITY.md` - AI 助手身份定义
- `TOOLS.md` - 本地工具配置
- `HEARTBEAT.md` - 定期检查任务列表
- `memory/` - 每日记忆记录目录

## 工作空间结构

### 标准结构
```
~/.openclaw/workspace/
├── AGENTS.md          # 工作空间指南
├── SOUL.md           # 助手个性定义
├── USER.md           # 用户信息
├── IDENTITY.md       # 助手身份
├── TOOLS.md          # 本地工具配置
├── HEARTBEAT.md      # 心跳任务
├── memory/           # 记忆存储
│   ├── YYYY-MM-DD.md # 每日记录
│   └── ...
├── projects/         # 项目目录
└── .git/             # Git 版本控制
```

### 记忆管理
```bash
# 创建每日记忆文件
echo "# 2026-02-01 工作记录" > memory/2026-02-01.md

# 搜索记忆
openclaw memory search "关键词"

# 读取记忆片段
openclaw memory get memory/2026-02-01.md --lines 10
```

## 常用工具和命令

### 1. 文件操作
```bash
# 读取文件
openclaw agent --message "读取 AGENTS.md 文件"

# 编辑文件
openclaw agent --message "编辑 SOUL.md，添加新规则"

# 执行命令
openclaw agent --message "运行 ls -la 查看目录"
```

### 2. Git 操作
```bash
# 查看状态
openclaw agent --message "查看 Git 状态"

# 添加文件
openclaw agent --message "添加所有文件到暂存区"

# 提交更改
openclaw agent --message "提交更改，消息：更新文档"

# 推送到远程
openclaw agent --message "推送到 origin/master"
```

### 3. 系统管理
```bash
# 查看网关状态
openclaw gateway status

# 重启网关
openclaw gateway restart

# 查看会话列表
openclaw sessions list

# 查看健康状态
openclaw health
```

## 飞书集成

### 1. 文档操作
```bash
# 读取飞书文档
openclaw agent --message "读取飞书文档 token: doc_xxx"

# 创建新文档
openclaw agent --message "创建飞书文档，标题：项目计划"

# 更新文档内容
openclaw agent --message "更新飞书文档 token: doc_xxx，内容：..."
```

### 2. 文件夹管理
```bash
# 列出文件夹内容
openclaw agent --message "列出飞书文件夹 token: folder_xxx"

# 创建子文件夹
openclaw agent --message "在飞书文件夹中创建子文件夹"
```

### 3. 块级操作
```bash
# 列出文档块
openclaw agent --message "列出飞书文档的所有块"

# 更新特定块
openclaw agent --message "更新飞书文档块 block_id: blk_xxx"

# 删除块
openclaw agent --message "删除飞书文档块 block_id: blk_xxx"
```

## 项目管理

### 1. 项目初始化
```bash
# 创建项目目录
mkdir -p projects/my-project
cd projects/my-project

# 初始化项目文件
touch README.md
touch requirements.txt
```

### 2. 文档管理
```markdown
# 项目文档结构
projects/my-project/
├── README.md          # 项目说明
├── docs/             # 详细文档
│   ├── api.md       # API 文档
│   └── setup.md     # 安装指南
├── src/             # 源代码
└── tests/           # 测试文件
```

### 3. 版本控制
```bash
# 初始化 Git
git init
git add .
git commit -m "初始提交"

# 连接到远程仓库
git remote add origin https://github.com/username/repo.git
git push -u origin master
```

## 最佳实践

### 1. 记忆管理
- **每日记录**：在 `memory/YYYY-MM-DD.md` 中记录重要事件
- **长期记忆**：定期整理重要信息到 `MEMORY.md`
- **搜索优先**：回答问题前先搜索相关记忆

### 2. 文件操作
- **版本控制**：所有重要文件都使用 Git 管理
- **定期提交**：完成阶段性工作后立即提交
- **备份重要文件**：关键配置文件要定期备份

### 3. 安全注意事项
- **敏感信息**：不要将密码、密钥等写入普通文件
- **外部操作**：发送邮件、推文等外部操作前要确认
- **权限管理**：谨慎执行需要权限的命令

### 4. 性能优化
- **批量操作**：相似操作尽量批量处理
- **缓存结果**：重复查询的结果可以缓存
- **异步处理**：耗时任务使用子代理异步执行

## 故障排除

### 常见问题

#### 1. 网关无法启动
```bash
# 检查端口占用
lsof -i :18789

# 强制重启
openclaw gateway --force
```

#### 2. 飞书权限问题
```bash
# 检查应用权限
openclaw agent --message "检查飞书应用权限"

# 重新授权
# 需要用户重新扫码授权
```

#### 3. 记忆搜索无结果
```bash
# 重建索引
openclaw memory search --rebuild

# 检查文件路径
ls -la memory/
```

#### 4. Git 操作失败
```bash
# 检查 Git 配置
git config --list

# 检查远程仓库
git remote -v

# 检查网络连接
ping github.com
```

### 调试工具
```bash
# 查看详细日志
openclaw logs --follow

# 健康检查
openclaw doctor

# 查看配置
openclaw config get
```

### 获取帮助
```bash
# 查看所有命令
openclaw --help

# 查看特定命令帮助
openclaw gateway --help
openclaw message --help

# 访问文档
openclaw docs open
```

## 实际使用示例

### 示例 1：创建项目文档
```bash
# 1. 创建工作空间
mkdir -p ~/.openclaw/workspace/projects/my-app
cd ~/.openclaw/workspace/projects/my-app

# 2. 创建基础文件
touch README.md
touch requirements.txt
mkdir docs src tests

# 3. 初始化 Git
git init
git add .
git commit -m "初始项目结构"

# 4. 推送到 GitHub
git remote add origin https://github.com/username/my-app.git
git push -u origin master
```

### 示例 2：整理会议记录
```bash
# 1. 读取飞书会议文档
openclaw agent --message "读取飞书会议记录 doc_token: doc_xxx"

# 2. 提取关键信息
openclaw agent --message "从会议记录中提取行动项和决策"

# 3. 创建任务列表
openclaw agent --message "创建任务列表文档"

# 4. 设置提醒
openclaw agent --message "设置下周会议提醒"
```

### 示例 3：自动化报告
```bash
# 1. 收集数据
openclaw agent --message "读取本周工作记录"

# 2. 分析数据
openclaw agent --message "分析工作进度和问题"

# 3. 生成报告
openclaw agent --message "生成周报文档"

# 4. 发送报告
openclaw agent --message "发送周报到飞书群组"
```

## 总结

OpenClaw 是一个功能强大的 AI 助手平台，通过合理的工作空间管理和工具使用，可以显著提高工作效率。关键点包括：

1. **结构化工作空间**：保持文件组织清晰
2. **系统化记忆管理**：记录重要信息和决策
3. **自动化常规任务**：利用工具减少重复工作
4. **安全第一**：谨慎处理敏感操作
5. **持续学习**：根据使用经验优化工作流程

通过实践这些指南，你可以更好地利用 OpenClaw 完成各种任务，从简单的文件操作到复杂的项目管理。