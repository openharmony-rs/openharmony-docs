# installEnterpriseReSignatureCertificate

## Modules to Import

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## installEnterpriseReSignatureCertificate

```TypeScript
function installEnterpriseReSignatureCertificate(admin: Want, certificateAlias: string, fd: number, accountId: number): void
```

Installs the enterprise application re-signing certificate. After the installation is successful, the enterprise can use the certificate to re-sign applications.

A maximum of 10 distinct certificates can be deployed per user. The certificate alias serves as a unique identifier for each certificate and cannot be duplicated during deployment. To update a certificate with an existing alias, you must first uninstall the old certificate by calling [uninstallEnterpriseReSignatureCertificate](arkts-mdm-securitymanager-uninstallenterpriseresignaturecertificate-f.md).

The installed certificates are retained on the device and will not be removed when the MDM app is uninstalled or the admin privilege is deactivated.

In the enterprise app distribution scenario, you can use the re-signing certificate to re- sign enterprise apps. After re-signing, the app package is provided to enterprise administrators, who can then install the re-signed app on enterprise devices where the corresponding re-signing certificate has been deployed.

Process of using the enterprise application re-signing certificate:

1. Install the enterprise application re-signing certificate through the MDM application.
2. Re-sign the original HAP package using a signing tool (**ohos-signer** or the DevEco Studio signing plugin).
3. Install the re-signed app (through the enterprise private app store).
4. Launch and run the app.

Specifications:

1. Apps signed with the old certificate will continue to run normally after a new re-signing certificate is
installed.
2. After a new enterprise signing certificate is installed for an installed enterprise app, if the installed app
needs to be updated, you can directly overwrite the original app without uninstalling it.
3. In enterprise scenarios (especially those involving information security), enterprises need to ensure that only
designated internal software and tools are installed and run on employees' mobile devices. The enterprise application re-signing certificate, in conjunction with the system's application management and permission control mechanisms (via a unified application ID), supports silent installation of enterprise applications, controlled invocation of system capabilities, and restriction of application running scopes. This enables admission control and security governance for enterprise software on managed devices.

**Since:** 24

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| certificateAlias | string | Yes | Certificate alias, which must end with **.cer**. |
| fd | number | Yes | Descriptor of an existing re-signing certificate file. The certificate file must be stored in the [app sandbox directory](../../../file-management/app-sandbox-directory.md). |
| accountId | number | Yes | User ID, which must be greater than or equal to 0. You can call [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid) of **@ohos.account.osAccount** to obtain the user ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [9201006](../errorcode-enterpriseDeviceManager.md#9201006-installed-enterprise-re-signing-certificate-exceeding-the-limit) | The number of certificates has reached the limit. |
| [9201007](../errorcode-enterpriseDeviceManager.md#9201007-invalid-enterprise-re-signing-certificate) | The certificate is invalid. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |

**Examples**

```TypeScript
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { fileIo as fs } from '@kit.CoreFileKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// The test.cer certificate file must be placed in the application sandbox and be a valid enterprise application re-signing certificate.
// Replace with actual values.
const filePath = '/test.cer';
// Replace with actual values.
let certificateAlias: string = 'test.cer';
let fd: number = fs.openSync(filePath, fs.OpenMode.READ_ONLY).fd;
// Replace with actual values.
let accountId: number = 100;
try {
  securityManager.installEnterpriseReSignatureCertificate(
    wantTemp, certificateAlias, fd, accountId);
  console.info('Success to install enterprise re signature certificate.');
} catch (err) {
  console.error(`Failed to install enterprise re signature certificate.
    Code: ${err.code}, message: ${err.message}`);
};
```
