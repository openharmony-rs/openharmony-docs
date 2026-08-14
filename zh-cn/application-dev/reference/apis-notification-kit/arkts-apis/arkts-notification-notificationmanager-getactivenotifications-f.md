# getActiveNotifications

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## getActiveNotifications

```TypeScript
function getActiveNotifications(callback: AsyncCallback<Array<NotificationRequest>>): void
```

获取当前应用未删除的通知列表。使用callback异步回调。 用于查询当前应用在通知中心中所有存量通知的详细信息列表，包括每条通知的ID、标签、内容、创建时间等。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-notificationManager-function getActiveNotifications(callback: AsyncCallback<Array<NotificationRequest>>): void--><!--Device-notificationManager-function getActiveNotifications(callback: AsyncCallback<Array<NotificationRequest>>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参见：**

setBadgeNumber 设置角标个数。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;NotificationRequest&gt;&gt; | 是 | 回调函数。当获取未删除的通知列表成功，err为undefined，data为获取到的通知列表，否则为错 误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let getActiveNotificationsCallback = (err: BusinessError, data: Array<notificationManager.NotificationRequest>): void => {
  if (err) {
    console.error(`Failed to get active notifications. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in getting active notifications, data is ${JSON.stringify(data)}`);
  }
}
notificationManager.getActiveNotifications(getActiveNotificationsCallback);
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let getActiveNotificationsCallback = (err: BusinessError | null, data: Array<notificationManager.NotificationRequest> | undefined | null): void => {
  if (err) {
    console.error(`Failed to get active notifications. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in getting active notifications, data is ${JSON.stringify(data)}`);
  }
}
notificationManager.getActiveNotifications(getActiveNotificationsCallback);
```


## getActiveNotifications

```TypeScript
function getActiveNotifications(): Promise<Array<NotificationRequest>>
```

获取当前应用未删除的通知列表。使用Promise异步回调。 用于查询当前应用在通知中心中所有存量通知的详细信息列表，包括每条通知的ID、标签、内容、创建时间等。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-notificationManager-function getActiveNotifications(): Promise<Array<NotificationRequest>>--><!--Device-notificationManager-function getActiveNotifications(): Promise<Array<NotificationRequest>>-End-->

**系统能力：** SystemCapability.Notification.Notification

**参见：**

setBadgeNumber 设置角标个数。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;NotificationRequest&gt;&gt; | Promise对象，返回当前应用的通知列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.getActiveNotifications().then((data: Array<notificationManager.NotificationRequest>) => {
  console.info(`Succeeded in getting active notifications, data is ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get active notifications. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.getActiveNotifications().then((data: Array<notificationManager.NotificationRequest>) => {
  console.info(`Succeeded in getting active notifications, data is ${JSON.stringify(data)}`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get active notifications. Code is ${error.code}, message is ${error.message}`);
});
```

