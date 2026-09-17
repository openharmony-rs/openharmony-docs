# removeInstallationAllowedAppDistributionTypes

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.MDMKit';
```

## removeInstallationAllowedAppDistributionTypes

```TypeScript
function removeInstallationAllowedAppDistributionTypes(admin: Want, appDistributionTypes: Array<AppDistributionType>): void
```

Removes the distribution type of an application. If only some distribution types in the array are removed, the current device can install applications of the remaining distribution types in the array, but cannot install applications of the distribution types not included in [AppDistributionType](arkts-mdm-bundlemanager-appdistributiontype-e.md).

For details about the distribution type of the application signing certificate, refer to the **appDistributionType** attribute in [ApplicationInfo](../../apis-ability-kit/arkts-apis/arkts-ability-applicationinfo-i.md).

**Since:** 20

**Required permissions:** ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| appDistributionTypes | Array&lt;[AppDistributionType](arkts-mdm-bundlemanager-appdistributiontype-e.md)&gt; | Yes | Distribution types of the application signing certificate. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |

**Examples**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { bundleManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let appDistributionTypes: Array<bundleManager.AppDistributionType> = [bundleManager.AppDistributionType.APP_GALLERY];
  bundleManager.removeInstallationAllowedAppDistributionTypes(wantTemp, appDistributionTypes);
  console.info('Succeeded in removing allowed appDistributionTypes.');
} catch (err) {
  console.error(`Failed to remove allowed appDistributionTypes. Code: ${err.code}, message: ${err.message}`);
}
```
