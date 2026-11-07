# CliToolEvent (CLI Tool Session Event)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=fc68633c2e4c22d7a461369c2832721e99739c6b translatedAt=2026-11-04T09:54:43.735Z pushedAt=2026-11-04T10:00:00.437Z nl=1 -->

CliToolEvent describes the session event information generated during the running of a CLI tool process.

**Since:** 26.0.1

## Modules to Import

```ts
import { common } from '@kit.AbilityKit';
```

## CliToolEvent

Describes the session event information of the CLI tool process.

**Since:** 26.0.1

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Model restriction:** This API can be used only in the stage model.

| Name          | Type                              | Read-only | Optional | Description              |
| ------------- | --------------------------------- | --------- | -------- | ------------------------ |
| toolEventType | [ToolEventType](#tooleventtype)   | No        | No       | Type of the CLI tool event.     |
| data          | string                            | No        | No       | Data of the CLI tool event.     |

## ToolEventType

Enumerates the session event types of the CLI tool.

**Since:** 26.0.1

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Model restriction:** This API can be used only in the stage model.

| Name   | Value       | Description           |
| ------ | -------- | -------------- |
| STDOUT | 'stdout' | Standard output event. |
| STDERR | 'stderr' | Standard error event. |
| EXIT   | 'exit'   | Process exit event. |
| ERROR  | 'error'  | Process error event. |
