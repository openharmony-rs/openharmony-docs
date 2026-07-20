# removeSlot

<a id="removeslot"></a>
## removeSlot

```TypeScript
function removeSlot(slotType: SlotType, callback: AsyncCallback<void>): void
```

删除指定类型的通知通道（callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** removeSlot

<!--Device-notification-function removeSlot(slotType: SlotType, callback: AsyncCallback<void>): void--><!--Device-notification-function removeSlot(slotType: SlotType, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotType | [SlotType](arkts-notification-notificationmanager-slottype-e.md) | 是 | 通知渠道类型,目前分为社交通信、服务提醒、内容咨询和其他类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 表示被指定的回调方法。 |


<a id="removeslot-1"></a>
## removeSlot

```TypeScript
function removeSlot(slotType: SlotType): Promise<void>
```

删除指定类型的通知通道（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** removeSlot

<!--Device-notification-function removeSlot(slotType: SlotType): Promise<void>--><!--Device-notification-function removeSlot(slotType: SlotType): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotType | [SlotType](arkts-notification-notificationmanager-slottype-e.md) | 是 | 通知渠道类型,目前分为社交通信、服务提醒、内容咨询和其他类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

