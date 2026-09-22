# getRecentOperatingHandStatus

## Modules to Import

```TypeScript
import { motion } from '@kit.MultimodalAwarenessKit';
```

## getRecentOperatingHandStatus

```TypeScript
function getRecentOperatingHandStatus(): OperatingHandStatus
```

Obtains the latest operating hand status.

**Since:** 15

**Required permissions:** 
- API version 20 and later: ohos.permission.ACTIVITY_MOTION or ohos.permission.DETECT_GESTURE
- API versions 15 to 19: ohos.permission.ACTIVITY_MOTION

**System capability:** SystemCapability.MultimodalAwareness.Motion

**Return value:**

| Type | Description |
| --- | --- |
| [OperatingHandStatus](arkts-multimodalawareness-motion-operatinghandstatus-e.md) | Status of the operating hand. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. An attempt was made to get the recent operating hand<br> status forbidden by permission: ohos.permission.ACTIVITY_MOTION or ohos.permission.DETECT_GESTURE. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function can not work correctly due to limited<br> device capabilities. |
| [31500001](../errorcode-motion.md#31500001-service-exception) | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception;<br> 2. N-API invocation exception, invalid N-API status. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let data:motion.OperatingHandStatus = motion.getRecentOperatingHandStatus();
    console.info('get succeeded' + data);
} catch (err) {
    let error = err as BusinessError;
    console.error("Failed get and err code is " + error.code);
}
```
