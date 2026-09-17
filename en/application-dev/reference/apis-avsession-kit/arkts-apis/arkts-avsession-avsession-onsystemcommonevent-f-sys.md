# onSystemCommonEvent (System API)

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## onSystemCommonEvent

```TypeScript
function onSystemCommonEvent(callback: EventProcess): void
```

Register system common event callback

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [EventProcess](arkts-avsession-avsession-eventprocess-t.md) | Yes | Used to handle event when the common command is received |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
