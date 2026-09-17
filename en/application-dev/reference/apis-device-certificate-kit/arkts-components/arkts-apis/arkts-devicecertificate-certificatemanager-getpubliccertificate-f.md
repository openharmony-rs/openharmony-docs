# getPublicCertificate

## Modules to Import

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## getPublicCertificate

```TypeScript
function getPublicCertificate(keyUri: string): Promise<CMResult>
```

Obtains detailed information about a public credential. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.ACCESS_CERT_MANAGER

**System capability:** SystemCapability.Security.CertificateManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyUri | string | Yes | Unique identifier of a user's public credential. The value contains up to 256 bytes. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)&gt; | Promise used to return the detailed information about the user's public credential obtained, that is, **credential** in the [CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md) object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-internal-error) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500002](../errorcode-certManager.md#17500002-certificate-not-exist) | The certificate does not exist. |
| [17500005](../errorcode-certManager.md#17500005-application-not-authorized) | The application is not authorized by the user. |

**Examples**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let uri: string = 'test'; /* The user needs to use the unique identifier of the credential to obtain the public credential details, which is not elaborated here. */
try {
  certificateManager.getPublicCertificate(uri).then((cmResult) => {
    if (cmResult?.credential == undefined) {
      console.info('The result of getting public certificate is undefined.');
    } else {
      let cred = cmResult.credential;
      console.info('Succeeded in getting Public certificate.');
    }
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to get Public certificate. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to get Public certificate. Code: ${error.code}, message: ${error.message}`);
}
```
