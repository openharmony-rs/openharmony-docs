# off

## 导入模块

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## off('userAgeGroupDetected')

```TypeScript
function off(type: 'userAgeGroupDetected', callback?: Callback<UserClassification>): void
```

取消订阅年龄群组检测功能。

> **说明：**
> 
> 该接口仅在部分Phone中支持使用，当Phone设备不支持时返回33900003错误码。

**起始版本：** 20

**废弃版本：** 24

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'userAgeGroupDetected' | 是 | 事件类型。type为“userAgeGroupDetected”，表示年龄群组检测功能。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[UserClassification](arkts-multimodalawareness-userstatus-userclassification-i.md)&gt; | 否 | 回调函数，返回检测结果。需要取消监听的回调函数，需与订阅时传入的回调函数一致。 若不填，则取消当前监听该事件的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function can not work correctly due to limited device capabilities. |
| [33900001](../errorcode-userStatus.md#33900001-服务异常) | Service exception. Possible causes:  1. System error, such as a null pointer and container-related exception.  2. Node-API invocation exception, such as invalid Node-API status. |
| [33900003](../errorcode-userStatus.md#33900003-取消订阅失败) | Unsubscription failed. Possible causes:  1. Callback failure.  2. Node-API invocation exception, such as invalid Node-API status.  3. IPC request exception. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    userStatus.off('userAgeGroupDetected');
    console.info("off succeeded");
} catch (err) {
    let error = err as BusinessError;
    console.error("Failed off and err code is " + error.code);
}
```
