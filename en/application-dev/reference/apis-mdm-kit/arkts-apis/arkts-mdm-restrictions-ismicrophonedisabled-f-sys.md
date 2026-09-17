# isMicrophoneDisabled (System API)

## Modules to Import

```TypeScript
import { restrictions } from '@kit.MDMKit';
```

## isMicrophoneDisabled

```TypeScript
function isMicrophoneDisabled(admin: Want): boolean
```

Queries whether the microphone is disabled.

**Since:** 11

**Deprecated since:** 26.0.0

**Substitutes:** [getDisallowedPolicy](arkts-mdm-restrictions-getdisallowedpolicy-f.md)(admin: Want | null, feature: FeatureForDevice)

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the microphone is disabled; returns **false** otherwise. |

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
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let result = restrictions.isMicrophoneDisabled(wantTemp);
  console.info(`Succeeded in querying is microphone disabled : ${result}`);
} catch (err) {
  console.error(`Failed to query is microphone disabled or not. Code is ${err.code}, message is ${err.message}`);
}
```
