# updateSpatialActionEnableStatus (System API)

## Modules to Import

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## updateSpatialActionEnableStatus

```TypeScript
function updateSpatialActionEnableStatus(event: number): void
```

Updates the awareness enabling event when the app subscribes to the function.

**Since:** 26.0.1

**Required permissions:** ohos.permission.vehicle.MMA_SPATIALACTION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | number | Yes | Awareness enabling event. 0: end; 1: start. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission check failed. A non-system application uses the system capability. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Car awareness not supported. Function can not work correctly due to limited device capabilities. |
| [34000001](../errorcode-carAwareness.md#34000001-service-exception) | Service exception. |
| [34000002](../errorcode-carAwareness.md#34000002-specified-capability-not-supported) | Specific capability not supported. |
