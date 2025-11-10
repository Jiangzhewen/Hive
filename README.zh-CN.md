# Hive - AI 开发团队 🚀

<p align="center">
  <strong>
    <a href="README.md">🇺🇸 English</a> |
    <a href="README.zh-CN.md">🇨🇳 中文</a>
  </strong>
</p>

## 🙏 致谢

本项目基于优秀的 [awesome-claude-agents](https://github.com/vijaythecoder/awesome-claude-agents) 由 [@vijaythecoder](https://github.com/vijaythecoder) 创建并进行了功能增强。特别感谢他为这个令人惊叹的 Claude Code 多智能体编排系统创建了基础。

## 🎯 本分支的主要不同

### 主要增强功能：
1. **📋 增强问题生成（最少20-25个问题）**
   - UX/UI 设计师生成全面的设计问卷
   - 产品经理创建更彻底的需求收集
   - 动态、上下文感知的问题而非固定模板

2. **📄 改进文档流程**
   - 所有开发智能体的强制文档阅读协议
   - 清晰的文档存储路径（requirements/、design/）
   - 智能体间明确的上下文传递
   - 更好的 PRD 和设计系统文档结构

3. **🔄 更强的工作流程执行**
   - CLAUDE.md 中的 CRITICAL 标记用于强制步骤
   - 添加了文档阅读协议部分
   - 增强了智能体通信指南
   - 更详细的场景示例（企业 SaaS、电子商务、内容平台）

4. **🌏 双语支持**
   - 增强的中文示例文档
   - 改进的国际化可用性

---

**通过智能需求和设计收集进行增强！** 使用专业的 AI 智能体团队为 Claude Code 赋能，这些智能体协同工作来构建完整功能、调试复杂问题，并以专家级知识处理任何技术栈。

## ⚠️ 重要更新 - 增强工作流程

**新的强制工作流程**：所有项目现在都以交互式问答开始（如计划模式），智能收集需求和设计规范。这确保每个项目在开发开始前都有清晰的需求和设计指导。

## ⚠️ 重要提示

**本项目是实验性的且消耗大量 token。** 我正在积极使用 Claude 订阅测试这些智能体 - 在复杂工作流程中预期会有高 token 消耗。多智能体编排每个复杂功能可能消耗 10-50k token。请谨慎使用并监控你的使用量。

## 🚀 快速开始（3分钟）

### 先决条件
- **Claude Code CLI** 已安装并认证
- **Claude 订阅** - 密集型智能体工作流程必需
- 包含代码库的活动项目目录
- **可选**：[Context7 MCP](docs/dependencies.md) 增强文档访问

### 1. 安装智能体
```bash
git clone https://github.com/Jiangzhewen/Hive.git
```

#### 选项 A：符号链接（推荐 - 自动更新）

**macOS/Linux:**
```bash
# 如果 agents 目录不存在则创建（保留现有智能体）
mkdir -p ~/.claude/agents

# 符号链接 Hive 智能体集合
ln -sf "$(pwd)/Hive/agents/" ~/.claude/agents/hive
```

**Windows (PowerShell):**
```powershell
# 创建 agents 目录
New-Item -Path "$env:USERPROFILE\.claude\agents" -ItemType Directory -Force

# 创建符号链接
cmd /c mklink /D "$env:USERPROFILE\.claude\agents\hive" "$(Get-Location)\Hive\agents"
```

#### 选项 B：复制（静态 - 无自动更新）
```bash
# 如果 agents 目录不存在则创建
mkdir -p ~/.claude/agents

# 复制所有智能体
cp -r Hive/agents ~/.claude/agents/hive
```

### 2. 验证安装
```bash
claude /agents
# 应该显示所有 24 个智能体。
```

### 3. 初始化你的项目
**导航**到你的**项目目录**并运行以下命令来配置你的 AI 团队：

```bash
claude "use @agent-team-configurator and optimize my project to best use the available subagents."
```

### 4. 使用增强工作流程开始构建
```bash
# 新工作流程 - 自动首先收集需求和设计
claude "use @agent-tech-lead-orchestrator and build a user authentication system"

# Tech-lead 将自动：
# 1. 首先调用 product-manager 收集需求（20-25个智能问题）
# 2. 然后调用 ux-ui-designer 创建设计规范
# 3. 最后基于文档分配开发任务
```

你的 AI 团队将自动收集需求，然后设计规范，最后基于清晰的文档进行实现！

## 🆕 增强工作流程功能

### 智能需求收集（产品经理）
- **动态问题**：基于你的具体项目上下文生成 20-25 个问题
- **交互选择**：使用键盘导航（如计划模式）选择答案
- **智能上下文**：问题根据你之前的答案进行调整
- **PRD 生成**：自动创建专业的产品需求文档

### 智能设计规范（UX/UI 设计师）
- **PRD 驱动**：首先阅读需求，然后询问设计问题
- **项目感知**：B2B 与 B2C、SaaS 与电子商务的不同问题
- **技术栈智能**：根据你的技术栈建议合适的 UI 框架
- **设计系统**：生成包含颜色、排版、组件的完整设计指导

### 新工作流程的好处
- ✅ **不再猜测**：编码开始前有清晰需求
- ✅ **一致设计**：所有 UI 遵循相同的设计系统
- ✅ **更好沟通**：PRD 和设计文档保持团队一致
- ✅ **更少修订**：通过清晰规范第一次就做对

## 🎯 自动配置如何工作

@agent-team-configurator 自动设置你的完美 AI 开发团队。当被调用时，它会：

1. **定位 CLAUDE.md** - 查找现有项目配置并保留 "AI Team Configuration" 部分之外的所有自定义内容
2. **检测技术栈** - 检查 package.json、composer.json、requirements.txt、go.mod、Gemfile 和构建配置以了解你的项目
3. **发现可用智能体** - 扫描 ~/.claude/agents/ 和 .claude/ 文件夹，构建所有可用专业化的能力表
4. **选择专业化**：优先选择框架特定智能体而非通用智能体，始终包含 @agent-code-reviewer 和 @agent-performance-optimizer 进行质量保证
5. **更新 CLAUDE.md** - 创建带时间戳的 "AI Team Configuration" 部分，包含检测到的技术栈和 Task|Agent|Notes 映射表
6. **提供使用指导** - 显示检测到的技术栈、选择的智能体，并给出开始构建的示例命令


## 👥 认识你的 AI 开发团队

### 🎭 编排器（5个智能体）- 新增2个智能智能体！
- **[产品经理](agents/orchestrators/product-manager.md)** 🆕 - 智能需求收集专家，动态生成基于上下文的20-25个问题并创建专业PRD文档（必须首先执行）
- **[UX/UI 设计师](agents/orchestrators/ux-ui-designer.md)** 🆕 - 智能设计规范专家，基于PRD和项目类型生成设计问题，创建设计系统（第二执行）
- **[技术主管编排器](agents/orchestrators/tech-lead-orchestrator.md)** - 增强的技术主管，确保需求和设计在开发前完成
- **[项目分析师](agents/orchestrators/project-analyst.md)** - 技术栈检测专家，启用智能智能体路由
- **[团队配置器](agents/orchestrators/team-configurator.md)** - AI 团队设置专家，检测你的技术栈并配置最优智能体映射

### 💼 框架专家（13个智能体）
- **Laravel（2个智能体）**
  - **[后端专家](agents/specialized/laravel/laravel-backend-expert.md)** - 包含 MVC、服务和 Eloquent 模式的综合 Laravel 开发
  - **[Eloquent 专家](agents/specialized/laravel/laravel-eloquent-expert.md)** - 高级 ORM 优化、复杂查询和数据库性能
- **Django（3个智能体）**
  - **[后端专家](agents/specialized/django/django-backend-expert.md)** - 遵循当前 Django 约定的模型、视图、服务
  - **[API 开发者](agents/specialized/django/django-api-developer.md)** - Django REST Framework 和 GraphQL 实现
  - **[ORM 专家](agents/specialized/django/django-orm-expert.md)** - Django 应用的查询优化和数据库性能
- **Rails（3个智能体）**
  - **[后端专家](agents/specialized/rails/rails-backend-expert.md)** - 遵循约定的全栈 Rails 开发
  - **[API 开发者](agents/specialized/rails/rails-api-developer.md)** - 使用 Rails 模式的 RESTful API 和 GraphQL
  - **[ActiveRecord 专家](agents/specialized/rails/rails-activerecord-expert.md)** - 复杂查询和数据库优化
- **React（2个智能体）**
  - **[组件架构师](agents/specialized/react/react-component-architect.md)** - 现代 React 模式、hooks 和组件设计
  - **[Next.js 专家](agents/specialized/react/react-nextjs-expert.md)** - SSR、SSG、ISR 和全栈 Next.js 应用
- **Vue（3个智能体）**
  - **[组件架构师](agents/specialized/vue/vue-component-architect.md)** - Vue 3 Composition API 和组件模式
  - **[Nuxt 专家](agents/specialized/vue/vue-nuxt-expert.md)** - SSR、SSG 和全栈 Nuxt 应用
  - **[状态管理器](agents/specialized/vue/vue-state-manager.md)** - Pinia 和 Vuex 状态架构

### 🌐 通用专家（4个智能体）
- **[后端开发者](agents/universal/backend-developer.md)** - 跨多个语言和框架的多语言后端开发
- **[前端开发者](agents/universal/frontend-developer.md)** - 任何框架的现代网络技术和响应式设计
- **[API 架构师](agents/universal/api-architect.md)** - RESTful 设计、GraphQL 和框架无关的 API 架构
- **[Tailwind 前端专家](agents/universal/tailwind-css-expert.md)** - Tailwind CSS 样式、实用优先开发和响应式组件

### 🔧 核心团队（4个智能体）
- **[代码考古学家](agents/core/code-archaeologist.md)** - 探索、文档化和分析不熟悉或遗留的代码库
- **[代码审查者](agents/core/code-reviewer.md)** - 具有严重性标记报告的严格安全感知审查
- **[性能优化器](agents/core/performance-optimizer.md)** - 识别瓶颈并应用可扩展系统的优化
- **[文档专家](agents/core/documentation-specialist.md)** - 制作全面的 README、API 规范和技术文档

**总计：26个专业化智能体** 协同工作构建你的项目！

[浏览所有智能体 →](agents/)


## 🔥 团队胜过单独 AI 的原因

- **专业化专业知识**：每个智能体精通其领域，拥有深入、前沿的知识
- **真实协作**：智能体无缝协调，共享上下文和交接任务
- **定制解决方案**：获得匹配你确切技术栈并遵循其最佳实践的代码
- **并行执行**：多个专业人才同时工作以更快交付

## 📈 影响

- **更快发布** - 分钟而非天内完成功能
- **更好代码质量** - 每行都遵循最佳实践
- **边编码边学习** - 看专家如何处理问题
- **自信扩展** - 为增长设计的架构

## 📚 了解更多

- [创建自定义智能体](docs/creating-agents.md) - 为你的需求构建专业人才
- [最佳实践](docs/best-practices.md) - 从你的 AI 团队获得最大收益

## 💝 支持项目

如果您觉得这个项目对您有帮助，欢迎通过以下方式支持持续开发：

- ⭐ **Star 这个仓库** - 免费但非常有价值！
- 📱 **微信赞赏码** - 扫描下方二维码通过微信支持
- 🐛 [报告问题](https://github.com/Jiangzhewen/Hive/issues) - 帮助我们改进
- 💡 [分享想法](https://github.com/Jiangzhewen/Hive/discussions) - 为项目路线图做贡献
- 📢 **分享给他人** - 帮助社区成长

### 微信赞赏码

<p align="center">
  <img src="https://lsky.zhongzhuan.chat/i/2025/11/10/6910f083aebc9.jpg" alt="微信赞赏码" width="200">
</p>

您的支持帮助我们维护和改进 Hive：

- 🖥️ 服务器和基础设施成本
- 📚 文档和教程改进
- 🚀 新功能开发
- 🛠️ 错误修复和改进
- 🌟 社区支持和互动

每一份贡献都很重要，无论是代码、反馈还是资金支持。感谢您成为 Hive 社区的一部分！

## 💬 加入社区

- ⭐ **Star 这个仓库**以表示支持
- 🐛 [报告问题](https://github.com/Jiangzhewen/Hive/issues)
- 💡 [分享想法](https://github.com/Jiangzhewen/Hive/discussions)
- 🎉 [成功案例](https://github.com/Jiangzhewen/Hive/discussions/categories/show-and-tell)

## 📄 许可证

MIT 许可证 - 在你的项目中自由使用！

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=Jiangzhewen/Hive&type=date&owner=true&legend=top-left)](https://www.star-history.com/#Jiangzhewen/Hive&type=date&owner=true&legend=top-left)

<p align="center">
  <strong>将 Claude Code 转变为能发布生产就绪功能的 AI 开发团队</strong><br>
  <em>简单设置。强大结果。只需描述和构建。</em>
</p>

<p align="center">
  <a href="https://github.com/Jiangzhewen/Hive">GitHub</a> •
  <a href="docs/creating-agents.md">文档</a> •
  <a href="https://github.com/Jiangzhewen/Hive/discussions">社区</a>
</p>

