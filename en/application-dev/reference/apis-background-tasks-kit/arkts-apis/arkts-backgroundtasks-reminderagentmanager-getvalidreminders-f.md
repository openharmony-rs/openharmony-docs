# getValidReminders

## Modules to Import

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## getValidReminders

```TypeScript
function getValidReminders(callback: AsyncCallback<Array<ReminderRequest>>): void
```

Obtains all [valid (not yet expired) reminders](../../../task-management/agent-powered-reminder.md#constraints) set by the current application. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[ReminderRequest](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md)&gt;&gt; | Yes | Callback used to return the result. If the agent-powered reminder is queried, **err** is **undefined**, and **data** contains all valid (not yet expired) reminders set by the current application. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [1700004](../errorcode-reminderAgentManager.md#1700004-nonexistent-bundle-name) | The bundle name does not exist. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

reminderAgentManager.getValidReminders((err: BusinessError, reminders: Array<reminderAgentManager.ReminderRequest>) => {
  if (err.code) {
    console.error("callback err code:" + err.code + " message:" + err.message);
  } else {
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
  }
});
```


<a id="getvalidreminders-1"></a>

## getValidReminders

```TypeScript
function getValidReminders(): Promise<Array<ReminderRequest>>
```

Obtains all [valid (not yet expired) reminders](../../../task-management/agent-powered-reminder.md#constraints) set by the current application. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[ReminderRequest](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md)&gt;&gt; | Promise used to return all the valid reminders. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [1700004](../errorcode-reminderAgentManager.md#1700004-nonexistent-bundle-name) | The bundle name does not exist. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

reminderAgentManager.getValidReminders().then((reminders: Array<reminderAgentManager.ReminderRequest>) => {
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
}).catch((err: BusinessError) => {
  console.error("promise err code:" + err.code + " message:" + err.message);
});
```
