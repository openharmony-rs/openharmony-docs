# @ohos.multimodalAwareness.motion (Motion Awareness) (System API)

<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @saga2025-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=d18790e6ef1247c1fd8194f3838e7698bf6e9bf2 translatedAt=2026-06-24T06:30:12.461Z pushedAt=2026-06-25T01:35:11.435Z -->

This module provides the capability to perceive user motions, including gestures and movements.

**Since:** 26.0.0

> **NOTE**
>
> The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { motion } from '@kit.MultimodalAwarenessKit';
```

## PickupEvent

Enumerates the pickup events.

**Since:** 26.0.0

**System Capability**: SystemCapability.MultimodalAwareness.Motion

**System API**: This API is a system API.

| Name       | Value | Description                     |
| ---------- | ---- | ------------------------ |
| PICKED_UP  | 0    | A pickup action is detected (the device is being lifted). |

## RotateEvent

Enumerates the rotation events.

**Since:** 26.0.0

**System Capability**: SystemCapability.MultimodalAwareness.Motion

**System API**: This API is a system API.

| Name      | Value | Description                                                         |
| --------- | ---- | ------------------------------------------------------------ |
| UNCHANGED | -1   | The device is rotated, but the movement is insufficient to change the current orientation, which remains the same as before. |
| UPRIGHT   | 0    | The device is placed upright.                                           |
| LEFT      | 1    | The device is rotated to the left.                                           |
| INVERTED  | 2    | The device is inverted.                                               |
| RIGHT     | 3    | The device is rotated to the right.                                           |

## PhysicalOrientation

Enumerates the physical orientations detected by the sensor.

**Since:** 26.0.0

**System Capability**: SystemCapability.MultimodalAwareness.Motion

**System API**: This API is a system API.

| Name      | Value | Description                              |
| --------- | ----- | ---------------------------------------- |
| UPRIGHT   | 0     | Upright.          |
| LEFT      | 1     | Left.          |
| INVERTED  | 2     | Inverted. |
| RIGHT     | 3     | Right.         |
| FACE_UP   | 4     | Face-up.           |
| FACE_DOWN | 5     | Face-down.         |

## LogicalOrientation

Enumerates the logical orientations calculated by the smart algorithm.

**Since:** 26.0.0

**System Capability**: SystemCapability.MultimodalAwareness.Motion

**System API**: This API is a system API.

| Name      | Value | Description                                     |
| --------- | ---- | ---------------------------------------- |
| UNKNOWN   | -1   | Unknown. |
| UPRIGHT   | 0    | Vertical.                               |
| LEFT      | 1    | Left.                               |
| INVERTED  | 2    | Inverted.                       |
| RIGHT     | 3    | Right.                               |

## SmartRotateEvent

Defines the basic data structure of the smart rotation sensor event.

**Since:** 26.0.0

**System Capability**: SystemCapability.MultimodalAwareness.Motion

**System API**: This API is a system API.

| Name               | Type                   | Read-only      | Optional       | Description     |
| -------------------| ----------------------| ----------|----------|--------|
| physicalOrientation       | [PhysicalOrientation](#physicalorientation)   | No        | No         | Physical orientation reported by the gravity sensor.|
| logicalOrientation        | [LogicalOrientation](#logicalorientation)     | No        | Yes          | Logical orientation adjusted by the smart algorithm.|

## motion.onPickupChange

onPickupChange(callback: Callback&lt;PickupEvent&gt;): void

Subscribes to pickup sensor events.

**Since:** 26.0.0

**System Capability**: SystemCapability.MultimodalAwareness.Motion

**System API**: This API is a system API and can be called only by system applications.

**Parameters**

| Name   | Type                                             | Mandatory | Description                           |
| -------- | ------------------------------------------------ | ---- | ------------------------------ |
| callback | Callback&lt;[PickupEvent](#pickupevent)&gt;     | Yes   | Callback used to receive the pickup status.   |

**Error codes**

For details about the following error codes, see [Motion Awareness Error Codes](errorcode-motion.md) and [General Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ------------------------------------------------------------ |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities. |
| 31500001 | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status. |

**Example**:

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { motion } from '@kit.MultimodalAwarenessKit';

try {
    motion.onPickupChange((data: motion.PickupEvent) => {
        console.info('callback succeeded: ' + data);
    });
} catch (err) {
    let error = err as BusinessError;
    console.error("Failed onPickupChange and err code is " + error.code);
}
```

## motion.onRotateChange

onRotateChange(callback: Callback&lt;RotateEvent&gt;): void

Subscribes to rotation sensor events.

**Since:** 26.0.0

**System Capability**: SystemCapability.MultimodalAwareness.Motion

**System API**: This API is a system API and can be called only by system applications.

**Parameters**

| Name   | Type                                             | Mandatory | Description                               |
| -------- | ------------------------------------------------ | ---- | ---------------------------------- |
| callback | Callback&lt;[RotateEvent](#rotateevent)&gt;     | Yes   | Callback used to receive the rotation orientation.       |

**Error codes**

For details about the following error codes, see [Motion Awareness Error Codes](errorcode-motion.md) and [General Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | Permission verification failed. A non-system application calls a system API.                                      |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities.                                    |
| 31500001 | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status.                                           |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { motion } from '@kit.MultimodalAwarenessKit';

try {
    motion.onRotateChange((data: motion.RotateEvent) => {
        console.info('callback succeeded: ' + data);
    });
} catch (err) {
    let error = err as BusinessError;
    console.error("Failed onRotateChange and err code is " + error.code);
}
```

## motion.onSmartRotateChange

onSmartRotateChange(callback: Callback&lt;SmartRotateEvent&gt;): void

Subscribes to smart rotation sensor events.

**Since:** 26.0.0

**System Capability**: SystemCapability.MultimodalAwareness.Motion

**System API**: This API is a system API and can be called only by system applications.

**Parameters**

| Name     | Type                                                     | Mandatory | Description                                   |
| -------- | -------------------------------------------------------- | --------- | --------------------------------------------- |
| callback | Callback&lt;[SmartRotateEvent](#smartrotateevent)&gt;   | Yes       | Callback used to receive smart rotation orientation information. |

**Error codes**

For details about the following error codes, see [Motion Awareness Error Codes](errorcode-motion.md) and [General Error Codes](../errorcode-universal.md).

| ID  | Error Message                                                     |
| --- | ------------------------------------------------------------ |
| 202 | Permission verification failed. A non-system application calls a system API.                                      |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities.                                    |
| 31500001 | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status.                                           |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { motion } from '@kit.MultimodalAwarenessKit';

try {
    motion.onSmartRotateChange((data: motion.SmartRotateEvent) => {
        console.info('callback succeeded: physicalOrientation=' + data.physicalOrientation);
    });
} catch (err) {
    let error = err as BusinessError;
    console.error("Failed onSmartRotateChange and err code is " + error.code);
}
```

## motion.offPickupChange

offPickupChange(callback?: Callback&lt;PickupEvent&gt;): void

Unsubscribes from pickup sensor events.

**Since:** 26.0.0

**System Capability**: SystemCapability.MultimodalAwareness.Motion

**System API**: This API is a system API and can be called only by system applications.

**Parameters**

| Name   | Type                                             | Mandatory | Description                                   |
| -------- | ------------------------------------------------ | ---- | -------------------------------------- |
| callback | Callback&lt;[PickupEvent](#pickupevent)&gt;     | No   | Callback of the pickup event to be unsubscribed. If this parameter is not specified, then all callbacks of the pickup event are unsubscribed.             |

**Error codes**

For details about the following error codes, see [Motion Awareness Error Codes](errorcode-motion.md) and [General Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | Permission verification failed. A non-system application calls a system API.                                      |
| 31500001 | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status.                                           |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { motion } from '@kit.MultimodalAwarenessKit';

try {
    motion.offPickupChange();
    console.info("offPickupChange succeeded");
} catch (err) {
    let error = err as BusinessError;
    console.error("Failed offPickupChange and err code is " + error.code);
}
```

## motion.offRotateChange

offRotateChange(callback?: Callback&lt;RotateEvent&gt;): void

Unsubscribe from the rotation sensor event.

**Since:** 26.0.0

**System Capability**: SystemCapability.MultimodalAwareness.Motion

**System API**: This API is a system API and can be called only by system applications.

**Parameters**

| Name   | Type                                             | Mandatory | Description                                   |
| -------- | ------------------------------------------------ | ---- | -------------------------------------- |
| callback | Callback&lt;[RotateEvent](#rotateevent)&gt;     | No   | Callback of the rotation sensor event to be unsubscribed. If this parameter is not specified, then all callbacks of the rotation sensor event are unsubscribed.             |

**Error codes**

For details about the following error codes, see [Motion Awareness Error Codes](errorcode-motion.md) and [General Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | Permission verification failed. A non-system application calls a system API.                                      |
| 31500001 | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status.                                           |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { motion } from '@kit.MultimodalAwarenessKit';

try {
    motion.offRotateChange();
    console.info("offRotateChange succeeded");
} catch (err) {
    let error = err as BusinessError;
    console.error("Failed offRotateChange and err code is " + error.code);
}
```

## motion.offSmartRotateChange

offSmartRotateChange(callback?: Callback&lt;SmartRotateEvent&gt;): void

Unsubscribes from smart rotation sensor events.

**Since:** 26.0.0

**System Capability**: SystemCapability.MultimodalAwareness.Motion

**System API**: This API is a system API and can be called only by system applications.

**Parameters**

| Name   | Type                                                     | Mandatory | Description                                       |
| -------- | -------------------------------------------------------- | ---- | ------------------------------------------ |
| callback | Callback&lt;[SmartRotateEvent](#smartrotateevent)&gt;   | No   | Callback of the smart rotation event to be unsubscribed. If this parameter is not specified, then all callbacks of the smart rotation event are unsubscribed.             |

**Error codes**

For details about the following error codes, see [Motion Awareness Error Codes](errorcode-motion.md) and [General Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | Permission verification failed. A non-system application calls a system API.                                      |
| 31500001 | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status.                                           |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { motion } from '@kit.MultimodalAwarenessKit';

try {
    motion.offSmartRotateChange();
    console.info("offSmartRotateChange succeeded");
} catch (err) {
    let error = err as BusinessError;
    console.error("Failed offSmartRotateChange and err code is " + error.code);
}
```