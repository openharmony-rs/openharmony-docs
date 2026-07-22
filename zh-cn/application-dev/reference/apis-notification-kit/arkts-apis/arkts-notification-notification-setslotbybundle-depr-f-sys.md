# setSlotByBundle（系统接口）

## setSlotByBundle

```TypeScript
function setSlotByBundle(bundle: BundleOption, slot: NotificationSlot, callback: AsyncCallback<void>): void
```

设定指定应用的通知通道（Callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** setSlotByBundle

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function setSlotByBundle(bundle: BundleOption, slot: NotificationSlot, callback: AsyncCallback<void>): void--><!--Device-notification-function setSlotByBundle(bundle: BundleOption, slot: NotificationSlot, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | [BundleOption](arkts-notification-notificationcommondef-bundleoption-i.md) | 是 | 指定应用的包信息。 |
| slot | [NotificationSlot](arkts-notification-notificationslot-notificationslot-i-sys.md) | 是 | 通知通道。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 设定通知通道回调函数。 |


## setSlotByBundle

```TypeScript
function setSlotByBundle(bundle: BundleOption, slot: NotificationSlot): Promise<void>
```

设定指定应用的通知通道（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** setSlotByBundle

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function setSlotByBundle(bundle: BundleOption, slot: NotificationSlot): Promise<void>--><!--Device-notification-function setSlotByBundle(bundle: BundleOption, slot: NotificationSlot): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | [BundleOption](arkts-notification-notificationcommondef-bundleoption-i.md) | 是 | 指定应用的包信息。 |
| slot | [NotificationSlot](arkts-notification-notificationslot-notificationslot-i-sys.md) | 是 | 通知通道。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

