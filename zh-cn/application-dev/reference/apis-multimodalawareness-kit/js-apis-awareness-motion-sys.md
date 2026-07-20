# @ohos.multimodalAwareness.motion (动作感知能力)(系统接口)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @saga2025-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->

本模块提供对用户手势识别、设备姿态监听等动作感知能力，用于感知设备状态、识别用户行为，优化交互体验。

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

| 名称       | 值   | 说明                 |
| ---------- | ---- |--------------------|
| PICKED_UP  | 0    | 表示检测到拾取动作（设备被抬起）。 |

## RotateEvent

旋转事件枚举。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.Motion

**系统接口**：该接口为系统接口。

| 名称      | 值   | 说明                                                         |
| --------- | ---- | ------------------------------------------------------------ |
| UNCHANGED | -1   | 表示设备有旋转动作，但旋转幅度不足以改变当前方向，方向保持与之前一致。 |
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

智能旋转传感器事件的基本数据结构。该事件包含传感器检测到的物理方向和由智能算法计算得出的逻辑方向。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.Motion

**系统接口**：该接口为系统接口。

| 名称               | 类型                   | 只读      | 可选       | 说明     |
| -------------------| ----------------------| ----------|----------|--------|
| physicalOrientation       | [PhysicalOrientation](#physicalorientation)   | 否        | 否         | 重力传感器报告的物理方向。|
| logicalOrientation        | [LogicalOrientation](#logicalorientation)     | 否        | 是          | 智能算法调整后的逻辑方向。|

## motion.onPickupChange

onPickupChange(callback: Callback&lt;PickupEvent&gt;): void

订阅拾取传感器事件。需与offPickupChange配对使用，使用完毕后应调用offPickupChange取消订阅以释放系统资源。

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
    console.error(`Failed onPickupChange. Code: ${error.code}, message: ${error.message}`);
}
```

## motion.onRotateChange

onRotateChange(callback: Callback&lt;RotateEvent&gt;): void

订阅旋转传感器事件。需与offRotateChange配对使用，使用完毕后应调用offRotateChange取消订阅以释放系统资源。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.Motion

**系统接口**：此接口为系统接口，仅系统应用可调用。

**参数**：

| 参数名   | 类型                                             | 必填 | 说明             |
| -------- | ------------------------------------------------ | ---- |----------------|
| callback | Callback&lt;[RotateEvent](#rotateevent)&gt;     | 是   | 回调函数，用于接收旋转事件。 |

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
    console.error(`Failed onRotateChange. Code: ${error.code}, message: ${error.message}`);
}
```

## motion.onSmartRotateChange

onSmartRotateChange(callback: Callback&lt;SmartRotateEvent&gt;): void

订阅智能旋转传感器事件。需与offSmartRotateChange配对使用，使用完毕后应调用offSmartRotateChange取消订阅以释放系统资源。

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
        console.info('callback succeeded: physicalOrientation=' + data.physicalOrientation + 
            ', logicalOrientation=' + (data.logicalOrientation ?? 'unknown'));
    });
} catch (err) {
    let error = err as BusinessError;
    console.error(`Failed onSmartRotateChange. Code: ${error.code}, message: ${error.message}`);
}
```

## motion.offPickupChange

offPickupChange(callback?: Callback&lt;PickupEvent&gt;): void

取消订阅拾取传感器事件。当应用不再需要监听拾取事件时使用，如页面销毁、应用进入后台或暂停相关功能时，应调用此接口取消订阅以释放系统资源。

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
    const callback = (data: motion.PickupEvent) => {
        console.info('callback succeeded: ' + data);
    };
    motion.onPickupChange(callback);
    motion.offPickupChange(callback); // 取消指定回调
    console.info('offPickupChange succeeded');
} catch (err) {
    let error = err as BusinessError;
    console.error(`Failed offPickupChange. Code: ${error.code}, message: ${error.message}`);
}
```

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { motion } from '@kit.MultimodalAwarenessKit';

try {
    motion.offPickupChange(); // 取消所有回调
    console.info('offPickupChange succeeded');
} catch (err) {
    let error = err as BusinessError;
    console.error(`Failed offPickupChange. Code: ${error.code}, message: ${error.message}`);
}
```

## motion.offRotateChange

offRotateChange(callback?: Callback&lt;RotateEvent&gt;): void

取消订阅旋转传感器事件。当应用不再需要监听旋转事件时使用，应调用此接口取消订阅以释放系统资源。

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
    const callback = (data: motion.RotateEvent) => {
        console.info('callback succeeded: ' + data);
    };
    motion.onRotateChange(callback);
    motion.offRotateChange(callback); // 取消指定回调
    console.info('offRotateChange succeeded');
} catch (err) {
    let error = err as BusinessError;
    console.error(`Failed offRotateChange. Code: ${error.code}, message: ${error.message}`);
}
```

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { motion } from '@kit.MultimodalAwarenessKit';

try {
    motion.offRotateChange(); // 取消所有回调
    console.info('offRotateChange succeeded');
} catch (err) {
    let error = err as BusinessError;
    console.error(`Failed offRotateChange. Code: ${error.code}, message: ${error.message}`);
}
```

## motion.offSmartRotateChange

offSmartRotateChange(callback?: Callback&lt;SmartRotateEvent&gt;): void

取消订阅智能旋转传感器事件。当应用不再需要监听智能旋转事件时使用，应调用此接口取消订阅以释放系统资源。

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
    const callback = (data: motion.SmartRotateEvent) => {
        console.info('callback succeeded: physicalOrientation=' + data.physicalOrientation + 
            ', logicalOrientation=' + (data.logicalOrientation ?? 'unknown'));
    };
    motion.onSmartRotateChange(callback);
    motion.offSmartRotateChange(callback); // 取消指定回调
    console.info('offSmartRotateChange succeeded');
} catch (err) {
    let error = err as BusinessError;
    console.error(`Failed offSmartRotateChange. Code: ${error.code}, message: ${error.message}`);
}
```

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { motion } from '@kit.MultimodalAwarenessKit';

try {
    motion.offSmartRotateChange(); // 取消所有回调
    console.info('offSmartRotateChange succeeded');
} catch (err) {
    let error = err as BusinessError;
    console.error(`Failed offSmartRotateChange. Code: ${error.code}, message: ${error.message}`);
}
```
