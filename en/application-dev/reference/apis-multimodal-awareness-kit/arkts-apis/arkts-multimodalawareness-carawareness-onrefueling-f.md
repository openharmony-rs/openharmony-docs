# onRefueling

## Modules to Import

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## onRefueling

```TypeScript
function onRefueling(callback: Callback<RefuelingInfo>): void
```

Subscribes to the refueling status awareness result. If the device does not support this capability, error code 34000002 is thrown. You can obtain the supported capabilities by calling the getAllCapabilityList method. The data is returned asynchronously through the callback.

**Since:** 26.0.1

**Required permissions:** ohos.permission.vehicle.MMA_ENERGYREFILL

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-carAwareness-function onRefueling(callback: Callback<RefuelingInfo>): void--><!--Device-carAwareness-function onRefueling(callback: Callback<RefuelingInfo>): void-End-->

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RefuelingInfo](arkts-multimodalawareness-carawareness-refuelinginfo-i.md)&gt; | Yes | Callback invoked to return the refueling recognition data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [34000001](../errorcode-carAwareness.md#34000001-service-exception) | Service exception. |
| [34000002](../errorcode-carAwareness.md#34000002-specified-capability-not-supported) | Specific capability not supported. |
