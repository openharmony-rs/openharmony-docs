# RenderExitReason

Enum type supplied to [renderExitReason](arkts-na-web-onrenderexitedevent-i.md#renderExitReason) when onRenderExited being called.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare enum RenderExitReason--><!--Device-unnamed-export declare enum RenderExitReason-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## PROCESS_ABNORMAL_TERMINATION

```TypeScript
PROCESS_ABNORMAL_TERMINATION = 0
```

Render process non-zero exit status.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-RenderExitReason-PROCESS_ABNORMAL_TERMINATION = 0--><!--Device-RenderExitReason-PROCESS_ABNORMAL_TERMINATION = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## PROCESS_WAS_KILLED

```TypeScript
PROCESS_WAS_KILLED = 1
```

SIGKILL or task manager kill.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-RenderExitReason-PROCESS_WAS_KILLED = 1--><!--Device-RenderExitReason-PROCESS_WAS_KILLED = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## PROCESS_CRASHED

```TypeScript
PROCESS_CRASHED = 2
```

The rendering process crashes and exits, such as a segment error.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-RenderExitReason-PROCESS_CRASHED = 2--><!--Device-RenderExitReason-PROCESS_CRASHED = 2-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## PROCESS_OOM

```TypeScript
PROCESS_OOM = 3
```

Out of memory.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-RenderExitReason-PROCESS_OOM = 3--><!--Device-RenderExitReason-PROCESS_OOM = 3-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## PROCESS_EXIT_UNKNOWN

```TypeScript
PROCESS_EXIT_UNKNOWN = 4
```

Unknown reason.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-RenderExitReason-PROCESS_EXIT_UNKNOWN = 4--><!--Device-RenderExitReason-PROCESS_EXIT_UNKNOWN = 4-End-->

**系统能力：** SystemCapability.Web.Webview.Core

