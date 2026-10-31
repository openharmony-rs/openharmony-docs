# ToolEventCallback (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=e2c3267fc728379ed661f6395560cc18d085c54a translatedAt=2026-09-03T12:04:16.580Z pushedAt=2026-09-05T10:47:30.869Z -->

ToolEventCallback is used to receive session events generated during the running of a CLI tool process.

**Since:** 26.0.0

> **NOTE**
>
> The APIs of this module are system APIs.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { common } from '@kit.AbilityKit';
```

## ToolEventCallback

Callback interface for session events generated during the running of a CLI tool process.

**Since:** 26.0.0

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Model restriction:** This API can be used only in the stage model.

| Name    | Type                                                 | Read-only | Optional | Description                      |
| ------- | ---------------------------------------------------- | ---- | ---- | ------------------------- |
| onEvent | (event: [CliToolEvent](js-apis-inner-application-cliToolEvent-sys.md#clitoolevent)) => void | No   | No   | Callback for the CLI tool session event. |

**Example**

```ts
import { common } from '@kit.AbilityKit';

// Define the callback object for the CLI tool session event.
let callback: common.ToolEventCallback = {
  onEvent: (event: common.CliToolEvent) => {
    console.info('tool event type: ' + event.toolEventType + ', data: ' + event.data);
  }
};
```
