# onUserAgeGroupDetected

## onUserAgeGroupDetected

```TypeScript
function onUserAgeGroupDetected(callback: Callback<UserClassification>): void
```

订阅年龄群组检测功能。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** 24

<!--Device-userStatus-function onUserAgeGroupDetected(callback: Callback<UserClassification>): void--><!--Device-userStatus-function onUserAgeGroupDetected(callback: Callback<UserClassification>): void-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[UserClassification](arkts-multimodalawareness-userstatus-userclassification-i.md)&gt; | 是 | 回调函数，返回检测结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function can not work correctly due to limited &lt;br&gt; device capabilities. |
| [33900001](../../apis-multimodalawareness-kit/errorcode-userStatus.md#33900001-服务异常) | Service exception. Possible causes: &lt;br&gt;1. System error, such as a null pointer and container-related exception. &lt;br&gt;2. Node-API invocation exception, such as invalid Node-API status. |
| [33900002](../../apis-multimodalawareness-kit/errorcode-userStatus.md#33900002-订阅失败) | Subscription failed. Possible causes: &lt;br&gt;1. Callback registration failed. &lt;br&gt;2. Failed to bind the native object to the JS wrapper. &lt;br&gt;3. Node-API invocation exception, such as invalid Node-API status. &lt;br&gt;4. IPC request exception. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    userStatus.onUserAgeGroupDetected((data: userStatus.UserClassification) => {
        console.info('callback success, ageGroup:' + data.ageGroup + ", confidence:" + data.confidence);
    });
    console.info("on succeeded");
} catch (err) {
    let error = err as BusinessError;
    console.error("Failed on and err code is " + error.code);
}
```

