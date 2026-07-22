# removeNotificationSlot

## 导入模块

```TypeScript
import { reminderAgent } from '@kit.BackgroundTasksKit';
```

## removeNotificationSlot

```TypeScript
function removeNotificationSlot(slotType: notification.SlotType, callback: AsyncCallback<void>): void
```

删除目标NotificationSlot，使用callback方式实现异步调用。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [removeNotificationSlot](arkts-backgroundtasks-reminderagentmanager-removenotificationslot-f.md#removenotificationslot)

<!--Device-reminderAgent-function removeNotificationSlot(slotType: notification.SlotType, callback: AsyncCallback<void>): void--><!--Device-reminderAgent-function removeNotificationSlot(slotType: notification.SlotType, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotType | notification.SlotType | 是 | 目标notification.slot的类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异步回调。 |

**示例：**

```TypeScript
import { BusinessError } from '@ohos.base';
import notification from '@ohos.notification';
import reminderAgent from '@ohos.reminderAgent';

reminderAgent.removeNotificationSlot(notification.SlotType.CONTENT_INFORMATION, (err: BusinessError, data: void) => {
  console.info("removeNotificationSlot callback");
});

```


## removeNotificationSlot

```TypeScript
function removeNotificationSlot(slotType: notification.SlotType): Promise<void>
```

删除目标NotificationSlot，使用Promise方式实现异步调用。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [removeNotificationSlot](arkts-backgroundtasks-reminderagentmanager-removenotificationslot-f.md#removenotificationslot)

<!--Device-reminderAgent-function removeNotificationSlot(slotType: notification.SlotType): Promise<void>--><!--Device-reminderAgent-function removeNotificationSlot(slotType: notification.SlotType): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotType | notification.SlotType | 是 | 目标notification.slot的类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise类型异步回调。 |

**示例：**

```TypeScript
import notification from '@ohos.notification';
import reminderAgent from '@ohos.reminderAgent';

reminderAgent.removeNotificationSlot(notification.SlotType.CONTENT_INFORMATION).then(() => {
  console.info("removeNotificationSlot promise");
});

```

