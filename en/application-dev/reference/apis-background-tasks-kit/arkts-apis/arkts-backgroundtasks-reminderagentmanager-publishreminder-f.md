# publishReminder

## Modules to Import

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## publishReminder

```TypeScript
function publishReminder(reminderReq: ReminderRequest, callback: AsyncCallback<number>): void
```

Publishes a reminder. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API can be called only after the
> [notificationManager.requestEnableNotification](../../apis-notification-kit/arkts-apis/arkts-notification-notificationmanager-requestenablenotification-f.md#requestenablenotification-1)
> permission is obtained. &gt;

**Since:** 9

**Required permissions:** ohos.permission.PUBLISH_AGENT_REMINDER

**System capability:** SystemCapability.Notification.ReminderAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| reminderReq | [ReminderRequest](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md) | Yes | Request used for publishing the reminder. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. After the agent-powered reminder is published, **err** is **undefined**, and **data** is the ID of the published reminder. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [1700001](../errorcode-reminderAgentManager.md#1700001-notification-disabled) | Notification is not enabled. |
| [1700002](../errorcode-reminderAgentManager.md#1700002-too-many-reminders) | The number of reminders exceeds the limit. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

let timer: reminderAgentManager.ReminderRequestTimer = {
  reminderType: reminderAgentManager.ReminderType.REMINDER_TYPE_TIMER,
  triggerTimeInSeconds: 10
}

reminderAgentManager.publishReminder(timer, (err: BusinessError, reminderId: number) => {
  if (err.code) {
    console.error("callback err code:" + err.code + " message:" + err.message);
  } else {
    console.info("callback, reminderId = " + reminderId);
  }
});
```


<a id="publishreminder-1"></a>

## publishReminder

```TypeScript
function publishReminder(reminderReq: ReminderRequest): Promise<number>
```

Publishes a reminder. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API can be called only after the
> [notificationManager.requestEnableNotification](../../apis-notification-kit/arkts-apis/arkts-notification-notificationmanager-requestenablenotification-f.md#requestenablenotification-1)
> permission is obtained. &gt;

**Since:** 9

**Required permissions:** ohos.permission.PUBLISH_AGENT_REMINDER

**System capability:** SystemCapability.Notification.ReminderAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| reminderReq | [ReminderRequest](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md) | Yes | Request used for publishing the reminder. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the published reminder ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [1700001](../errorcode-reminderAgentManager.md#1700001-notification-disabled) | Notification is not enabled. |
| [1700002](../errorcode-reminderAgentManager.md#1700002-too-many-reminders) | The number of reminders exceeds the limit. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

let timer: reminderAgentManager.ReminderRequestTimer = {
  reminderType: reminderAgentManager.ReminderType.REMINDER_TYPE_TIMER,
  triggerTimeInSeconds: 10
}

reminderAgentManager.publishReminder(timer).then((reminderId: number) => {
  console.info("promise, reminderId = " + reminderId);
}).catch((err: BusinessError) => {
  console.error("promise err code:" + err.code + " message:" + err.message);
});
```
