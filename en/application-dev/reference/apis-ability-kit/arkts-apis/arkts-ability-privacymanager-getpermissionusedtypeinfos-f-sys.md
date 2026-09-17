# getPermissionUsedTypeInfos (System API)

## Modules to Import

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
```

## getPermissionUsedTypeInfos

```TypeScript
function getPermissionUsedTypeInfos(
    tokenId?: number | null,
    permissionName?: Permissions): Promise<Array<PermissionUsedTypeInfo>>
```

Obtains information about how a sensitive permission is used by an application.

**Since:** 12

**Required permissions:** ohos.permission.PERMISSION_USED_STATS

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tokenId | number &#124; null | No | Application identity identifier for accessing sensitive permissions. It can be obtained through the [accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid) field of ApplicationInfo. Pass a specific tokenId when querying the access type information of sensitive permissions for a particular app; 0 or null indicates querying the access type information of sensitive permissions for all apps. Starting from API version 20, the null type is newly supported. <br>Default value: 0. |
| permissionName | [Permissions](arkts-ability-permissions-t.md) | No | Name of the sensitive permission being accessed. Pass a specific permission name when querying the access type information of a particular sensitive permission; empty indicates querying the access type information of all sensitive permissions. Passing an invalid value returns error code 12100001.<br>Value constraint: The permission name length cannot exceed 256 characters. Default value: Empty string. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[PermissionUsedTypeInfo](arkts-ability-privacymanager-permissionusedtypeinfo-i-sys.md)&gt;&gt; | Promise used to return the list of permission access type information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. Interface caller does not have permission"ohos.permission.PERMISSION_USED_STATS". |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system app. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-invalid-parameters) | Invalid parameter. PermissionName exceeds 256 characters. |
| [12100002](../errorcode-access-token.md#12100002-tokenid-not-exist) | The input tokenId does not exist. |
| [12100003](../errorcode-access-token.md#12100003-permission-not-exist) | The input permissionName does not exist. |
| [12100009](../errorcode-access-token.md#12100009-internal-service-error) | Common inner error. A database error occurs. |

**Examples**

```TypeScript
import { privacyManager, Permissions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tokenId: number = 0; // Obtained from the accessTokenId field of ApplicationInfo in the BundleInfo of the application.
let permissionName: Permissions = 'ohos.permission.CAMERA';
// Without any parameter.
privacyManager.getPermissionUsedTypeInfos().then((data: Array<privacyManager.PermissionUsedTypeInfo>) => {
  console.info('getPermissionUsedTypeInfos success, result: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`getPermissionUsedTypeInfos fail, code: ${err.code}, message: ${err.message}`);
});
// Pass in tokenId only.
privacyManager.getPermissionUsedTypeInfos(tokenId).then((data: Array<privacyManager.PermissionUsedTypeInfo>) => {
  console.info('getPermissionUsedTypeInfos success, result: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`getPermissionUsedTypeInfos fail, code: ${err.code}, message: ${err.message}`);
});
// Pass in permissionName only.
privacyManager.getPermissionUsedTypeInfos(null, permissionName).then((data: Array<privacyManager.PermissionUsedTypeInfo>) => {
  console.info('getPermissionUsedTypeInfos success, result: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`getPermissionUsedTypeInfos fail, code: ${err.code}, message: ${err.message}`);
});
// Pass in tokenId and permissionName.
privacyManager.getPermissionUsedTypeInfos(tokenId, permissionName).then((data: Array<privacyManager.PermissionUsedTypeInfo>) => {
  console.info('getPermissionUsedTypeInfos success, result: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`getPermissionUsedTypeInfos fail, code: ${err.code}, message: ${err.message}`);
});
```
