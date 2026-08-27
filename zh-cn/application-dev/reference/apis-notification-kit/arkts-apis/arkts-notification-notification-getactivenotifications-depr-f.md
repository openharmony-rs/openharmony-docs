# getActiveNotifications

## 导入模块

```TypeScript
```

## getActiveNotifications

```TypeScript
function getActiveNotifications(callback: AsyncCallback<Array<NotificationRequest>>): void
```

获取当前应用未删除的通知列表（Callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getActiveNotifications](arkts-notification-notificationmanager-getactivenotifications-f.md)

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[NotificationRequest](arkts-notification-notificationrequest-notificationrequest-i.md)&gt;&gt; | 是 | 获取当前应用通知列表回调函数。 |

**示例**

```TypeScript
import Base from '@ohos.base';
import NotificationManager from '@ohos.notificationManager';

let getActiveNotificationsCallback = (err: Base.BusinessError, data: NotificationManager.NotificationRequest[]) => {
  if (err) {
    console.error("getActiveNotifications failed " + JSON.stringify(err));
  } else {
    console.info("getActiveNotifications success");
  }
}

Notification.getActiveNotifications(getActiveNotificationsCallback);
```


## getActiveNotifications

```TypeScript
function getActiveNotifications(): Promise<Array<NotificationRequest>>
```

获取当前应用未删除的通知列表（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getActiveNotifications](arkts-notification-notificationmanager-getactivenotifications-f.md)

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[NotificationRequest](arkts-notification-notificationrequest-notificationrequest-i.md)&gt;&gt; | 以Promise形式返回获取当前应用通知列表。 |

**示例**

```TypeScript
import Base from '@ohos.base';
import NotificationManager from '@ohos.notificationManager';

let getActiveNotificationsCallback = (err: Base.BusinessError, data: NotificationManager.NotificationRequest[]) => {
  if (err) {
    console.error("getActiveNotifications failed " + JSON.stringify(err));
  } else {
    console.info("getActiveNotifications success");
  }
}

Notification.getActiveNotifications(getActiveNotificationsCallback);
```

```TypeScript
import Base from '@ohos.base';
import NotificationManager from '@ohos.notificationManager';

Notification.getActiveNotifications().then((data: NotificationManager.NotificationRequest[]) => {
  console.info("getActiveNotifications success, data: " + JSON.stringify(data));
}).catch((err: Base.BusinessError) => {
  console.error(`getActiveNotifications failed, code is ${err}`);
});
```
