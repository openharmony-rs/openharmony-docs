# isAddOsAccountByUserDisallowed (System API)

## Modules to Import

```TypeScript
import { accountManager } from '@kit.MDMKit';
```

## isAddOsAccountByUserDisallowed

```TypeScript
function isAddOsAccountByUserDisallowed(admin: Want, userId: number): boolean
```

Queries whether to disallow a user to add accounts.

**Since:** 11

**Deprecated since:** 26.0.0

**Substitutes:** [isOsAccountAdditionDisallowed](arkts-mdm-accountmanager-isosaccountadditiondisallowed-f.md)

**Required permissions:** ohos.permission.ENTERPRISE_SET_ACCOUNT_POLICY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| userId | number | Yes | User ID, which must be greater than or equal to 0. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the user is not allowed to add system accounts;<br>returns **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { accountManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace parameters with actual values.
  let isDisallowed: boolean = accountManager.isAddOsAccountByUserDisallowed(wantTemp, 100);
  console.info(`Succeeded in querying the user can add os account or not: ${isDisallowed}`);
} catch (err) {
  console.error(`Failed to query the user can add os account or not. Code: ${err.code}, message: ${err.message}`);
}
```
