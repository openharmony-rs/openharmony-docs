# isAbilityDisabled

## Modules to Import

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## isAbilityDisabled

```TypeScript
function isAbilityDisabled(admin: Want, bundleName: string, accountId: number, abilityName: string): boolean
```

Checks whether the Ability component of a specified application (system application or third-party application) is disabled.

**Since:** 23

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| bundleName | string | Yes | App bundle name. |
| accountId | number | Yes | Account ID. <br>The value must be an integer greater than or equal to 0. <br> You can call [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid) of @ohos.account.osAccount to obtain the ID. |
| abilityName | string | Yes | Name of the ability to be disabled or enabled. Currently, only UIAbility is supported. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the ability is disabled. **true**: The ability is disabled. **false**: The ability is not disabled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |

**Examples**

```TypeScript
import { applicationManager, common } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace it as required.
  let bundleName: string = "com.example.exampleapplication";
  let accountId: number = 100;
  let abilityName: string = "EntryAbility";
  let isDisabled: boolean = applicationManager.isAbilityDisabled(wantTemp, bundleName, accountId, abilityName);
  console.info(`Succeeded in querying whether the ability is disabled, isDisabled: ${isDisabled}`);
} catch(err) {
  console.error(`Failed to query whether the ability is disabled. Code: ${err.code}, message: ${err.message}`);
}
```


## isAbilityDisabled

```TypeScript
function isAbilityDisabled(admin: Want | null, bundleName: string, accountId: number, abilityName: string): boolean
```

Checks whether the Ability component of a specified application (system application or third-party application) is disabled.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) &#124; null | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the. EnterpriseAdminExtensionAbility and the bundle name of the application.<br>If the device has multiple MDM applications, you can pass **admin** to query the corresponding policies. If **null** is passed, the policies that actually take effect on the device are returned. |
| bundleName | string | Yes | App bundle name. |
| accountId | number | Yes | Account ID. The value is an integer greater than or equal to 0. <br> You can call [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid) of @ ohos.account.osAccount to obtain the ID. |
| abilityName | string | Yes | Name of the ability to be disabled or enabled. Currently, only UIAbility is supported. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the ability is disabled. **true**: The ability is disabled. **false**: The ability is not disabled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |

**Examples**

See [isAbilityDisabled](#isabilitydisabled)
