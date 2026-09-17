# isLastWorkTimeOut

## Modules to Import

```TypeScript
import { workScheduler } from '@kit.BackgroundTasksKit';
```

## isLastWorkTimeOut

```TypeScript
function isLastWorkTimeOut(workId: number, callback: AsyncCallback<void>): boolean
```

Checks whether the last execution of a task timed out. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [isLastWorkTimeOut](arkts-backgroundtasks-workscheduler-islastworktimeout-f.md)(workId: number, callback: AsyncCallback&lt;boolean&gt;)

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| workId | number | Yes | ID of the deferred task. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the last execution of a deferred task timed out. If **workId** is valid, it returns whether the last execution of the task obtained from WorkSchedulerService timed out; otherwise, an exception is thrown. **true** indicates that the last execution of the deferred task corresponding to the **workId** timed out, while **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Parameter verification failed. |
| [9700001](../errorcode-workScheduler.md#9700001-memory-operation-failure) | Memory operation failed. |
| [9700002](../errorcode-workScheduler.md#9700002-parcel-operation-failure) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| [9700003](../errorcode-workScheduler.md#9700003-system-service-failure) | System service operation failed. |
| [9700004](../errorcode-workScheduler.md#9700004-workinfo-verification-failure) | Check on workInfo failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
  import { workScheduler } from '@kit.BackgroundTasksKit';

  workScheduler.isLastWorkTimeOut(500, (error: BusinessError, res: boolean) =>{
    if (error) {
      console.error(`workschedulerLog isLastWorkTimeOut failed. code is ${error.code} message is ${error.message}`);
    } else {
      console.info(`workschedulerLog isLastWorkTimeOut success, data is: ${res}`);
    }
  });
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
  import { workScheduler } from '@kit.BackgroundTasksKit';

  workScheduler.isLastWorkTimeOut(500)
    .then((res: boolean) => {
      console.info(`workschedulerLog isLastWorkTimeOut success, data is: ${res}`);
    })
    .catch((error: BusinessError) =>  {
      console.error(`workschedulerLog isLastWorkTimeOut failed. code is ${error.code} message is ${error.message}`);
    });
```


## isLastWorkTimeOut

```TypeScript
function isLastWorkTimeOut(workId: number, callback: AsyncCallback<boolean>): void
```

Checks whether the last execution of a task timed out. This API uses an asynchronous callback to return the result.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| workId | number | Yes | ID of the deferred task. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Parameter verification failed. |
| [9700001](../errorcode-workScheduler.md#9700001-memory-operation-failure) | Memory operation failed. |
| [9700002](../errorcode-workScheduler.md#9700002-parcel-operation-failure) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| [9700003](../errorcode-workScheduler.md#9700003-system-service-failure) | System service operation failed. |
| [9700004](../errorcode-workScheduler.md#9700004-workinfo-verification-failure) | Check on workInfo failed. |

**Examples**

See [isLastWorkTimeOut](#islastworktimeout)


## isLastWorkTimeOut

```TypeScript
function isLastWorkTimeOut(workId: number): Promise<boolean>
```

Checks whether the last execution of a task timed out. This API uses a promise to return the result.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| workId | number | Yes | ID of the deferred task. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means that the last execution of the specified task times out, and **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Parameter verification failed. |
| [9700001](../errorcode-workScheduler.md#9700001-memory-operation-failure) | Memory operation failed. |
| [9700002](../errorcode-workScheduler.md#9700002-parcel-operation-failure) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| [9700003](../errorcode-workScheduler.md#9700003-system-service-failure) | System service operation failed. |
| [9700004](../errorcode-workScheduler.md#9700004-workinfo-verification-failure) | Check on workInfo failed. |

**Examples**

See [isLastWorkTimeOut](#islastworktimeout)
