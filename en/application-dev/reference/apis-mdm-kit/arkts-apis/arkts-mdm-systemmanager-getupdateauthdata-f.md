# getUpdateAuthData

## Modules to Import

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## getUpdateAuthData

```TypeScript
function getUpdateAuthData(admin: Want): Promise<string>
```

Obtains the authentication data for system update verification. This API uses a promise to return the result. This API is applicable to intranet update scenarios. Enterprise administrators can use the authentication data to verify the validity and integrity of the system update package, preventing malicious update packages and improving system security.

**Since:** 19

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the authentication data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |

**Examples**

```TypeScript
import { systemManager } from '@kit.MDMKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
systemManager.getUpdateAuthData(wantTemp).then((result: string) => {
  console.info(`Succeeded in getting update auth data: ${JSON.stringify(result)}`);
}).catch((error: BusinessError) => {
  console.error(`Get update auth data failed. Code is ${error.code},message is ${error.message}`);
});
```
