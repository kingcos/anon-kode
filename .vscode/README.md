# VSCode 配置说明

本项目已配置完整的VSCode调试和开发环境。

## 调试配置

### 可用调试选项：

1. **Debug CLI** - 启动主要的CLI应用程序
   - 入口点：`src/entrypoints/cli.tsx`
   - 运行参数：`--verbose`
   - 如需修改参数，可在 `.vscode/launch.json` 中编辑 `args` 数组

## 使用方法

### 启动调试：

1. 打开任意 `.tsx` 或 `.ts` 文件
2. 在VSCode侧边栏点击调试面板（虫子图标）
3. 选择要使用的调试配置
4. 点击绿色播放按钮或按 `F5` 启动调试

### 设置断点：

1. 点击行号左侧设置断点
2. 启动调试时程序会在断点处停止
3. 使用调试工具栏进行单步调试

## 准备工作

### 首次使用：

1. **安装项目依赖**：运行 `npm install` 或 `pnpm install`（推荐使用pnpm）
2. **验证Node.js版本**：确保使用Node.js 18.0.0或更高版本：`node --version`
3. **检查tsx运行时**：运行 `npx tsx --version` 确认tsx可用

## 常用任务

### 可用任务：

1. **dev** - 启动开发服务器（默认任务）
2. **build** - 构建生产版本
3. **format** - 格式化代码
4. **format:check** - 检查代码格式
5. **install dependencies** - 安装依赖

### 运行任务：

1. 在VSCode中按 `Ctrl+Shift+P` (Mac: `Cmd+Shift+P`)
2. 输入 "Tasks: Run Task"
3. 选择要运行的任务

## 推荐扩展

打开扩展面板（`Ctrl+Shift+X`），搜索并安装推荐的扩展：

- **Prettier** - 代码格式化
- **TypeScript Hero** - TypeScript增强
- **Tailwind CSS IntelliSense** - Tailwind CSS支持
- **ESLint** - 代码检查
- **Auto Rename Tag** - 自动重命名标签
- **Path Intellisense** - 路径智能提示

## 快捷键

- `F5` - 启动调试
- `Ctrl+Shift+D` - 打开调试面板
- `F10` - 单步执行
- `F11` - 单步进入
- `Shift+F11` - 单步退出
- `Ctrl+Shift+F5` - 重启调试
- `Shift+F5` - 停止调试

## 故障排除

如果调试不工作：

1. **确保安装了所有依赖**：运行 `npm install` 或 `pnpm install`（推荐使用pnpm）
2. **检查Node.js版本**：确保使用Node.js 18.0.0或更高版本：`node --version`
3. **验证tsx是否可用**：运行 `npx tsx --version` 检查tsx运行时
4. **确认TypeScript编译无错误**：运行 `npx tsc --noEmit` 检查类型错误
5. **检查launch.json中的路径是否正确**
6. **如果是首次使用**：可能需要重启VSCode或重新加载窗口

### 常见错误：

**"bad option: --verbose"**
- 这个问题发生在`--verbose`标志被错误地传递给Node.js而不是应用程序
- 确保在launch.json中，`--verbose`位于`args`数组中，而不是`runtimeArgs`数组中

**断点不停下来或被跳过**
1. **确认断点位置**：在`async function onQuery()`函数内设置断点，而不是在定义处
2. **检查断点状态**：确保断点是实心红点，而不是空心圆圈（空心表示未绑定）
3. **使用调试控制台**：在调试时查看"调试控制台"面板的输出，确认源映射是否正确加载
4. **重启调试器**：有时需要停止调试并重新启动（`Shift+F5` 然后 `F5`）
5. **确认代码执行路径**：在`onQuery`被调用之前的代码处设置断点，确认程序执行流程
6. **清除VSCode缓存**：如果问题持续，尝试重新加载窗口（`Cmd+Shift+P` → "Reload Window"）

## 项目结构

- `src/entrypoints/cli.tsx` - 主入口文件
- `src/entrypoints/mcp.ts` - MCP服务器入口
- `src/` - 源代码目录
- `dist/` - 编译输出目录
