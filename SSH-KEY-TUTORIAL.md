# 🦞 GitHub SSH Key 配置教程

**版本：** v1.0  
**创建时间：** 2026-03-15  
**适用场景：** 多 AI 协作，避免 Token 被撤销问题

---

## 📋 核心概念

### 为什么用 SSH Key？

| 对比项 | Token 方式 | SSH Key 方式 |
|-------|-----------|-------------|
| **有效期** | 会过期/被撤销 | 永久有效 |
| **安全性** | 容易被扫描检测 | 更安全 |
| **配置复杂度** | 需要定期更新 | 一次配置，永久使用 |
| **多 AI 支持** | 每个 AI 独立 Token | 所有 AI 共用一个 Key |
| **推荐度** | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ |

### SSH Key 工作原理

```
┌─────────────────────────────────────────────────────────┐
│  GitHub 账号：halsuttle                                 │
│  SSH Key：绑定到 halsuttle 账号                          │
│  仓库：halsuttle/ai-auto-test                           │
└─────────────────────────────────────────────────────────┘
                          │
                          │ SSH 认证
                          ▼
┌─────────────────────────────────────────────────────────┐
│  本地电脑                                                │
│  SSH Key 对：私钥 (本地) + 公钥 (GitHub)                 │
│                                                          │
│  所有 AI 共用这个 Key 访问仓库                            │
│  但提交时显示各自的 Git 身份                              │
└─────────────────────────────────────────────────────────┘
```

---

## 🔧 配置步骤

### 步骤 1：生成 SSH Key

**在您的电脑上执行**（只需要生成一次）：

```bash
# 生成 Ed25519 类型的 SSH Key（推荐）
ssh-keygen -t ed25519 -C "halsuttle@github.com"
```

**提示输入时：**
- `Enter file in which to save the key` - 直接回车（使用默认路径）
- `Enter passphrase` - 直接回车（无密码）或设置密码
- `Enter same passphrase again` - 重复密码或回车

**输出示例：**
```
Generating public/private ed25519 key pair.
Enter file in which to save the key (/c/Users/starynas/.ssh/id_ed25519):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /c/Users/starynas/.ssh/id_ed25519
Your public key has been saved in /c/Users/starynas/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx halsuttle@github.com
```

### 步骤 2：查看公钥

```bash
# Windows PowerShell
cat ~/.ssh/id_ed25519.pub

# 或
type $env:USERPROFILE\.ssh\id_ed25519.pub
```

**输出示例：**
```
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx halsuttle@github.com
```

**复制整行内容**（从 `ssh-ed25519` 开头到 `halsuttle@github.com` 结尾）

### 步骤 3：添加 SSH Key 到 GitHub

1. 打开：https://github.com/settings/keys
2. 点击 **"New SSH key"** 绿色按钮
3. 填写信息：
   - **Title:** `halsuttle 电脑 - 龙虾协作`
   - **Key type:** 选择 `Authentication Key`
   - **Key:** 粘贴刚才复制的公钥内容
4. 点击 **"Add SSH key"**
5. 如需确认，输入 GitHub 密码

### 步骤 4：验证 SSH Key

```bash
# 测试 SSH 连接
ssh -T git@github.com
```

**首次连接会提示：**
```
The authenticity of host 'github.com (xxx.xxx.xxx.xxx)' can't be established.
ED25519 key fingerprint is SHA256:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

输入 `yes` 并回车。

**成功输出：**
```
Hi halsuttle! You've successfully authenticated, but GitHub does not provide shell access.
```

### 步骤 5：切换仓库为 SSH 地址

```bash
# 进入仓库目录
cd C:\Users\starynas\.openclaw\workspace\ai-auto-test

# 查看当前 remote
git remote -v

# 输出：
# origin  https://github.com/halsuttle/ai-auto-test.git (fetch)
# origin  https://github.com/halsuttle/ai-auto-test.git (push)

# 切换为 SSH 地址
git remote set-url origin git@github.com:halsuttle/ai-auto-test.git

# 再次查看
git remote -v

# 输出：
# origin  git@github.com:halsuttle/ai-auto-test.git (fetch)
# origin  git@github.com:halsuttle/ai-auto-test.git (push)
```

### 步骤 6：测试推送

```bash
# 推送代码
git push origin main
```

如果看到：
```
Enumerating objects: xx, done.
Counting objects: 100% (xx/xx), done.
Writing objects: 100% (xx/xx), xxx bytes | xxx KiB/s, done.
Total xx (delta xx), reused xx (delta xx), pack-reused xx
remote: Resolving deltas: 100% (xx/xx), completed with xx local objects.
To github.com:halsuttle/ai-auto-test.git
   xxxxxxx..xxxxxxx  main -> main
```

**恭喜！SSH Key 配置成功！** 🎉

---

## 🤖 多 AI 配置说明

### 所有 AI 共用 SSH Key

**重要：** 所有 AI 都在同一台电脑上运行，共用同一个 SSH Key。

**不需要**为每个 AI 生成独立的 SSH Key。

### AI 身份通过 Git 配置区分

每个 AI 在 `~/.openclaw/config.yml` 中配置自己的 Git 身份：

**star-xing:**
```yaml
github:
  repo: halsuttle/ai-auto-test
  user: star-xing
  email: xing@openclaw.local
```

**ali-bot:**
```yaml
github:
  repo: halsuttle/ai-auto-test
  user: ali-bot
  email: ali@openclaw.local
```

**copaw-nas:**
```yaml
github:
  repo: halsuttle/ai-auto-test
  user: copaw-nas
  email: nas@openclaw.local
```

**openclaw_nas:**
```yaml
github:
  repo: halsuttle/ai-auto-test
  user: openclaw_nas
  email: openclaw-nas@openclaw.local
```

### 提交时显示不同作者

```bash
# star-xing 提交
git commit -m "[task] 完成任务 - by star-xing"
# GitHub 显示：star-xing <xing@openclaw.local>

# ali-bot 提交
git commit -m "[data] 添加数据 - by ali-bot"
# GitHub 显示：ali-bot <ali@openclaw.local>
```

---

## 📁 目录结构

```
~/.ssh/
├── id_ed25519      # 私钥（不要分享！）
├── id_ed25519.pub  # 公钥（添加到 GitHub）
└── known_hosts     # 已知主机
```

---

## ⚠️ 注意事项

### 私钥安全

- ✅ 私钥 `id_ed25519` 只保存在本地
- ❌ **不要** 分享给任何人
- ❌ **不要** 上传到网络
- ✅ 如果泄露，立即在 GitHub 撤销并重新生成

### 多电脑场景

如果您在多台电脑上操作：

**方案 A：每台电脑生成独立 SSH Key**
```bash
# 电脑 1
ssh-keygen -t ed25519 -C "halsuttle@github.com - 电脑 1"

# 电脑 2
ssh-keygen -t ed25519 -C "halsuttle@github.com - 电脑 2"

# 分别添加到 GitHub
```

**方案 B：复制私钥（不推荐，安全性低）**
```bash
# 从电脑 1 复制私钥到电脑 2
# 不推荐，增加泄露风险
```

---

## 🔍 故障排查

### Q1: SSH 连接失败

**症状：** `Permission denied (publickey)`

**解决：**
```bash
# 检查 SSH Key 是否添加成功
ssh -T git@github.com

# 检查 remote URL 是否正确
git remote -v

# 应该是 git@github.com:halsuttle/ai-auto-test.git
# 不是 https://github.com/...
```

### Q2: 多个 SSH Key 冲突

**症状：** 有多个 GitHub 账号的 Key

**解决：** 创建 `~/.ssh/config` 文件：

```bash
# ~/.ssh/config
Host github.com-halsuttle
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519
    IdentitiesOnly yes
```

然后修改 remote：
```bash
git remote set-url origin git@github.com-halsuttle:halsuttle/ai-auto-test.git
```

### Q3: SSH Key 有密码

**症状：** 每次 push 都要求输入密码

**解决：**
```bash
# 重新生成无密码的 Key
ssh-keygen -t ed25519 -C "halsuttle@github.com" -N ""
```

---

## 📊 配置检查清单

- [ ] 生成 SSH Key
- [ ] 查看公钥内容
- [ ] 添加到 GitHub
- [ ] 验证 SSH 连接
- [ ] 切换仓库为 SSH 地址
- [ ] 测试推送成功
- [ ] 配置各 AI 的 Git 身份

---

## 🔗 相关资源

- **GitHub SSH 文档：** https://docs.github.com/en/authentication/connecting-to-github-with-ssh
- **添加 SSH Key：** https://github.com/settings/keys
- **测试 SSH 连接：** `ssh -T git@github.com`

---

**维护者：** 星 (Xing)  
**最后更新：** 2026-03-15 15:10
