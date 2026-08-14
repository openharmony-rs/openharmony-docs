# getRecentOperatingHandStatus

## getRecentOperatingHandStatus

```TypeScript
function getRecentOperatingHandStatus(): OperatingHandStatus
```

获取最新触控操作手状态。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** 
- API版本20+：ohos.permission.ACTIVITY_MOTION or ohos.permission.DETECT_GESTURE
- API版本15 - 19：ohos.permission.ACTIVITY_MOTION

<!--Device-motion-function getRecentOperatingHandStatus(): OperatingHandStatus--><!--Device-motion-function getRecentOperatingHandStatus(): OperatingHandStatus-End-->

**系统能力：** SystemCapability.MultimodalAwareness.Motion

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [OperatingHandStatus](arkts-multimodalawareness-motion-operatinghandstatus-e.md) | 返回触控操作手状态信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function can not work correctly due to limited &lt;br&gt; device capabilities. |
| [31500001](../../apis-multimodalawareness-kit/errorcode-motion.md#31500001-服务异常) | Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; &lt;br&gt; 2. N-API invocation exception, invalid N-API status. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. An attempt was made to get the recent operating hand &lt;br&gt; status forbidden by permission: ohos.permission.ACTIVITY_MOTION or ohos.permission.DETECT_GESTURE. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let data:motion.OperatingHandStatus = motion.getRecentOperatingHandStatus();
    console.info('get succeeded' + data);
} catch (err) {
    let error = err as BusinessError;
    console.error("Failed get and err code is " + error.code);
}
```

