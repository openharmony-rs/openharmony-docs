# distributeOperation（系统接口）

## 导入模块

```TypeScript
import { notificationSubscribe } from '@kit.NotificationKit';
```

## distributeOperation

```TypeScript
function distributeOperation(hashcode: string, operationInfo?: OperationInfo): Promise<void>
```

触发指定通知的[跨设备协同](../../../notification/notification-glossary.md#cross-device-collaboration跨设备协同)操作（例如通知跨设备点击跳转、通知跨设备快捷回复等）。使用Promise异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationSubscribe-function distributeOperation(hashcode: string, operationInfo?: OperationInfo): Promise<void>--><!--Device-notificationSubscribe-function distributeOperation(hashcode: string, operationInfo?: OperationInfo): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hashcode | string | 是 | 通知唯一ID。可以通过[onConsume](arkts-notification-notificationsubscriber-i-sys.md#onconsume)回调的入参[SubscribeCallbackData](arkts-notification-notificationsubscriber-subscribecallbackdata-i-sys.md)获取其内部[NotificationRequest](arkts-notification-notificationrequest-i.md)对象中的hashCode。 |
| operationInfo | [OperationInfo](arkts-notification-notificationsubscribe-operationinfo-i-sys.md) | 否 | 跨设备协同操作信息，不传递该参数时，使用系统默认协同操作配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.         2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600010](../errorcode-notification.md#1600010-分布式操作失败) | Distributed operation failed. |
| [1600021](../errorcode-notification.md#1600021-跨设备通信超时) | Distributed operation timed out. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let hashCode: string = 'hashCode';
let operationInfo: notificationSubscribe.OperationInfo = {
  actionName: 'actionName',
  userInput: 'userInput',
  operationType: 1,
  buttonIndex: 1,
};
notificationSubscribe.distributeOperation(hashCode, operationInfo).then(() => {
  console.info('distributeOperation success');
}).catch((err: BusinessError) => {
  console.error(`distributeOperation fail, code is ${err.code}, message is ${err.message}`);
});
```

<!--DelEnd-->
