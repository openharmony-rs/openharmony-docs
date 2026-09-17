# getTask

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## getTask

```TypeScript
function getTask(context: BaseContext, id: string, token?: string): Promise<Task>
```

Obtains task information based on the task ID. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-basecontext-c.md) | Yes | Application-based context. |
| id | string | Yes | Task ID. |
| token | string | No | Token for task query. The default value is empty. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Task](arkts-basicservices-agent-task-i.md)&gt; | Promise used to return the created task. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |
| [13400003](../errorcode-request.md#13400003-service-error) | Task service ability error. |
| [21900006](../errorcode-request.md#21900006-task-not-found) | Task removed or not found. |
