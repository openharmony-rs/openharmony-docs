# addNotificationSlot

## 导入模块

```TypeScript
import { reminderAgent } from '@kit.BackgroundTasksKit';
```

<a id="addnotificationslot"></a>
## addNotificationSlot

```TypeScript
function addNotificationSlot(slot: NotificationSlot, callback: AsyncCallback<void>): void
```

添加一个NotificationSlot，使用回调的方式实现异步调用。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [addNotificationSlot](arkts-backgroundtasks-reminderagentmanager-addnotificationslot-f.md#addnotificationslot-1)

<!--Device-reminderAgent-function addNotificationSlot(slot: NotificationSlot, callback: AsyncCallback<void>): void--><!--Device-reminderAgent-function addNotificationSlot(slot: NotificationSlot, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slot | [NotificationSlot](../../apis-notification-kit/arkts-apis/arkts-notification-notificationslot-notificationslot-i.md) | 是 | notification.slot实例，仅支持设置其type属性。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异步回调。 |

**示例：**

```TypeScript
import { BusinessError } from '@ohos.base';
import notification from '@ohos.notification';
import reminderAgent from '@ohos.reminderAgent';
import { NotificationSlot } from './notification/notificationSlot';

let mySlot:NotificationSlot = {
  type: notification.SlotType.SOCIAL_COMMUNICATION
}
reminderAgent.addNotificationSlot(mySlot, (err: BusinessError, data: void) => {
  console.info("addNotificationSlot callback");
});

```


<a id="addnotificationslot-1"></a>
## addNotificationSlot

```TypeScript
function addNotificationSlot(slot: NotificationSlot): Promise<void>
```

添加一个NotificationSlot，使用Promise方式实现异步调用。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [addNotificationSlot](arkts-backgroundtasks-reminderagentmanager-addnotificationslot-f.md#addnotificationslot-1)

<!--Device-reminderAgent-function addNotificationSlot(slot: NotificationSlot): Promise<void>--><!--Device-reminderAgent-function addNotificationSlot(slot: NotificationSlot): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slot | [NotificationSlot](../../apis-notification-kit/arkts-apis/arkts-notification-notificationslot-notificationslot-i.md) | 是 | notification.slot实例，仅支持设置其type属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise类型异步回调。 |

**示例：**

```TypeScript
import notification from '@ohos.notification';
import reminderAgent from '@ohos.reminderAgent';
import { NotificationSlot } from './notification/notificationSlot';

let mySlot:NotificationSlot = {
  type: notification.SlotType.SOCIAL_COMMUNICATION
}
reminderAgent.addNotificationSlot(mySlot).then(() => {
  console.info("addNotificationSlot promise");
});

```

