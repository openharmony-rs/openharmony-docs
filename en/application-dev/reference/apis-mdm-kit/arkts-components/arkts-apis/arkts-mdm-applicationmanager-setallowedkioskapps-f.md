# setAllowedKioskApps

## Modules to Import

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## setAllowedKioskApps

```TypeScript
function setAllowedKioskApps(admin: Want, appIdentifiers: Array<string>): void
```

Sets applications allowed to run in kiosk mode.

Kiosk mode is a system-level runtime mode that restricts a device to a single application or a set of applications. It controls the lock screen, status bar, gestures, and key features to prevent users from launching other applications or performing other operations on the device.

**Since:** 20

**Required permissions:** ohos.permission.ENTERPRISE_SET_KIOSK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| appIdentifiers | Array&lt;string&gt; | Yes | Array of [unique identifiers](../../apis-ability-kit/arkts-apis/arkts-ability-bundleinfo-signatureinfo-i.md) of an application. You can call the [bundleManager.getBundleInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfo-f.md) API to obtain the **bundleInfo.signatureInfo.appIdentifier**. In case of repeated configuration, the newly configured array will overwrite the old one, with a maximum limit of 200 entries. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API. |

**Examples**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { applicationManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.edmtest',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace it as required.
  let appIdentifiers: Array<string> = ['6917****3569'];
  applicationManager.setAllowedKioskApps(wantTemp, appIdentifiers);
  console.info('Succeeded in setting allowed kiosk apps.');
} catch (err) {
  console.error(`Failed to set allowed kiosk apps. Code is ${err.code}, message is ${err.message}`);
}
```
