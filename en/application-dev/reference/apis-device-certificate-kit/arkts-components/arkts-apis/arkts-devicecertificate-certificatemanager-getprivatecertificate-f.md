# getPrivateCertificate

## Modules to Import

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## getPrivateCertificate

```TypeScript
function getPrivateCertificate(keyUri: string, callback: AsyncCallback<CMResult>): void
```

Obtains detailed information about a private credential. This API uses an asynchronous callback to return the result.

**Since:** 11

**Required permissions:** ohos.permission.ACCESS_CERT_MANAGER

**System capability:** SystemCapability.Security.CertificateManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyUri | string | Yes | Unique identifier of the credential to be obtained. The value contains up to 256 bytes. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is **credential** in the [CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md) object. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-internal-error) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500002](../errorcode-certManager.md#17500002-certificate-not-exist) | The certificate does not exist. Possible causes: 1. The certificate URI is incorrect; 2. The certificate has been uninstalled. Please check the certificate URI. |

**Examples**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';

let uri: string = 'test'; /* The service needs to use the unique identifier of the credential to obtain the private credential details, which is not elaborated here. */
try {
  certificateManager.getPrivateCertificate(uri, (err, cmResult) => {
    if (err != null) {
      console.error(`Failed to get private certificate. Code: ${err.code}, message: ${err.message}`);
    } else {
      if (cmResult?.credential == undefined) {
        console.info('The result of getting private certificate is undefined.');
      } else {
        let list = cmResult?.credential;
        console.info('Succeeded in getting private certificate.');
      }
    }
  });
} catch (error) {
  console.error(`Failed to get private certificate. Code: ${error.code}, message: ${error.message}`);
}
```


<a id="getprivatecertificate-1"></a>

## getPrivateCertificate

```TypeScript
function getPrivateCertificate(keyUri: string): Promise<CMResult>
```

Obtains detailed information about a private credential. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.ACCESS_CERT_MANAGER

**System capability:** SystemCapability.Security.CertificateManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyUri | string | Yes | Unique identifier of the credential to be obtained. The value contains up to 256 bytes. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)&gt; | Promise used to return the private credential details obtained, that is, **credential** in the [CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md) object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-internal-error) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500002](../errorcode-certManager.md#17500002-certificate-not-exist) | The certificate does not exist. |

**Examples**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let uri: string = 'test'; /* The service needs to use the unique identifier of the credential to obtain the private credential details, which is not elaborated here. */
try {
  certificateManager.getPrivateCertificate(uri).then((cmResult) => {
    if (cmResult?.credential == undefined) {
      console.info('The result of getting private certificate is undefined.');
    } else {
      let list = cmResult.credential;
      console.info('Succeeded in getting private certificate.');
    }
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to get private certificate. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to get private certificate. Code: ${error.code}, message: ${error.message}`);
}
```
