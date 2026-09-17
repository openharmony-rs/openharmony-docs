# cancelBackgroundRunning

## Modules to Import

```TypeScript
import { particleAbility } from '@kit.AbilityKit';
```

## cancelBackgroundRunning

```TypeScript
function cancelBackgroundRunning(callback: AsyncCallback<void>): void
```

Requests to cancel a continuous task from the system. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [stopBackgroundRunning](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md)

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the continuous task is canceled, **err** is **undefined**. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { particleAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback(error: BusinessError, data: void) {
  if (error && error.code !== 0) {
    console.error(`Operation failed error: ${JSON.stringify(error)}`);
  } else {
    console.info(`Operation succeeded, data: ${data}`);
  }
}

particleAbility.cancelBackgroundRunning(callback);
```

```TypeScript
import { particleAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

particleAbility.cancelBackgroundRunning().then(() => {
  console.info('Operation succeeded');
}).catch((err: BusinessError) => {
  console.error(`Operation failed cause: ${JSON.stringify(err)}`);
});
```


## cancelBackgroundRunning

```TypeScript
function cancelBackgroundRunning(): Promise<void>
```

Requests to cancel a continuous task from the system. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [stopBackgroundRunning](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md)

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. Promise that returns no value. |

**Examples**

See [cancelBackgroundRunning](#cancelbackgroundrunning)
