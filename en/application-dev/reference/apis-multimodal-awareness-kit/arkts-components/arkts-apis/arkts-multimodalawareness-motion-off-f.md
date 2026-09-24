# off

## Modules to Import

```TypeScript
import { motion } from '@kit.MultimodalAwarenessKit';
```

## off('operatingHandChanged')

```TypeScript
function off(type: 'operatingHandChanged', callback?: Callback<OperatingHandStatus>): void
```

Unsubscribes from operating hand change events.

**Since:** 15

**Required permissions:** 
- API version 20 and later: ohos.permission.ACTIVITY_MOTION or ohos.permission.DETECT_GESTURE
- API versions 15 to 19: ohos.permission.ACTIVITY_MOTION

**System capability:** SystemCapability.MultimodalAwareness.Motion

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'operatingHandChanged' | Yes | Event type. This parameter has a fixed value of **operatingHandChanged**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OperatingHandStatus](arkts-multimodalawareness-motion-operatinghandstatus-e.md)&gt; | No | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. An attempt was made to unsubscribe operatingHandChanged<br> event forbidden by permission: ohos.permission.ACTIVITY_MOTION or ohos.permission.DETECT_GESTURE. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function can not work correctly due to limited<br> device capabilities. |
| [31500001](../errorcode-motion.md#31500001-service-exception) | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception;<br> 2. N-API invocation exception, invalid N-API status. |
| [31500003](../errorcode-motion.md#31500003-unsubscription-failed) | Unsubscription failed. Possible causes: 1. Callback failure;<br> 2. N-API invocation exception, invalid N-API status; 3. IPC request exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    motion.off('operatingHandChanged');
    console.info("off succeeded");
} catch (err) {
    let error = err as BusinessError;
    console.error("Failed off and err code is " + error.code);
}
```


## off('holdingHandChanged')

```TypeScript
function off(type: 'holdingHandChanged', callback?: Callback<HoldingHandStatus>): void
```

Disables listening for holding hand status changes.

**Since:** 20

**Required permissions:** ohos.permission.DETECT_GESTURE

**System capability:** SystemCapability.MultimodalAwareness.Motion

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'holdingHandChanged' | Yes | Event type. The value **holdingHandChanged** indicates the holding hand status change event. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HoldingHandStatus](arkts-multimodalawareness-motion-holdinghandstatus-e.md)&gt; | No | Callback to unregister. If this parameter is not passed, all callbacks for the holding hand status change event will be unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. An attempt was made to unsubscribe holdingHandChanged<br> event forbidden by permission: ohos.permission.DETECT_GESTURE. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function can not work correctly due to limited<br> device capabilities. |
| [31500001](../errorcode-motion.md#31500001-service-exception) | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception;<br> 2. N-API invocation exception, invalid N-API status. |
| [31500003](../errorcode-motion.md#31500003-unsubscription-failed) | Unsubscription failed. Possible causes: 1. Callback failure;<br> 2. N-API invocation exception, invalid N-API status; 3. IPC request exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  motion.off('holdingHandChanged'); // Unregister all callbacks for the holding hand status change event.
  console.info('off succeeded');
} catch (err) {
  let error = err as BusinessError;
  console.error('Failed off; err code = ' + error.code);
}
```
