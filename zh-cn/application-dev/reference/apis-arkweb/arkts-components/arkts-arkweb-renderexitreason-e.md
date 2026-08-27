# RenderExitReason

onRenderExited接口返回的渲染进程退出的具体原因。

**起始版本：** 9

**系统能力：** SystemCapability.Web.Webview.Core

## ProcessAbnormalTermination

```TypeScript
ProcessAbnormalTermination = 0
```

渲染进程异常退出，可能原因包括：渲染进程启动超时、达到进程数量上限导致系统回收旧渲染进程、多个页签同时关闭等。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## ProcessWasKilled

```TypeScript
ProcessWasKilled = 1
```

收到SIGKILL，或被手动终止。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## ProcessCrashed

```TypeScript
ProcessCrashed = 2
```

渲染进程崩溃退出，如段错误。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## ProcessOom

```TypeScript
ProcessOom = 3
```

程序内存不足。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## ProcessExitUnknown

```TypeScript
ProcessExitUnknown = 4
```

其他原因，比如渲染进程孵化失败。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core
