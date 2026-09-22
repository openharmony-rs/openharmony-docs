# @ohos.multimodalAwareness.motion (Motion Awareness)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @saga2025-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=06c751e035ad62c8d7f27ef01002e3d38739d6ba translatedAt=2026-09-14T02:06:42.016Z pushedAt=2026-09-14T10:03:33.579Z -->

This module provides awareness capabilities for user motions, supporting the recognition of user gestures and motion states. It is suitable for interactive scenarios where responses are required based on user gestures or motions, such as gesture recognition and motion triggering, helping applications deliver a more natural interactive experience and precise scenario awareness.

> **NOTE**
>
> The initial APIs of this module are supported since API version 15. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```ts
import { motion } from '@kit.MultimodalAwarenessKit';
```

## OperatingHandStatus

Defines the status of the operating hand.

**System capability**: SystemCapability.MultimodalAwareness.Motion

| Name               | Value  | Description                  |
| ------------------- | ---- | ---------------------- |
| UNKNOWN_STATUS      | 0    | Unknown status.|
| LEFT_HAND_OPERATED  | 1    | Left hand in use.|
| RIGHT_HAND_OPERATED | 2    | Right hand in use.|

## HoldingHandStatus<sup>20+</sup>

Defines the holding hand state information, which represents the result of a holding hand state change awareness event. After subscribing to the event, the current holding hand state information is returned.

**System capability**: SystemCapability.MultimodalAwareness.Motion

| Name           | Value  | Description          |
| --------------- | ---- | -------------- |
| NOT_HELD        | 0    | No holding.  |
| LEFT_HAND_HELD  | 1    | Holding with the left hand.|
| RIGHT_HAND_HELD | 2    | Holding with the right hand.|
| BOTH_HANDS_HELD | 3    | Holding with both hands.|
| UNKNOWN_STATUS  | 16   | Unknown status.  |

## motion.on('operatingHandChanged')

on(type: 'operatingHandChanged', callback: Callback&lt;OperatingHandStatus&gt;): void

Subscribes to operating hand awareness events. The system collects user touch data through touchscreen sensors and combines gesture recognition algorithms to determine whether the current operating hand is the left hand or the right hand. This is suitable for scenarios such as gesture interaction and single-hand or dual-hand operation adaptation, optimizing the UI layout and interaction mode by identifying the user's operating hand state. It is recommended that you call **off()** to unsubscribe and release resources after use, to avoid unnecessary performance and power consumption overhead. Related method: **off('operatingHandChanged')**: unsubscribes from operating hand awareness events.

If the device does not support this function, error code 801 is returned.

**Required permissions:**
- API version 20+: **ohos.permission.ACTIVITY_MOTION** or **ohos.permission.DETECT_GESTURE**
- API versions 15 to 19: **ohos.permission.ACTIVITY_MOTION**

**System capability**: SystemCapability.MultimodalAwareness.Motion

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                           | Yes   | Event type. Fixed input **'operatingHandChanged'**, indicating an operating hand state change. |
| callback | Callback&lt;[OperatingHandStatus](#operatinghandstatus)&gt; | Yes   | Callback invoked to return the operating hand state information. |

**Error codes**

For details about the error codes, see [Motion Awareness Error Codes](errorcode-motion.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to subscribe operatingHandChanged event forbidden by permission: ohos.permission.ACTIVITY_MOTION or ohos.permission.DETECT_GESTURE. |
| 401      | Parameter error. Parameter verification failed. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 31500001 | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status. |
| 31500002 | Subscription failed. Possible causes: 1. Callback registration failure; 2. Failed to bind native object to js wrapper; 3. N-API invocation exception, invalid N-API status; 4. IPC request exception. |

**Example**

```ts
import { BusinessError, Callback } from '@kit.BasicServicesKit';
import { motion } from '@kit.MultimodalAwarenessKit';

let callback:Callback<motion.OperatingHandStatus> = (data:motion.OperatingHandStatus) => {
    console.info('operatingHandStatus: ' + data);
};

try {
    motion.on('operatingHandChanged', callback);  
    console.info('on succeeded');
} catch (err) {
    let error = err as BusinessError;
    console.error(`Failed to subscribe operatingHandChanged. Code: ${error.code}, message: ${error.message}`);
}
```

## motion.off('operatingHandChanged')

off(type: 'operatingHandChanged', callback?: Callback&lt;OperatingHandStatus&gt;): void

Unsubscribes from operating hand awareness events. If **off()** is called without first calling **on()**, this method throws an exception. Related method: **on('operatingHandChanged')**: subscribes to operating hand awareness events.

**Required permissions:**
- API version 20+: **ohos.permission.ACTIVITY_MOTION** or **ohos.permission.DETECT_GESTURE**
- API versions 15 to 19: **ohos.permission.ACTIVITY_MOTION**

**System capability**: SystemCapability.MultimodalAwareness.Motion

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                           | Yes   | Event type. Fixed input **'operatingHandChanged'**, indicating a change in the operating hand state. |
| callback | Callback&lt;[OperatingHandStatus](#operatinghandstatus)&gt; | No   | Callback for the operating hand state change event. To unsubscribe from a specific callback, the callback passed in must be the same as the one passed in during subscription. If this parameter is not specified, all callbacks currently listening for this event are unsubscribed. |

**Error codes**

For details about the error codes, see [Motion Awareness Error Codes](errorcode-motion.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to unsubscribe operatingHandChanged event forbidden by permission: ohos.permission.ACTIVITY_MOTION or ohos.permission.DETECT_GESTURE. |
| 401      | Parameter error. Parameter verification failed. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 31500001 | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status. |
| 31500003 | Unsubscription failed. Possible causes: 1. Callback failure; 2. N-API invocation exception, invalid N-API status; 3. IPC request exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
    motion.off('operatingHandChanged');
    console.info('off succeeded');
} catch (err) {
    let error = err as BusinessError;
    console.error(`Failed to unsubscribe operatingHandChanged. Code: ${error.code}, message: ${error.message}`);
}
```

## motion.getRecentOperatingHandStatus()

getRecentOperatingHandStatus(): OperatingHandStatus

Obtains the latest operating hand status. This method directly returns the latest operating hand status and can be called without subscribing to events.

**Required permissions**:
- API version 20+: **ohos.permission.ACTIVITY_MOTION** or **ohos.permission.DETECT_GESTURE**
- API version 15-19: **ohos.permission.ACTIVITY_MOTION**

**System capability**: SystemCapability.MultimodalAwareness.Motion

**Return value**

| Type                         | Description                                |
| ----------------------------- | ------------------------------------ |
| [OperatingHandStatus](#operatinghandstatus) | Status of the operating hand.|

**Error codes**

For details about the error codes, see [Motion Awareness Error Codes](errorcode-motion.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to get the recent operating hand status forbidden by permission: ohos.permission.ACTIVITY_MOTION or ohos.permission.DETECT_GESTURE. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 31500001 | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let data:motion.OperatingHandStatus = motion.getRecentOperatingHandStatus();
    console.info('get succeeded: ' + data);
} catch (err) {
    let error = err as BusinessError;
    console.error(`Failed to get recent operating hand status. Code: ${error.code}, message: ${error.message}`);
}
```

## motion.on('holdingHandChanged') <sup>20+</sup>

on(type: 'holdingHandChanged', callback: Callback&lt;HoldingHandStatus&gt;): void

Subscribes to the holding hand status change awareness event. The system uses sensor data combined with recognition algorithms to determine whether the current holding hand is the left hand or the right hand. This is suitable for scenarios where reading applications, video playback, and other applications need to adjust the UI layout or functions based on the user's holding hand status. It is recommended that you call **off()** to unsubscribe and release resources after use to avoid unnecessary performance and power consumption overhead. Related method: **off('holdingHandChanged')**: unsubscribes from the holding hand status change awareness event.

**Required permissions**: ohos.permission.DETECT_GESTURE

**System capability**: SystemCapability.MultimodalAwareness.Motion

**Parameters**

| Name  | Type                                             | Mandatory| Description                                  |
| -------- | ------------------------------------------------- | ---- | -------------------------------------- |
| type     | string                                            | Required   | Event type. Fixed input **'holdingHandChanged'**, indicating a holding hand state change. |
| callback | Callback&lt;[HoldingHandStatus](#holdinghandstatus20)&gt; | Required   | Callback function used to return the holding hand state information. |

**Error codes**

For details about the error codes, see [Motion Awareness Error Codes](errorcode-motion.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to subscribe holdingHandChanged event forbidden by permission: ohos.permission.DETECT_GESTURE. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 31500001 | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status. |
| 31500002 | Subscription failed. Possible causes: 1. Callback registration failure; 2. Failed to bind native object to js wrapper; 3. N-API invocation exception, invalid N-API status; 4. IPC request exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let callback:Callback<motion.HoldingHandStatus> = (data:motion.HoldingHandStatus) => {
  console.info('holdingHandStatus: ' + data);
};

try {
  motion.on('holdingHandChanged', callback);
  console.info('on succeeded');
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to subscribe holdingHandChanged. Code: ${error.code}, message: ${error.message}`);
}
```

## motion.off('holdingHandChanged') <sup>20+</sup>

off(type: 'holdingHandChanged', callback?: Callback&lt;HoldingHandStatus&gt;): void

Unsubscribes from the holding hand status change awareness event. If **off()** is called without first calling **on()**, this method throws an exception. Related method: **on('holdingHandChanged')**: subscribes to the holding hand status change awareness event.

**Required permissions**: ohos.permission.DETECT_GESTURE

**System capability**: SystemCapability.MultimodalAwareness.Motion

**Parameters**

| Name  | Type                                             | Mandatory| Description                                          |
| -------- | ------------------------------------------------- | ---- | ---------------------------------------------- |
| type     | string                                            | Yes   | Event type. The value is fixed at **'holdingHandChanged'**, indicating a holding hand state change.         |
| callback | Callback&lt;[HoldingHandStatus](#holdinghandstatus20)&gt; | No   | Callback function used to return the holding hand state information. The callback to be unsubscribed must be the same as the one passed in when subscribing. If this parameter is not specified, all callbacks currently listening for this event are unsubscribed. |

**Error Code**:

For details about the error codes, see [Motion Awareness Error Codes](errorcode-motion.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to unsubscribe holdingHandChanged event forbidden by permission: ohos.permission.DETECT_GESTURE. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 31500001 | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status. |
| 31500003 | Unsubscription failed. Possible causes: 1. Callback failure; 2. N-API invocation exception, invalid N-API status; 3. IPC request exception. |

**Example**:

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  motion.off('holdingHandChanged'); // Unregister all callbacks for the holding hand status change event.
  console.info('off succeeded');
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to unsubscribe holdingHandChanged. Code: ${error.code}, message: ${error.message}`);
}
```
