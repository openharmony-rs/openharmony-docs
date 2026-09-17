# setActivationLockDisabled

## Modules to Import

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## setActivationLockDisabled

```TypeScript
function setActivationLockDisabled(admin: Want, isDisabled: boolean, credential?: string): Promise<void>
```

Enables or disables the device activation lock. After the device activation lock is disabled, the Find Device function will no longer be available. This function is only available on certain devices.

**Since:** 24

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| isDisabled | boolean | Yes | Whether to disable the activation lock. The value **true** indicates yes, and the value **false** indicates no. |
| credential | string | No | Credential for disabling the activation lock. To disable the activation lock, you must set this parameter to a valid credential. Leave this parameter empty when enabling the activation lock. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. An error object is thrown when the activation lock fails to be enabled or disabled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
| [9201011](../errorcode-enterpriseDeviceManager.md#9201011-invalid-activation-lock-credential) | The credential of the activation lock is invalid. |
| [9201012](../errorcode-enterpriseDeviceManager.md#9201012-failed-to-enable-or-disable-activation-lock) | Failed to enable or disable the activation lock. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |

**Examples**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { systemManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let credential: string = "XXX";
let isDisabled: boolean = true;
systemManager.setActivationLockDisabled(wantTemp, isDisabled, credential).then(() => {
  console.info('Succeeded in setting activation lock status.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set activation lock status. Code: ${err.code}, message: ${err.message}`);
});
```
