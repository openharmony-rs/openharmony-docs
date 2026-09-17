# uninstallUserCertificate

## Modules to Import

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## uninstallUserCertificate

```TypeScript
function uninstallUserCertificate(admin: Want, certUri: string): Promise<void>
```

Uninstalls a user certificate. This API uses a promise to return the result. This API is applicable to enterprise certificate management scenarios, such as replacing an expired certificate and revoking an employee's access to enterprise resources. Enterprises can call this API to uninstall a certificate when the certificate expires, is replaced, or is no longer needed, ensuring the flexibility and security of device certificate management.

**Since:** 12

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_CERTIFICATE

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| certUri | string | Yes | Certificate URI, which is set and returned by the [installUserCertificate](arkts-mdm-securitymanager-installusercertificate-f.md) API for installing a user certificate. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. An error object is thrown when a user certificate fails to be uninstalled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9201001](../errorcode-enterpriseDeviceManager.md#9201001-failed-to-manage-the-certificate) | Failed to manage the certificate. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let aliasStr = "certName";
securityManager.uninstallUserCertificate(wantTemp, aliasStr).then(() => {
  console.info(`Succeeded in uninstalling user certificate.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to uninstall user certificate. Code is ${err.code}, message is ${err.message}`);
});
```
