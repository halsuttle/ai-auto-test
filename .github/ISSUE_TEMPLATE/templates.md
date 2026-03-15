# GitHub Issues 模板

用于多龙虾协作的任务分配和跟踪。

---

## 📋 Issue 模板

### 模板 1: 任务分配

```markdown
---
name: 🎯 任务分配
description: 分配协作任务给特定 AI
title: "[任务] 简短描述"
labels: ["task", "needs-triage"]
assignees: []
body:
  - type: markdown
    attributes:
      value: |
        ## 任务描述
        请详细描述任务内容和期望输出
        
  - type: textarea
    id: description
    attributes:
      label: 任务描述
      description: 详细说明任务内容
      placeholder: 请抓取 XXX 数据，分析 XXX...
    validations:
      required: true
      
  - type: dropdown
    id: assignee
    attributes:
      label: 执行者
      description: 选择负责此任务的 AI
      multiple: true
      options:
        - star-xing (主管)
        - ali-bot (海外数据)
        - copaw-nas (存储计算)
        - openclaw_nas (存储备份)
    validations:
      required: true
      
  - type: textarea
    id: output
    attributes:
      label: 期望输出
      description: 说明期望的交付成果
      placeholder: |
        1. Excel 表格，包含字段：...
        2. 分析报告：...
    validations:
      required: true
      
  - type: input
    id: deadline
    attributes:
      label: 截止时间
      description: 格式：YYYY-MM-DD
      placeholder: "2026-03-20"
    validations:
      required: false
      
  - type: textarea
    id: notes
    attributes:
      label: 备注
      description: 其他说明或注意事项
      placeholder: 数据保存到 data/xxx 目录...
    validations:
      required: false
---
```

---

### 模板 2: 技能开发

```markdown
---
name: 🛠️ 技能开发
description: 提议开发新的 OpenClaw 技能
title: "[skill] 新技能名称"
labels: ["skill", "enhancement"]
assignees: []
body:
  - type: markdown
    attributes:
      value: |
        ## 新技能提议
        描述新技能的功能和使用场景
        
  - type: input
    id: skill-name
    attributes:
      label: 技能名称
      description: 技能的英文名称（用于目录名）
      placeholder: "weather-skill"
    validations:
      required: true
      
  - type: textarea
    id: description
    attributes:
      label: 功能描述
      description: 详细描述技能功能
      placeholder: 获取天气预报并生成日报...
    validations:
      required: true
      
  - type: textarea
    id: use-cases
    attributes:
      label: 使用场景
      description: 列举使用场景和示例
      placeholder: |
        - 每天早上自动获取天气
        - 出行前检查天气状况
    validations:
      required: true
      
  - type: dropdown
    id: dependencies
    attributes:
      label: 依赖工具
      description: 需要哪些 OpenClaw 工具支持
      multiple: true
      options:
        - web_search
        - web_fetch
        - browser
        - message
        - feishu_doc
        - feishu_wiki
        - 其他（请在备注中说明）
        
  - type: dropdown
    id: developer
    attributes:
      label: 开发者
      description: 谁来实现这个技能
      options:
        - star-xing
        - ali-bot
        - copaw-nas
        - openclaw_nas
        - 待定
    validations:
      required: true
      
  - type: textarea
    id: notes
    attributes:
      label: 备注
      description: 其他说明
    validations:
      required: false
---
```

---

### 模板 3: Bug 报告

```markdown
---
name: 🐛 Bug 报告
description: 报告技能或协作流程中的问题
title: "[bug] 简短描述"
labels: ["bug", "needs-triage"]
assignees: []
body:
  - type: markdown
    attributes:
      value: |
        ## Bug 报告
        请详细描述遇到的问题
        
  - type: textarea
    id: description
    attributes:
      label: 问题描述
      description: 清晰简洁地描述问题
      placeholder: 当...时，发生...
    validations:
      required: true
      
  - type: textarea
    id: reproduction
    attributes:
      label: 复现步骤
      description: 如何复现这个问题
      placeholder: |
        1. 执行...
        2. 然后...
        3. 出现错误...
    validations:
      required: true
      
  - type: textarea
    id: expected
    attributes:
      label: 期望行为
      description: 期望发生什么
      placeholder: 应该...
    validations:
      required: true
      
  - type: textarea
    id: actual
    attributes:
      label: 实际行为
      description: 实际发生了什么
      placeholder: 但是...
    validations:
      required: true
      
  - type: dropdown
    id: ai
    attributes:
      label: 涉及的 AI
      description: 哪个 AI 遇到的问题
      options:
        - star-xing
        - ali-bot
        - copaw-nas
        - openclaw_nas
        - 所有 AI
        
  - type: textarea
    id: logs
    attributes:
      label: 日志/错误信息
      description: 如有错误日志，请粘贴
      render: shell
    validations:
      required: false
---
```

---

### 模板 4: 测试验证

```markdown
---
name: ✅ 测试验证
description: 测试协作流程或新功能
title: "[test] 测试描述"
labels: ["test", "verification"]
assignees: []
body:
  - type: markdown
    attributes:
      value: |
        ## 测试任务
        完成测试并反馈结果
        
  - type: textarea
    id: test-content
    attributes:
      label: 测试内容
      description: 需要测试什么
      placeholder: 测试 GitHub 推送流程...
    validations:
      required: true
      
  - type: dropdown
    id: testers
    attributes:
      label: 测试者
      description: 参与测试的 AI
      multiple: true
      options:
        - star-xing
        - ali-bot
        - copaw-nas
        - openclaw_nas
    validations:
      required: true
      
  - type: textarea
    id: steps
    attributes:
      label: 测试步骤
      description: 具体的测试操作
      placeholder: |
        1. Clone 仓库
        2. 创建测试文件
        3. 提交并推送
    validations:
      required: true
      
  - type: textarea
    id: results
    attributes:
      label: 测试结果
      description: 测试完成后填写
      placeholder: |
        - [ ] star-xing: ✅ 成功 / ❌ 失败
        - [ ] ali-bot: ✅ 成功 / ❌ 失败
        - [ ] copaw-nas: ✅ 成功 / ❌ 失败
    validations:
      required: false
      
  - type: input
    id: deadline
    attributes:
      label: 截止时间
      description: 格式：YYYY-MM-DD
      placeholder: "2026-03-16"
    validations:
      required: false
---
```

---

## 🏷️ Label 分类

| Label | 说明 | 颜色 |
|-------|------|------|
| `task` | 常规任务 | #4CAF50 |
| `skill` | 技能开发 | #2196F3 |
| `bug` | Bug 修复 | #F44336 |
| `test` | 测试验证 | #FF9800 |
| `enhancement` | 功能增强 | #9C27B0 |
| `documentation` | 文档更新 | #607D3B |
| `needs-triage` | 待分类 | #FDD835 |
| `in-progress` | 进行中 | #03A9F4 |
| `blocked` | 已阻塞 | #E91E63 |
| `done` | 已完成 | #8BC34A |

---

## 📊 Issue 工作流

```
新建 Issue → 分配 Label → 指派执行者 → 执行中 → 完成 → 关闭
    ↓           ↓
需要 triage   需要更多信息
```

---

## 💡 使用示例

### 示例 1: 创建任务 Issue

**标题：** `[任务] 抓取拼多多 3D 打印产品数据`

**内容：**
```markdown
## 任务描述
请抓取拼多多平台的 3D 打印产品数据，共 50 个产品。

## 执行者
- [x] ali-bot

## 期望输出
1. CSV 文件，包含字段：
   - 产品名称
   - 价格
   - 销量
   - 店铺名称
   - 商品链接

2. 保存到：`data/3d-print/pinduoduo.csv`

## 截止时间
2026-03-18

## 备注
使用 browser 工具，profile: "user" 模式
```

### 示例 2: 创建技能开发 Issue

**标题：** `[skill] 天气查询技能`

**内容：**
```markdown
## 技能名称
weather-skill

## 功能描述
通过 wttr.in API 获取天气预报，生成日报。

## 使用场景
- 每天早上自动获取天气
- 出行前检查天气状况
- 生成天气周报

## 依赖工具
- web_fetch
- message

## 开发者
ali-bot

## 备注
参考 https://wttr.in/ 的 API 文档
```

---

**最后更新：** 2026-03-15 14:18
