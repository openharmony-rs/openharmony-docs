# revokePermission

## Modules to Import

```TypeScript
import { fileShare } from '@kit.CoreFileKit';
```

## revokePermission

```TypeScript
function revokePermission(policies: Array<PolicyInfo>): Promise<void>
```

Revoke persistence permissions for the URI

**Since:** 11

**Required permissions:** ohos.permission.FILE_ACCESS_PERSIST

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| policies | Array&lt;[PolicyInfo](arkts-corefile-fileshare-policyinfo-i.md)&gt; | Yes | Policy information to grant permission on URIs. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 13900001 | Operation not permitted. |
| 13900042 | Out of memory |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { picker } from '@kit.CoreFileKit';

async function revokePermissionExample() {
  try {
    let DocumentSelectOptions = new picker.DocumentSelectOptions();
    let documentPicker = new picker.DocumentViewPicker();
    let uris = await documentPicker.select(DocumentSelectOptions);
    let policyInfo: fileShare.PolicyInfo = {
      uri: uris[0], 
      // Multiple permissions can be revoked in combination. For example, the read and write permissions can be revoked using fileShare.OperationMode.READ_MODE | fileShare.OperationMode.WRITE_MODE.
      operationMode: fileShare.OperationMode.READ_MODE,
    };
    let policies: Array<fileShare.PolicyInfo> = [policyInfo];
    fileShare.revokePermission(policies).then(() => {
      console.info("revokePermission successfully");
    }).catch((err: BusinessError<Array<fileShare.PolicyErrorResult>>) => {
      console.error("revokePermission failed with error message: " + err.message + ", error code: " + err.code);
        if (err.code == 13900001 && err.data) {
          for (let i = 0; i < err.data.length; i++) {
            console.error("error code : " + JSON.stringify(err.data[i].code));
            console.error("error uri : " + JSON.stringify(err.data[i].uri));
            console.error("error reason : " + JSON.stringify(err.data[i].message));
          }
        }
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error('revokePermission failed with err: ' + JSON.stringify(err));
  }
}
```
