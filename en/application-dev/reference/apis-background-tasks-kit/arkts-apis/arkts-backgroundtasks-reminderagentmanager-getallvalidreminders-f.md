# getAllValidReminders

## Modules to Import

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## getAllValidReminders

```TypeScript
function getAllValidReminders(): Promise<Array<ReminderInfo>>
```

Obtains all [valid (not yet expired) reminders](../../../task-management/agent-powered-reminder.md#constraints) set by the current application. This API uses a promise to return the result. To call this API, you need to request the ohos.permission.PUBLISH_AGENT_REMINDER permission.

**Since:** 12

**System capability:** SystemCapability.Notification.ReminderAgent

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[ReminderInfo](arkts-backgroundtasks-reminderagentmanager-reminderinfo-i.md)&gt;&gt; | Promise used to return all the valid reminders. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

reminderAgentManager.getAllValidReminders().then((reminders: Array<reminderAgentManager.ReminderInfo>) => {
  console.info("promise, getAllValidReminders length = " + reminders.length);
  for (let i = 0; i < reminders.length; i++) {
    console.info("getAllValidReminders, reminderId = " + reminders[i].reminderId);
    console.info("getAllValidReminders, reminderType = " + reminders[i].reminderReq.reminderType);
    const actionButton = reminders[i].reminderReq.actionButton || [];
    for (let j = 0; j < actionButton.length; j++) {
      console.info("getAllValidReminders, actionButton.title = " + actionButton[j]?.title);
      console.info("getAllValidReminders, actionButton.type = " + actionButton[j]?.type);
    }
    console.info("getAllValidReminders, wantAgent.pkgName = " + reminders[i].reminderReq.wantAgent?.pkgName);
    console.info("getAllValidReminders, wantAgent.abilityName = " + reminders[i].reminderReq.wantAgent?.abilityName);
    console.info("getAllValidReminders, ringDuration = " + reminders[i].reminderReq.ringDuration);
    console.info("getAllValidReminders, snoozeTimes = " + reminders[i].reminderReq.snoozeTimes);
    console.info("getAllValidReminders, timeInterval = " + reminders[i].reminderReq.timeInterval);
    console.info("getAllValidReminders, title = " + reminders[i].reminderReq.title);
    console.info("getAllValidReminders, content = " + reminders[i].reminderReq.content);
    console.info("getAllValidReminders, expiredContent = " + reminders[i].reminderReq.expiredContent);
    console.info("getAllValidReminders, snoozeContent = " + reminders[i].reminderReq.snoozeContent);
    console.info("getAllValidReminders, notificationId = " + reminders[i].reminderReq.notificationId);
    console.info("getAllValidReminders, slotType = " + reminders[i].reminderReq.slotType);
  }
}).catch((err: BusinessError) => {
  console.error("promise err code:" + err.code + " message:" + err.message);
});
```
