# getActiveNotifications

## getActiveNotifications

```TypeScript
function getActiveNotifications(callback: AsyncCallback<Array<NotificationRequest>>): void
```

获取当前应用未删除的通知列表（Callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getActiveNotifications

<!--Device-notification-function getActiveNotifications(callback: AsyncCallback<Array<NotificationRequest>>): void--><!--Device-notification-function getActiveNotifications(callback: AsyncCallback<Array<NotificationRequest>>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<NotificationRequest>> | 是 | 获取当前应用通知列表回调函数。 |


## getActiveNotifications

```TypeScript
function getActiveNotifications(): Promise<Array<NotificationRequest>>
```

获取当前应用未删除的通知列表（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getActiveNotifications

<!--Device-notification-function getActiveNotifications(): Promise<Array<NotificationRequest>>--><!--Device-notification-function getActiveNotifications(): Promise<Array<NotificationRequest>>-End-->

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<NotificationRequest>> | 以Promise形式返回获取当前应用通知列表。 |

