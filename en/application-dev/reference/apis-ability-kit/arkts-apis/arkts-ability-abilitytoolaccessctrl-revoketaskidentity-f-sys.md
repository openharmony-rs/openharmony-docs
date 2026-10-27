# revokeTaskIdentity (System API)

## Modules to Import

```TypeScript
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
```

## revokeTaskIdentity

```TypeScript
export function revokeTaskIdentity(taskId: string[]): Promise<void>
```

Batch revoke task authentication identities for agent commands. This function batch revokes the task authentication identities and deletes the local cache of task attributes.

**Since:** 26.1.0

**Required permissions:** ohos.permission.QUERY_TOOL_PERMISSIONS

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-abilityToolAccessCtrl-export function revokeTaskIdentity(taskId: string[]): Promise<void>--><!--Device-abilityToolAccessCtrl-export function revokeTaskIdentity(taskId: string[]): Promise<void>-End-->

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| taskId | string[] | Yes | Task ID list to revoke authentication identity. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The interface caller does not have permission "ohos.permission.QUERY_TOOL_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [24010000](../errorcode-abilityToolAccessCtrl-sys.md#24010000-invalid-parameter) | Invalid parameter. TicketExpireTime exceeds 24h, etc. |
| [24010001](../errorcode-abilityToolAccessCtrl-sys.md#24010001-system-service-abnormal) | Service is abnormal. Possible cause: IPC failed. |
| [24010002](../errorcode-abilityToolAccessCtrl-sys.md#24010002-internal-service-error) | Common internal error. Possible cause: dependent service unavailable, resource access failure, etc. |
