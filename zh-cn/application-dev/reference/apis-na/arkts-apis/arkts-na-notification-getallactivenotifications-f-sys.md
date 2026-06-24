# getAllActiveNotifications（系统接口）

## getAllActiveNotifications

```TypeScript
function getAllActiveNotifications(callback: AsyncCallback<Array<NotificationRequest>>): void
```

获取当前未删除的所有通知（Callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getAllActiveNotifications

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;Array&lt;NotificationRequest&gt;&gt; | 是 | 获取活动通知回调函数。 |


## getAllActiveNotifications

```TypeScript
function getAllActiveNotifications(): Promise<Array<NotificationRequest>>
```

获取当前未删除的所有通知（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getAllActiveNotifications

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;NotificationRequest&gt;&gt; | 以Promise形式返回获取活动通知。 |

