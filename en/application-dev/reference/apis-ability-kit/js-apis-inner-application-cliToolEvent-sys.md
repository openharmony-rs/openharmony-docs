# CliToolEvent (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=79ff6b5cab3530f52af035cd9f5c5b50875571fe translatedAt=2026-09-03T11:53:44.262Z pushedAt=2026-09-05T10:47:30.715Z -->

CliToolEvent describes the session event information generated during the running of a CLI tool process.

**Since:** 26.0.0

> **NOTE**
>
> The APIs of this module are system APIs.

## Modules to Import

```ts
import { common } from '@kit.AbilityKit';
```

## CliToolEvent

Describes the session event information of the CLI tool process.

**Since:** 26.0.0

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Model restriction:** This API can be used only in the stage model.

| Name          | Type                              | Read-only | Optional | Description              |
| ------------- | --------------------------------- | --------- | -------- | ------------------------ |
| toolEventType | [ToolEventType](#tooleventtype)   | No        | No       | Type of the CLI tool event. |
| data          | string                            | No        | No       | Data of the CLI tool event. |

## ToolEventType

Enumerates the session event types of the CLI tool.

**Since:** 26.0.0

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Model restriction:** This API can be used only in the stage model.

| Name   | Value    | Description          |
| ------ | -------- | -------------------- |
| STDOUT | 'stdout' | Standard output event. |
| STDERR | 'stderr' | Standard error event. |
| EXIT   | 'exit'   | Process exit event. |
| ERROR  | 'error'  | Process error event. |
