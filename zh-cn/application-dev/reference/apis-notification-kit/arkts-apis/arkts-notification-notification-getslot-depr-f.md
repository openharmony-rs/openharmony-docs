# getSlot

## getSlot

```TypeScript
function getSlot(slotType: SlotType, callback: AsyncCallback<NotificationSlot>): void
```

获取一个指定类型的通知通道（callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getSlot

<!--Device-notification-function getSlot(slotType: SlotType, callback: AsyncCallback<NotificationSlot>): void--><!--Device-notification-function getSlot(slotType: SlotType, callback: AsyncCallback<NotificationSlot>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotType | [SlotType](arkts-notification-notificationmanager-slottype-e.md) | 是 | 通知渠道类型，目前分为社交通信、服务提醒、内容咨询和其他类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<NotificationSlot> | 是 | 表示被指定的回调方法。 |


## getSlot

```TypeScript
function getSlot(slotType: SlotType): Promise<NotificationSlot>
```

获取一个指定类型的通知通道（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getSlot

<!--Device-notification-function getSlot(slotType: SlotType): Promise<NotificationSlot>--><!--Device-notification-function getSlot(slotType: SlotType): Promise<NotificationSlot>-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotType | [SlotType](arkts-notification-notificationmanager-slottype-e.md) | 是 | 通知渠道类型，目前分为社交通信、服务提醒、内容咨询和其他类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<NotificationSlot> | 以Promise形式返回获取一个通知通道。 |

