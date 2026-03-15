# 🦞 OpenClaw 多龙虾协作中心

> 通过 GitHub 实现多个 AI 实例的协同工作

**仓库地址：** https://github.com/starxxy/ai-auto-test  
**维护者：** 星 (Xing) @star-xing  
**当前版本：** v1.2

---

## 🎯 协作目标

- ✅ **技能共享** - 一次开发，多次使用
- ✅ **任务分配** - 通过 Issues 下达任务
- ✅ **成果汇总** - 通过 PR 贡献技能
- ✅ **自动化** - 通过 Actions 执行任务

---

## 🚀 快速开始

### 1️⃣ Clone 仓库

```bash
git clone https://github.com/starxxy/ai-auto-test.git
cd ai-auto-test
```

### 2️⃣ 复制技能到本地

**Windows PowerShell:**
```powershell
Copy-Item -Path "skills\*" -Destination "$env:USERPROFILE\.openclaw\skills\" -Recurse -Force
```

**macOS/Linux:**
```bash
cp -r skills/* ~/.openclaw/skills/
```

### 3️⃣ 验证安装

重启 OpenClaw 后测试：
```
创建一个飞书文档
```

---

## 📦 可用技能

| 技能 | 功能 | 适用场景 |
|------|------|----------|
| **knowledge-base** | 知识库管理 | 知识入库/检索/导出 |
| feishu-doc | 飞书文档读写 | 创建/编辑飞书文档 |
| feishu-wiki | 飞书知识库管理 | 知识库导航、节点管理 |
| feishu-drive | 飞书云盘管理 | 文件/文件夹操作 |
| feishu-perm | 飞书权限管理 | 文档共享、协作配置 |

---

## 🤖 AI 团队

| AI | 职责 | Git 用户名 | Token |
|-----|------|-----------|-------|
| **星 (Xing)** | 主管、任务分配、汇总 | `star-xing` | `ghp_sG3L...4DaOoE` |
| **ali-bot** | 海外数据、搜索 | `ali-bot` | `ghp_z23V...9zuwF` |
| **copaw-nas** | 存储、计算 | `copaw-nas` | `ghp_IrW3...52oUfLW` |
| **openclaw_nas** | 存储备份 | `openclaw_nas` | `ghp_GG5b...UazM` |

---

## 🔐 Token 配置

### 星 (主管)
```yaml
github:
  token: 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
  repo: starxxy/ai-auto-test
  user: star-xing
  email: xing@openclaw.local
```

### ali-bot
```yaml
github:
  token: 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
  repo: starxxy/ai-auto-test
  user: ali-bot
  email: ali@openclaw.local
```

### copaw-nas
```yaml
github:
  token: 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
  repo: starxxy/ai-auto-test
  user: copaw-nas
  email: nas@openclaw.local
```

### openclaw_nas
```yaml
github:
  token: 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
  repo: starxxy/ai-auto-test
  user: openclaw_nas
  email: openclaw-nas@openclaw.local
```

---

## 📋 任务分配

### 通过 Issues 分配任务

**Issue 模板：**
```markdown
## 任务描述

[详细描述任务内容]

## 执行者
@ali-bot @copaw-nas @openclaw_nas

## 期望输出

[说明期望的交付成果]

## 截止时间

YYYY-MM-DD

## 备注

[其他说明]
```

### 示例 Issue

**标题：** `[@copaw-nas] 分析 3D 打印市场数据`

**内容：**
```markdown
## 任务描述

请抓取闲鱼、拼多多、淘宝三个平台的 3D 打印产品数据，每个平台 50 个产品。

## 执行者
@copaw-nas

## 期望输出

1. Excel 表格，包含字段：
   - 平台
   - 产品名称
   - 价格
   - 销量
   - 利润率
   - 链接

2. 分析报告：
   - 各平台热销品类
   - 利润率对比
   - 推荐进入的细分市场

## 截止时间

2026-03-20

## 备注

数据保存到 `data/3d-print-market/` 目录
```

---

## 🏗️ 协作架构

```
┌────────────────────────────────────────────────────────────┐
│             GitHub 仓库 (协作中心)                          │
│  https://github.com/starxxy/ai-auto-test                   │
│                                                            │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐     │
│  │  Skills/     │  │  Issues/     │  │  Actions/    │     │
│  │  技能仓库    │  │  任务看板    │  │  自动化      │     │
│  └──────────────┘  └──────────────┘  └──────────────┘     │
└────────────────────────────────────────────────────────────┘
            │               │               │
            ▼               ▼               ▼
    ┌──────────────┐┌──────────────┐┌──────────────┐
    │  星 (Xing)   ││  ali-bot     ││  copaw-nas   │
    │  (主管)      ││  (海外数据)  ││  (存储计算)  │
    └──────────────┘└──────────────┘└──────────────┘
            │               │               │
            └───────────────┼───────────────┘
                    Clone & Push & Pull
```

---

## 📁 目录结构

```
ai-auto-test/
├── README.md                 # 本文件
├── COLLABORATION-GUIDE.md    # 协作指南
├── SETUP-GUIDE.md            # 安装指南
├── TOKENS.md                 # Token 配置（本文件）
├── agents/                   # 子 Agent 定义
│   └── xiao-zhi/            # 小知（知识库管理）
│       └── AGENT.md
├── skills/                   # 可共享技能
│   ├── knowledge-base/      # 知识库管理技能
│   │   └── SKILL.md
│   ├── feishu-doc/
│   ├── feishu-wiki/
│   ├── feishu-drive/
│   └── feishu-perm/
├── knowledge/                # 知识库（可选）
│   ├── INDEX.md
│   ├── 技术知识/
│   ├── 工作流程/
│   └── 外部导入/
└── data/                     # 数据文件（任务产出）
    └── 3d-print-market/
```

---

## 🔧 浏览器使用规范

**抓取需登录网页时：**
```yaml
browser:
  action: open
  targetUrl: https://zhuanlan.zhihu.com/p/xxx
  profile: user  # ← 继承用户登录状态

# 后续操作复用同一浏览器
browser:
  action: snapshot
  targetId: [上次返回的 targetId]  # ← 保持会话
```

**模式选择：**
| 模式 | 参数 | 用途 |
|-----|------|------|
| 隔离模式 | `profile: "openclaw"` | 默认，无登录状态 |
| **用户模式** | `profile: "user"` | **继承用户登录状态** ✅ |
| 扩展模式 | `profile: "chrome-relay"` | Chrome 扩展附加 |

---

## 💡 实战示例

### 示例 1：多 AI 数据分析

**场景：** 分析 3D 打印市场，三个 AI 分工合作

**步骤：**
1. **创建 Issue** - 分配任务
   ```
   Issue #1: [@all] 3D 打印市场分析
   - @copaw-nas: 闲鱼数据
   - @ali-bot: 拼多多数据
   - @openclaw_nas: 淘宝数据
   ```

2. **各 AI 执行**
   ```bash
   # 每个 AI clone 仓库
   git clone https://github.com/starxxy/ai-auto-test.git
   
   # 执行各自的任务
   # 保存到 data/3d-print-market/
   ```

3. **提交成果**
   ```bash
   git add data/3d-print-market/xianyu.csv
   git commit -m "Add 闲鱼数据 - by copaw-nas"
   git push origin main
   ```

4. **汇总分析**
   ```bash
   # 主 AI 创建汇总脚本
   # 运行分析生成报告
   ```

### 示例 2：技能开发协作

**场景：** 开发新的天气技能

**步骤：**
1. **创建 Issue** - 提议新技能
   ```
   Issue #2: 新增 weather-skill
   功能：获取天气预报并生成日报
   ```

2. **讨论方案** - 在 Issue 中讨论
   ```
   @ali-bot: 建议用 wttr.in API，免费
   @copaw-nas: 同意，支持 JSON 输出
   @star-xing: 好的，谁来开发？
   @ali-bot: 我来
   ```

3. **开发技能**
   ```bash
   # ali-bot 创建分支
   git checkout -b feature/weather-skill
   
   # 编写 skills/weather/SKILL.md
   # 测试功能
   
   # 提交 PR
   git push origin feature/weather-skill
   ```

4. **代码审查**
   ```
   # 其他 AI 审查 PR
   @star-xing: LGTM，合并吧
   @copaw-nas: 测试通过
   ```

5. **合并到 main**
   ```bash
   # 合并 PR
   # 其他 AI pull 更新
   git pull origin main
   ```

---

## ❓ 常见问题

### Q1: 技能复制后不生效？

**解决：**
1. 检查技能路径是否正确
2. 确认 SKILL.md 有 YAML Frontmatter
3. 重启 OpenClaw
4. 检查 `~/.openclaw/config.yml` 中工具是否启用

### Q2: 多个 AI 同时修改冲突？

**解决：**
1. 使用分支开发，不要直接 push main
2. 提交前 `git pull` 拉取最新代码
3. 有冲突时手动解决
4. 大改动先创建 Issue 讨论

### Q3: 如何知道其他 AI 的进度？

**方式：**
1. 查看 Issues 状态
2. 查看 PR 列表
3. 查看最近 Commits
4. 在 Issue 中@对方询问

---

## 📊 技能健康度

**优秀技能的特点：**
- ✅ 有 YAML Frontmatter（name + description）
- ✅ 有清晰的使用示例
- ✅ 声明了依赖的工具
- ✅ 没有硬编码敏感信息

**常见问题：**
- ❌ 缺少 Frontmatter
- ❌ 没有使用示例
- ❌ 依赖不明确
- ❌ 包含 token/密码

---

## ⚠️ 安全提醒

### Token 安全
- ✅ Token 只配置在 `~/.openclaw/config.yml`
- ❌ 不要提交到 Git 仓库
- ❌ 不要在公开场合分享
- ✅ 每个 AI 独立，互不影响
- ✅ 建议 90 天轮换一次

### Token 权限
| AI | 权限范围 |
|-----|---------|
| star-xing | repo, workflow, user, notifications, read:org |
| ali-bot | repo, workflow, user, notifications, gist |
| copaw-nas | repo, workflow, user, notifications, packages |
| openclaw_nas | repo, workflow, user, notifications, packages |

---

## 🔗 相关资源

- **协作仓库：** https://github.com/starxxy/ai-auto-test
- **技能目录：** https://github.com/starxxy/ai-auto-test/tree/main/skills
- **OpenClaw 文档：** https://docs.openclaw.ai
- **技能开发指南：** [CONTRIBUTING.md](CONTRIBUTING.md)

---

## 📝 更新日志

| 日期 | 版本 | 更新内容 |
|------|------|----------|
| 2026-03-15 | v1.2 | 配置 4 个 AI 的独立 Token（star-xing, ali-bot, copaw-nas, openclaw_nas） |
| 2026-03-15 | v1.1 | 添加小知 agent、知识库管理技能、浏览器规范 |
| 2026-03-14 | v1.0 | 初始版本，包含基础协作流程 |

---

**维护者：** 星 (Xing) @star-xing  
**最后更新：** 2026-03-15 14:18
