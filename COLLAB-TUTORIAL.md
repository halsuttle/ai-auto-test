# 🦞 多龙虾 GitHub 协作教程（多 Token 版）

**版本：** v1.0  
**创建时间：** 2026-03-15  
**适用场景：** 一个老板操作多个 AI 实例，通过 GitHub 协作

---

## 📋 方案优势

| 优势 | 说明 |
|-----|------|
| ✅ **身份隔离** | 每个 AI 有独立的 Git 身份和 Token |
| ✅ **权限清晰** | 不同 AI 有不同权限，职责分明 |
| ✅ **安全可控** | Token 独立，可随时撤销/重置，不影响其他 AI |
| ✅ **易于管理** | 所有 AI 相关在一个仓库下，便于追踪 |
| ✅ **避免封禁** | 每个 AI 独立 Token，降低被 GitHub 检测风险 |

---

## 🚀 执行步骤

### 步骤 1：创建 GitHub 账号和 Token

**账号信息：**
- **账号名：** `starxxy`（或其他）
- **仓库名：** `ai-auto-test`

**Token 清单：**

| AI | Token | 权限 |
|-----|-------|------|
| **star-xing** (主管) | `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` | repo, workflow, user, notifications, read:org |
| **ali-bot** | `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` | repo, workflow, user, notifications, gist |
| **copaw-nas** | `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` | repo, workflow, user, notifications, packages |
| **openclaw_nas** | `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` | repo, workflow, user, notifications, packages |

---

### 步骤 2：Clone 仓库

每个 AI 在各自的环境中执行：

```bash
# Clone 仓库
git clone https://github.com/starxxy/ai-auto-test.git
cd ai-auto-test
```

---

### 步骤 3：配置 Git 身份

**星 (Xing):**
```bash
git config user.name "star-xing"
git config user.email "xing@openclaw.local"
```

**ali-bot:**
```bash
git config user.name "ali-bot"
git config user.email "ali@openclaw.local"
```

**copaw-nas:**
```bash
git config user.name "copaw-nas"
git config user.email "nas@openclaw.local"
```

**openclaw_nas:**
```bash
git config user.name "openclaw_nas"
git config user.email "openclaw-nas@openclaw.local"
```

---

### 步骤 4：配置 Token

每个 AI 在各自的 `~/.openclaw/config.yml` 中配置：

**星 (Xing):**
```yaml
github:
  token: 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
  repo: starxxy/ai-auto-test
  user: star-xing
  email: xing@openclaw.local
```

**ali-bot:**
```yaml
github:
  token: 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
  repo: starxxy/ai-auto-test
  user: ali-bot
  email: ali@openclaw.local
```

**copaw-nas:**
```yaml
github:
  token: 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
  repo: starxxy/ai-auto-test
  user: copaw-nas
  email: nas@openclaw.local
```

**openclaw_nas:**
```yaml
github:
  token: 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
  repo: starxxy/ai-auto-test
  user: openclaw_nas
  email: openclaw-nas@openclaw.local
```

---

### 步骤 5：复制技能到本地

**Windows PowerShell:**
```powershell
Copy-Item -Path "ai-auto-test\skills\*" -Destination "$env:USERPROFILE\.openclaw\skills\" -Recurse -Force
```

**macOS/Linux:**
```bash
cp -r ai-auto-test/skills/* ~/.openclaw/skills/
```

---

### 步骤 6：验证配置

每个 AI 执行以下命令验证：

```bash
# 检查 Git 配置
git config user.name
git config user.email

# 检查远程仓库
git remote -v

# 测试 Token（替换为实际 Token）
curl -H "Authorization: token YOUR_TOKEN" https://api.github.com/user

# 测试推送
echo "Test by $(git config user.name)" > test-$(git config user.name).txt
git add .
git commit -m "[test] 测试提交 - by $(git config user.name)"
git push origin main
```

---

## 📁 目录结构

```
ai-auto-test/
├── README.md                 # 仓库说明
├── TOKENS.md                 # Token 配置（保密！）
├── AI-CONFIGS.md             # AI 配置模板
├── COLLABORATION-GUIDE.md    # 协作指南
├── SETUP-GUIDE.md            # 安装指南
├── agents/                   # 子 Agent 定义
│   └── xiao-zhi/
│       └── AGENT.md
├── skills/                   # 技能仓库
│   ├── knowledge-base/
│   ├── feishu-doc/
│   └── ...
├── knowledge/                # 知识库
│   ├── INDEX.md
│   └── ...
└── data/                     # 数据文件
    └── 3d-print-market/
```

---

## 💡 实战示例

### 示例 1: 多 AI 数据分析任务

**场景：** 分析 3D 打印市场，三个 AI 分工合作

**步骤：**

#### 1. 创建 Issue
星 (Xing) 创建 Issue：
- **标题：** `[任务] 3D 打印市场分析`
- **内容：**
  ```markdown
  ## 任务描述
  抓取闲鱼、拼多多、淘宝三个平台的 3D 打印产品数据。
  
  ## 执行者
  - copaw-nas: 闲鱼数据（50 个产品）
  - ali-bot: 拼多多数据（50 个产品）
  - openclaw_nas: 淘宝数据（50 个产品）
  
  ## 期望输出
  1. CSV 文件：data/3d-print-market/{platform}.csv
  2. 分析报告：data/3d-print-market/analysis.md
  
  ## 截止时间
  2026-03-20
  ```

#### 2. 各 AI 执行任务

**copaw-nas:**
```bash
git checkout -b task/xianyu-data
# 执行抓取任务
# 保存数据到 data/3d-print-market/xianyu.csv
git add .
git commit -m "[data] Add 闲鱼 3D 打印数据 - by copaw-nas"
git push origin task/xianyu-data
# 创建 Pull Request
```

**ali-bot:**
```bash
git checkout -b task/pinduoduo-data
# 执行抓取任务
# 保存数据到 data/3d-print-market/pinduoduo.csv
git add .
git commit -m "[data] Add 拼多多 3D 打印数据 - by ali-bot"
git push origin task/pinduoduo-data
# 创建 Pull Request
```

**openclaw_nas:**
```bash
git checkout -b task/taobao-data
# 执行抓取任务
# 保存数据到 data/3d-print-market/taobao.csv
git add .
git commit -m "[data] Add 淘宝 3D 打印数据 - by openclaw_nas"
git push origin task/taobao-data
# 创建 Pull Request
```

#### 3. 星 (Xing) 汇总

```bash
# 审查并合并 PR
# 创建汇总分析脚本
# 生成最终报告
git add .
git commit -m "[analysis] 3D 打印市场分析报告 - by star-xing"
git push origin main
```

---

### 示例 2: 技能开发协作

**场景：** 开发新的天气技能

**步骤：**

#### 1. 创建 Issue
**标题：** `[skill] 天气查询技能`
**内容：**
```markdown
## 技能名称
weather-skill

## 功能描述
通过 wttr.in API 获取天气预报，生成日报。

## 开发者
ali-bot

## 截止时间
2026-03-18
```

#### 2. ali-bot 开发技能

```bash
git checkout -b feature/weather-skill
mkdir -p skills/weather
# 编写 SKILL.md
# 测试功能
git add .
git commit -m "[skill] Add weather-skill - by ali-bot"
git push origin feature/weather-skill
# 创建 Pull Request
```

#### 3. 星 (Xing) 审查

```bash
# 审查代码
# 测试功能
# 合并 PR
git merge feature/weather-skill
git push origin main
```

#### 4. 其他 AI 同步

```bash
git pull origin main
# 复制新技能到本地
# 测试使用
```

---

## 📊 提交流程

```
创建分支 → 开发/执行 → 提交代码 → 推送 → 创建 PR → 审查 → 合并
```

### 提交规范

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
git commit -m "[skill] Add weather-skill - by ali-bot"
git commit -m "[doc] Update README.md - by star-xing"
```

---

## ⚠️ 注意事项

### 1. Token 安全

- ✅ Token 只配置在 `~/.openclaw/config.yml`
- ❌ **不要** 提交到 Git 仓库
- ❌ **不要** 公开分享
- ✅ 每个 AI 独立，互不影响
- ✅ 建议 90 天轮换一次

### 2. Git 配置

- ✅ 每个 AI 有独立的 Git 用户名和邮箱
- ✅ 提交时显示正确的作者
- ✅ 便于追踪任务执行情况

### 3. 分支策略

- `main` - 主分支（稳定，受保护）
- `feature/*` - 新功能开发
- `task/*` - 任务数据
- `bugfix/*` - Bug 修复

### 4. 冲突处理

```bash
# 提交前拉取最新代码
git pull origin main

# 如有冲突，手动解决
# 然后提交
git add .
git commit -m "Merge conflict resolved - by star-xing"
git push origin main
```

---

## 🔍 故障排查

### Q1: Token 无效

**症状：** `401 Bad credentials`

**解决：**
1. 检查 Token 是否正确复制
2. 检查 Token 是否过期
3. 重新生成 Token

### Q2: Git 配置错误

**症状：** 提交显示错误的作者

**解决：**
```bash
# 检查当前配置
git config user.name
git config user.email

# 重新配置
git config user.name "正确的用户名"
git config user.email "正确的邮箱"
```

### Q3: 推送失败

**症状：** `Permission denied`

**解决：**
1. 检查 Token 权限
2. 检查是否有仓库写权限
3. 检查远程仓库 URL 是否正确

### Q4: 技能不生效

**症状：** OpenClaw 不识别新技能

**解决：**
1. 检查 SKILL.md 是否有 YAML Frontmatter
2. 检查技能路径是否正确
3. 重启 OpenClaw

---

## 📝 更新日志

| 日期 | 版本 | 更新内容 |
|------|------|----------|
| 2026-03-15 | v1.0 | 初始版本，配置 4 个 AI 的独立 Token |

---

## 🔗 相关资源

- **仓库地址：** https://github.com/starxxy/ai-auto-test
- **TOKENS.md:** Token 配置详情
- **AI-CONFIGS.md:** AI 配置模板
- **COLLABORATION-GUIDE.md:** 协作指南

---

**维护者：** 星 (Xing) @star-xing  
**最后更新：** 2026-03-15 14:18
