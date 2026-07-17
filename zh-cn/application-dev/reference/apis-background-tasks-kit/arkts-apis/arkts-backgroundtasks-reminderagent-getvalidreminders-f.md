# getValidReminders

## 导入模块

```TypeScript
import { reminderAgent } from '@kit.BackgroundTasksKit';
```

## getValidReminders

```TypeScript
function getValidReminders(callback: AsyncCallback<Array<ReminderRequest>>): void
```

获取当前应用已设置的所有有效（未过期）的提醒，使用回调的方式实现异步调用。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getValidReminders](arkts-backgroundtasks-reminderagentmanager-getvalidreminders-f.md#getvalidreminders-1)

<!--Device-reminderAgent-function getValidReminders(callback: AsyncCallback<Array<ReminderRequest>>): void--><!--Device-reminderAgent-function getValidReminders(callback: AsyncCallback<Array<ReminderRequest>>): void-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<ReminderRequest>> | 是 | 异步回调，返回当前应用已设置的所有有效（未过期）的提醒。 |

**示例：**

```TypeScript
import { BusinessError } from '@ohos.base';
import reminderAgent from '@ohos.reminderAgent';

reminderAgent.getValidReminders((err: BusinessError, reminders: Array<reminderAgent.ReminderRequest>) => {
  console.info("callback, getValidReminders length = " + reminders.length);
  for (let i = 0; i < reminders.length; i++) {
    console.info("getValidReminders = " + reminders[i]);
    console.info("getValidReminders, reminderType = " + reminders[i].reminderType);
    const actionButton = reminders[i].actionButton || [];
    for (let j = 0; j < actionButton.length; j++) {
      console.info("getValidReminders, actionButton.title = " + actionButton[j]?.title);
      console.info("getValidReminders, actionButton.type = " + actionButton[j]?.type);
    }
    console.info("getValidReminders, wantAgent.pkgName = " + reminders[i].wantAgent?.pkgName);
    console.info("getValidReminders, wantAgent.abilityName = " + reminders[i].wantAgent?.abilityName);
    console.info("getValidReminders, ringDuration = " + reminders[i].ringDuration);
    console.info("getValidReminders, snoozeTimes = " + reminders[i].snoozeTimes);
    console.info("getValidReminders, timeInterval = " + reminders[i].timeInterval);
    console.info("getValidReminders, title = " + reminders[i].title);
    console.info("getValidReminders, content = " + reminders[i].content);
    console.info("getValidReminders, expiredContent = " + reminders[i].expiredContent);
    console.info("getValidReminders, snoozeContent = " + reminders[i].snoozeContent);
    console.info("getValidReminders, notificationId = " + reminders[i].notificationId);
    console.info("getValidReminders, slotType = " + reminders[i].slotType);
  }
})

```


## getValidReminders

```TypeScript
function getValidReminders(): Promise<Array<ReminderRequest>>
```

获取当前应用已设置的所有有效（未过期）的提醒，使用Promise方式实现异步调用。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getValidReminders](arkts-backgroundtasks-reminderagentmanager-getvalidreminders-f.md#getvalidreminders-1)

<!--Device-reminderAgent-function getValidReminders(): Promise<Array<ReminderRequest>>--><!--Device-reminderAgent-function getValidReminders(): Promise<Array<ReminderRequest>>-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<ReminderRequest>> | 返回当前应用已设置的所有有效（未过期）的提醒。 |

**示例：**

```TypeScript
import reminderAgent from '@ohos.reminderAgent';

reminderAgent.getValidReminders().then((reminders: Array<reminderAgent.ReminderRequest>) => {
  console.info("promise, getValidReminders length = " + reminders.length);
  for (let i = 0; i < reminders.length; i++) {
    console.info("getValidReminders = " + reminders[i]);
    console.info("getValidReminders, reminderType = " + reminders[i].reminderType);
    const actionButton = reminders[i].actionButton || [];
    for (let j = 0; j < actionButton.length; j++) {
      console.info("getValidReminders, actionButton.title = " + actionButton[j]?.title);
      console.info("getValidReminders, actionButton.type = " + actionButton[j]?.type);
    }
    console.info("getValidReminders, wantAgent.pkgName = " + reminders[i].wantAgent?.pkgName);
    console.info("getValidReminders, wantAgent.abilityName = " + reminders[i].wantAgent?.abilityName);
    console.info("getValidReminders, ringDuration = " + reminders[i].ringDuration);
    console.info("getValidReminders, snoozeTimes = " + reminders[i].snoozeTimes);
    console.info("getValidReminders, timeInterval = " + reminders[i].timeInterval);
    console.info("getValidReminders, title = " + reminders[i].title);
    console.info("getValidReminders, content = " + reminders[i].content);
    console.info("getValidReminders, expiredContent = " + reminders[i].expiredContent);
    console.info("getValidReminders, snoozeContent = " + reminders[i].snoozeContent);
    console.info("getValidReminders, notificationId = " + reminders[i].notificationId);
    console.info("getValidReminders, slotType = " + reminders[i].slotType);
  }
})

```

