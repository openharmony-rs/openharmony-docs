# obtainAllWorks

## Modules to Import

```TypeScript
import { workScheduler } from '@kit.BackgroundTasksKit';
```

## obtainAllWorks

```TypeScript
function obtainAllWorks(callback: AsyncCallback<void>): Array<WorkInfo>
```

Obtains all the deferred tasks. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [obtainAllWorks](#obtainallworks-1)(callback: AsyncCallback&lt;Array&lt;WorkInfo&gt;&gt;)

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If all the deferred tasks are obtained, **err** is **undefined**. Otherwise, **err** is an error object. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[WorkInfo](arkts-backgroundtasks-workscheduler-workinfo-i.md)&gt; | List of deferred tasks. If deferred tasks have been added to the execution queue, the list of all deferred tasks in the current application is returned. Otherwise, an empty list is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [9700001](../errorcode-workScheduler.md#9700001-memory-operation-failure) | Memory operation failed. |
| [9700002](../errorcode-workScheduler.md#9700002-parcel-readwrite-operation-failure) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| [9700003](../errorcode-workScheduler.md#9700003-system-service-failure) | System service operation failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
  import { workScheduler } from '@kit.BackgroundTasksKit';

  workScheduler.obtainAllWorks((error: BusinessError, res: Array<workScheduler.WorkInfo>) =>{
    if (error) {
      console.error(`workschedulerLog obtainAllWorks failed. code is ${error.code} message is ${error.message}`);
    } else {
      console.info(`workschedulerLog obtainAllWorks success, data is: ${JSON.stringify(res)}`);
    }
  });
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
  import { workScheduler } from '@kit.BackgroundTasksKit';

  workScheduler.obtainAllWorks().then((res: Array<workScheduler.WorkInfo>) => {
    console.info(`workschedulerLog obtainAllWorks success, data is: ${JSON.stringify(res)}`);
  }).catch((error: BusinessError) => {
    console.error(`workschedulerLog obtainAllWorks failed. code is ${error.code} message is ${error.message}`);
  })
```


<a id="obtainallworks-1"></a>

## obtainAllWorks

```TypeScript
function obtainAllWorks(callback: AsyncCallback<Array<WorkInfo>>): void
```

Obtains all the deferred tasks. This API uses an asynchronous callback to return the result.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[WorkInfo](arkts-backgroundtasks-workscheduler-workinfo-i.md)&gt;&gt; | Yes | Callback used to return the list of all deferred tasks in the current application. If the list fails to be obtained, an exception is thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [9700001](../errorcode-workScheduler.md#9700001-memory-operation-failure) | Memory operation failed. |
| [9700002](../errorcode-workScheduler.md#9700002-parcel-readwrite-operation-failure) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| [9700003](../errorcode-workScheduler.md#9700003-system-service-failure) | System service operation failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
  import { workScheduler } from '@kit.BackgroundTasksKit';

  workScheduler.obtainAllWorks((error: BusinessError, res: Array<workScheduler.WorkInfo>) =>{
    if (error) {
      console.error(`workschedulerLog obtainAllWorks failed. code is ${error.code} message is ${error.message}`);
    } else {
      console.info(`workschedulerLog obtainAllWorks success, data is: ${JSON.stringify(res)}`);
    }
  });
```


<a id="obtainallworks-2"></a>

## obtainAllWorks

```TypeScript
function obtainAllWorks(): Promise<Array<WorkInfo>>
```

Obtains all the deferred tasks. This API uses a promise to return the result.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[WorkInfo](arkts-backgroundtasks-workscheduler-workinfo-i.md)&gt;&gt; | Promise used to return all the deferred tasks. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [9700001](../errorcode-workScheduler.md#9700001-memory-operation-failure) | Memory operation failed. |
| [9700002](../errorcode-workScheduler.md#9700002-parcel-readwrite-operation-failure) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| [9700003](../errorcode-workScheduler.md#9700003-system-service-failure) | System service operation failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
  import { workScheduler } from '@kit.BackgroundTasksKit';

  workScheduler.obtainAllWorks().then((res: Array<workScheduler.WorkInfo>) => {
    console.info(`workschedulerLog obtainAllWorks success, data is: ${JSON.stringify(res)}`);
  }).catch((error: BusinessError) => {
    console.error(`workschedulerLog obtainAllWorks failed. code is ${error.code} message is ${error.message}`);
  })
```
