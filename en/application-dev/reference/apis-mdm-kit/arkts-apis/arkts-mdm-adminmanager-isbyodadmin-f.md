# isByodAdmin

## Modules to Import

```TypeScript
import { adminManager } from '@kit.MDMKit';
```

## isByodAdmin

```TypeScript
function isByodAdmin(admin: Want): boolean
```

Checks whether the current application is activated as a BYOD device administrator application based on the **EnterpriseAdminExtensionAbility** component.

**Since:** 20

**Required permissions:** ohos.permission.START_PROVISIONING_MESSAGE

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. Only the **EnterpriseAdminExtensionAbility** component of the current application can be passed. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | The value **true** indicates the application is activated as a BYOD device administrator application, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |

**Examples**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { adminManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let result: boolean = adminManager.isByodAdmin(wantTemp);
  console.info(`Succeeded in querying admin is byod admin or not : ${result}`);
} catch (error) {
  console.error(`Failed to query admin is byod admin or not. Code is ${error.code}, message is ${error.message}`);
}
```
