# getSlots

## getSlots

```TypeScript
function getSlots(callback: AsyncCallback<Array<NotificationSlot>>): void
```

获取此应用程序的所有通知通道（callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getSlots

<!--Device-notification-function getSlots(callback: AsyncCallback<Array<NotificationSlot>>): void--><!--Device-notification-function getSlots(callback: AsyncCallback<Array<NotificationSlot>>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<NotificationSlot>> | 是 | 以callback形式返回获取此应用程序的所有通知通道的结果。 |


## getSlots

```TypeScript
function getSlots(): Promise<Array<NotificationSlot>>
```

获取此应用程序的所有通知通道（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getSlots

<!--Device-notification-function getSlots(): Promise<Array<NotificationSlot>>--><!--Device-notification-function getSlots(): Promise<Array<NotificationSlot>>-End-->

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<NotificationSlot>> | 以Promise形式返回获取此应用程序的所有通知通道的结果。 |

