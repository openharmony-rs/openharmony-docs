# on

## 导入模块

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## on('userAgeGroupDetected')

```TypeScript
function on(type: 'userAgeGroupDetected', callback: Callback<UserClassification>): void
```

订阅年龄群组检测功能。订阅成功后，可以获取用户年龄群组的分类结果，应用可根据此结果做相应的内容推荐。

> **说明：**
> 
> 该接口仅在部分Phone中支持使用，当Phone设备不支持时返回801错误码。

**起始版本：** 20

**废弃版本：** 24

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'userAgeGroupDetected' | 是 | 事件类型。type为“userAgeGroupDetected”，表示年龄群组检测功能。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[UserClassification](arkts-multimodalawareness-userstatus-userclassification-i.md)&gt; | 是 | 回调函数，返回检测结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function can not work correctly due to limited device capabilities. |
| [33900001](../errorcode-userStatus.md#33900001-服务异常) | Service exception. Possible causes:  1. System error, such as a null pointer and container-related exception.  2. Node-API invocation exception, such as invalid Node-API status. |
| [33900002](../errorcode-userStatus.md#33900002-订阅失败) | Subscription failed. Possible causes:  1. Callback registration failed.  2. Failed to bind the native object to the JS wrapper.  3. Node-API invocation exception, such as invalid Node-API status.  4. IPC request exception. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    userStatus.on('userAgeGroupDetected', (data: userStatus.UserClassification) => {
        console.info('callback succeeded, ageGroup:' + data.ageGroup + ", confidence:" + data.confidence);
    });
    console.info("on succeeded");
} catch (err) {
    let error = err as BusinessError;
    console.error("Failed on and err code is " + error.code);
}
```
