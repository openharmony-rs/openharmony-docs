# offDropDetect

## Modules to Import

```TypeScript
import { deviceStatus } from '@kit.MultimodalAwarenessKit';
```

## offDropDetect

```TypeScript
function offDropDetect(callback?: Callback<DropDetectionStatus>): void
```

Unsubscribes from drop detection events.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-deviceStatus-function offDropDetect(callback?: Callback<DropDetectionStatus>): void--><!--Device-deviceStatus-function offDropDetect(callback?: Callback<DropDetectionStatus>): void-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DropDetectionStatus](arkts-multimodalawareness-devicestatus-dropdetectionstatus-e.md)&gt; | No | Indicates the callback for device-drop event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Failed due to limited device capabilities. |
| [32500001](../errorcode-deviceStatus.md#32500001-abnormal-service) | Service exception. |
| [32500003](../errorcode-deviceStatus.md#32500003-unsubscription-failed) | Unsubscription failed. |
