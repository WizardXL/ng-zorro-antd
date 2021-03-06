---
category: Components
subtitle: 代码编辑器
type: 数据录入
title: Code Editor
cols: 1
experimental: true
---

monaco editor 组件。

## 何时使用

- 需要在网页上渲染 monaco editor 时使用。

## API

使用该组件之前，需要加载 monaco editor 本身的资源。你可以通过 Angular CLI 提供的配置项将这些资源添加到 assets 目录下。例子，在 `angular.json` 中添加：

```diff
"assets": [
+ {
+   "glob": "**/*",
+   "input": "./node_modules/monaco-editor/min/vs",
+   "output": "/assets/vs/"
+ }
],
```

或者通过修改配置项中的 `assetsRoot` 指定资源位置。

另外别忘记安装 monaco editor：

```sh
npm install monaco-editor
```

### nz-code-editor

| 参数 | 说明 | 类型 | 默认值 |
| --- | --- | --- | --- |
| `[nzEditorMode]` | 编辑器的模式 | `normal`\|`diff` | `normal` |
| `[nzLoading]` | 加载中 | `boolean` | `false` |
| `[nzOriginalText]` | Diff 模式下，左半边的文本内容 | `boolean` | `false` |
| `[nzFullControl]` | 完全控制模式，此模式下组件不会帮助用户处理 `TextModel`，用户应当自行管理 monaco editor 实例 | `boolean` | `false` |
| `[nzEditorOption]` | 编辑器选项，[参考 monaco editor 的定义](https://microsoft.github.io/monaco-editor/api/interfaces/monaco.editor.ieditorconstructionoptions.html) | `IEditorConstructionOptions` | `{}` |
| `[nzToolkit]` | 暴露快捷操作 | `TemplateRef<void>` | - |
| `(nzEditorInitialized)` | 当编辑器组件初始化完毕之后派发事件  | `IEditor` \| `IDiffEditor` | - |

#### 方法

| 名称 | 描述 |
| --- | --- |
| `layout()` | 强制组件重新渲染 |

### NZ_CODE_EDITOR_CONFIG

你可以通过注入令牌 `NZ_CODE_EDITOR_CONFIG` 提供一个符合 `NzCodeEditorConfig` 接口的对象，来进行配置、使用钩子或设置编辑器默认选项。

| 属性 | 说明 | 类型 | 默认值 |
| --- | --- | --- | --- |
| `assetsRoot` | 组件加载 monaco editor 资源文件的位置 | `string` \| `SageUrl` | - |
| `defaultEditorOption` | 默认的编辑器设置，[参考 monaco editor 的定义](https://microsoft.github.io/monaco-editor/api/interfaces/monaco.editor.ieditorconstructionoptions.html) | `IEditorConstructionOptions` | `{}` |
| `onLoad` | 当 monaco editor 资源加载完毕时触发的钩子，此时全局对象 `monaco` 可用 | `() => void` | - |
| `onFirstEditorInit` | 当第一个编辑器请求初始化时触发的钩子 | `() => void` | - |
| `onInit` | 每个编辑器请求初始化时触发的钩子  | `() => void`  | - |
