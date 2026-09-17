# disableDeviceAdmin

## Modules to Import

```TypeScript
import { adminManager } from '@kit.MDMKit';
```

## disableDeviceAdmin

```TypeScript
function disableDeviceAdmin(admin: Want): Promise<void>
```

Disables a [DA](../../../mdm/mdm-kit-term.md#device-admin-da) application by a [SDA](../../../mdm/mdm-kit-term.md#super-device-admin-sda) application. This API uses a promise to return the result. After this API is called successfully, the specified device administrator application is disabled and no longer has the device management capability. This API can be called only by super device administrator applications.

**Since:** 23

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_DEVICE_ADMIN

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. If the operation fails, an error object will be thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200005](../errorcode-enterpriseDeviceManager.md#9200005-failed-to-disable-the-device-administrator-application) | Failed to deactivate the administrator application of the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |

**Examples**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { adminManager } from '@kit.MDMKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

adminManager.disableDeviceAdmin(wantTemp).catch((err: BusinessError) => {
  console.error(`Failed to disable device admin. Code: ${err.code}, message: ${err.message}`);
});
```
