# deleteGroup

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## deleteGroup

```TypeScript
function deleteGroup(gid: string): Promise<void>
```

Deletes a specified group. No task ID can be added to the group. This API uses a promise to return the result.

When all tasks in a group are succeeded, failed, or removed and the group is deleted, the completion and failure notifications of this group are displayed.

**Since:** 15

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| gid | string | Yes | Target group ID. The value must be the same as the ID of the created task group, that is, the return value of the task group created using the [request.agent.createGroup](arkts-basicservices-agent-creategroup-f.md) API. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |
| [13400003](../errorcode-request.md#13400003-service-error) | Task service ability error. |
| [21900008](../errorcode-request.md#21900008-task-group-not-found-or-deleted) | Group deleted or not found. |
