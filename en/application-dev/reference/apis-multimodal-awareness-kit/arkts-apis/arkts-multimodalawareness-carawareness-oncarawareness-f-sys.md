# onCarAwareness (System API)

## Modules to Import

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## onCarAwareness

```TypeScript
function onCarAwareness(capability: Capability, callback: Callback<CarAwarenessInfo[]>, options?:
  CarAwarenessOptions): void
```

Subscribes to car awareness results. If the device does not support the capability, error code 34000002 is thrown. You can obtain the supported capabilities by calling the getAllCapabilityList method. The data is returned asynchronously through the callback.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-carAwareness-function onCarAwareness(capability: Capability, callback: Callback<CarAwarenessInfo[]>, options?:  CarAwarenessOptions): void--><!--Device-carAwareness-function onCarAwareness(capability: Capability, callback: Callback<CarAwarenessInfo[]>, options?:  CarAwarenessOptions): void-End-->

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| capability | [Capability](arkts-multimodalawareness-carawareness-capability-e.md) | Yes | Specifies the type of the awareness capability to subscribe to. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CarAwarenessInfo](arkts-multimodalawareness-carawareness-carawarenessinfo-i-sys.md)[]&gt; | Yes | Callback used to return the array of awareness response data. |
| options | [CarAwarenessOptions](arkts-multimodalawareness-carawareness-carawarenessoptions-i-sys.md) | No | Optional configuration items of the awareness capability. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [34000001](../errorcode-carAwareness.md#34000001-service-exception) | Service exception. |
| [34000002](../errorcode-carAwareness.md#34000002-specified-capability-not-supported) | Specific capability not supported. |
