# offPickupChange (System API)

## Modules to Import

```TypeScript
import { motion } from '@kit.MultimodalAwarenessKit';
```

## offPickupChange

```TypeScript
function offPickupChange(callback?: Callback<PickupEvent>): void
```

Unsubscribes from the pickup sensor event. This API takes effect only after onPickupChange is called to subscribe; if not subscribed, it will not take effect. When the application no longer needs to monitor the pickup event, such as page destruction, application entering the background, or pausing related functions, call this API to unsubscribe and release system resources.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-motion-function offPickupChange(callback?: Callback<PickupEvent>): void--><!--Device-motion-function offPickupChange(callback?: Callback<PickupEvent>): void-End-->

**System capability:** SystemCapability.MultimodalAwareness.Motion

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PickupEvent](arkts-multimodalawareness-motion-pickupevent-e-sys.md)&gt; | No | Callback used for pick up event unsubscription. <br> If this parameter is not specified, all callbacks of the pick up event are unsubscribed from. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [31500001](../errorcode-motion.md#31500001-service-exception) | Service exception. Possible causes: 1. A system error, such as null pointer, <br> container-related exception; 2. N-API invocation exception, invalid N-API status. |
