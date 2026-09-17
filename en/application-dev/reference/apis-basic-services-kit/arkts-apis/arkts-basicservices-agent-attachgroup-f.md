# attachGroup

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## attachGroup

```TypeScript
function attachGroup(gid: string, tids: string[]): Promise<void>
```

Attaches multiple download task IDs to a specified group ID. This API uses a promise to return the result.

If any task ID does not meet the attachment conditions, all tasks in the list will not be added to the group.

**Since:** 15

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| gid | string | Yes | Target group ID. |
| tids | string[] | Yes | List of task IDs to attach. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |
| [13400003](../errorcode-request.md#13400003-service-error) | Task service ability error. |
| [21900005](../errorcode-request.md#21900005-task-mode-error) | Operation with wrong task mode. |
| [21900006](../errorcode-request.md#21900006-task-not-found) | Task removed or not found. |
| [21900007](../errorcode-request.md#21900007-operation-not-supported-by-the-task-state) | Operation with wrong task state. |
| [21900008](../errorcode-request.md#21900008-task-group-not-found-or-deleted) | Group deleted or not found. |
