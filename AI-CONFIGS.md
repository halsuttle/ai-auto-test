# AI 配置文件

每个 AI 在 `~/.openclaw/config.yml` 中的配置模板。

---

## 星 (Xing) - 主管 AI

**Git 用户名:** `star-xing`  
**Git 邮箱:** `xing@openclaw.local`  
**Token:** `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`

```yaml
# ~/.openclaw/config.yml

github:
  token: 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
  repo: starxxy/ai-auto-test
  user: star-xing
  email: xing@openclaw.local

# Git 配置命令
git config user.name "star-xing"
git config user.email "xing@openclaw.local"
```

**权限范围：**
- ✅ repo (Full control of private repositories)
- ✅ workflow (Update GitHub Actions workflows)
- ✅ user (Read user information)
- ✅ notifications (Read notifications)
- ✅ read:org (Read org information)

**职责：**
- 任务分配和协调
- 代码审查和合并
- 仓库管理
- 汇总报告

---

## ali-bot - 海外数据 AI

**Git 用户名:** `ali-bot`  
**Git 邮箱:** `ali@openclaw.local`  
**Token:** `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`

```yaml
# ~/.openclaw/config.yml

github:
  token: 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
  repo: starxxy/ai-auto-test
  user: ali-bot
  email: ali@openclaw.local

# Git 配置命令
git config user.name "ali-bot"
git config user.email "ali@openclaw.local"
```

**权限范围：**
- ✅ repo (Full control of private repositories)
- ✅ workflow (Update GitHub Actions workflows)
- ✅ user (Read user information)
- ✅ notifications (Read notifications)
- ✅ gist (Create gists)

**职责：**
- 海外数据抓取
- 搜索和调研
- 英文内容处理
- Gist 分享代码片段

---

## copaw-nas - 存储计算 AI

**Git 用户名:** `copaw-nas`  
**Git 邮箱:** `nas@openclaw.local`  
**Token:** `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`

```yaml
# ~/.openclaw/config.yml

github:
  token: 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
  repo: starxxy/ai-auto-test
  user: copaw-nas
  email: nas@openclaw.local

# Git 配置命令
git config user.name "copaw-nas"
git config user.email "nas@openclaw.local"
```

**权限范围：**
- ✅ repo (Full control of private repositories)
- ✅ workflow (Update GitHub Actions workflows)
- ✅ user (Read user information)
- ✅ notifications (Read notifications)
- ✅ read:packages (Download packages)
- ✅ write:packages (Upload packages)

**职责：**
- 数据存储和管理
- 计算任务执行
- GitHub Packages 管理
- 数据备份

---

## openclaw_nas - 存储备份 AI

**Git 用户名:** `openclaw_nas`  
**Git 邮箱:** `openclaw-nas@openclaw.local`  
**Token:** `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`

```yaml
# ~/.openclaw/config.yml

github:
  token: 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
  repo: starxxy/ai-auto-test
  user: openclaw_nas
  email: openclaw-nas@openclaw.local

# Git 配置命令
git config user.name "openclaw_nas"
git config user.email "openclaw-nas@openclaw.local"
```

**权限范围：**
- ✅ repo (Full control of private repositories)
- ✅ workflow (Update GitHub Actions workflows)
- ✅ user (Read user information)
- ✅ notifications (Read notifications)
- ✅ read:packages (Download packages)
- ✅ write:packages (Upload packages)

**职责：**
- 数据备份
- 冗余存储
- 数据同步

---

## 提交规范

```bash
# 格式
git commit -m "[类型] 描述 - by Git 用户名"

# 类型说明
[data]     - 数据文件
[skill]    - 技能开发
[doc]      - 文档更新
[test]     - 测试相关
[fix]      - Bug 修复
[feature]  - 新功能
[config]   - 配置更新

# 示例
git commit -m "[data] Add 闲鱼 3D 打印数据 - by copaw-nas"
git commit -m "[skill] 添加知识库管理技能 - by star-xing"
git commit -m "[doc] 更新 TOKENS.md - by star-xing"
git commit -m "[test] 测试提交 - by ali-bot"
```

---

## 验证配置

每个 AI 执行以下命令验证配置：

```bash
# 1. 检查 Git 配置
git config user.name
git config user.email

# 2. 检查远程仓库
git remote -v

# 3. 测试 Token（替换 YOUR_TOKEN）
curl -H "Authorization: token YOUR_TOKEN" https://api.github.com/user

# 4. 测试推送
echo "Test by $(git config user.name)" > test-$(git config user.name).txt
git add .
git commit -m "[test] 测试提交 - by $(git config user.name)"
git push origin main
```

---

## 安全提醒

⚠️ **重要：**
- 此文件包含敏感 Token 信息
- **不要** 提交到 Git 仓库
- **不要** 公开分享
- 每个 AI 的配置文件应单独保存在各自的 `~/.openclaw/config.yml`
- 建议 90 天轮换一次 Token

---

**最后更新：** 2026-03-15 14:18
