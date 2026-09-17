# getExcludeDates

## Modules to Import

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## getExcludeDates

```TypeScript
function getExcludeDates(reminderId: number): Promise<Array<Date>>
```

Obtains all non-reminder dates for a recurring calendar reminder with a specific ID. This API uses a promise to return the result.

**Since:** 12

**System capability:** SystemCapability.Notification.ReminderAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| reminderId | number | Yes | ID of the agent-powered reminder to be queried. The reminder ID is returned when the [publishReminder](arkts-backgroundtasks-reminderagentmanager-publishreminder-f.md) API is called. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;Date&gt;&gt; | Promise used to return all the non-reminder dates. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [1700003](../errorcode-reminderAgentManager.md#1700003-nonexistent-reminder) | The reminder does not exist. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

let reminderId: number = 1;
reminderAgentManager.getExcludeDates(reminderId).then((dates) => {
  console.info("getExcludeDates promise length: " + dates.length);
  for (let i = 0; i < dates.length; i++) {
    console.info("getExcludeDates promise date is: " + dates[i].toString());
  }
}).catch((err: BusinessError) => {
  console.error("promise err code:" + err.code + " message:" + err.message);
});
```
