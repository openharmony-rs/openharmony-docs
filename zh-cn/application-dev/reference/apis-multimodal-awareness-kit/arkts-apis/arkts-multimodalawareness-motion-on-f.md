# on

## 导入模块

```TypeScript
import { motion } from '@kit.MultimodalAwarenessKit';
```

## on('operatingHandChanged')

```TypeScript
function on(type: 'operatingHandChanged', callback: Callback<OperatingHandStatus>): void
```

订阅触控操作手感知事件。系统通过触控屏传感器采集用户触控数据，结合手势识别算法判断当前操作手是左手还是右手。适用于手势交付、单双手操作适配等场景， 通过识别用户的触控操作手状态优化界面布局和交互方式。建议在使用完毕后调用off()取消订阅以释放资源，避免多余的性能功耗开销。 相关方法：off('operatingHandChanged')：取消订阅触控操作手感知事件。如果设备不支持此功能，将返回801错误码。

**起始版本：** 15

**需要权限：** 
- API版本20+：ohos.permission.ACTIVITY_MOTION 或 ohos.permission.DETECT_GESTURE
- API版本15 - 19：ohos.permission.ACTIVITY_MOTION

**系统能力：** SystemCapability.MultimodalAwareness.Motion

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'operatingHandChanged' | 是 | 事件类型。固定传入'operatingHandChanged'，表示操作手状态变化。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OperatingHandStatus](arkts-multimodalawareness-motion-operatinghandstatus-e.md)&gt; | 是 | 回调函数，返回操作手状态信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. An attempt was made to subscribe operatingHandChanged event forbidden by permission: ohos.permission.ACTIVITY_MOTION 或 ohos.permission.DETECT_GESTURE. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function can not work correctly due to limited device capabilities. |
| [31500001](../errorcode-motion.md#31500001-服务异常) | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception;   2. N-API invocation exception, invalid N-API status. |
| [31500002](../errorcode-motion.md#31500002-订阅失败) | Subscription failed. Possible causes: 1. Callback registration failure;   2. Failed to bind native object to js wrapper; 3. N-API invocation exception, invalid N-API status; 4. IPC request exception. |

**示例**

```TypeScript
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


## on('holdingHandChanged')

```TypeScript
function on(type: 'holdingHandChanged', callback: Callback<HoldingHandStatus>): void
```

订阅握持手状态变化感知事件。系统通过传感器数据，结合识别算法判断当前握持手是左手还是右手。适用于阅读应用、视频播放等需要根据用户握持手状态调整界面布局或功能的场景。 建议在使用完毕后调用off()取消订阅以释放资源，避免多余的性能功耗开销。相关方法：off('holdingHandChanged')：取消订阅握持手状态变化感知事件。

**起始版本：** 20

**需要权限：** ohos.permission.DETECT_GESTURE

**系统能力：** SystemCapability.MultimodalAwareness.Motion

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'holdingHandChanged' | 是 | 事件类型，固定传入'holdingHandChanged'，表示握持手状态变化。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HoldingHandStatus](arkts-multimodalawareness-motion-holdinghandstatus-e.md)&gt; | 是 | 回调函数，返回握持手状态信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. An attempt was made to subscribe holdingHandChanged event forbidden by permission: ohos.permission.DETECT_GESTURE. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function can not work correctly due to limited device capabilities. |
| [31500001](../errorcode-motion.md#31500001-服务异常) | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception;   2. N-API invocation exception, invalid N-API status. |
| [31500002](../errorcode-motion.md#31500002-订阅失败) | Subscription failed. Possible causes: 1. Callback registration failure;   2. Failed to bind native object to js wrapper; 3. N-API invocation exception, invalid N-API status; 4. IPC request exception. |

**示例**

```TypeScript
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
