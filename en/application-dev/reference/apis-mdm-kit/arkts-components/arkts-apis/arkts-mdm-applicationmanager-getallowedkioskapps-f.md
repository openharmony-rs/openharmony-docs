# getAllowedKioskApps

## Modules to Import

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## getAllowedKioskApps

```TypeScript
function getAllowedKioskApps(admin: Want): Array<string>
```

Obtains the applications allowed to run in kiosk mode.

**Since:** 20

**Required permissions:** ohos.permission.ENTERPRISE_SET_KIOSK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | List of [unique identifiers](../../apis-ability-kit/arkts-apis/arkts-ability-bundleinfo-signatureinfo-i.md) of an application that can run in kiosk mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API |

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
  let appIdentifiers: Array<string> = applicationManager.getAllowedKioskApps(wantTemp);
  console.info(`Succeeded in getting allowed kiosk apps, appIdentifiers: ${JSON.stringify(appIdentifiers)}`);
} catch (err) {
  console.error(`Failed to get allowed kiosk apps. Code is ${err.code}, message is ${err.message}`);
}
```


## getAllowedKioskApps

```TypeScript
function getAllowedKioskApps(admin: Want | null): Array<string>
```

Obtains the applications allowed to run in kiosk mode.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ENTERPRISE_SET_KIOSK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) &#124; null | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the. EnterpriseAdminExtensionAbility and the bundle name of the application.<br>If the device has multiple MDM applications, you can pass **admin** to query the corresponding policies. If **null** is passed, the policies that actually take effect on the device are returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | List of [unique identifiers](../../apis-ability-kit/arkts-apis/arkts-ability-bundleinfo-signatureinfo-i.md) of an application that can run in kiosk mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.The application does not have the permission required to call the API |

**Examples**

See [getAllowedKioskApps](#getallowedkioskapps)
