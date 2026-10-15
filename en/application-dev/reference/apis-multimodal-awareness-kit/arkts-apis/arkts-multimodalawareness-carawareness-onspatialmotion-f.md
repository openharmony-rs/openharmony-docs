# onSpatialMotion

## Modules to Import

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## onSpatialMotion

```TypeScript
function onSpatialMotion(callback: Callback<SpatialMotionInfo>): void
```

Subscribes to spatial motion awareness results. If the device does not support this capability, error code 34000002 is thrown. You can obtain the supported capabilities by calling the getAllCapabilityList method. The data is returned asynchronously through the callback.

**Since:** 26.0.1

**Required permissions:** ohos.permission.vehicle.MMA_SPATIALACTION

**Model restriction:** This API can be used only in the stage model.

<!--Device-carAwareness-function onSpatialMotion(callback: Callback<SpatialMotionInfo>): void--><!--Device-carAwareness-function onSpatialMotion(callback: Callback<SpatialMotionInfo>): void-End-->

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SpatialMotionInfo](arkts-multimodalawareness-carawareness-spatialmotioninfo-i.md)&gt; | Yes | Callback invoked to return the spatial motion awareness data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [34000001](../errorcode-carAwareness.md#34000001-service-exception) | Service exception. |
| [34000002](../errorcode-carAwareness.md#34000002-specified-capability-not-supported) | Specific capability not supported. |
