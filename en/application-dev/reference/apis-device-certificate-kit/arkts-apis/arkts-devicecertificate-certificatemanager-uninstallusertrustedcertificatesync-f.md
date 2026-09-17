# uninstallUserTrustedCertificateSync

## Modules to Import

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## uninstallUserTrustedCertificateSync

```TypeScript
function uninstallUserTrustedCertificateSync(certUri: string): void
```

Uninstalls a user CA certificate.

**Since:** 18

**Required permissions:** ohos.permission.ACCESS_ENTERPRISE_USER_TRUSTED_CERT or ohos.permission.ACCESS_USER_TRUSTED_CERT

**System capability:** SystemCapability.Security.CertificateManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| certUri | string | Yes | Unique identifier of the certificate to be uninstalled. The value contains a maximum of 256 bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-internal-error) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [17500002](../errorcode-certManager.md#17500002-certificate-not-exist) | Indicates that the certificate does not exist. |

**Examples**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';

let certUri: string = "test"; /* The service needs to use the certificate identifier to delete the certificate, which is not elaborated here. */
try {
  certificateManager.uninstallUserTrustedCertificateSync(certUri);
} catch (error) {
  console.error(`Failed to uninstall user trusted certificate. Code: ${error.code}, message: ${error.message}`);
}
```
