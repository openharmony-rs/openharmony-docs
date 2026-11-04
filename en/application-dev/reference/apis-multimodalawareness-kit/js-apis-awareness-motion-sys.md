# @ohos.multimodalAwareness.motion (Motion Awareness) (System API)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @saga2025-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=9fddba7cff4ec815ef39c869017e0dacba49e413 translatedAt=2026-11-04T06:19:32.496Z pushedAt=2026-11-04T08:04:44.828Z nl=1 -->

This module provides motion awareness capabilities such as user gesture recognition and device posture monitoring, for perceiving device status, recognizing user behavior, and optimizing the interaction experience.

**Since**: 26.0.0

> **NOTE**
>
> The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { motion } from '@kit.MultimodalAwarenessKit';
```

## PickupEvent

Enumerates the pickup events.

**Since**: 26.0.0

**System Capability**: SystemCapability.MultimodalAwareness.Motion

**System API**: This is a system API.

| Name       | Value | Description                     |
| ---------- | ---- | ------------------------ |
| PICKED_UP  | 0    | Detects a pickup action (the device is lifted). |

## RotateEvent

Enumerates the rotation events.

**Since**: 26.0.0

**System Capability**: SystemCapability.MultimodalAwareness.Motion

**System API**: This API is a system API.

| Name      | Value | Description                                                         |
| --------- | ---- | ------------------------------------------------------------ |
| UNCHANGED | -1   | Indicates that the device has a rotation action, but the rotation amplitude is insufficient to change the current direction, and the direction remains the same as before. |
| UPRIGHT   | 0    | The device is placed upright.                                           |
| LEFT      | 1    | The device is rotated to the left.                                           |
| INVERTED  | 2    | The device is inverted.                                               |
| RIGHT     | 3    | The device is rotated to the right.                                           |

## PhysicalOrientation

Enumerates the physical orientations detected by the sensor.

**Since**: 26.0.0

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

**Since**: 26.0.0

**System Capability**: SystemCapability.MultimodalAwareness.Motion

**System API**: This API is a system API.

| Name      | Value | Description                                     |
| --------- | ---- | ---------------------------------------- |
| UNKNOWN   | -1   | Unknown. |
| UPRIGHT   | 0    | Vertical.                               |
| LEFT      | 1    | Left.                               |
| INVERTED  | 2    | Inverted.                       |
| RIGHT     | 3    | Right.                               |

## HoverHandAction

Enumerates the hover hand actions.

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.Motion

**System API**: This API is a system API.

| Name | Value   | Description                     |
| ---- | ---- | ------------------------ |
| DOWN | 0    | The hover hand enters the detection area. |
| UP   | 1    | The hover hand leaves the detection area. |

## SmartRotateEvent

Defines the basic data structure of the smart rotation sensor event. The event contains the physical orientation detected by the sensor and the logical orientation calculated by the smart algorithm.

**Since:** 26.0.0

**System Capability**: SystemCapability.MultimodalAwareness.Motion

**System API**: This API is a system API.

| Name               | Type                   | Read-only      | Optional       | Description     |
| -------------------| ----------------------| ----------|----------|--------|
| physicalOrientation       | [PhysicalOrientation](#physicalorientation)   | No        | No         | Physical orientation reported by the gravity sensor.|
| logicalOrientation        | [LogicalOrientation](#logicalorientation)     | No        | Yes          | Logical orientation adjusted by the smart algorithm. When the smart algorithm cannot determine the orientation, this field may be empty or not returned.|

## HoverHandDetectionArea

Basic data structure of the floating manual rectangular detection area.

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.Motion

**System API**: This API is a system API.

| Name   | Type   | Read-Only | Optional | Description                                                         |
| ------ | ------ | ---- | ---- | ------------------------------------------------------------ |
| left   | number | No   | No   | Left boundary of the rectangular area, in px. This parameter must be an integer, with a value range of [-2147483648, 2147483647]. |
| top    | number | No   | No   | Top boundary of the rectangular area, in px. This parameter must be an integer, with a value range of [-2147483648, 2147483647]. |
| width  | number | No   | No   | Width of the rectangular area, in px. This parameter must be an integer, with a value range of [1, 2147483647]. |
| height | number | No   | No   | Height of the rectangular area, in px. This parameter must be an integer, with a value range of [1, 2147483647]. |

## motion.onPickupChange

onPickupChange(callback: Callback&lt;PickupEvent&gt;): void

Subscribes to the pickup sensor event. This event is triggered and the callback is invoked when the system detects that the device is picked up. It can be used in scenarios such as triggering smart wake-up. This API must be used in pair with offPickupChange. After use, call offPickupChange to unsubscribe and release system resources.

**Since**: 26.0.0

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
    console.error(`Failed onPickupChange. Code: ${error.code}, message: ${error.message}`);
}
```

## motion.onRotateChange

onRotateChange(callback: Callback&lt;RotateEvent&gt;): void

Subscribes to the rotation sensor event. This event is triggered and the callback is invoked when the device rotates and causes an orientation change. It is used when functions such as adaptive screen orientation need to be implemented. This API must be used in pair with offRotateChange. After use, call offRotateChange to unsubscribe and release system resources.

**Since**: 26.0.0

**System Capability**: SystemCapability.MultimodalAwareness.Motion

**System API**: This API is a system API and can be called only by system applications.

**Parameters**

| Name   | Type                                             | Mandatory | Description                               |
| -------- | ------------------------------------------------ | ---- | ---------------------------------- |
| callback | Callback&lt;[RotateEvent](#rotateevent)&gt; | Yes | Callback invoked to return the rotation event. |

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
    console.error(`Failed onRotateChange. Code: ${error.code}, message: ${error.message}`);
}
```

## motion.onSmartRotateChange

onSmartRotateChange(callback: Callback&lt;SmartRotateEvent&gt;): void

Subscribes to the smart rotation sensor event. This event is triggered and the callback is invoked when the physical orientation of the device changes or the smart algorithm adjusts the logical orientation. It is used in scenarios such as implementing smart screen rotation. This API must be used in pair with offSmartRotateChange. After use, call offSmartRotateChange to unsubscribe and release system resources.

Compared with onRotateChange, onSmartRotateChange not only returns the physical orientation detected by the gravity sensor, but also provides the logical orientation adjusted by the smart algorithm

**Since**: 26.0.0

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
        console.info('callback succeeded: physicalOrientation=' + data.physicalOrientation + 
            ', logicalOrientation=' + (data.logicalOrientation ?? 'unknown'));
    });
} catch (err) {
    let error = err as BusinessError;
    console.error(`Failed onSmartRotateChange. Code: ${error.code}, message: ${error.message}`);
}
```

## motion.onHoverHandChange

onHoverHandChange(detectionArea: HoverHandDetectionArea, callback: Callback&lt;HoverHandAction&gt;): void

Subscribes to the floating manual event and immediately starts floating manual event detection, with a detection duration of five seconds. This API must be used in pair with offHoverHandChange. After use, call offHoverHandChange to unsubscribe and release system resources.

> **NOTE**
>
> After the detection duration expires, floating manual event detection is automatically terminated and floating manual events are no longer reported. The developer needs to call this API again to restart detection.

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.Motion

**System API**: This API is a system API and can be called only by system applications.

**Parameters**

| Name          | Type                                                | Mandatory | Description                                                         |
| ------------- | --------------------------------------------------- | --------- | ------------------------------------------------------------ |
| detectionArea | [HoverHandDetectionArea](#hoverhanddetectionarea)   | Yes       | Rectangular area for floating manual detection, used to specify the area on the device screen where floating manual events are detected.<br/>If this API is called repeatedly, the previously passed detection area is overwritten.<br/>If the rectangular area exceeds the screen, the overlapping part of the rectangular area and the screen is detected by default. |
| callback      | Callback&lt;[HoverHandAction](#hoverhandaction)&gt; | Yes       | Callback invoked to return the floating manual action information.                           |

**Error codes**

For details about the following error codes, see [Motion Awareness Error Codes](errorcode-motion.md) and [General Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |
| 31500001 | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status. |
| 31500002 | Subscription failed. Possible causes: 1. Callback registration failure; 2. Failed to bind native object to js wrapper; 3. N-API invocation exception, invalid N-API status; 4. IPC request exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { motion } from '@kit.MultimodalAwarenessKit';

try {
    let area: motion.HoverHandDetectionArea = {
      left: 0,
      top: 0,
      width: 100,
      height: 100
    };
    motion.onHoverHandChange(area, (data: motion.HoverHandAction) => {
        console.info('callback succeeded: hoverHandAction=' + data);
    });
} catch (err) {
    let error = err as BusinessError;
    console.error(`Failed onHoverHandChange. Code: ${error.code}, message: ${error.message}`);
}
```

## motion.onHoverHandChange

onHoverHandChange(detectionArea: HoverHandDetectionArea, duration: int, callback: Callback&lt;HoverHandAction&gt;): void

Subscribes to the floating manual event and immediately starts floating manual event detection, with support for specifying the detection duration. This API must be used in pair with offHoverHandChange. After use, call offHoverHandChange to unsubscribe and release system resources.

> **NOTE**
>
> After the detection duration expires, floating hand event detection is automatically terminated and floating hand events are no longer reported. The developer needs to call this API again to restart detection.

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.Motion

**System API**: This API is a system API and can be called only by system applications.

**Parameters**

| Name          | Type                                                | Mandatory | Description                                                         |
| ------------- | --------------------------------------------------- | --------- | ------------------------------------------------------------ |
| detectionArea | [HoverHandDetectionArea](#hoverhanddetectionarea)   | Yes       | Target detection rectangular area, used to specify the area on the device screen for detecting floating manual events.<br/>If this API is called repeatedly, the previously passed detection area is overwritten.<br/>If the rectangular area exceeds the screen, the overlapping part of the rectangular area and the screen is detected by default. |
| duration      | number                                              | Yes       | Target detection duration, in seconds. This parameter must be an integer, with a value range of [1, 10].<br/>Floating manual detection is a high-power-consumption detection. It is recommended that developers set the detection duration as needed. |
| callback      | Callback&lt;[HoverHandAction](#hoverhandaction)&gt; | Yes       | Callback invoked to return the floating manual action information.                           |

**Error codes**

For details about the following error codes, see [Motion Awareness Error Codes](errorcode-motion.md) and [General Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |
| 31500001 | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status. |
| 31500002 | Subscription failed. Possible causes: 1. Callback registration failure; 2. Failed to bind native object to js wrapper; 3. N-API invocation exception, invalid N-API status; 4. IPC request exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { motion } from '@kit.MultimodalAwarenessKit';

try {
    let area: motion.HoverHandDetectionArea = {
      left: 0,
      top: 0,
      width: 100,
      height: 100
    };
    let duration: number = 6;
    motion.onHoverHandChange(area, duration, (data: motion.HoverHandAction) => {
        console.info('callback succeeded: hoverHandAction=' + data);
    });
} catch (err) {
    let error = err as BusinessError;
    console.error(`Failed onHoverHandChange. Code: ${error.code}, message: ${error.message}`);
}
```

## motion.offPickupChange

offPickupChange(callback?: Callback&lt;PickupEvent&gt;): void

Unsubscribes from the pickup sensor event. This API takes effect only after onPickupChange is called to subscribe. If no subscription is made, it does not take effect. Use this API when the application no longer needs to listen for pickup events, for example, when a page is destroyed, the application enters the background, or related functions are paused, to unsubscribe and release system resources.

**Since**: 26.0.0

**System Capability**: SystemCapability.MultimodalAwareness.Motion

**System API**: This API is a system API and can be called only by system applications.

**Parameters**

| Name   | Type                                             | Mandatory | Description                                   |
| -------- | ------------------------------------------------ | ---- | -------------------------------------- |
| callback | Callback&lt;[PickupEvent](#pickupevent)&gt;     | No   | Callback for the pickup event. If this parameter is not passed, all callbacks for the pickup event are unsubscribed.             |

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
    console.error(`Failed offPickupChange. Code: ${error.code}, message: ${error.message}`);
}
```

## motion.offRotateChange

offRotateChange(callback?: Callback&lt;RotateEvent&gt;): void

Unsubscribes from the rotation sensor event. This API takes effect only after onRotateChange is called to subscribe. If no subscription is made, it does not take effect. Use this API when the application no longer needs to listen for rotation events, for example, when a page is destroyed, the application enters the background, or related functions are paused, to unsubscribe and release system resources.

**Since**: 26.0.0

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
    console.error(`Failed offRotateChange. Code: ${error.code}, message: ${error.message}`);
}
```

## motion.offSmartRotateChange

offSmartRotateChange(callback?: Callback&lt;SmartRotateEvent&gt;): void

Unsubscribes from the smart rotation sensor event. This API takes effect only after onSmartRotateChange is called to subscribe. If no subscription is made, it does not take effect. Use this API when the application no longer needs to listen for smart rotation events, for example, when a page is destroyed, the application enters the background, or related functions are paused, to unsubscribe and release system resources.

**Since**: 26.0.0

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
    console.error(`Failed offSmartRotateChange. Code: ${error.code}, message: ${error.message}`);
}
```

## motion.offHoverHandChange

offHoverHandChange(callback?: Callback&lt;HoverHandAction&gt;): void

Unsubscribes from the floating manual event. When an application no longer needs to listen for the floating manual event, it should call this API to unsubscribe and release system resources.

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.Motion

**System API**: This API is a system API and can be called only by system applications.

**Parameters**

| Name   | Type                                                | Mandatory | Description                                                         |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[HoverHandAction](#hoverhandaction)&gt; | No   | Callback for the floating manual event to be unsubscribed from. If this parameter is not specified, all callbacks for the floating manual event are unsubscribed from. |

**Error codes**

For details about the following error codes, see [Motion Awareness Error Codes](errorcode-motion.md) and [General Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 31500001 | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status. |
| 31500003 | Unsubscription failed. Possible causes: 1. Callback failure; 2. N-API invocation exception, invalid N-API status; 3. IPC request exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { motion } from '@kit.MultimodalAwarenessKit';

try {
    const callback = (data: motion.HoverHandAction) => {
        console.info('callback succeeded: ' + data);
    };
    let area: motion.HoverHandDetectionArea = {
      left: 0,
      top: 0,
      width: 100,
      height: 100
    };
    motion.onHoverHandChange(area, callback);
    motion.offHoverHandChange(callback); // Unsubscribe the specified callback.
    console.info('offHoverHandChange succeeded');
} catch (err) {
    let error = err as BusinessError;
    console.error(`Failed offHoverHandChange. Code: ${error.code}, message: ${error.message}`);
}
```

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { motion } from '@kit.MultimodalAwarenessKit';

try {
    motion.offHoverHandChange(); // Unsubscribe all callbacks.
    console.info('offHoverHandChange succeeded');
} catch (err) {
    let error = err as BusinessError;
    console.error(`Failed offHoverHandChange. Code: ${error.code}, message: ${error.message}`);
}
```
