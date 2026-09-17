# cancelAllReminders

## Modules to Import

```TypeScript
import { reminderAgent } from '@kit.BackgroundTasksKit';
```

## cancelAllReminders

```TypeScript
function cancelAllReminders(callback: AsyncCallback<void>): void
```

Cancels all reminders set by the current application. This API uses an asynchronous callback to return the cancellation result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** cancelAllReminders

**System capability:** SystemCapability.Notification.ReminderAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';
import reminderAgent from '@ohos.reminderAgent';

reminderAgent.cancelAllReminders((err: BusinessError, data: void) =>{
  console.info("cancelAllReminders callback")
})
```

```TypeScript
import reminderAgent from '@ohos.reminderAgent';

reminderAgent.cancelAllReminders().then(() => {
    console.info("cancelAllReminders promise")
})
```


## cancelAllReminders

```TypeScript
function cancelAllReminders(): Promise<void>
```

Cancels all reminders set by the current application. This API uses a promise to return the cancellation result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** cancelAllReminders

**System capability:** SystemCapability.Notification.ReminderAgent

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Examples**

See [cancelAllReminders](#cancelallreminders)
