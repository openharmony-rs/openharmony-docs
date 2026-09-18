# query (System API)

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## query

```TypeScript
function query(id: string, callback: AsyncCallback<TaskInfo>): void
```

Queries specified task details. Creates a group based on GroupConfig

**Since:** 10

**Required permissions:** ohos.permission.DOWNLOAD_SESSION_MANAGER or ohos.permission.UPLOAD_SESSION_MANAGER

**System capability:** SystemCapability.Request.FileTransferAgent

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | the task id. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[TaskInfo](arkts-basicservices-agent-taskinfo-i.md)&gt; | Yes | callback function with a `TaskInfo` argument for informations of the current task. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | permission verification failed, application which is not a system application uses system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. |
| [13400003](../errorcode-request.md#13400003-service-error) | Task service ability error. |
| [21900006](../errorcode-request.md#21900006-task-not-found) | Task removed or not found. |


## query

```TypeScript
function query(id: string): Promise<TaskInfo>
```

Queries specified task details.

**Since:** 10

**Required permissions:** ohos.permission.DOWNLOAD_SESSION_MANAGER or ohos.permission.UPLOAD_SESSION_MANAGER

**System capability:** SystemCapability.Request.FileTransferAgent

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | the task id. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[TaskInfo](arkts-basicservices-agent-taskinfo-i.md)&gt; | the promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | permission verification failed, application which is not a system application uses system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. |
| [13400003](../errorcode-request.md#13400003-service-error) | Task service ability error. |
| [21900006](../errorcode-request.md#21900006-task-not-found) | Task removed or not found. |
