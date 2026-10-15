# updateSpatialActionEnableStatus (System API)

## Modules to Import

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## updateSpatialActionEnableStatus

```TypeScript
function updateSpatialActionEnableStatus(event: number): void
```

Updates the start/stop status of spatial action awareness.

**Since:** 26.0.1

**Required permissions:** ohos.permission.vehicle.MMA_SPATIALACTION

**Model restriction:** This API can be used only in the stage model.

<!--Device-carAwareness-function updateSpatialActionEnableStatus(event: number): void--><!--Device-carAwareness-function updateSpatialActionEnableStatus(event: number): void-End-->

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | number | Yes | Start/stop status value. 0: end 1: start The value must be an integer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [34000001](../errorcode-carAwareness.md#34000001-service-exception) | Service exception. |
| [34000002](../errorcode-carAwareness.md#34000002-specified-capability-not-supported) | Specific capability not supported. |
