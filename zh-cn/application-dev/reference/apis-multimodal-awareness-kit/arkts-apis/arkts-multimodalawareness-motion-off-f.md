# off

## 导入模块

```TypeScript
import { motion } from '@kit.MultimodalAwarenessKit';
```

## off('operatingHandChanged')

```TypeScript
function off(type: 'operatingHandChanged', callback?: Callback<OperatingHandStatus>): void
```

取消订阅触控操作手感知事件。若未调用on()就调用off()，该方法会抛出异常。相关方法：on('operatingHandChanged')：订阅触控操作手感知事件。

**起始版本：** 15

**需要权限：** 
- API版本20+：ohos.permission.ACTIVITY_MOTION 或 ohos.permission.DETECT_GESTURE
- API版本15 - 19：ohos.permission.ACTIVITY_MOTION

**系统能力：** SystemCapability.MultimodalAwareness.Motion

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'operatingHandChanged' | 是 | 事件类型。固定传入'operatingHandChanged'，表示操作手状态变化。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OperatingHandStatus](arkts-multimodalawareness-motion-operatinghandstatus-e.md)&gt; | 否 | 回调函数，返回操作手状态信息。需要取消监听的回调函数，需与订阅时传入的回调函数一致。 若不填，则取消当前监听该事件的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. An attempt was made to unsubscribe operatingHandChanged event forbidden by permission: ohos.permission.ACTIVITY_MOTION 或 ohos.permission.DETECT_GESTURE. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function can not work correctly due to limited device capabilities. |
| [31500001](../errorcode-motion.md#31500001-服务异常) | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception;   2. N-API invocation exception, invalid N-API status. |
| [31500003](../errorcode-motion.md#31500003-取消订阅失败) | Unsubscription failed. Possible causes: 1. Callback failure;   2. N-API invocation exception, invalid N-API status; 3. IPC request exception. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    motion.off('operatingHandChanged');
    console.info('off succeeded');
} catch (err) {
    let error = err as BusinessError;
    console.error(`Failed to unsubscribe operatingHandChanged. Code: ${error.code}, message: ${error.message}`);
}
```


## off('holdingHandChanged')

```TypeScript
function off(type: 'holdingHandChanged', callback?: Callback<HoldingHandStatus>): void
```

取消订阅握持手状态变化感知事件。若未调用on()就调用off()，该方法会抛出异常。相关方法：on('holdingHandChanged')：订阅握持手状态变化感知事件。

**起始版本：** 20

**需要权限：** ohos.permission.DETECT_GESTURE

**系统能力：** SystemCapability.MultimodalAwareness.Motion

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'holdingHandChanged' | 是 | 事件类型，固定传入'holdingHandChanged'，表示握持手状态变化。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HoldingHandStatus](arkts-multimodalawareness-motion-holdinghandstatus-e.md)&gt; | 否 | 回调函数，返回握持手状态信息。需要取消监听的回调函数，需与订阅时传入的回调函数一致。 若不填，则取消当前监听该事件的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. An attempt was made to unsubscribe holdingHandChanged event forbidden by permission: ohos.permission.DETECT_GESTURE. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function can not work correctly due to limited device capabilities. |
| [31500001](../errorcode-motion.md#31500001-服务异常) | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception;   2. N-API invocation exception, invalid N-API status. |
| [31500003](../errorcode-motion.md#31500003-取消订阅失败) | Unsubscription failed. Possible causes: 1. Callback failure;   2. N-API invocation exception, invalid N-API status; 3. IPC request exception. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  motion.off('holdingHandChanged'); // 移除所有同类订阅
  console.info('off succeeded');
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to unsubscribe holdingHandChanged. Code: ${error.code}, message: ${error.message}`);
}
```
