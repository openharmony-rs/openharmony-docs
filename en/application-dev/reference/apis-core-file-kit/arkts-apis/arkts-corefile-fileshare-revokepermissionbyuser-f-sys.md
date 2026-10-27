# revokePermissionByUser (System API)

## Modules to Import

```TypeScript
import { fileShare } from '@kit.CoreFileKit';
```

## revokePermissionByUser

```TypeScript
function revokePermissionByUser(tokenID: number, policies: Array<PolicyInfo>): Promise<void>
```

Revoke the URIs permission by user.

**Since:** 26.1.0

**Required permissions:** ohos.permission.REVOKE_SENSITIVE_PERMISSIONS

**Model restriction:** This API can be used only in the stage model.

<!--Device-fileShare-function revokePermissionByUser(tokenID: int, policies: Array<PolicyInfo>): Promise<void>--><!--Device-fileShare-function revokePermissionByUser(tokenID: int, policies: Array<PolicyInfo>): Promise<void>-End-->

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tokenID | number | Yes | Token ID of the application. <br>The value should be an integer. |
| policies | Array&lt;[PolicyInfo](arkts-corefile-fileshare-policyinfo-i.md)&gt; | Yes | Policy information to revoke permission on URIs. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| 13900001 | Operation not permitted. |
| 13900011 | Out of memory |
| 13900020 | Invalid tokenID |
