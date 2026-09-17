# openInstallCertificateDialog

## Modules to Import

```TypeScript
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
```

## openInstallCertificateDialog

```TypeScript
function openInstallCertificateDialog(context: common.Context, certType: CertificateType, certScope: CertificateScope, cert: Uint8Array): Promise<string>
```

Opens the Certificate Management Install Certificate dialog box. After the certificate is successfully installed, the unique identifier of the certificate is returned. Applications can use the identifier to use the certificate. Use Promise asynchronous callback.

**Since:** 14

**Required permissions:** ohos.permission.ACCESS_CERT_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManagerDialog

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [common.Context](../../apis-ability-kit/arkts-apis/arkts-ability-common-context-t.md) | Yes | Context of the application. |
| certType | [CertificateType](arkts-devicecertificate-certificatemanagerdialog-certificatetype-e.md) | Yes | Type of the certificate to install. **CA_CERT**, **CREDENTIAL_USER**, and **CREDENTIAL_SYSTEM** are currently supported. |
| certScope | [CertificateScope](arkts-devicecertificate-certificatemanagerdialog-certificatescope-e.md) | Yes | Usage scope of the certificate to install. **CURRENT_USER** and **NOT_SPECIFIED** are currently supported. |
| cert | Uint8Array | Yes | The certificate data. The size cannot exceed 8 KB.<br>When certType is set to CA_CERT, the certificate data must be in PEM or DER format. <br>When certType is set to CREDENTIAL_USER or CREDENTIAL_SYSTEM, the value must be in the P12 encoding format. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the certificate URI. The value contains up to 256 bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | The certificate management application Hap is not preinstalled in the system, and the capability is not supported.<br>**Applicable version:** 26.0.0 and later |
| [29700001](../errorcode-certManagerDialog.md#29700001-internal-error) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [29700002](../errorcode-certManagerDialog.md#29700002-operation-canceled) | The user cancels the installation operation. |
| [29700003](../errorcode-certManagerDialog.md#29700003-failed-to-install-the-certificate) | The user install certificate failed in the certificate manager dialog, such as the certificate is in an invalid format. |
| [29700004](../errorcode-certManagerDialog.md#29700004-operation-not-supported-by-the-device) | For security purposes, the current device does not support this API. You can use the [supportsCACertDialog](arkts-devicecertificate-certificatemanagerdialog-supportscacertdialog-f.md) to determine whether the device supports opening the dialog box for installing a CA certificate with certType set to CA. |
| [29700005](../errorcode-certManagerDialog.md#29700005-non-secure-operation) | The operation does not comply with the device security policy, such as the device does not allow users to manage the CA certificate of the global user.<br>**Applicable version:** 18 and later |

**Examples**

```TypeScript
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';

/* context is application context information, which is obtained by the caller. The context here is only an example. */
let context: common.Context = new UIContext().getHostContext() as common.Context;
/* certificateType specifies the certificate type. The value CA_CERT here indicates a CA certificate. */
let certificateType: certificateManagerDialog.CertificateType = certificateManagerDialog.CertificateType.CA_CERT;
/* certificateScope specifies the usage scope of the certificate. The value CURRENT_USER here means the certificate can be used by the current user. */
let certificateScope: certificateManagerDialog.CertificateScope = certificateManagerDialog.CertificateScope.CURRENT_USER;
/* The CA certificate data must be assigned by the service. In this example, the data is not CA certificate data. */
let caCert: Uint8Array = new Uint8Array([
  0x30, 0x82, 0x0b, 0xc1, 0x02, 0x01,
]);
try {
  certificateManagerDialog.openInstallCertificateDialog(context, certificateType, certificateScope, caCert).then((uri: string) => {
    console.info('Succeeded in opening install certificate');
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to open install certificate dialog. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to open install certificate dialog. Code: ${error.code}, message: ${error.message}`);
}
```
