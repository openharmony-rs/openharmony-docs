# cancelGroup

## 导入模块

```TypeScript
import { notificationManager } from '@ohos.notificationManager';
```

## cancelGroup

```TypeScript
function cancelGroup(groupName: string, callback: AsyncCallback<void>): void
```

取消当前应用指定组下的通知。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| groupName | string | 是 | 通知组名称，此名称需要在发布通知时通过<br/>[NotificationRequest](arkts-notification-notificationrequest-i.md#NotificationRequest)对象指定。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当取消当前应用指定组下的通知成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../../errorcode-universal.md#1600001-Internal) | Internal error. |
| [1600002](../../errorcode-universal.md#1600002-Marshalling) | Marshalling or unmarshalling error. |
| [1600003](../../errorcode-universal.md#1600003-Failed) | Failed to connect to the service. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let cancelGroupCallback = (err: BusinessError): void => {
  if (err) {
    console.error(`Failed to cancel group. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in canceling group.`);
  }
}
let groupName: string = "GroupName";
notificationManager.cancelGroup(groupName, cancelGroupCallback);

```


## cancelGroup

```TypeScript
function cancelGroup(groupName: string): Promise<void>
```

取消当前应用指定组下的通知。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| groupName | string | 是 | 通知组名称，此名称需要在发布通知时通过<br/>[NotificationRequest](arkts-notification-notificationrequest-i.md#NotificationRequest)对象指定。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../../errorcode-universal.md#1600001-Internal) | Internal error. |
| [1600002](../../errorcode-universal.md#1600002-Marshalling) | Marshalling or unmarshalling error. |
| [1600003](../../errorcode-universal.md#1600003-Failed) | Failed to connect to the service. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let groupName: string = "GroupName";
notificationManager.cancelGroup(groupName).then(() => {
  console.info(`Succeeded in canceling group.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to cancel group. Code is ${err.code}, message is ${err.message}`);
});

```

