# offOperatingHandChanged

## 导入模块

```TypeScript
import { motion } from '@kit.MultimodalAwarenessKit';
```

## offOperatingHandChanged

```TypeScript
function offOperatingHandChanged(callback?: Callback<OperatingHandStatus>): void
```

取消订阅触控操作手变化事件。

**起始版本：** 23

**需要权限：** ohos.permission.ACTIVITY_MOTION 或 ohos.permission.DETECT_GESTURE

<!--Device-motion-function offOperatingHandChanged(callback?: Callback<OperatingHandStatus>): void--><!--Device-motion-function offOperatingHandChanged(callback?: Callback<OperatingHandStatus>): void-End-->

**系统能力：** SystemCapability.MultimodalAwareness.Motion

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[OperatingHandStatus](arkts-multimodalawareness-motion-operatinghandstatus-e.md)&gt; | 否 | 回调函数，返回操作手状态信息。需要取消监听的回调函数，需与订阅时传入的回调函数一致。 <br>若不填，则取消当前监听该事件的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function can not work correctly due to limited <br> device capabilities. |
| [31500001](../../apis-multimodalawareness-kit/errorcode-motion.md#31500001-服务异常) | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; <br> 2. N-API invocation exception, invalid N-API status. |
| [31500003](../../apis-multimodalawareness-kit/errorcode-motion.md#31500003-取消订阅失败) | Unsubscription failed. Possible causes: 1. Callback failure; <br> 2. N-API invocation exception, invalid N-API status; 3. IPC request exception. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. An attempt was made to unsubscribe operatingHandChanged <br> event forbidden by permission: ohos.permission.ACTIVITY_MOTION 或 ohos.permission.DETECT_GESTURE. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import motion from '@ohos.multimodalAwareness.motion';

try {
    motion.offOperatingHandChanged();
    console.info("off succeeded");
} catch (err) {
    let error = err as BusinessError;
    console.error("Failed off and err code is " + error.code);
}
```

