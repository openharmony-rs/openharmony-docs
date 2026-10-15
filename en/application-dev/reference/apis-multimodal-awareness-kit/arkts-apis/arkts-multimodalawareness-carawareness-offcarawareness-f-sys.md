# offCarAwareness (System API)

## Modules to Import

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## offCarAwareness

```TypeScript
function offCarAwareness(capability: Capability, callback?: Callback<CarAwarenessInfo[]>, options?:
  CarAwarenessOptions): void
```

Unsubscribes from the specific car awareness capability result.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-carAwareness-function offCarAwareness(capability: Capability, callback?: Callback<CarAwarenessInfo[]>, options?:  CarAwarenessOptions): void--><!--Device-carAwareness-function offCarAwareness(capability: Capability, callback?: Callback<CarAwarenessInfo[]>, options?:  CarAwarenessOptions): void-End-->

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| capability | [Capability](arkts-multimodalawareness-carawareness-capability-e.md) | Yes | Specifies the type of the awareness capability to unsubscribe. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CarAwarenessInfo](arkts-multimodalawareness-carawareness-carawarenessinfo-i-sys.md)[]&gt; | No | Callback used to return specific car awareness event. If a specific callback is passed in, only the corresponding listener is unregistered; otherwise, all listeners are unregistered. |
| options | [CarAwarenessOptions](arkts-multimodalawareness-carawareness-carawarenessoptions-i-sys.md) | No | Optional configuration items of the awareness capability. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [34000001](../errorcode-carAwareness.md#34000001-service-exception) | Service exception. |
