# getSlots

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## getSlots

```TypeScript
function getSlots(callback: AsyncCallback<Array<NotificationSlot>>): void
```

获取当前应用的所有通知渠道。使用callback异步回调。

用于批量查询当前应用已创建的所有通知渠道的配置信息，包括各渠道的类型、提醒方式、级别等设置。适用于需要查看所有渠道配置的场景。

**起始版本：** 9

<!--Device-notificationManager-function getSlots(callback: AsyncCallback<Array<NotificationSlot>>): void--><!--Device-notificationManager-function getSlots(callback: AsyncCallback<Array<NotificationSlot>>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;NotificationSlot&gt;&gt; | 是 | 回调函数。当获取通知渠道成功，err为undefined，data为获取到的NotificationSlot数组，否则为错误对象。 |

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

// getSlots回调
let getSlotsCallback = (err: BusinessError, data: Array<notificationManager.NotificationSlot>): void => {
  if (err) {
    console.error(`Failed to get slots. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in getting slots, data is ${JSON.stringify(data)}`);
  }
}
notificationManager.getSlots(getSlotsCallback);

```


## getSlots

```TypeScript
function getSlots(): Promise<Array<NotificationSlot>>
```

获取当前应用的所有通知渠道。使用Promise异步回调。

用于批量查询当前应用已创建的所有通知渠道的配置信息，包括各渠道的类型、提醒方式、级别等设置。适用于需要查看所有渠道配置的场景。

**起始版本：** 9

<!--Device-notificationManager-function getSlots(): Promise<Array<NotificationSlot>>--><!--Device-notificationManager-function getSlots(): Promise<Array<NotificationSlot>>-End-->

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;NotificationSlot&gt;&gt; | Promise对象，返回通知渠道对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.getSlots().then((data: Array<notificationManager.NotificationSlot>) => {
  console.info(`Succeeded in getting slots, data is ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get slots. Code is ${err.code}, message is ${err.message}`);
});

```

