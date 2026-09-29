# on

## Modules to Import

```TypeScript
import { motion } from '@kit.MultimodalAwarenessKit';
```

## on('operatingHandChanged')

```TypeScript
function on(type: 'operatingHandChanged', callback: Callback<OperatingHandStatus>): void
```

Subscribes to operating hand awareness events. The system collects user touch data through touchscreen sensors and combines gesture recognition algorithms to determine whether the current operating hand is the left hand or the right hand. This is suitable for scenarios such as gesture interaction and single-hand or dual-hand operation adaptation, optimizing the UI layout and interaction mode by identifying the user's operating hand state. It is recommended that you call off() to unsubscribe and release resources after use, to avoid unnecessary performance and power consumption overhead. Related method: off('operatingHandChanged'): unsubscribes from operating hand awareness events.

If the device does not support this function, error code 801 is returned.

**Since:** 15

**Required permissions:** 
- API version 20 and later: ohos.permission.ACTIVITY_MOTION or ohos.permission.DETECT_GESTURE
- API versions 15 to 19: ohos.permission.ACTIVITY_MOTION

<!--Device-motion-function on(type: 'operatingHandChanged', callback: Callback<OperatingHandStatus>): void--><!--Device-motion-function on(type: 'operatingHandChanged', callback: Callback<OperatingHandStatus>): void-End-->

**System capability:** SystemCapability.MultimodalAwareness.Motion

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'operatingHandChanged' | Yes | Event type. This parameter has a fixed value of **operatingHandChanged**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OperatingHandStatus](arkts-multimodalawareness-motion-operatinghandstatus-e.md)&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. An attempt was made to subscribe operatingHandChanged<br> event forbidden by permission: ohos.permission.ACTIVITY_MOTION or ohos.permission.DETECT_GESTURE. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function can not work correctly due to limited<br> device capabilities. |
| [31500001](../errorcode-motion.md#31500001-service-exception) | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception;<br> 2. N-API invocation exception, invalid N-API status. |
| [31500002](../errorcode-motion.md#31500002-subscription-failed) | Subscription failed. Possible causes: 1. Callback registration failure;<br> 2. Failed to bind native object to js wrapper; 3. N-API invocation exception, invalid N-API status; 4. IPC request exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let callback:Callback<motion.OperatingHandStatus> = (data:motion.OperatingHandStatus) => {
    console.info('callback succeeded' + data);
};

try {
    motion.on('operatingHandChanged', callback);  
    console.info("on succeeded");
} catch (err) {
    let error = err as BusinessError;
    console.error("Failed on and err code is " + error.code);
}
```


## on('holdingHandChanged')

```TypeScript
function on(type: 'holdingHandChanged', callback: Callback<HoldingHandStatus>): void
```

Subscribes to the holding hand status change awareness event. The system uses sensor data combined with recognition algorithms to determine whether the current holding hand is the left hand or the right hand. This is suitable for scenarios where reading applications, video playback, and other applications need to adjust the UI layout or functions based on the user's holding hand status. It is recommended that you call off() to unsubscribe and release resources after use to avoid unnecessary performance and power consumption overhead. Related method: off('holdingHandChanged'): unsubscribes from the holding hand status change awareness event.

**Since:** 20

**Required permissions:** ohos.permission.DETECT_GESTURE

<!--Device-motion-function on(type: 'holdingHandChanged', callback: Callback<HoldingHandStatus>): void--><!--Device-motion-function on(type: 'holdingHandChanged', callback: Callback<HoldingHandStatus>): void-End-->

**System capability:** SystemCapability.MultimodalAwareness.Motion

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'holdingHandChanged' | Yes | Event type. The value **holdingHandChanged** indicates the holding hand status change event. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HoldingHandStatus](arkts-multimodalawareness-motion-holdinghandstatus-e.md)&gt; | Yes | Callback used to return the holding hand status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. An attempt was made to subscribe holdingHandChanged<br> event forbidden by permission: ohos.permission.DETECT_GESTURE. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function can not work correctly due to limited<br> device capabilities. |
| [31500001](../errorcode-motion.md#31500001-service-exception) | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception;<br> 2. N-API invocation exception, invalid N-API status. |
| [31500002](../errorcode-motion.md#31500002-subscription-failed) | Subscription failed. Possible causes: 1. Callback registration failure;<br> 2. Failed to bind native object to js wrapper; 3. N-API invocation exception, invalid N-API status; 4. IPC request exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let callback:Callback<motion.HoldingHandStatus> = (data:motion.HoldingHandStatus) => {
  console.info('callback succeeded: ' + data);
};

try {
  motion.on('holdingHandChanged', callback);
  console.info('on succeeded');
} catch (err) {
  let error = err as BusinessError;
  console.error('Failed on; err code = ' + error.code);
}
```
