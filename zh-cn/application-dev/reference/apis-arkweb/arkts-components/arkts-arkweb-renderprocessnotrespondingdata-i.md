# RenderProcessNotRespondingData

提供渲染进程无响应的详细信息。适用于需要诊断渲染进程异常的场景，提升故障排查的准确性和效率。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## jsStack

```TypeScript
jsStack: string
```

网页的JavaScript调用栈信息。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## pid

```TypeScript
pid: number
```

网页的进程id。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## reason

```TypeScript
reason: RenderProcessNotRespondingReason
```

触发渲染进程无响应回调的原因。

**类型：** [RenderProcessNotRespondingReason](arkts-arkweb-renderprocessnotrespondingreason-e.md)

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core
