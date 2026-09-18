# openAuthorizeDialog

## Modules to Import

```TypeScript
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
```

## openAuthorizeDialog

```TypeScript
function openAuthorizeDialog(context: common.Context): Promise<string>
```

Opens the authorization page of the certificate management dialog box to grant a credential to the application. After the API is successfully called, the app can use the URI of the authorization certificate returned by the API to sign, verify the signature, and query details. This API uses a promise to return the result.

**Since:** 20

**Required permissions:** ohos.permission.ACCESS_CERT_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManagerDialog

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [common.Context](../../apis-ability-kit/arkts-apis/arkts-ability-common-context-t.md) | Yes | Context of the application. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the URI of the certificate authorized. The value contains up to 256 bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. A mandatory parameter is left unspecified. 2. Incorrect parameter type. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | The certificate management application Hap is not preinstalled in the system, and the capability is not supported.<br>**Applicable version:** 26.0.0 and later |
| [29700001](../errorcode-certManagerDialog.md#29700001-internal-error) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [29700002](../errorcode-certManagerDialog.md#29700002-operation-canceled) | The user cancels the authorization. |

**Examples**

```TypeScript
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';

/* context is application context information, which is obtained by the caller. The context here is only an example. */
let context: common.Context = new UIContext().getHostContext() as common.Context;
try {
  certificateManagerDialog.openAuthorizeDialog(context).then((uri: string) => {
    console.info(`Succeeded in authorizing certificate, uri: ${uri}`)
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to authorize certificate. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to authorize certificate. Code: ${error.code}, message: ${error.message}`);
}
```

```TypeScript
import { certificateManagerDialog, certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';

/* context is application context information, which is obtained by the caller. The context here is only an example. */
let context: common.Context = new UIContext().getHostContext() as common.Context;
let certTypes: Array<certificateManagerDialog.CertificateType> = [
  certificateManagerDialog.CertificateType.CREDENTIAL_USER,
  certificateManagerDialog.CertificateType.CREDENTIAL_APP,
  certificateManagerDialog.CertificateType.CREDENTIAL_UKEY
];
let certPurpose: certificateManager.CertificatePurpose = certificateManager.CertificatePurpose.PURPOSE_DEFAULT;
let authorizeRequest: certificateManagerDialog.AuthorizeRequest = { certTypes: certTypes, certPurpose: certPurpose };
try {
  certificateManagerDialog.openAuthorizeDialog(context, authorizeRequest).then((certReference: certificateManagerDialog.CertReference) => {
    let reference = certReference;
    console.info(`Succeeded in opening authorize dialog.`)
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to open authorize dialog. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to open authorize dialog. Code: ${error.code}, message: ${error.message}`);
}
```


## openAuthorizeDialog

```TypeScript
function openAuthorizeDialog(context: common.Context, authorizeRequest: AuthorizeRequest): Promise<CertReference>
```

Opens the Certificate Credential Authorization page of the Certificate Management dialog box. On the page that is displayed, you can authorize the application to use certificate credentials. After the API is called successfully, the app can use the URI of the authorization certificate returned by the API to sign, verify the signature, and query details. The types of certificates that can be authorized include application certificate credentials, user certificate credentials, and USB Key certificate credentials. Using Promise Asynchronous Callbacks.

**Since:** 22

**Required permissions:** ohos.permission.ACCESS_CERT_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManagerDialog

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [common.Context](../../apis-ability-kit/arkts-apis/arkts-ability-common-context-t.md) | Yes | Context of the application. |
| authorizeRequest | [AuthorizeRequest](arkts-devicecertificate-certificatemanagerdialog-authorizerequest-i.md) | Yes | Authorization request information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CertReference](arkts-devicecertificate-certificatemanagerdialog-certreference-i.md)&gt; | Promise used to return the result of the authorization certificate reference. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [29700001](../errorcode-certManagerDialog.md#29700001-internal-error) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error; 4. Call other service failed. Please try again. |
| [29700002](../errorcode-certManagerDialog.md#29700002-operation-canceled) | The user cancels the authorization. |
| [29700006](../errorcode-certManagerDialog.md#29700006-failed-to-validate-the-input-parameter) | Indicates that the input parameters validation failed. for example, the parameter format is incorrect or the value range is invalid. |
| [29700007](../errorcode-certManagerDialog.md#29700007-no-available-authorization-certificate) | No available certificate for authorization. Possible causes: 1. No certificate matches the filter criteria; 2. All certificates have been deleted. |

**Examples**

See [openAuthorizeDialog](#openauthorizedialog)
