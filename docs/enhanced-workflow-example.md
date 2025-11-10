# 增强工作流测试示例

本文档展示新的智能需求收集和设计规范制定工作流程。

## 测试场景

用户请求："帮我开发一个在线教育平台"

## 工作流程执行

### 第一阶段：产品经理智能收集需求

产品经理Agent会基于"在线教育平台"这个关键词，智能生成相关问题：

```javascript
// Round 1: 基础信息收集
questions: [
  {
    question: "您的教育平台主要面向哪个教育阶段？",
    header: "教育阶段",
    multiSelect: true,
    options: [
      { label: "K12教育", description: "中小学基础教育" },
      { label: "职业培训", description: "技能培训、认证考试" },
      { label: "高等教育", description: "大学、研究生教育" },
      { label: "兴趣爱好", description: "艺术、体育、生活技能" }
    ]
  },
  {
    question: "计划支持哪些授课模式？",
    header: "授课模式",
    multiSelect: true,
    options: [
      { label: "录播课程", description: "预录制视频课程" },
      { label: "直播授课", description: "实时互动教学" },
      { label: "1对1辅导", description: "个性化指导" },
      { label: "混合模式", description: "线上线下结合" }
    ]
  },
  {
    question: "需要哪些核心功能？",
    header: "核心功能",
    multiSelect: true,
    options: [
      { label: "课程管理", description: "创建、编辑、发布课程" },
      { label: "学习追踪", description: "进度跟踪、数据分析" },
      { label: "作业考试", description: "作业布置、在线考试" },
      { label: "社区交流", description: "论坛、答疑、讨论组" }
    ]
  }
]

// Round 2: 基于用户选择"职业培训"深入询问
questions: [
  {
    question: "职业培训的认证需求是什么？",
    header: "认证体系",
    multiSelect: false,
    options: [
      { label: "平台认证", description: "平台自己颁发证书" },
      { label: "官方认证", description: "接入官方认证体系" },
      { label: "企业认证", description: "企业定制认证" },
      { label: "无需认证", description: "纯学习无认证需求" }
    ]
  },
  {
    question: "收费模式是怎样的？",
    header: "商业模式",
    multiSelect: true,
    options: [
      { label: "单课程付费", description: "按课程单独收费" },
      { label: "会员订阅", description: "月度/年度会员" },
      { label: "免费+增值", description: "基础免费高级付费" },
      { label: "企业采购", description: "B2B企业培训" }
    ]
  }
]

// ... 继续收集约20-25个问题
```

**生成PRD文档**: `requirements/PRD-education-platform.md`

### 第二阶段：UX/UI设计师基于PRD制定设计规范

设计师Agent读取PRD后，发现是教育平台，生成相关设计问题：

```javascript
// 基于教育平台特性的设计问题
questions: [
  {
    question: "教育平台的视觉风格倾向？",
    header: "视觉风格",
    multiSelect: false,
    options: [
      { label: "学术专业", description: "严谨、知识感、可信赖" },
      { label: "活泼友好", description: "亲和力、趣味性、年轻化" },
      { label: "科技现代", description: "创新、前沿、数字化" },
      { label: "简约清新", description: "清爽、专注、无干扰" }
    ]
  },
  {
    question: "课程展示界面偏好？",
    header: "课程展示",
    multiSelect: false,
    options: [
      { label: "卡片网格", description: "视觉冲击力强" },
      { label: "列表详情", description: "信息展示充分" },
      { label: "大图轮播", description: "突出重点课程" },
      { label: "分类导航", description: "清晰的分类结构" }
    ]
  },
  {
    question: "学习界面布局？",
    header: "学习界面",
    multiSelect: false,
    options: [
      { label: "视频为主", description: "大视频+小侧栏" },
      { label: "三栏布局", description: "目录+视频+笔记" },
      { label: "沉浸模式", description: "全屏专注学习" },
      { label: "分屏模式", description: "视频+互动并重" }
    ]
  }
]
```

**生成设计系统文档**: `design/design-system-education.md`

### 第三阶段：Tech-Lead基于文档分配开发任务

Tech-Lead读取PRD和设计文档后，制定开发计划：

```
### 需求与设计阶段（已完成）
✅ Task 1: 收集产品需求 → AGENT: @agent-product-manager
✅ Task 2: 制定设计规范 → AGENT: @agent-ux-ui-designer

### 开发任务分配（基于PRD和设计文档）
Task 3: 设计数据库模型（用户、课程、学习记录） → AGENT: @agent-django-backend-expert
Task 4: 实现用户认证系统 → AGENT: @agent-django-backend-expert
Task 5: 开发课程管理API → AGENT: @agent-django-api-developer
Task 6: 实现视频流媒体服务 → AGENT: @agent-backend-developer
Task 7: 开发前端课程展示组件 → AGENT: @agent-react-component-architect
Task 8: 实现学习界面（遵循设计规范） → AGENT: @agent-react-component-architect
Task 9: 集成支付系统 → AGENT: @agent-api-architect
Task 10: 代码审查和优化 → AGENT: @agent-code-reviewer

### Execution Order
- Sequential: Task 3 → Task 4 → Task 5
- Parallel: Tasks 5, 7（API和UI并行）
- Sequential: Tasks 8 → Task 9 → Task 10
```

## 工作流优势

1. **需求明确**：通过20-25个智能问题，充分理解用户需求
2. **设计一致**：生成完整的设计系统，确保UI统一
3. **文档驱动**：PRD和设计文档指导所有开发工作
4. **减少返工**：明确的规范减少误解和重做
5. **用户体验**：交互式选择，用户通过键盘即可完成选择

## 如何使用

```bash
# 启动项目时，tech-lead会自动执行新工作流
claude "use @agent-tech-lead-orchestrator to build [your project]"

# 工作流程：
# 1. 自动调用 product-manager 收集需求
# 2. 自动调用 ux-ui-designer 制定设计
# 3. 基于文档开始技术实施
```

## 注意事项

- 所有问题都是基于用户输入动态生成的，不是固定模板
- 问题会根据用户的回答逐步深入
- 生成的文档会保存供所有agents参考
- 开发agents必须遵循PRD和设计规范

## 文档位置

- PRD文档：`requirements/PRD-[timestamp].md`
- 设计系统：`design/design-system-[timestamp].md`