# addSlot

<a id="addslot"></a>
## addSlot

```TypeScript
function addSlot(type: SlotType, callback: AsyncCallback<void>): void
```

创建指定类型的通知通道（callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** addSlot

<!--Device-notification-function addSlot(type: SlotType, callback: AsyncCallback<void>): void--><!--Device-notification-function addSlot(type: SlotType, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [SlotType](arkts-notification-notificationmanager-slottype-e.md) | 是 | 要创建的通知通道的类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 表示被指定的回调方法。 |


<a id="addslot-1"></a>
## addSlot

```TypeScript
function addSlot(type: SlotType): Promise<void>
```

创建指定类型的通知通道（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** addSlot

<!--Device-notification-function addSlot(type: SlotType): Promise<void>--><!--Device-notification-function addSlot(type: SlotType): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [SlotType](arkts-notification-notificationmanager-slottype-e.md) | 是 | 要创建的通知通道的类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

