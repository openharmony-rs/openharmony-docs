# getSystemTrustedCertificateList (System API)

## Modules to Import

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## getSystemTrustedCertificateList

```TypeScript
function getSystemTrustedCertificateList(): Promise<CMResult>
```

Obtains the list of CA certificates trusted by the system. This API is called only by the certificate management application. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_CERT_MANAGER and ohos.permission.ACCESS_CERT_MANAGER_INTERNAL

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManager

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)&gt; | Promise used to return the operation result, that is, **certList** in the [CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md) object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.<br>The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [17500001](../errorcode-certManager.md#17500001-internal-error) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |

**Examples**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  certificateManager.getSystemTrustedCertificateList().then((cmResult: certificateManager.CMResult) => {
    if (cmResult === undefined) { // If the number of trusted CA certificates is 0, the returned cmResult is undefined.
      console.info('The count of system trusted certificates is 0.');
    } else if (cmResult.certList == undefined) {
      console.info('The result of getting system trusted certificates is undefined.');
    } else {
      let list: Array<certificateManager.CertAbstract> = cmResult.certList;
      console.info('Succeeded in getting system trusted certificates.');
    }
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to get system trusted certificates. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to get system trusted certificates. Code: ${error.code}, message: ${error.message}`);
}
```
