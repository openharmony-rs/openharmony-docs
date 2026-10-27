# getStatusByPermission (System API)

## Modules to Import

```TypeScript
import { fileShare } from '@kit.CoreFileKit';
```

## getStatusByPermission

```TypeScript
function getStatusByPermission(tokenIDList: Array<number>): Promise<Array<PermissionStatusInfo>>
```

Get the status of URIs permission for applications.

**Since:** 26.1.0

**Required permissions:** ohos.permission.GET_SENSITIVE_PERMISSIONS

**Model restriction:** This API can be used only in the stage model.

<!--Device-fileShare-function getStatusByPermission(tokenIDList: Array<int>): Promise<Array<PermissionStatusInfo>>--><!--Device-fileShare-function getStatusByPermission(tokenIDList: Array<int>): Promise<Array<PermissionStatusInfo>>-End-->

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tokenIDList | Array&lt;number&gt; | Yes | List of token IDs of the applications. <br>The value should be an array of integers. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[PermissionStatusInfo](arkts-corefile-fileshare-permissionstatusinfo-i-sys.md)&gt;&gt; | Promise used to return {Array<PermissionStatusInfo>} |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| 13900001 | Operation not permitted. |
| 13900011 | Out of memory |
| 13900020 | Invalid tokenID |
