# recordInputEventTime (System API)

## Modules to Import

```TypeScript
import { performanceMonitor } from '@kit.ArkUI';
```

## recordInputEventTime

```TypeScript
function recordInputEventTime(type: ActionType, sourceType: SourceType, time: number): void
```

Records the trigger event type and time before the start of the animation scene.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [ActionType](arkts-arkui-performancemonitor-actiontype-e-sys.md) | Yes | Trigger mode of the user scene. |
| sourceType | [SourceType](../arkts-components/arkts-arkui-sourcetype-e.md) | Yes | Trigger source of the user scene. |
| time | number | Yes | Scenario trigger timestamp (in ms), for example, **1751508570794**. Values equal to or less than 0 will be automatically converted to the current system time, while positive values will be used as- is. Incorrect parameters may cause abnormal response latency metrics. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application. |

**Examples**

```TypeScript
import { systemDateTime, BusinessError } from '@kit.BasicServicesKit';
import { performanceMonitor } from '@kit.ArkUI';

// Obtain the current system time.
let time = systemDateTime.getTime(false);
// Update the user trigger event type and time.
performanceMonitor.recordInputEventTime(performanceMonitor.ActionType.LAST_UP, performanceMonitor.SourceType.PERF_MOUSE_EVENT, time);
```
