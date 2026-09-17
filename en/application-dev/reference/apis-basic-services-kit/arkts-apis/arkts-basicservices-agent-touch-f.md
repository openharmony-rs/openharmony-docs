# touch

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## touch

```TypeScript
function touch(id: string, token: string, callback: AsyncCallback<TaskInfo>): void
```

Queries the task details based on the task ID and token. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | Task ID. |
| token | string | Yes | Token for task query. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[TaskInfo](arkts-basicservices-agent-taskinfo-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the **TaskInfo** object obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |
| [13400003](../errorcode-request.md#13400003-service-error) | Task service ability error. |
| [21900006](../errorcode-request.md#21900006-task-not-found) | Task removed or not found. |


## touch

```TypeScript
function touch(id: string, token: string): Promise<TaskInfo>
```

Queries the task details based on the task ID and token. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | Task ID. |
| token | string | Yes | Token for task query. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[TaskInfo](arkts-basicservices-agent-taskinfo-i.md)&gt; | Promise used to return the **TaskInfo** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |
| [13400003](../errorcode-request.md#13400003-service-error) | Task service ability error. |
| [21900006](../errorcode-request.md#21900006-task-not-found) | Task removed or not found. |
