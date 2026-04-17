# @ohos.enterprise.deviceSettings (Device Settings Management)
<!--Kit: MDM Kit-->
<!--Subsystem: Customization-->
<!--Owner: @huanleima-->
<!--Designer: @hp_guo-->
<!--Tester: @lpw_work-->
<!--Adviser: @zhang_yixin13-->

The **deviceSettings** module provides APIs for setting enterprise devices, including setting and obtaining the screen-off time of a device.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.
>
> The APIs of this module can be called only by a device administrator application that is enabled. For details, see [MDM Kit Development](../../mdm/mdm-kit-guide.md).

## Modules to Import

```ts
import { deviceSettings } from '@kit.MDMKit';
```

## deviceSettings.setValue

setValue(admin: Want, item: string, value: string): void

Sets the device policy.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SETTINGS

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Conflict rule**: [Latest configuration precedence](../../mdm/mdm-kit-multi-mdm.md#rule-3-latest-configuration-precedence).

**Parameters**

<!--Table: 10%; 10%; 10%; 70%-->
| Name| Type                                                   | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| item   | string                                                  | Yes  | Type of the policy to set.<br>- **screenOff**: device screen-off policy. For PCs/2-in-1 devices, the screen-off policies for the battery and power supply modes can be set.<br>- **dateTime**: system time settings.<br>- **powerPolicy**: device power policy. For PCs/2-in-1 devices, only the power policy for the battery mode can be set.<br>- **eyeComfort**: eye comfort mode. This parameter is supported since API version 23. This mode can only be enabled all day or disabled.<br>- **defaultInputMethod**: default input method. This parameter is supported since API version 23.|
| value  | string                                                  | Yes  | Policy type value.<br>If **item** is **screenOff**, **value** is the screen-off time, in ms.<br>If **item** is **dateTime**, **value** is the system time to set, in ms.<br>If **item** is **powerPolicy**, **value** is a JSON string in {"powerScene":xx,"powerPolicy":{"powerPolicyAction":xx,"delayTime":xx}} format. **powerScene** specifies the power policy scenario; **delayTime** specifies the delay time in ms (it cannot be set to 30000 ms); **powerPolicyAction** specifies the sleep policy.<br>The value of **powerScene** can be:<br>- **0**: timeout.<br>The value of **powerPolicyAction** can be:<br>- **0**: No action is performed.<br>- **1**: enter sleep mode automatically.<br>- **2**: forcibly enter sleep mode.<br>- **3**: enter sleep mode. This policy does not take effect currently.<br>- **4**: power off.<br>If **item** is **eyeComfort**, **value** is a string indicating the status of the eye comfort mode.<br>- **on**: The eye comfort mode is enabled all day.<br>- **off**: The eye comfort mode is disabled.<br>If **item** is **defaultInputMethod**, **value** is a string indicating the name of the input method application bundle.<br>- You can use [getCurrentInputMethod](../apis-ime-kit/js-apis-inputmethod.md#inputmethodgetcurrentinputmethod9) to obtain the current input method application bundle name.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
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

## deviceSettings.getValue

getValue(admin: Want, item: string): string

Obtains a device setting policy.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SETTINGS

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| item   | string                                                  | Yes  | Type of the policy to set.<br>- **screenOff**: device screen-off policy. For PCs/2-in-1 devices, the screen-off policies for the battery and power supply modes can be obtained.<br>- **powerPolicy**: device power policy. For PCs/2-in-1 devices, only the power policy for the battery mode can be obtained.<br>- **eyeComfort**: eye comfort mode. This parameter is supported since API version 23.|

**Return value**

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| string | Policy type value.<br>If **item** is **screenOff**, the device screen-off time (in ms) is returned. For PCs/2-in-1 devices, the device screen-off time (in ms) in battery mode is returned.<br>If **item** is **powerPolicy**, the power policy is returned. For PCs/2-in-1 devices, the power policy in battery mode is returned. The power policy a JSON string in {"powerScene":xx,"powerPolicy":{"powerPolicyAction":xx,"delayTime":xx}} format. **powerScene** indicates the power policy scenario, **delayTime** indicates the delay time (in ms), and **powerPolicyAction** indicates the sleep policy.<br>The value of **powerScene** can be:<br>- **0**: timeout.<br>The value of **powerPolicyAction** can be:<br>- **0**: No action is performed.<br>- **1**: enter sleep mode automatically.<br>- **2**: forcibly enter sleep mode.<br>- **3**: enter sleep mode. This policy does not take effect currently.<br>- **4**: power off.<br>If **item** is **eyeComfort**, **value** is a string indicating the status of the eye comfort mode.<br>- **on**: The eye comfort mode is enabled all day.<br>- **off**: The eye comfort mode is disabled.<br>- **unknown**: other modes.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
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

## deviceSettings.setHomeWallpaper<sup>20+</sup>

setHomeWallpaper(admin: Want, fd: number): Promise&lt;void&gt;

Sets the home screen wallpaper. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ENTERPRISE_SET_WALLPAPER

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Conflict rule**: [Latest configuration precedence](../../mdm/mdm-kit-multi-mdm.md#rule-3-latest-configuration-precedence).

**Parameters**

| Name| Type                                                   | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| fd     | number                                                  | Yes  | File descriptor of the image to be set as the home screen wallpaper. The file descriptor of an image in the application's sandbox directory can be obtained via the file.fs.[openSync](../apis-core-file-kit/js-apis-file-fs.md#fileioopensync) API. The size of the wallpaper image must not exceed 100 MB.|

**Return value**

| Type                  | Description                     |
| --------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. An error object is thrown when the home screen wallpaper fails to be set.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed.                               |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

<!--code_no_check-->
```ts
import { deviceSettings } from '@kit.MDMKit';
import { common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo as fs }  from '@kit.CoreFileKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
// Replace parameters with actual values.
let filename: string = "homewallpaper.jpg";
let filePath: string = context.filesDir + '/' + filename;
let fd: number = fs.openSync(filePath, fs.OpenMode.READ_WRITE).fd;
deviceSettings.setHomeWallpaper(wantTemp, fd).then(() => {
  console.info('Succeeded in setting home wallpaper');
}).catch((err: BusinessError) => {
  console.error(`Failed to set home wallpaper. Code: ${err.code}, message: ${err.message}`);
}).finally(() => {
  fs.closeSync(fd);
});
```
## deviceSettings.setUnlockWallpaper<sup>20+</sup>

setUnlockWallpaper(admin: Want, fd: number): Promise&lt;void&gt;

Sets the lock screen wallpaper. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ENTERPRISE_SET_WALLPAPER

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Conflict rule**: [Latest configuration precedence](../../mdm/mdm-kit-multi-mdm.md#rule-3-latest-configuration-precedence).

**Parameters**

| Name| Type                                                   | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| fd     | number                                                  | Yes  | File descriptor of the image to be set as the lock screen wallpaper. The file descriptor of an image in the application's sandbox directory can be obtained via the file.fs.[openSync](../apis-core-file-kit/js-apis-file-fs.md#fileioopensync) API. The size of the wallpaper image must not exceed 100 MB.|

**Return value**

| Type                  | Description                     |
| --------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. An error object is thrown when the lock screen wallpaper fails to be set.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed.                               |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

<!--code_no_check-->
```ts
import { deviceSettings } from '@kit.MDMKit';
import { common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo as fs }  from '@kit.CoreFileKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
// Replace parameters with actual values.
let filename: string = "lockwallpaper.jpg";
let filePath: string = context.filesDir + '/' + filename;
let fd: number = fs.openSync(filePath, fs.OpenMode.READ_WRITE).fd;
deviceSettings.setUnlockWallpaper(wantTemp, fd).then(() => {
  console.info('Succeeded in setting lock wallpaper');
}).catch((err: BusinessError) => {
  console.error(`Failed to set lock wallpaper. Code: ${err.code}, message: ${err.message}`);
});
```

## deviceSettings.setValueForAccount<sup>24+</sup>

setValueForAccount(admin: Want, item: SettingsItem, accountId: number, value: string): void

Sets the device policy for a specified user. This API allows you to set a specific parameter for a given user, such as setting the device name for user 100.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SETTINGS

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| item   | [SettingsItem](#settingsitem24)                                                  | Yes  | Type of the policy to set.|
| accountId | number                                                 | Yes  | User ID, which must be greater than or equal to 0.<br>You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9) to obtain the user ID.                      |
| value  | string                                                  | Yes  | Policy type value.<br>When **item** is set to [SettingsItem.DEVICE_NAME](#settingsitem24), **value** is the device name, which is a character string. The string length ranges from 1 to 100.<br>当item为[SettingsItem.FLOATING_NAVIGATION](#settingsitem24)时，value为三键导航的开关状态，'0'表示三键导航已开启（在[Kiosk模式](../apis-ability-kit/js-apis-app-ability-kioskManager.md#kioskmanagerenterkioskmode)下，三键导航显示依赖底部手势开启；即三键导航开关和底部手势开关同时开启时，三键导航才会显示。底部手势可通过接口[applicationManager.setKioskFeatures](./js-apis-enterprise-applicationManager.md#applicationmanagersetkioskfeatures20)设置开启或关闭），'1'表示三键导航已关闭。<br>当item为[SettingsItem.FLOATING_NAVIGATION](#settingsitem24)时，该接口在Phone和Tablet设备中可正常调用，在其他设备中返回801错误码。|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed.  |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { deviceSettings } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace with actual values.
  let accountId = 100;
  let deviceName: string = "deviceName"
  deviceSettings.setValueForAccount(wantTemp, deviceSettings.SettingsItem.DEVICE_NAME, accountId, deviceName);
  console.info('Succeeded in setting device name.');
} catch (err) {
  console.error(`Failed to set device name. Code: ${err.code}, message: ${err.message}`);
}
```

## deviceSettings.getValueForAccount<sup>24+</sup>

getValueForAccount(admin: Want, item: SettingsItem, accountId: number): string

Obtains the device policy of a specified user. This API allows you to obtain a specific parameter of a given user, such as obtaining the device name of user 100.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SETTINGS

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| item   | [SettingsItem](#settingsitem24)                         | Yes  | Type of the policy to set.|
| accountId | number                                                 | Yes  | User ID, which must be greater than or equal to 0.<br>You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9) to obtain the user ID. |

**Return value**

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| string | Policy type value.<br>If **item** is set to [SettingsItem.DEVICE_NAME](#settingsitem24), the device name is returned.<br>If **item** is set to [SettingsItem.FLOATING_NAVIGATION](#settingsitem24), this API returns the three-key navigation switch state of the specified user.<br>When **item** is set to [SettingsItem.FLOATING_NAVIGATION](#settingsitem24), this API can be called properly on phones and tablets but returns error code 801 on other devices.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed.  |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { deviceSettings } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace with actual values.
  let accountId = 100;
  let result: string = deviceSettings.getValueForAccount(wantTemp, deviceSettings.SettingsItem.DEVICE_NAME, accountId);
  console.info(`Succeeded in getting device name, result : ${result}`);
} catch (err) {
  console.error(`Failed to get device name. Code: ${err.code}, message: ${err.message}`);
}
```

## deviceSettings.addHiddenSettingsMenu<sup>24+</sup>

addHiddenSettingsMenu(admin: Want, menusToHidden: Array\<SettingsMenu>): void

添加设置项至当前用户下的隐藏设置项列表。添加至隐藏设置项列表的设置项在当前用户的设置菜单中会被隐藏，隐藏后不可以在设置的搜索中搜索到。如果通过某种方式搜索到该设置项，点击后也无法打开。调用接口后即刻生效，无需重启设置应用。

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SETTINGS

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**设备行为差异：** 该接口在Phone和Tablet设备中可正常调用，在其他设备中返回801错误码。

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| menusToHidden | Array\<[SettingsMenu](#settingsmenu24)>          | Yes  | 隐藏的设置项列表。|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed.  |
| 9200016  | Service timeout. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { deviceSettings } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

let menusToHidden: Array<deviceSettings.SettingsMenu> = [
  // 需根据实际情况进行替换或增加
  deviceSettings.SettingsMenu.ACCOUNT_ID,
  deviceSettings.SettingsMenu.WIFI,
]

try {
  deviceSettings.addHiddenSettingsMenu(wantTemp, menusToHidden);
  console.info('Succeeded in adding hidden settings menu.');
} catch (err) {
  console.error(`Failed to add hidden settings menu. Code: ${err.code}, message: ${err.message}`);
}
```

## deviceSettings.removeHiddenSettingsMenu<sup>24+</sup>

removeHiddenSettingsMenu(admin: Want, menusToHidden: Array\<SettingsMenu>): void

将设置项从当前用户下的隐藏设置项列表中移除。隐藏设置项列表中的设置项在当前用户的设置菜单中会被隐藏，隐藏后不可以在设置的搜索中搜索到，如果通过某种方式搜索到该设置项，点击后也无法打开。若移除后剩余的隐藏设置项列表为空，则设置项会全部显示。调用接口后即刻生效，无需重启设置应用。

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SETTINGS

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**设备行为差异：** 该接口在Phone和Tablet设备中可正常调用，在其他设备中返回801错误码。

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| menusToHidden | Array\<[SettingsMenu](#settingsmenu24)>          | Yes  | 隐藏的设置项列表。|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed.  |
| 9200016  | Service timeout. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { deviceSettings } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

let menusToHidden: Array<deviceSettings.SettingsMenu> = [
  // 需根据实际情况进行替换或增加
  deviceSettings.SettingsMenu.ACCOUNT_ID,
  deviceSettings.SettingsMenu.WIFI,
]

try {
  deviceSettings.removeHiddenSettingsMenu(wantTemp, menusToHidden);
  console.info('Succeeded in removing hidden settings menu.');
} catch (err) {
  console.error(`Failed to remove hidden settings menu. Code: ${err.code}, message: ${err.message}`);
}
```

## deviceSettings.getHiddenSettingsMenu<sup>24+</sup>

getHiddenSettingsMenu(admin: Want): Array\<SettingsMenu>

获取配置在当前用户下被隐藏的设置项列表。

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SETTINGS

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**设备行为差异：** 该接口在Phone和Tablet设备中可正常调用，在其他设备中返回801错误码。

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|

**Return value**

| Type                                                        | Description                |
| ------------------------------------------------------------ | -------------------- |
| Array\<[SettingsMenu](#settingsmenu24)> | 隐藏的设置项列表。 |

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { deviceSettings } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  const rawList: Array<number> = deviceSettings.getHiddenSettingsMenu(wantTemp) as Array<number>;
  for (const item of rawList) {
      const menu: deviceSettings.SettingsMenu = item as deviceSettings.SettingsMenu;
      console.info(`Valid SettingsMenu item: ${item} -> ${menu}`);
  }
  console.info('Succeeded in getting hidden settings menu.');
} catch (err) {
  console.error(`Failed to get hidden settings menu. Code: ${err.code}, message: ${err.message}`);
}
```

## deviceSettings.setSwitchStatus

setSwitchStatus(admin: Want, key: SwitchKey, status: SwitchStatus): void

设置开关的状态。支持设置星闪、蓝牙、Wi-Fi的状态为开启或关闭，设置完毕后，用户可以手动开关。若已经通过[setDisallowedPolicy](js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicy) 接口禁用了某个开关，则通过本接口设置这个开关的状态会抛出错误码203，需通过[setDisallowedPolicy](js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicy) 接口解除该开关禁用策略。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SETTINGS 或 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type                                          | Mandatory  | Description                                 |
| ------- | ---------------------------------------------- | ---- |------------------------------------------------------------|
| admin   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.  |
| key     | [SwitchKey](#switchkey)                        | Yes     | 开关的名称，应用申请权限 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS 并[激活为自带设备管理应用](./js-apis-enterprise-adminManager.md#adminmanagerstartadminprovision15)，可以使用此接口设置以下开关：星闪、蓝牙、Wi-Fi。 |
| status  | [SwitchStatus](#switchstatus)                  | Yes     | 开关的状态，应用申请权限 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS 并[激活为自带设备管理应用](./js-apis-enterprise-adminManager.md#adminmanagerstartadminprovision15)，可以使用此接口设置以下状态：ON、OFF。 |

**Error codes**

以下的错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed.  |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 203      | This function is prohibited by enterprise management policies. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { deviceSettings } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace with actual values.
  let key: deviceSettings.SwitchKey = deviceSettings.SwitchKey.BLUETOOTH;
  let status: deviceSettings.SwitchStatus  = deviceSettings.SwitchStatus.ON;
  deviceSettings.setSwitchStatus(wantTemp, key, status);
  console.info(`Succeeded in setting switch status.`);
} catch (err) {
  console.error(`Failed to set switch status. Code: ${err.code}, message: ${err.message}`);
}
```

## SettingsItem<sup>24+</sup>

Policy type.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager


| Name| Value  | Description          |
| ---- | ---- | -------------- |
| DEVICE_NAME   | 0    | Device name.|
| FLOATING_NAVIGATION<sup>24+</sup>   | 1   | Three-key navigation.|

## SettingsMenu<sup>24+</sup>

设置项列表。

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

| Name  | Value| Description        |
| ------ | ------ | ----------- |
| ACCOUNT_ID                  | 0      | 账号。 |
| WIFI                        | 1      | WLAN。 |
| WIFI_PROXY_SETTINGS         | 2      | WLAN 代理。 |
| WIFI_IP_SETTINGS            | 3      | WLAN IP 。 |
| BLUETOOTH                   | 4      | 星闪和蓝牙/蓝牙。 |
| NETWORK                     | 5      | 网络。 |
| MOBILE_NETWORK              | 6      | 移动网络。 |
| SUPER_DEVICE                | 7      | 多设备协同-超级终端。 |
| MORE_CONNECTIVITY_OPTIONS   | 8      | 多设备协同。 |
| HOME_SCREEN_STYLE           | 9      | 桌面和个性化。 |
| DISPLAY_BRIGHTNESS          | 10     | 显示和亮度。 |
| SOUND_VIBRATION             | 11     | 声音和振动。 |
| NOTIFICATIONS               | 12     | 通知和状态栏。 |
| BIOMETRICS_PASSWORD         | 13     | 生物识别和密码。 |
| APPS_AND_SERVICES           | 14     | 应用和元服务。 |
| BATTERY                     | 15     | 电池。 |
| STORAGE                     | 16     | 存储。 |
| PRIVACY_AND_SECURITY        | 17     | 隐私和安全。 |
| DIGITAL_BALANCE             | 18     | 健康使用设备。 |
| SMART_ASSISTANT             | 19     | 智能助手。 |
| ACCESSIBILITY               | 20     | 关怀和无障碍。 |
| SYSTEM                      | 21     | 系统。 |
| ABOUT_DEVICE                | 22     | 关于本机。 |
| SYSTEM_NAVIGATION           | 23     | 系统-系统导航。 |
| LANGUAGE_REGION             | 24     | 系统-语言和地区。 |
| INPUT_METHODS               | 25     | 系统-输入法。 |
| DATE_TIME                   | 26     | 系统-日期和时间。 |
| DATA_CLONE                  | 27     | 系统-数据克隆。 |
| BACKUP_SETTINGS             | 28     | 系统-备份和恢复。 |
| RESET                       | 29     | 系统-重置。 |
| SUPERHUB                    | 30     | 系统-中转站。 |
| USER_EXPERIENCE             | 31     | 系统-用户体验改进计划。 |
| SCREEN_CAST                 | 32     | 多设备协同-无线投屏。 |
| PRINTERS_SCANNERS           | 33     | 打印机和扫描仪。 |
| MOBILE_DATA                 | 34     | 移动网络-移动数据。 |
| PERSONAL_HOTSPOT            | 35     | 移动网络-个人热点。 |
| SIM_MANAGEMENT              | 36     | 移动网络-SIM卡管理。 |
| AIRPLANE_MODE               | 37     | 移动网络-飞行模式。 |
| MANAGE_DATA_USAGE           | 38     | 移动网络-流量管理。 |
| VPN_SETTINGS                | 39     | 移动网络-VPN。 |
| TEXT_DISPLAY_SIZE           | 40     | 显示和亮度-字体大小和界面缩放。 |
| APP_DUPLICATOR              | 41     | 系统-应用分身。 |
| SEARCH                      | 42     | 搜索。 |

## SwitchKey

开关名称的枚举。

**起始版本：** 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

| Name      | Value  | Description      | 需要权限 |
| ---------- | --- | -----------|----------|
| NEARLINK  | 0    | 星闪开关。 | ohos.permission.ENTERPRISE_MANAGE_SETTINGS 或 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS |
| BLUETOOTH | 1    | 蓝牙开关。 | ohos.permission.ENTERPRISE_MANAGE_SETTINGS 或 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS |
| WIFI      | 2    | Wi-Fi开关。 | ohos.permission.ENTERPRISE_MANAGE_SETTINGS 或 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS |

## SwitchStatus

开关状态的枚举。

**起始版本：** 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

| Name| Value  | Description     | 需要权限 |
| ----| ---- | ----------|----------|
| ON  | 0    | 开启状态。 | ohos.permission.ENTERPRISE_MANAGE_SETTINGS 或 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS |
| OFF | 1    | 关闭状态。 | ohos.permission.ENTERPRISE_MANAGE_SETTINGS 或 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS |
