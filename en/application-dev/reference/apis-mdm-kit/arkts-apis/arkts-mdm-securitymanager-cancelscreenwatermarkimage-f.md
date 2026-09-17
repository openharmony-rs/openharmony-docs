# cancelScreenWatermarkImage

## Modules to Import

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## cancelScreenWatermarkImage

```TypeScript
function cancelScreenWatermarkImage(admin: Want): void
```

Cancels a screen watermark policy, which takes effect for all users. After the cancellation is successful, the watermark on the device screen disappears. When a device no longer requires screen watermark protection, enterprises can call this API to cancel the watermark policy. Only the user who sets the screen watermark can cancel it. For example, user 101 cannot cancel the screen mark set by user 100

**Since:** 26.0.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
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
try {
    securityManager.cancelScreenWatermarkImage(wantTemp);
    console.info(`Succeeded in canceling screen watermark image.`);
} catch(err) {
    console.error(`Failed to cancel screen watermark image. Code: ${err.code}, message: ${err.message}`);
}
```
