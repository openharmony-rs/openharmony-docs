# installUserTrustedCertificateSync

## Modules to Import

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## installUserTrustedCertificateSync

```TypeScript
function installUserTrustedCertificateSync(cert: Uint8Array, certScope: CertScope): CMResult
```

Installs a user CA certificate.

**Since:** 18

**Required permissions:** ohos.permission.ACCESS_ENTERPRISE_USER_TRUSTED_CERT or ohos.permission.ACCESS_USER_TRUSTED_CERT

**System capability:** SystemCapability.Security.CertificateManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cert | Uint8Array | Yes | CA certificate data. The value contains up to 8196 bytes. |
| certScope | [CertScope](arkts-devicecertificate-certificatemanager-certscope-e.md) | Yes | Scope of the CA certificate. |

**Return value:**

| Type | Description |
| --- | --- |
| [CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md) | CA certificate installation result. The **uri** property in **CMResult** is returned if the certificate is installed successfully. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-internal-error) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500003](../errorcode-certManager.md#17500003-invalid-certificate-or-credential) | Indicates that the certificate is in an invalid format. |
| [17500004](../errorcode-certManager.md#17500004-the-number-of-certificates-or-credentials-reaches-the-limit) | Indicates that the number of certificates reaches the maximum allowed. |
| [17500007](../errorcode-certManager.md#17500007-device-in-advanced-security-mode) | Indicates that the device enters advanced security mode. In this mode, the user CA certificate cannot be installed. |

**Examples**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';

/* The CA certificate data must be assigned by the service. In this example, the data is not CA certificate data. */
let certData: Uint8Array = new Uint8Array([
  0x30, 0x82, 0x0b, 0xc1, 0x02, 0x01,
]);
try {
  let result: certificateManager.CMResult = certificateManager.installUserTrustedCertificateSync(certData, certificateManager.CertScope.CURRENT_USER);
  let certUri = result.uri;
  if (certUri === undefined) {
    console.error("The result of install user trusted certificate is undefined.");
  } else {
    console.info("Succeeded to install user trusted certificate.");
  }
} catch (error) {
  console.error(`Failed to install user trusted certificate. Code: ${error.code}, message: ${error.message}`);
}
```
