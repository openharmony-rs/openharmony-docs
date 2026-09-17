# installMarketApps

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.MDMKit';
```

## installMarketApps

```TypeScript
function installMarketApps(admin: Want, bundleNames: Array<string>): void
```

Downloads and installs an application from AppGallery.

> **NOTE:** 
> 
> After this API is successfully called, an application download task is generated on the home screen. The task is
> the same as that created during download from AppGallery. Upon completion of the download and installation, the
> installation result is returned through the
> [EnterpriseAdminExtensionAbility.onMarketAppInstallResult](arkts-mdm-enterprise-enterpriseadminextensionability-enterpriseadminextensionability-c.md#onmarketappinstallresult)
> callback.

**Since:** 22

**Required permissions:** ohos.permission.ENTERPRISE_INSTALL_BUNDLE

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| bundleNames | Array&lt;string&gt; | Yes | Application bundle name list. A maximum of 10 bundle names can be passed at a time. The bundle name must be the same as that on AppGallery. Otherwise, the download task cannot be created, and error code 9201002 will be reported. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [9201002](../errorcode-enterpriseDeviceManager.md#9201002-failed-to-install-the-enterprise-application) | Failed to install the application. |
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
// Replace with actual values.
let bundleNames: Array<string> = [ 'com.huaweicloud.m' ];
try {
  bundleManager.installMarketApps(wantTemp, bundleNames);
  console.info(`Succeeded in installing market apps.`);
} catch(err) {
  console.error(`Failed to install market apps. Code: ${err.code}, message: ${err.message}`);
}
```
