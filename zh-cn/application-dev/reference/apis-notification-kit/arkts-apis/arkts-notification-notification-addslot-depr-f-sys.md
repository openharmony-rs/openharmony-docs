# addSlot（系统接口）

## addSlot

```TypeScript
function addSlot(slot: NotificationSlot, callback: AsyncCallback<void>): void
```

创建通知渠道。使用callback异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** ohos.notificationManager/notificationManager#addSlot

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function addSlot(slot: NotificationSlot, callback: AsyncCallback<void>): void--><!--Device-notification-function addSlot(slot: NotificationSlot, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slot | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要创建的通知渠道对象。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 表示被指定通道的回调方法。 |


## addSlot

```TypeScript
function addSlot(slot: NotificationSlot): Promise<void>
```

创建通知渠道。使用Promise异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** ohos.notificationManager/notificationManager#addSlot

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function addSlot(slot: NotificationSlot): Promise<void>--><!--Device-notification-function addSlot(slot: NotificationSlot): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slot | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要创建的通知渠道对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

