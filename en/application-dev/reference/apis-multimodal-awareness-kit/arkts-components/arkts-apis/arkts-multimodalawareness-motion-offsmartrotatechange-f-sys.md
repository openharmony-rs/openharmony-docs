# offSmartRotateChange (System API)

## Modules to Import

```TypeScript
import { motion } from '@kit.MultimodalAwarenessKit';
```

## offSmartRotateChange

```TypeScript
function offSmartRotateChange(callback?: Callback<SmartRotateEvent>): void
```

Unsubscribe to smart rotate sensor event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.Motion

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SmartRotateEvent](arkts-multimodalawareness-motion-smartrotateevent-i-sys.md)&gt; | No | Callback used for smart rotate event unsubscription.<br> If this parameter is not specified, all callbacks of the smart rotate event are unsubscribed from. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [31500001](../errorcode-motion.md#31500001-service-exception) | Service exception. Possible causes: 1. A system error, such as null pointer,<br> container-related exception; 2. N-API invocation exception, invalid N-API status. |
