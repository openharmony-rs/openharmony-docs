# onOperatingHandChanged

## onOperatingHandChanged

```TypeScript
function onOperatingHandChanged(callback: Callback<OperatingHandStatus>): void
```

订阅触控操作手变化事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.ACTIVITY_MOTION or ohos.permission.DETECT_GESTURE

<!--Device-motion-function onOperatingHandChanged(callback: Callback<OperatingHandStatus>): void--><!--Device-motion-function onOperatingHandChanged(callback: Callback<OperatingHandStatus>): void-End-->

**系统能力：** SystemCapability.MultimodalAwareness.Motion

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[OperatingHandStatus](arkts-multimodalawareness-motion-operatinghandstatus-e.md)&gt; | 是 | 回调函数，返回操作手状态信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function can not work correctly due to limited &lt;br&gt; device capabilities. |
| [31500001](../../apis-multimodalawareness-kit/errorcode-motion.md#31500001-服务异常) | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; &lt;br&gt; 2. N-API invocation exception, invalid N-API status. |
| [31500002](../../apis-multimodalawareness-kit/errorcode-motion.md#31500002-订阅失败) | Subscription failed. Possible causes: 1. Callback registration failure; &lt;br&gt; 2. Failed to bind native object to js wrapper; 3. N-API invocation exception, invalid N-API status; 4. IPC request exception. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. An attempt was made to subscribe operatingHandChanged &lt;br&gt; event forbidden by permission: ohos.permission.ACTIVITY_MOTION or ohos.permission.DETECT_GESTURE. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import motion from '@ohos.multimodalAwareness.motion';

callback(data:motion.OperatingHandStatus) {
    console.info('callback success' + data);
};

try {
    motion.onOperatingHandChanged(this.callback);  
    console.info("on succeeded");
} catch (err) {
    let error = err as BusinessError;
    console.error("Failed on and err code is " + error.code);
}
```

