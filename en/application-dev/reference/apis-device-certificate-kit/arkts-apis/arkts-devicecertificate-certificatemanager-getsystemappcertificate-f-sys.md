# getSystemAppCertificate (System API)

## Modules to Import

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## getSystemAppCertificate

```TypeScript
function getSystemAppCertificate(keyUri: string) : Promise<CMResult>
```

Obtains the credential details of the system application. This API is called only by the certificate management application. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_CERT_MANAGER and ohos.permission.ACCESS_SYSTEM_APP_CERT

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyUri | string | Yes | Unique identifier of a system application credential. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)&gt; | Promise used to return the operation result, that is, **credential** in the [CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md) object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.<br> The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter verification failed.<br> Possible causes: the URI is null or the URI format is wrong. |
| [17500001](../errorcode-certManager.md#17500001-internal-error) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500002](../errorcode-certManager.md#17500002-certificate-not-exist) | Indicates that the certificate does not exist. |

**Examples**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let keyUri: string = 'test'; /* Unique identifier of the system application credential. */
try {
  certificateManager.getSystemAppCertificate(keyUri).then((cmResult: certificateManager.CMResult) => {
    if (cmResult?.credential == undefined) {
      console.info('The result of getting system app certificate is undefined.');
    } else {
      let cred: certificateManager.Credential = cmResult.credential;
      console.info('Succeeded in getting system app certificate.');
    }
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to get system app certificate. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to get system app certificate. Code: ${error.code}, message: ${error.message}`);
}
```
