# getCarAwareness (System API)

## Modules to Import

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## getCarAwareness

```TypeScript
function getCarAwareness(capability: Capability, options?: CarAwarenessOptions): Promise<CarAwarenessInfo[]>
```

Obtains the car awareness result of the specified type once.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-carAwareness-function getCarAwareness(capability: Capability, options?: CarAwarenessOptions): Promise<CarAwarenessInfo[]>--><!--Device-carAwareness-function getCarAwareness(capability: Capability, options?: CarAwarenessOptions): Promise<CarAwarenessInfo[]>-End-->

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| capability | [Capability](arkts-multimodalawareness-carawareness-capability-e.md) | Yes | Specifies the type of the awareness capability result to obtain. |
| options | [CarAwarenessOptions](arkts-multimodalawareness-carawareness-carawarenessoptions-i-sys.md) | No | Optional configuration items of the awareness capability. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CarAwarenessInfo](arkts-multimodalawareness-carawareness-carawarenessinfo-i-sys.md)[]&gt; | Promise used to return an array of awareness result data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [34000001](../errorcode-carAwareness.md#34000001-service-exception) | Service exception. |
| [34000002](../errorcode-carAwareness.md#34000002-specified-capability-not-supported) | Specific capability not supported. |
