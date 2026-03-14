# 🦞 OpenClaw 龙虾配置指南

> 如何让多个 OpenClaw 实例通过 GitHub 协同工作

---

## 🎯 目标

配置所有龙虾实例，使其能够：
1. 读取 GitHub Issues 获取任务
2. 提交成果到 GitHub 仓库
3. 使用共享技能
4. 与其他龙虾协作

---

## 📋 龙虾列表

### Token 分配

| 龙虾 | Token | Git 用户名 | 用途 |
|------|-------|-----------|------|
| **星 (主管)** | `ghp_2nhTX...` (已有) | `星` | 主管、任务分配、汇总 |
| **ali** | `[新 Token]` | `ali` | 海外数据、搜索 |
| **copaw nas** | `[新 Token]` | `copaw-nas` | 存储、本地计算 |
| **copaw stary** | `[新 Token]` | `copaw-stary` | 辅助任务 |

### 配置 Git 身份

每个龙虾必须配置自己的 Git 身份，这样提交时才能区分是谁的贡献：

```bash
# 配置 Git 用户名和邮箱
git config user.name "龙虾名称"
git config user.email "龙虾名称@openclaw.local"

# 示例：ali 的配置
git config user.name "ali"
git config user.email "ali@openclaw.local"

# 示例：copaw-nas 的配置
git config user.name "copaw-nas"
git config user.email "copaw-nas@openclaw.local"
```

---

## 🔧 配置步骤

### 步骤 1：配置 GitHub Token

**方法 A：共用 Token（简单）**

所有龙虾使用同一个 Token（由老板配置）：
```
[GitHub Token - 联系老板获取]
```

在 `~/.openclaw/config.yml` 中添加：
```yaml
github:
  token: [你的 GitHub Token]
  repo: starxxy/ai-auto-test
```

**方法 B：独立 Token（推荐）**

为每个龙虾创建独立 Token：
1. 访问 https://github.com/settings/tokens
2. 创建 Token，Note 填写龙虾名称（如 "ali-bot"）
3. 勾选权限：`repo`, `workflow`
4. 复制 Token，填入对应龙虾的配置

---

### 步骤 2：Clone 协作仓库

每个龙虾执行：
```bash
# Clone 仓库
git clone https://github.com/starxxy/ai-auto-test.git

# 进入目录
cd ai-auto-test

# 配置 Git 用户信息
git config user.name "龙虾名称"
git config user.email "龙虾邮箱"
```

---

### 步骤 3：复制技能

```bash
# Windows PowerShell
Copy-Item -Path "skills\*" -Destination "$env:USERPROFILE\.openclaw\skills\" -Recurse -Force

# macOS/Linux
cp -r skills/* ~/.openclaw/skills/
```

---

### 步骤 4：验证配置

重启 OpenClaw，然后测试：

```
读取 GitHub Issues
```

或者测试技能：

```
创建一个飞书文档
```

---

## 📡 工作流程

### 接收任务

1. 主管龙虾（星）创建 GitHub Issue
2. 分配给对应龙虾（@ali @copaw-nas @copaw-stary）
3. 各龙虾读取 Issue，执行任务

### 提交成果

1. 龙虾执行任务
2. 保存成果到 `data/` 或 `tasks/` 目录
3. 提交到 GitHub（**必须标注身份**）：
   ```bash
   # 添加文件
   git add .
   
   # 提交（标注是谁的贡献）
   git commit -m "[类型] 描述 - by 龙虾名"
   
   # 示例：ali 提交
   git commit -m "[data] Add Etsy 数据 - by ali"
   
   # 示例：copaw-stary 提交
   git commit -m "[data] Add 淘宝数据 - by copaw-stary"
   
   # 推送
   git push origin main
   ```

### 汇总报告

1. 主管龙虾拉取最新代码
2. 汇总各龙虾成果
3. 生成报告
4. 发送给老板

---

## 🎯 任务示例

### Issue 模板

```markdown
## 任务类型
[ ] 数据收集  [ ] 文档处理  [ ] 技能开发

## 任务描述
[详细描述]

## 执行者
@ali @copaw-nas @copaw-stary

## 期望输出
[说明交付成果]

## 截止时间
YYYY-MM-DD

## 优先级
🔴 高  🟡 中  🟢 低
```

### 提交信息规范

**格式**：
```bash
git commit -m "[类型] 描述 - by 龙虾名"
```

**类型说明**：
- `[data]` - 数据收集
- `[skill]` - 技能开发
- `[doc]` - 文档更新
- `[task]` - 任务执行
- `[fix]` - 问题修复

**示例**：
```bash
# ali 提交海外数据
git commit -m "[data] Add Etsy 市场数据 - by ali"

# copaw-stary 提交淘宝数据
git commit -m "[data] Add 淘宝产品数据 - by copaw-stary"

# copaw-nas 准备存储
git commit -m "[task] 准备存储空间 - by copaw-nas"

# 星 汇总报告
git commit -m "[doc] 汇总 3D 打印市场报告 - by 星"

# 添加新技能
git commit -m "[skill] Add weather-skill - by ali"
```

**查看贡献历史**：
```bash
# 查看所有提交
git log --oneline

# 查看特定龙虾的贡献
git log --author="ali" --oneline
git log --author="copaw-stary" --oneline
git log --author="星" --oneline
```

---

## ⚠️ 注意事项

1. **Token 安全**：不要泄露 Token
2. **提交规范**：遵循 commit 格式
3. **冲突处理**：提交前 pull 最新代码
4. **技能测试**：新技能需要测试后再分享

---

## 📞 问题排查

### Q: 无法读取 Issues？
- 检查 GitHub Token 是否正确
- 检查网络连接
- 检查仓库权限

### Q: 提交失败？
- 检查是否有未解决的冲突
- 先 `git pull` 再 `git push`

### Q: 技能不生效？
- 检查技能路径是否正确
- 检查 SKILL.md 格式
- 重启 OpenClaw

---

## 🔗 相关资源

- **协作仓库**：https://github.com/starxxy/ai-auto-test
- **协作指南**： https://github.com/starxxy/ai-auto-test/blob/main/COLLABORATION-GUIDE.md
- **技能目录**： https://github.com/starxxy/ai-auto-test/tree/main/skills

---

**由 星 (Xing) 整理**
最后更新：2026-03-14
