# OpenClaw 工作空间和实用指南

基于实际使用经验整理的 OpenClaw 实用指南和最佳实践。

## 项目说明

这是一个用于学习和实践 OpenClaw 助手使用的项目仓库，包含完整的工作空间配置和使用指南。

## 文件结构

```
.
├── OPENCLAW-PRACTICAL-GUIDE.md  # 完整实用指南（基于实际经验）
├── AGENTS.md                    # 工作空间指南
├── SOUL.md                      # AI 助手个性定义
├── USER.md                      # 用户信息
├── IDENTITY.md                  # 助手身份
├── TOOLS.md                     # 本地工具配置
├── HEARTBEAT.md                 # 定期检查任务
├── memory/                      # 记忆存储目录
│   └── 2026-02-01.md           # 今日工作记录
└── projects/                    # 项目目录
    └── my-test/                 # 示例项目（Git 子模块）
```

## 快速开始

### 1. 查看完整指南
阅读 [OPENCLAW-PRACTICAL-GUIDE.md](OPENCLAW-PRACTICAL-GUIDE.md) 获取基于实际使用经验的详细说明。

### 2. 核心功能
- **文件操作**：读写编辑各种文件
- **命令执行**：安全执行系统命令
- **Git 管理**：版本控制操作
- **飞书集成**：文档和消息处理
- **记忆管理**：长期和短期记忆存储

### 3. 常用命令
```bash
# 查看帮助
openclaw --help

# 网关管理
openclaw gateway status
openclaw gateway restart

# 消息发送
openclaw message send --channel feishu --message "测试消息"

# 记忆搜索
openclaw memory search "关键词"
```

## OpenClaw 快速参考

### 基础命令
```bash
# 读取文件
read 文件名

# 写入文件
write 文件名 "内容"

# 执行命令
exec "命令"

# Git 操作
exec "git add ."
exec "git commit -m '提交信息'"
exec "git push"
```

### 飞书文档操作
```bash
# 创建文档
feishu_doc_create "标题"

# 读取文档
feishu_doc_read "doc_token"

# 写入文档
feishu_doc_write "doc_token" "内容"
```

## 最佳实践

1. **每日记录**：在 `memory/YYYY-MM-DD.md` 中记录重要工作
2. **版本控制**：定期提交重要更改到 Git
3. **安全第一**：谨慎处理敏感操作
4. **批量处理**：相似任务尽量批量完成

## 故障排除

- **网关问题**：使用 `openclaw gateway --force` 强制重启
- **权限问题**：检查应用权限配置
- **网络问题**：验证网络连接和代理设置

## 学习路径

1. 从 `OPENCLAW-PRACTICAL-GUIDE.md` 的基础部分开始
2. 实践文件操作和命令执行
3. 学习飞书集成功能
4. 探索高级功能如定时任务和浏览器自动化

## 相关资源

- [官方文档](https://docs.openclaw.ai)
- [GitHub 仓库](https://github.com/openclaw/openclaw)
- [社区 Discord](https://discord.com/invite/clawd)

## 贡献

欢迎提交改进建议和问题反馈：
1. Fork 本仓库
2. 创建功能分支
3. 提交更改
4. 创建 Pull Request

## 许可证

本项目内容遵循 MIT 许可证。

---

*最后更新: 2026-02-01*