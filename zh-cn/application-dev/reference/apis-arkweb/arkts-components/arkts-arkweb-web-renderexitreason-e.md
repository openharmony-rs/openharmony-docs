# RenderExitReason

Enum type supplied to {@link renderExitReason} when onRenderExited being called.

**起始版本：** 11

<!--Device-unnamed-declare enum RenderExitReason--><!--Device-unnamed-declare enum RenderExitReason-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## ProcessAbnormalTermination

```TypeScript
ProcessAbnormalTermination = 0
```

Render process non-zero exit status.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RenderExitReason-ProcessAbnormalTermination = 0--><!--Device-RenderExitReason-ProcessAbnormalTermination = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## ProcessWasKilled

```TypeScript
ProcessWasKilled = 1
```

SIGKILL or task manager kill.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RenderExitReason-ProcessWasKilled = 1--><!--Device-RenderExitReason-ProcessWasKilled = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## ProcessCrashed

```TypeScript
ProcessCrashed = 2
```

Segmentation fault.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RenderExitReason-ProcessCrashed = 2--><!--Device-RenderExitReason-ProcessCrashed = 2-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## ProcessOom

```TypeScript
ProcessOom = 3
```

Out of memory.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RenderExitReason-ProcessOom = 3--><!--Device-RenderExitReason-ProcessOom = 3-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## ProcessExitUnknown

```TypeScript
ProcessExitUnknown = 4
```

Unknown reason.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RenderExitReason-ProcessExitUnknown = 4--><!--Device-RenderExitReason-ProcessExitUnknown = 4-End-->

**系统能力：** SystemCapability.Web.Webview.Core

