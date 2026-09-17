# replaceSuperAdmin (System API)

## Modules to Import

```TypeScript
import { adminManager } from '@kit.MDMKit';
```

## replaceSuperAdmin

```TypeScript
function replaceSuperAdmin(oldAdmin: Want, newAdmin: Want, isKeepPolicy: boolean): void
```

Replaces a specified application with a super device administrator application.

**Since:** 18

**Required permissions:** ohos.permission.MANAGE_ENTERPRISE_DEVICE_ADMIN

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| oldAdmin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Old EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the old EnterpriseAdminExtensionAbility and the bundle name of the application. |
| newAdmin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | New EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the new EnterpriseAdminExtensionAbility and the bundle name of the application. |
| isKeepPolicy | boolean | Yes | A Boolean value indicates whether to retain the policy of the old **EnterpriseAdminExtensionAbility**. The value **true** means that the policy is retained, and the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200003](../errorcode-enterpriseDeviceManager.md#9200003-invalid-administrator-ability-component) | The administrator ability component is invalid. |
| [9200011](../errorcode-enterpriseDeviceManager.md#9200011-failed-to-replace-the-device-administrator-application) | Failed to replace the administrator application of the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let oldAdmin: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let newAdmin: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication_new',
  abilityName: 'NewEnterpriseAdminAbility'
};
try {
  adminManager.replaceSuperAdmin(oldAdmin, newAdmin, false);
  console.info(`Succeeded in replacing super admin.`);
} catch(err) {
  console.error(`Failed to replace super admin. Code: ${err.code}, message: ${err.message}`);
}
```
