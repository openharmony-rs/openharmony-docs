# getValue

## Modules to Import

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
```

## getValue

```TypeScript
function getValue(admin: Want, item: string): string
```

Obtains a device setting policy.

**Since:** 12

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SETTINGS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| item | string | Yes | Type of the policy to set.<br>- **screenOff**: device screen-off policy. For PCs/2-in-1 devices, the screen-off policy for battery supply can be queried. <br>- **powerPolicy**: device power policy, which takes effect only for PCs/2-in-1 devices. Only the power policy for battery supply can be queried. <br>- **eyeComfort**: eye comfort mode. This parameter is supported since API version 23. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Policy type value.<br>If **item** is **screenOff**, the device screen-off time (in ms) is returned. For PCs/2-in-1 devices, the device screen-off time (in ms) in battery mode is returned. <br>If **item** is **powerPolicy**, the power policy is returned. For PCs/2-in-1 devices, the power policy in battery mode is returned. The power policy a JSON string in {"powerScene":xx,"powerPolicy":{"powerPolicyAction":xx,"delayTime":xx}} format. **powerScene** indicates the power policy scenario, **delayTime** indicates the delay time (in milliseconds), and **powerPolicyAction** indicates the sleep policy. <br>The value of **powerScene** can be: <br>- **0**: timeout. <br>The value of **powerPolicyAction** can be: <br>- **0**: No action is performed. <br>- **1**: enter sleep mode automatically. <br>- **2**: forcibly enter sleep mode. <br>- **3**: enter sleep mode. This policy does not take effect currently. <br>- **4**: power off. <br>If **item** is **eyeComfort**, **value** is a string indicating the status of the eye comfort mode. <br>- **on**: The eye comfort mode is enabled all day. <br>- **off**: The eye comfort mode is disabled. <br>- **unknown**: other modes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace parameters with actual values.
  let result: string = deviceSettings.getValue(wantTemp, 'screenOff');
  console.info(`Succeeded in getting screen off time, result : ${result}`);
} catch (err) {
  console.error(`Failed to get screen off time. Code: ${err.code}, message: ${err.message}`);
}
```
