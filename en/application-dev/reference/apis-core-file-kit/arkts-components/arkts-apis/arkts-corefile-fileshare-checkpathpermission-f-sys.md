# checkPathPermission (System API)

## Modules to Import

```TypeScript
import { fileShare } from '@kit.CoreFileKit';
```

## checkPathPermission

```TypeScript
function checkPathPermission(tokenID: number, policies: Array<PathPolicyInfo>, policyType: PolicyType): Promise<Array<boolean>>
```

Check permissions for the path.

**Since:** 15

**Required permissions:** ohos.permission.CHECK_SANDBOX_POLICY

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tokenID | number | Yes | Token ID of the application. |
| policies | Array&lt;[PathPolicyInfo](arkts-corefile-fileshare-pathpolicyinfo-i.md)&gt; | Yes | Policy information to check on paths. |
| policyType | [PolicyType](arkts-corefile-fileshare-policytype-e.md) | Yes | Persistent or temporary type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;boolean&gt;&gt; | Returns the permission state of paths. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 13900042 | Out of memory. |

**Examples**

```TypeScript
import { fileShare } from '@kit.CoreFileKit';

async function checkPersistentPermissionExample() {
  try {
    let pathPolicyInfo1: fileShare.PathPolicyInfo = {
      path: '/storage/Users/currentUser/Documents/1.txt',
      operationMode: fileShare.OperationMode.READ_MODE,
    }
    let pathPolicyInfo2: fileShare.PathPolicyInfo = {
      path: '/storage/Users/currentUser/Desktop/2.txt',
      operationMode: fileShare.OperationMode.READ_MODE,
    }

    let policies: Array<fileShare.PathPolicyInfo> = [pathPolicyInfo1, pathPolicyInfo2];
    let policyType: fileShare.PolicyType = fileShare.PolicyType.PERSISTENT_TYPE;
    let tokenID = 537688848; // Use bundleManager.getApplicationInfo() to obtain the token ID for a system app, and use bundleManager.getBundleInfoForSelf() to obtain the token ID for a non-system app.

    fileShare.checkPathPermission(tokenID, policies, policyType).then((result: Array<boolean>) => {
      for (let hasPermission of result) {
        console.info('check permission result is', hasPermission);
      }
    });
    console.info('checkPathPermission finish');
  } catch (error) {
    console.info(`checkPathPermission error, Code: ${error.code}, message: ${error.message}`);
  }
}
```
