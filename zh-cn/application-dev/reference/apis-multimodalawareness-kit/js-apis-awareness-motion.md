# @ohos.multimodalAwareness.motion (动作感知)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @zou_ye-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->

本模块，提供对用户行为、动作的感知能力，包括用户的手势、动作等。

> **说明：**
>
> 本模块首批接口从API version 15开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## 导入模块

```ts
import { motion } from '@kit.MultimodalAwarenessKit';
```

## OperatingHandStatus

触控操作手状态信息。

**系统能力**：SystemCapability.MultimodalAwareness.Motion

| 名称                | 值   | 说明                   |
| ------------------- | ---- | ---------------------- |
| UNKNOWN_STATUS      | 0    | 表示未识别。 |
| LEFT_HAND_OPERATED  | 1    | 表示触控操作手是左手。 |
| RIGHT_HAND_OPERATED | 2    | 表示触控操作手是右手。 |

## HoldingHandStatus<sup>20+</sup>

手机握持手状态信息，表示握持手状态变化感知事件的结果。订阅握持手状态变化感知事件后，返回当前握持手状态信息。

**系统能力**：SystemCapability.MultimodalAwareness.Motion

| 名称            | 值   | 说明           |
| --------------- | ---- | -------------- |
| NOT_HELD        | 0    | 表示未握持。   |
| LEFT_HAND_HELD  | 1    | 表示左手握持。 |
| RIGHT_HAND_HELD | 2    | 表示右手握持。 |
| BOTH_HANDS_HELD | 3    | 表示双手握持。 |
| UNKNOWN_STATUS  | 16   | 表示未识别。   |

## motion.on('operatingHandChanged')

on(type: 'operatingHandChanged', callback: Callback&lt;OperatingHandStatus&gt;): void;

订阅触控操作手感知事件。

此功能如果设备不支持，将返回801错误码。

**需要权限**：ohos.permission.ACTIVITY_MOTION 或 ohos.permission.DETECT_GESTURE

**系统能力**：SystemCapability.MultimodalAwareness.Motion

**参数**：

| 参数名   | 类型                             | 必填 | 说明                                                         |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                           | 是   | 事件类型。type为“operatingHandChanged”，表示操作手状态变化。 |
| callback | Callback&lt;[OperatingHandStatus](#operatinghandstatus)&gt; | 是   | 回调函数，返回操作手结果。                                   |

**错误码**：

以下错误码的详细介绍请参见[动作感知错误码](errorcode-motion.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to subscribe operatingHandChanged event forbidden by permission: ohos.permission.ACTIVITY_MOTION or ohos.permission.DETECT_GESTURE. |
| 401      | Parameter error. Parameter verification failed. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 31500001 | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status. |
| 31500002 | Subscription failed. Possible causes: 1. Callback registration failure; 2. Failed to bind native object to js wrapper; 3. N-API invocation exception, invalid N-API status; 4. IPC request exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { Callback } from '@ohos.base';

let callback:Callback<motion.OperatingHandStatus> = (data:motion.OperatingHandStatus) => {
    console.info('callback success' + data);
};

try {
    motion.on('operatingHandChanged', callback);  
    console.info("on succeeded");
} catch (err) {
    let error = err as BusinessError;
    console.error("Failed on and err code is " + error.code);
}
```

## motion.off('operatingHandChanged')

off(type: 'operatingHandChanged', callback?: Callback&lt;OperatingHandStatus&gt;): void;

取消订阅触控操作手感知事件。

**需要权限**：ohos.permission.ACTIVITY_MOTION 或 ohos.permission.DETECT_GESTURE

**系统能力**：SystemCapability.MultimodalAwareness.Motion

**参数**：

| 参数名   | 类型                             | 必填 | 说明                                                         |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                           | 是   | 事件类型。type为“operatingHandChanged”，表示操作手状态变化。 |
| callback | Callback&lt;[OperatingHandStatus](#operatinghandstatus)&gt; | 否   | 回调函数，返回操作手结果。                                   |

**错误码**：

以下错误码的详细介绍请参见[动作感知错误码](errorcode-motion.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to unsubscribe operatingHandChanged event forbidden by permission: ohos.permission.ACTIVITY_MOTION or ohos.permission.DETECT_GESTURE. |
| 401      | Parameter error. Parameter verification failed. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 31500001 | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status. |
| 31500003 | Unsubscription failed. Possible causes: 1. Callback failure; 2. N-API invocation exception, invalid N-API status; 3. IPC request exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
    motion.off('operatingHandChanged');
    console.info("off succeeded");
} catch (err) {
    let error = err as BusinessError;
    console.error("Failed off and err code is " + error.code);
}
```

## motion.getRecentOperatingHandStatus()

getRecentOperatingHandStatus(): OperatingHandStatus;

获取最新触控操作手状态。

**需要权限**：ohos.permission.ACTIVITY_MOTION 或 ohos.permission.DETECT_GESTURE

**系统能力**：SystemCapability.MultimodalAwareness.Motion

**返回值**：

| 类型                          | 说明                                 |
| ----------------------------- | ------------------------------------ |
| [OperatingHandStatus](#operatinghandstatus) | 返回触控操作手状态信息。 |

**错误码**：

以下错误码的详细介绍请参见[动作感知错误码](errorcode-motion.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to get the recent operating hand status forbidden by permission: ohos.permission.ACTIVITY_MOTION or ohos.permission.DETECT_GESTURE. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 31500001 | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let data:motion.OperatingHandStatus = motion.getRecentOperatingHandStatus();
    console.info('get success' + data);
} catch (err) {
    let error = err as BusinessError;
    console.error("Failed get and err code is " + error.code);
}
```

## motion.on('holdingHandChanged') <sup>20+</sup>

on(type: 'holdingHandChanged', callback: Callback&lt;HoldingHandStatus&gt;): void;

订阅握持手状态变化感知事件。

**需要权限**：ohos.permission.DETECT_GESTURE

**系统能力**：SystemCapability.MultimodalAwareness.Motion

**参数**

| 参数名   | 类型                                              | 必填 | 说明                                   |
| -------- | ------------------------------------------------- | ---- | -------------------------------------- |
| type     | string                                            | 是   | 事件类型，type为"holdingHandChanged"。 |
| callback | Callback&lt;[HoldingHandStatus](#holdinghandstatus20)&gt; | 是   | 回调函数，返回握持手状态结果。         |

**错误码**

以下错误码的详细介绍请参见[动作感知错误码](errorcode-motion.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to subscribe holdingHandChanged event forbidden by permission: ohos.permission.DETECT_GESTURE. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 31500001 | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status. |
| 31500002 | Subscription failed. Possible causes: 1. Callback registration failure; 2. Failed to bind native object to js wrapper; 3. N-API invocation exception, invalid N-API status; 4. IPC request exception. |

**示例**

```typescript
import { BusinessError } from '@kit.BasicServicesKit';
import { Callback } from '@ohos.base';

let callback:Callback<motion.HoldingHandStatus> = (data:motion.HoldingHandStatus) => {
  console.info('callback success: ' + data);
};

try {
  motion.on('holdingHandChanged', callback);
  console.info('on succeeded');
} catch (err) {
  let error = err as BusinessError;
  console.error('Failed on; err code = ' + error.code);
}
```

## motion.off('holdingHandChanged') <sup>20+</sup>

off(type: 'holdingHandChanged', callback?: Callback&lt;HoldingHandStatus&gt;): void;

取消订阅握持手状态变化感知事件。

**需要权限**：ohos.permission.DETECT_GESTURE

**系统能力**：SystemCapability.MultimodalAwareness.Motion

**参数**

| 参数名   | 类型                                              | 必填 | 说明                                           |
| -------- | ------------------------------------------------- | ---- | ---------------------------------------------- |
| type     | string                                            | 是   | 事件类型，type为"holdingHandChanged"。         |
| callback | Callback&lt;[HoldingHandStatus](#holdinghandstatus20)&gt; | 否   | 需取消的回调函数。省略则移除该事件的所有回调。 |

**错误码**

以下错误码的详细介绍请参见[动作感知错误码](errorcode-motion.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to unsubscribe holdingHandChanged event forbidden by permission: ohos.permission.DETECT_GESTURE. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 31500001 | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status. |
| 31500003 | Unsubscription failed. Possible causes: 1. Callback failure; 2. N-API invocation exception, invalid N-API status; 3. IPC request exception. |

**示例**

```typescript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  motion.off('holdingHandChanged'); // 移除所有同类订阅
  console.info('off succeeded');
} catch (err) {
  let error = err as BusinessError;
  console.error('Failed off; err code = ' + error.code);
}
```
