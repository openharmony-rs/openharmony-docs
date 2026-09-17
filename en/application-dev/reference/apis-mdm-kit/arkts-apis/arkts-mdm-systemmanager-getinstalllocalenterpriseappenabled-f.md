# getInstallLocalEnterpriseAppEnabled

## Modules to Import

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## getInstallLocalEnterpriseAppEnabled

```TypeScript
function getInstallLocalEnterpriseAppEnabled(admin: Want | null): boolean
```

Checks whether local installation of enterprise applications is supported. This API is applicable to scenarios where there is a need to verify whether the local installation of enterprise applications is enabled on the device, helping enterprise administrators confirm the policy configuration status to ensure that enterprise applications can be properly installed.

**Since:** 20

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) &#124; null | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.<br>Before API version 24, this API can be called to check whether local installation of enterprise applications is supported. If the device has multiple MDM applications, you can pass **admin** to query the corresponding policies. Since API version 24, **admin** can be set to **null**. In this case, the policies that actually take effect on the device are returned.<br>**Since:** 24 |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether local installation of enterprise applications is supported. The value **true** indicates that local installation is supported, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |

**Examples**

```TypeScript
import { systemManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let isEnable: boolean = systemManager.getInstallLocalEnterpriseAppEnabled(wantTemp);
  console.info('Succeeded in getting installLocalEnterpriseAppEnabled.');
} catch (err) {
  console.error(`Failed to get installLocalEnterpriseAppEnabled. Code is ${err.code}, message is ${err.message}`);
}
```
