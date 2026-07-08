# @ohos.multimodalAwareness.motion (动作感知能力)(系统接口)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @saga2025-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->

本模块提供对用户动作的感知能力，包括用户的手势、动作等。

**起始版本**：26.0.0

> **说明：**
>
> 本模块为系统接口。

## 导入模块

```ts
import { motion } from '@kit.MultimodalAwarenessKit';
```

## PickupEvent

拾取事件枚举。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.Motion

**系统接口**：该接口为系统接口。

| 名称       | 值   | 说明                     |
| ---------- | ---- | ------------------------ |
| PICKED_UP  | 0    | 表示检测到拾取动作（设备正被抬起）。 |

## RotateEvent

旋转事件枚举。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.Motion

**系统接口**：该接口为系统接口。

| 名称      | 值   | 说明                                                         |
| --------- | ---- | ------------------------------------------------------------ |
| UNCHANGED | -1   | 表示设备已旋转，但移动幅度不足以改变当前方向，方向保持与之前一致。 |
| UPRIGHT   | 0    | 表示设备竖直放置。                                           |
| LEFT      | 1    | 表示设备向左旋转。                                           |
| INVERTED  | 2    | 表示设备倒置。                                               |
| RIGHT     | 3    | 表示设备向右旋转。                                           |

## PhysicalOrientation

传感器检测到的物理方向枚举。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.Motion

**系统接口**：该接口为系统接口。

| 名称      | 值   | 说明                   |
| --------- | ---- | ---------------------- |
| UPRIGHT   | 0    | 表示竖直。             |
| LEFT      | 1    | 表示向左。             |
| INVERTED  | 2    | 表示物理方向倒置。     |
| RIGHT     | 3    | 表示向右。             |
| FACE_UP   | 4    | 表示正面朝上。         |
| FACE_DOWN | 5    | 表示正面朝下。         |

## LogicalOrientation

由智能算法计算出的逻辑方向枚举。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.Motion

**系统接口**：该接口为系统接口。

| 名称      | 值   | 说明                                     |
| --------- | ---- | ---------------------------------------- |
| UNKNOWN   | -1   | 表示方向未知或无法确定（例如非握持状态）。 |
| UPRIGHT   | 0    | 表示竖直。                               |
| LEFT      | 1    | 表示向左。                               |
| INVERTED  | 2    | 表示逻辑方向倒置。                       |
| RIGHT     | 3    | 表示向右。                               |

## SmartRotateEvent

智能旋转传感器事件的基本数据结构。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.Motion

**系统接口**：该接口为系统接口。

| 名称               | 类型                   | 只读      | 可选       | 说明     |
| -------------------| ----------------------| ----------|----------|--------|
| physicalOrientation       | [PhysicalOrientation](#physicalorientation)   | 否        | 否         | 重力传感器报告的物理方向。|
| logicalOrientation        | [LogicalOrientation](#logicalorientation)     | 否        | 是          | 智能算法调整后的逻辑方向。|

## motion.onPickupChange

onPickupChange(callback: Callback&lt;PickupEvent&gt;): void

订阅拾取传感器事件。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.Motion

**系统接口**：此接口为系统接口，仅系统应用可调用。

**参数**：

| 参数名   | 类型                                             | 必填 | 说明                           |
| -------- | ------------------------------------------------ | ---- | ------------------------------ |
| callback | Callback&lt;[PickupEvent](#pickupevent)&gt;     | 是   | 回调函数，用于接收拾取状态。   |

**错误码**：

以下错误码的详细介绍请参见[动作感知错误码](errorcode-motion.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | Permission verification failed. A non-system application calls a system API.                                      |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities.                                    |
| 31500001 | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status.                                           |

**示例**：

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

订阅旋转传感器事件。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.Motion

**系统接口**：此接口为系统接口，仅系统应用可调用。

**参数**：

| 参数名   | 类型                                             | 必填 | 说明                               |
| -------- | ------------------------------------------------ | ---- | ---------------------------------- |
| callback | Callback&lt;[RotateEvent](#rotateevent)&gt;     | 是   | 回调函数，用于接收旋转方向。       |

**错误码**：

以下错误码的详细介绍请参见[动作感知错误码](errorcode-motion.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | Permission verification failed. A non-system application calls a system API.                                      |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities.                                    |
| 31500001 | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status.                                           |

**示例**：

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

订阅智能旋转传感器事件。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.Motion

**系统接口**：此接口为系统接口，仅系统应用可调用。

**参数**：

| 参数名   | 类型                                                     | 必填 | 说明                                   |
| -------- | -------------------------------------------------------- | ---- | -------------------------------------- |
| callback | Callback&lt;[SmartRotateEvent](#smartrotateevent)&gt;   | 是   | 回调函数，用于接收智能旋转方向信息。   |

**错误码**：

以下错误码的详细介绍请参见[动作感知错误码](errorcode-motion.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | Permission verification failed. A non-system application calls a system API.                                      |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities.                                    |
| 31500001 | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status.                                           |

**示例**：

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

取消订阅拾取传感器事件。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.Motion

**系统接口**：此接口为系统接口，仅系统应用可调用。

**参数**：

| 参数名   | 类型                                             | 必填 | 说明                                   |
| -------- | ------------------------------------------------ | ---- | -------------------------------------- |
| callback | Callback&lt;[PickupEvent](#pickupevent)&gt;     | 否   | 需取消的拾取事件回调函数，若无此参数，则取消订阅拾取事件的所有回调函数。             |

**错误码**：

以下错误码的详细介绍请参见[动作感知错误码](errorcode-motion.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | Permission verification failed. A non-system application calls a system API.                                      |
| 31500001 | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status.                                           |

**示例**：

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

取消订阅旋转传感器事件。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.Motion

**系统接口**：此接口为系统接口，仅系统应用可调用。

**参数**：

| 参数名   | 类型                                             | 必填 | 说明                                   |
| -------- | ------------------------------------------------ | ---- | -------------------------------------- |
| callback | Callback&lt;[RotateEvent](#rotateevent)&gt;     | 否   | 需取消的旋转事件回调函数，若无此参数，则取消订阅旋转事件的所有回调函数。             |

**错误码**：

以下错误码的详细介绍请参见[动作感知错误码](errorcode-motion.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | Permission verification failed. A non-system application calls a system API.                                      |
| 31500001 | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status.                                           |

**示例**：

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

取消订阅智能旋转传感器事件。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.Motion

**系统接口**：此接口为系统接口，仅系统应用可调用。

**参数**：

| 参数名   | 类型                                                     | 必填 | 说明                                       |
| -------- | -------------------------------------------------------- | ---- | ------------------------------------------ |
| callback | Callback&lt;[SmartRotateEvent](#smartrotateevent)&gt;   | 否   | 需取消的智能旋转事件回调函数，若无此参数，则取消订阅智能旋转事件的所有回调函数。             |

**错误码**：

以下错误码的详细介绍请参见[动作感知错误码](errorcode-motion.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | Permission verification failed. A non-system application calls a system API.                                      |
| 31500001 | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status.                                           |

**示例**：

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
