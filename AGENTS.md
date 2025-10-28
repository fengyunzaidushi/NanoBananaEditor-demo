<!-- OPENSPEC:START -->
# OpenSpec Instructions

These instructions are for AI assistants working in this project.

Always open `@/openspec/AGENTS.md` when the request:
- Mentions planning or proposals (words like proposal, spec, change, plan)
- Introduces new capabilities, breaking changes, architecture shifts, or big performance/security work
- Sounds ambiguous and you need the authoritative spec before coding

Use `@/openspec/AGENTS.md` to learn:
- How to create and apply change proposals
- Spec format and conventions
- Project structure and guidelines

Keep this managed block so 'openspec update' can refresh the instructions.

<!-- OPENSPEC:END -->

# 仓库指南

## 项目结构与模块组织

- `index.html` 引导 Vite 应用；React 入口位于 `src/main.tsx`，主布局在 `src/App.tsx`。
- 功能代码位于 `src/components`（UI）、`src/hooks`（逻辑复用）、`src/services`（API 和缓存）、以及 `src/store`（Zustand 状态）。
- 共享类型在 `src/types`，浏览器辅助工具在 `src/utils`。新增资源请放在其所属功能附近或放在专门的 `public/` 文件夹中。

## 构建、测试和开发命令

- `npm install`（或 CI 中使用 `npm ci`）恢复依赖。
- `npm run dev` 启动带热重载的 Vite 开发服务器；使用 `http://localhost:5173`。
- `npm run build` 在 `dist/` 生成生产包。
- `npm run preview` 提供服务构建产物以检查发布输出。
- `npm run lint` 在整个项目运行 ESLint；提交 PR 前先解决警告。

## 编码风格与命名约定

- 使用 TypeScript + React 函数式组件；优先使用 hooks 而非类。
- 遵循现有的两空格缩进和单引号 JSX 属性约定（可在 `src/components` 中看到）。
- 组件和 Zustand 存储使用 `PascalCase`（`ImageCanvas.tsx`、`useAppStore.ts`）；hooks 使用 `camelCase` 并以 `use` 前缀。
- 在添加新目录前，将共享逻辑集中在 `src/utils` 或 `src/services`。重构后运行 `npm run lint`。

## 测试指南

- 自动测试尚未配置；在 Vitest 设置完成前，通过 `npm run dev` 手动检查变更。
- 引入测试时，将测试规范放在 `src/__tests__` 或与组件并列为 `*.test.tsx`，并在此指南中记录命令（例如 `npm run test`）。
- 在 PR 中记录复现步骤或截图（用于 bug 修复）。

## 提交与 Pull Request 指南

- 保持提交主题简短且为命令式（基准：来自 `git log` 的 `Update README.md`）；逻辑上分组相关变更。
- 如适用，使用 `Fixes #123` 引用问题，并在 PR 描述中包含简要总结以及前后对比。
- 为影响 UI 的工作附上截图或短视频，并列出手动验证（浏览器、屏幕尺寸）。
- 确保 lint/build 命令成功后再请求审查；明确列出后续任务。

## 环境与配置

- 将 `.env.example` 复制为 `.env` 用于本地 API 密钥（例如 Google Generative AI）。切勿提交 `.env`。
- Tailwind 配置位于 `tailwind.config.js`；编辑后运行一次 `npm run dev` 以便 Vite 重新加载样式。
