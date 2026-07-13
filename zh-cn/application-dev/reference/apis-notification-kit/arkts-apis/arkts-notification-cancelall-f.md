# cancelAll

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## cancelAll

```TypeScript
function cancelAll(callback: AsyncCallback<void>): void
```

取消当前应用所有已发布的通知。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当取消当前应用所有已发布的通知成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// cancelAll回调
let cancelAllCallback = (err: BusinessError): void => {
  if (err) {
    console.error(`Failed to cancel all notification. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in canceling all notification.`);
  }
}
notificationManager.cancelAll(cancelAllCallback);

```


## cancelAll

```TypeScript
function cancelAll(): Promise<void>
```

取消当前应用所有已发布的通知。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.cancelAll().then(() => {
  console.info(`Succeeded in canceling all notification.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to cancel all notification. Code is ${err.code}, message is ${err.message}`);
});

```

