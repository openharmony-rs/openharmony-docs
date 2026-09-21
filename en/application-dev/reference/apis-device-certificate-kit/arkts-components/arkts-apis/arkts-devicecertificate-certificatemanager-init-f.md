# init

## Modules to Import

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## init

```TypeScript
function init(authUri: string, spec: CMSignatureSpec, callback: AsyncCallback<CMHandle>): void
```

Indicates the initialization of signature and signature verification using credentials. This is the first step in the signature verification process. Later, the update and finish interfaces need to be invoked in sequence to complete the operations. Use Callback to return the result asynchronously.

**Since:** 11

**Required permissions:** ohos.permission.ACCESS_CERT_MANAGER

**System capability:** SystemCapability.Security.CertificateManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| authUri | string | Yes | Unique identifier of the credential to be used. The value contains up to 256 bytes. |
| spec | [CMSignatureSpec](arkts-devicecertificate-certificatemanager-cmsignaturespec-i.md) | Yes | Parameters for the signing or signature verification operation. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[CMHandle](arkts-devicecertificate-certificatemanager-cmhandle-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the obtained **CMHandle**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-internal-error) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500002](../errorcode-certManager.md#17500002-certificate-not-exist) | The certificate does not exist. |
| [17500005](../errorcode-certManager.md#17500005-application-not-authorized) | The application is not authorized by the user. Please call [openAuthorizeDialog](arkts-devicecertificate-certificatemanagerdialog-openauthorizedialog-f.md) method to request user authorization for the certificate or credential.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';

let uri: string = 'test'; /* The service needs to use the unique identifier of the credential to initialize signing and signature verification, which is not elaborated here. */
const req: certificateManager.CMSignatureSpec = {
  purpose: certificateManager.CmKeyPurpose.CM_KEY_PURPOSE_SIGN,
  padding: certificateManager.CmKeyPadding.CM_PADDING_PSS,
  digest: certificateManager.CmKeyDigest.CM_DIGEST_SHA256
}
try {
  certificateManager.init(uri, req, (err, cmHandle) => {
    if (err != null) {
      console.error(`Failed to init. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('Succeeded in initiating.');
    }
  })
} catch (error) {
  console.error(`Failed to init. Code: ${error.code}, message: ${error.message}`);
}
```


<a id="init-1"></a>

## init

```TypeScript
function init(authUri: string, spec: CMSignatureSpec): Promise<CMHandle>
```

Initializes the signing or signature verification operation using the specified credential. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.ACCESS_CERT_MANAGER

**System capability:** SystemCapability.Security.CertificateManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| authUri | string | Yes | Unique identifier of the credential to be used. The value contains up to 256 bytes. |
| spec | [CMSignatureSpec](arkts-devicecertificate-certificatemanager-cmsignaturespec-i.md) | Yes | Parameters for the signing or signature verification operation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CMHandle](arkts-devicecertificate-certificatemanager-cmhandle-i.md)&gt; | Promise used to return the operation result, that is, the **CMHandle** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-internal-error) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500002](../errorcode-certManager.md#17500002-certificate-not-exist) | The certificate does not exist. |
| [17500005](../errorcode-certManager.md#17500005-application-not-authorized) | The application is not authorized by the user.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let uri: string = 'test'; /* The service needs to use the unique identifier of the credential to initialize signing and signature verification, which is not elaborated here. */
const req: certificateManager.CMSignatureSpec = {
  purpose: certificateManager.CmKeyPurpose.CM_KEY_PURPOSE_VERIFY,
  padding: certificateManager.CmKeyPadding.CM_PADDING_PSS,
  digest: certificateManager.CmKeyDigest.CM_DIGEST_MD5
}
try {
  certificateManager.init(uri, req).then((handle) => {
    console.info('Succeeded in initiating.');
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to init. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to init. Code: ${error.code}, message: ${error.message}`);
}
```
