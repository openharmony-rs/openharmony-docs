# setValue

## Modules to Import

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
```

## setValue

```TypeScript
function setValue(admin: Want, item: string, value: string): void
```

Sets the device policy.

**Since:** 12

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SETTINGS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| item | string | Yes | Type of the policy to set.<br>- **screenOff**: device screen-off policy. For PCs/2-in-1 devices, the device power policy can be set for both battery and power modes. <br>- **dateTime**: system time settings. <br>- **powerPolicy**: device power policy. This capability is supported only on PCs/2-in-1 devices. After the policy is set, the **Settings**   > **Power & battery** screen is not refreshed. The settings do not take effect on phones or tablets. <br>For PCs/2-in-1 devices, the device power policy can be set only for battery supply. When the sleep delay policy upon device screen-off due to timeout is set, the sleep action takes effect after the sleep time shown in the **Settings** > **Power & battery** screen, followed by an additional **delayTime**. <br>- **eyeComfort**: eye comfort mode. This parameter is supported since API version 23. This mode can only be enabled all day or disabled. <br>- **defaultInputMethod**: default input method. This parameter is supported since API version 23. |
| value | string | Yes | Policy type value. <br>If **item** is **screenOff**, **value** is the screen-off time, in ms. It is recommended that **value** be consistent with the options in the drop-down list box on the settings page. Passing **-1** to set the screen to never turn off is supported only on PCs/2‑in‑1 devices. This value does not take effect on other device types. <br>If **item** is **dateTime**, **value** is the system time to set, in ms. <br>If **item** is **powerPolicy**, **value** is a JSON string in {"powerScene":xx,"powerPolicy":{"powerPolicyAction":xx,"delayTime":xx}} format. <br>**powerScene** indicates the power policy scenario. The following values are supported: <br>- **0**: screen-off due to timeout. <br>**powerPolicyAction** indicates the sleep action policy scenario. The following values are supported: <br>- **0**: No action is performed. <br>- **1**: enter sleep mode automatically. <br>- **2**: forcibly enter sleep mode. <br>- **3**: enter sleep mode. This policy does not take effect currently. <br>- **4**: power off. <br>**delayTime** indicates the delay time (unit: ms). The value cannot be **30000**. Other values are allowed. <br>If **item** is **eyeComfort**, **value** is a string indicating the status of the eye comfort mode. <br>- **on**: The eye comfort mode is enabled all day. <br>- **off**: The eye comfort mode is disabled. <br>If **item** is **defaultInputMethod**, **value** is a string indicating the name of the input method application bundle. <br>- You can use [getCurrentInputMethod](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethod-getcurrentinputmethod-f.md) to obtain the current input method application bundle name. |

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
  // Replace with actual values.
  deviceSettings.setValue(wantTemp, 'screenOff', '3000');
  console.info(`Succeeded in setting screen off time.`);
} catch (err) {
  console.error(`Failed to set screen off time. Code: ${err.code}, message: ${err.message}`);
}
```
