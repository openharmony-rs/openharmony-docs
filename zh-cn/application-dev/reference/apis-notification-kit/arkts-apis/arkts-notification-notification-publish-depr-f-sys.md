# publish（系统接口）

## publish

```TypeScript
function publish(request: NotificationRequest, userId: number, callback: AsyncCallback<void>): void
```

发布通知给指定的用户。使用callback异步回调。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** ohos.notificationManager/notificationManager#publish

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function publish(request: NotificationRequest, userId: number, callback: AsyncCallback<void>): void--><!--Device-notification-function publish(request: NotificationRequest, userId: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 用于设置要发布通知的内容和相关配置信息。 |
| userId | number | 是 | 用户ID。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 被指定的回调方法。 |


## publish

```TypeScript
function publish(request: NotificationRequest, userId: number): Promise<void>
```

发布通知给指定的用户。使用Promise异步回调。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** ohos.notificationManager/notificationManager#publish

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function publish(request: NotificationRequest, userId: number): Promise<void>--><!--Device-notification-function publish(request: NotificationRequest, userId: number): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 用于设置要发布通知的内容和相关配置信息。 |
| userId | number | 是 | 用户ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

