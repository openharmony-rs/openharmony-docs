# RenderExitReason

```TypeScript
declare enum RenderExitReason
```

Enum type supplied to {@link renderExitReason} when onRenderExited being called.

**起始版本：** 11

**系统能力：** SystemCapability.Web.Webview.Core

## ProcessAbnormalTermination

```TypeScript
ProcessAbnormalTermination = 0
```

Render process non-zero exit status.

**起始版本：** 11

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## ProcessWasKilled

```TypeScript
ProcessWasKilled = 1
```

SIGKILL or task manager kill.

**起始版本：** 11

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## ProcessCrashed

```TypeScript
ProcessCrashed = 2
```

Segmentation fault.

**起始版本：** 11

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## ProcessOom

```TypeScript
ProcessOom = 3
```

Out of memory.

**起始版本：** 11

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## ProcessExitUnknown

```TypeScript
ProcessExitUnknown = 4
```

Unknown reason.

**起始版本：** 11

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

