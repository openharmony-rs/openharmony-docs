# uninstallEnterpriseReSignatureCertificate

## Modules to Import

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## uninstallEnterpriseReSignatureCertificate

```TypeScript
function uninstallEnterpriseReSignatureCertificate(admin: Want, certificateAlias: string, accountId: number): void
```

Uninstalls the enterprise application re-signing certificate. After the enterprise re-signing certificate is uninstalled, the applications signed using this certificate can run properly before the device is restarted, but cannot run after the device is restarted.

Usage scenarios:

1. Installing a new certificate: After a new certificate is installed via the
[installEnterpriseReSignatureCertificate](arkts-mdm-securitymanager-installenterpriseresignaturecertificate-f.md) API, applications re-signed using the new certificate can run properly. If the application corresponding to the old signing certificate is a super device administrator application, the application must be deactivated before the certificate can be uninstalled. Otherwise, after the certificate is uninstalled, the application cannot be uninstalled or run.
2. Restoring a mistakenly deleted certificate: After a mistakenly deleted certificate is re-installed via the
[installEnterpriseReSignatureCertificate](arkts-mdm-securitymanager-installenterpriseresignaturecertificate-f.md) API, re-signed applications can run normally without being affected.

> **NOTE:** 
> 
> Certificate deletion is typically performed in scenarios such as certificate expiration or certificate leakage.
> You are advised to implement this feature with a strong prompt to administrators, advising them to delete
> certificates with caution. Before deleting a certificate, ensure that a new re-signing certificate has been
> loaded and that all applications have been updated and switched to the new re-signing certificate. Otherwise,
> historically installed applications will fail to run after a device restart.

**Since:** 24

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| certificateAlias | string | Yes | Certificate alias, which must end with **.cer**. |
| accountId | number | Yes | User ID, which must be greater than or equal to 0. You can call [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid) of **@ohos.account.osAccount** to obtain the user ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [9201008](../errorcode-enterpriseDeviceManager.md#9201008-enterprise-re-signing-certificate-not-exist) | The certificate does not exist. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |

**Examples**

```TypeScript
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let certificateAlias: string = 'test.cer';
// Replace with actual values.
let accountId: number = 100;
try {
  securityManager.uninstallEnterpriseReSignatureCertificate(
    wantTemp, certificateAlias, accountId);
  console.info('Success to uninstall enterprise re signature certificate.');
} catch (err) {
  console.error(`Failed to uninstall enterprise re signature certificate.
    Code: ${err.code}, message: ${err.message}`);
};
```
