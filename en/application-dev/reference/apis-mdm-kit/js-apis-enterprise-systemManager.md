# @ohos.enterprise.systemManager (System Management)
<!--Kit: MDM Kit-->
<!--Subsystem: Customization-->
<!--Owner: @huanleima; @weizai16-->
<!--Designer: @hp_guo-->
<!--Tester: @lpw_work-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=f400a496b51ef33bf928f8716900091477352d7e translatedAt=2026-11-03T05:25:05.352Z pushedAt=2026-11-03T12:08:25.554Z nl=1 -->

This module provides system management capabilities, including NTP time server settings, OTA upgrade policy management, system update management, key event handling policies, log collection, device activation lock management, and volume management. It is applicable to enterprise device management scenarios, helping enterprise administrators centrally manage device system configurations, upgrade policies, and security policies, thereby improving the efficiency and security of enterprise device management.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.
>
> The APIs of this module can be called only by a device administrator application that is enabled. For details, see [MDM Kit Development](../../mdm/mdm-kit-guide.md).

## Modules to Import

```ts
import { systemManager } from '@kit.MDMKit';
```

## systemManager.setNTPServer

setNTPServer(admin: Want, server: string): void

Sets the Network Time Protocol (NTP) time server. After successful configuration, the system will use the specified NTP server for time synchronization to calibrate the system time. This API is suitable for scenarios where enterprise devices require unified time synchronization, ensuring that device time remains consistent with standard time and avoiding business issues caused by inaccurate time, such as inconsistent log timestamps and certificate validation failures.

> **NOTE**
>
> In multi-MDM application scenarios, the [configuration](../../mdm/mdm-kit-multi-mdm.md#rule-3-latest-configuration-precedence) rule is followed.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type                                 | Mandatory  | Description     |
| ----- | ----------------------------------- | ---- | ------- |
| admin | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes   | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| server | string | Yes| NTP server addresses separated by commas (,). For example, **ntpserver1.com,ntpserver2.com**. The value can contain a maximum of 96 bytes, including the null terminator (**\0**).|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                     |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device. |
| 9200002 | The administrator application does not have permission to manage the device. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { systemManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let server: string = "ntpserver.com";
try {
  systemManager.setNTPServer(wantTemp, server);
  console.info('Succeeded in setting NTPserver.');
} catch (err) {
  console.error(`Failed to set ntp server. Code is ${err.code}, message is ${err.message}`);
}
```

## systemManager.getNTPServer

getNTPServer(admin: Want): string

Obtains the NTP server information. This API is applicable to scenarios where you need to query the current NTP server address configured on the device, to verify whether the time synchronization configuration is correct, or to obtain the current configuration before making policy adjustments.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description                  |
| ------ | ------------------------------------------------------- | ---- | ---------------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|

**Return value**

| Type  | Description                               |
| ------ | ----------------------------------- |
| string | NTP server information.|

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
import { systemManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let result: string = systemManager.getNTPServer(wantTemp);
  console.info(`Succeeded in getting NTP server. result: ${result}`);
} catch (err) {
  console.error(`Failed to get ntp server. Code is ${err.code}, message is ${err.message}`);
}
```

## systemManager.setOtaUpdatePolicy

setOtaUpdatePolicy(admin: Want, policy: OtaUpdatePolicy): void

Sets the upgrade policy. After the setting is successful, the system performs OTA updates based on the specified policy type. Different policy types correspond to different update behaviors. In the intranet upgrade scenario, you need to first call the [systemManager.notifyUpdatePackages](#systemmanagernotifyupdatepackages) API to notify the system of the update packages, and then call this API to set the upgrade policy. When the upgrade policy is set to prohibit upgrades, the device will prohibit OTA upgrades, and the local HOTA domain set through the [systemManager.setLocalHotaDomain](#systemmanagersetlocalhotadomain) API will not take effect.

> **NOTE**
>
> In multi-MDM application scenarios, the [exclusive](../../mdm/mdm-kit-multi-mdm.md#rule-2-policy-exclusivity) rule is followed.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type                                 | Mandatory  | Description     |
| ----- | ----------------------------------- | ---- | ------- |
| admin | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes   | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| policy | [OtaUpdatePolicy](#otaupdatepolicy) | Yes| OTA update policy to set.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                     |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.                       |
| 9200002 | The administrator application does not have permission to manage the device. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.|

**Example**

```ts
import { systemManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Default update policy.
let otaUpdatePolicy1: systemManager.OtaUpdatePolicy = {
  "policyType": systemManager.PolicyType.DEFAULT,
  "version": "version_1.0.0.0"
};
try {
  systemManager.setOtaUpdatePolicy(wantTemp, otaUpdatePolicy1);
  console.info('Succeeded in setting ota update policy.');
} catch (err) {
  console.error(`Failed to set ota update policy. Code is ${err.code}, message is ${err.message}`);
}
// Prohibit update.
let otaUpdatePolicy2: systemManager.OtaUpdatePolicy = {
  "policyType": systemManager.PolicyType.PROHIBIT,
  "version": "version_1.0.0.1"
};
try {
  systemManager.setOtaUpdatePolicy(wantTemp, otaUpdatePolicy2);
  console.info('Succeeded in setting ota update policy.');
} catch (err) {
  console.error(`Failed to set ota update policy. Code is ${err.code}, message is ${err.message}`);
}
// Enforce update.
let otaUpdatePolicy3: systemManager.OtaUpdatePolicy = {
  "policyType": systemManager.PolicyType.UPDATE_TO_SPECIFIC_VERSION,
  "version": "version_1.0.0.2",
  "latestUpdateTime": 1716343200 // timestamp
};
try {
  systemManager.setOtaUpdatePolicy(wantTemp, otaUpdatePolicy3);
  console.info('Succeeded in setting ota update policy.');
} catch (err) {
  console.error(`Failed to set ota update policy. Code is ${err.code}, message is ${err.message}`);
}
// Update at the specified time period.
let otaUpdatePolicy4: systemManager.OtaUpdatePolicy = {
  "policyType": systemManager.PolicyType.WINDOWS,
  "version": "version_1.0.0.3",
  "installStartTime": 1716281049, // Timestamp.
  "installEndTime": 1716343200 // timestamp
};
try {
  systemManager.setOtaUpdatePolicy(wantTemp, otaUpdatePolicy4);
  console.info('Succeeded in setting ota update policy.');
} catch (err) {
  console.error(`Failed to set ota update policy. Code is ${err.code}, message is ${err.message}`);
}
// Delay the update.
let otaUpdatePolicy5: systemManager.OtaUpdatePolicy = {
  "policyType": systemManager.PolicyType.POSTPONE,
  "version": "version_1.0.0.4",
  "delayUpdateTime": 5 // unit (hour)
};
try {
  systemManager.setOtaUpdatePolicy(wantTemp, otaUpdatePolicy5);
  console.info('Succeeded in setting ota update policy.');
} catch (err) {
  console.error(`Failed to set ota update policy. Code is ${err.code}, message is ${err.message}`);
}
// Disable public network upgrade.
let otaUpdatePolicy6: systemManager.OtaUpdatePolicy = {
  "policyType": systemManager.PolicyType.DEFAULT,
  "version": "version_1.0.0.5",
  "disableSystemOtaUpdate": true
};
try {
  systemManager.setOtaUpdatePolicy(wantTemp, otaUpdatePolicy6);
  console.info('Succeeded in setting ota update policy.');
} catch (err) {
  console.error(`Failed to set ota update policy. Code is ${err.code}, message is ${err.message}`);
}
```

## systemManager.getOtaUpdatePolicy

getOtaUpdatePolicy(admin: Want): OtaUpdatePolicy

Checks the update policy. This API is applicable to scenarios where you need to obtain the current OTA update policy configuration of the device, to verify whether the policy is correctly delivered, or to obtain the current policy configuration before making policy adjustments.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description              |
| ------ | ------------------------------------------------------- | ---- | ------------------ |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|

**Return value**

| Type  | Description                           |
| ------ | ------------------------------- |
| [OtaUpdatePolicy](#otaupdatepolicy) | **OtaUpdatePolicy** object containing the update policy obtained.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device.       |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.|

**Example**

```ts
import { systemManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let policy: systemManager.OtaUpdatePolicy = systemManager.getOtaUpdatePolicy(wantTemp);
  console.info(`Succeeded in getting update policy: ${JSON.stringify(policy)}`);
} catch (err) {
  console.error(`Failed to get update policy. Code is ${err.code}, message is ${err.message}`);
}
```

## systemManager.notifyUpdatePackages

notifyUpdatePackages(admin: Want, packageInfo: UpdatePackageInfo): Promise&lt;void&gt;

Notifies the system of the update packages. In intranet updates, call this API to notify the system of the update packages, and then call [systemManager.setOtaUpdatePolicy](#systemmanagersetotaupdatepolicy) to set the update policy. This API uses a promise to return the result.
> **NOTE**
> 
> This API is time-consuming. Subsequent calls to other synchronous APIs in the application main thread must wait for the asynchronous return of this API.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                               | Mandatory| Description          |
| ------ | ----------------------------------- | ---- | -------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| packageInfo  | [UpdatePackageInfo](#updatepackageinfo) | Yes  | Information about the system update packages.<br>**Note**: The input **UpdatePackageInfo.packages.path** must be a .zip package starting with update. If a file in other formats is input, error code 9201004 will be reported.|

**Return value**

| Type                  | Description                     |
| --------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. An error object will be thrown if the operation fails.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device.       |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9201004  | The update packages do not exist or analyzing failed. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.|

**Example**

```ts
import { systemManager } from '@kit.MDMKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';
import { fileIo } from '@kit.CoreFileKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let notify: systemManager.NotifyDescription = {
  // Replace with actual values.
  "installTips": "installTips",
  "installTipsDetail": "installTips detail"
};
let description: systemManager.PackageDescription = {
  // Replace with actual values.
  "notify": notify
};
let updatePackages: Array<systemManager.Package> = [];
// Replace the application sandbox path with the actual one.
let fileDir = "/xxxx/xxxx/";
let path1: string = "update_sd_base.zip";
let path2: string = "update_sd_cust_xxxxx_all_cn.zip";
let path3: string = "update_sd_preload_xxxxx_all_cn_R1.zip";
let fd1: number = fileIo.openSync(fileDir + path1, fileIo.OpenMode.READ_ONLY).fd;
let fd2: number = fileIo.openSync(fileDir + "xxxxx/" + path2, fileIo.OpenMode.READ_ONLY).fd;
let fd3: number = fileIo.openSync(fileDir + "xxxxx/" + path3, fileIo.OpenMode.READ_ONLY).fd;
let package1: systemManager.Package = {
  // Replace with actual values.
  "type": systemManager.PackageType.FIRMWARE,
  "path": path1,
  "fd": fd1
};
let package2: systemManager.Package = {
  // Replace with actual values.
  "type": systemManager.PackageType.FIRMWARE,
  "path": path2,
  "fd": fd2
};
let package3: systemManager.Package = {
  // Replace with actual values.
  "type": systemManager.PackageType.FIRMWARE,
  "path": path3,
  "fd": fd3
};
updatePackages.push(package1);
updatePackages.push(package2);
updatePackages.push(package3);
let updatePackageInfo: systemManager.UpdatePackageInfo = {
  // Replace with actual values.
  "version" : "1.0",
  "packages" : updatePackages,
  "description" : description
};
systemManager.notifyUpdatePackages(wantTemp, updatePackageInfo).then(() => {
  console.info('Succeeded in notifying update packages.');
}).catch ((error: BusinessError) => {
  console.error(`Failed to notify update packages. Code is ${error.code},message is ${error.message}`);
});
```

## systemManager.getUpdateResult

getUpdateResult(admin: Want, version: string): Promise&lt;UpdateResult&gt;

Obtains the system update result. This API uses a promise to return the result. This API is applicable to scenarios where you need to check whether a system update is successful. It helps enterprise administrators understand the device update status and handle update failures in a timely manner to ensure that the device system version meets enterprise requirements.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                               | Mandatory| Description          |
| ------ | ----------------------------------- | ---- | -------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| version  | string | Yes  | Version of the update package.|

**Return value**

| Type                  | Description                     |
| --------------------- | ------------------------- |
| Promise&lt;[UpdateResult](#updateresult)&gt; | Promise used to return the system update result.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device.       |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.|

**Example**

```ts
import { systemManager } from '@kit.MDMKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
systemManager.getUpdateResult(wantTemp, "1.0").then((result:systemManager.UpdateResult) => {
  console.info(`Succeeded in getting update result: ${JSON.stringify(result)}`);
}).catch((error: BusinessError) => {
  console.error(`Get update result failed. Code is ${error.code},message is ${error.message}`);
});
```
## systemManager.getUpdateAuthData<sup>19+</sup>

getUpdateAuthData(admin: Want): Promise&lt;string&gt;

Obtains the authentication data for system update verification. This API uses a promise to return the result. This API is applicable to intranet update scenarios. Enterprise administrators can use the authentication data to verify the validity and integrity of the system update package, preventing malicious update packages and improving system security.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                               | Mandatory| Description          |
| ------ | ----------------------------------- | ---- | -------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|

**Return value**

| Type                  | Description                     |
| --------------------- | ------------------------- |
| Promise&lt;string&gt; | Promise used to return the authentication data.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device.       |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
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

## systemManager.setOtaUpdateNonceEnable

setOtaUpdateNonceEnable(admin: Want, isEnable: boolean): void

Sets the enablement status of Nonce during OTA updates (enabled by default). After it is enabled, the system verifies the validity of Nonce during the OTA update process, thereby preventing replay attacks and improving system security.
> **NOTE**
> 
> To ensure system security, it is not recommended to disable Nonce verification unless there are special service requirements such as intranet upgrades.
>
> In multi-MDM application scenarios, the [configuration](../../mdm/mdm-kit-multi-mdm.md#rule-3-latest-configuration-precedence) rule is followed.

**Since:** 26.0.0

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices but returns error code 801 on other devices.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description                  |
| ------ | ------------------------------------------------------- | ---- | ---------------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| isEnable | boolean | Yes| The value **true** means to enable nonce for OTA update, and the value **false** means to disable nonce for OTA update.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200016  | Service timeout. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { systemManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let isEnable: boolean = true;
try {
  systemManager.setOtaUpdateNonceEnable(wantTemp, isEnable);
  console.info('Succeeded in setting OTA update Nonce enable.');
} catch (err) {
  console.error(`Failed to set OTA update Nonce enable. Code is ${err.code}, message is ${err.message}`);
}
```

## systemManager.isOtaUpdateNonceEnable

isOtaUpdateNonceEnable(admin: Want): boolean

Checks whether nonce is enabled for OTA update. This API is applicable to scenarios where you need to verify the OTA update security configuration on the device. It helps enterprise administrators confirm the status of the nonce verification feature to ensure system update security.

**Since:** 26.0.0

> **NOTE**
>
> In multi-MDM application scenarios, the [configuration](../../mdm/mdm-kit-multi-mdm.md#rule-3-latest-configuration-precedence) rule is followed.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description                  |
| ------ | ------------------------------------------------------- | ---- | ---------------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|

**Return value**

| Type  | Description                               |
| ------ | ----------------------------------- |
| boolean | The value **true** means that the nonce for OTA update is enabled, and the value **false** means that the nonce for OTA update is disabled.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200016  | Service timeout. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { systemManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let result: boolean = systemManager.isOtaUpdateNonceEnable(wantTemp);
  console.info(`Succeeded in querying OTA update Nonce enable: ${result}`);
} catch (err) {
  console.error(`Failed to query OTA update Nonce enable. Code is ${err.code}, message is ${err.message}`);
}
```

## systemManager.setLocalHotaDomain

setLocalHotaDomain(domain: string): void

Sets the local HOTA (Huawei Over-the-Air) domain of the device. After the setting is successful, the system uses the specified HOTA domain for upgrades. This API is applicable to enterprise intranet upgrade scenarios and helps enterprise administrators specify the local HOTA domain of the device, so that the device can obtain upgrade packages from the upgrade server specified by the enterprise, avoiding upgrades over the public network and improving the security and controllability of upgrades. Before calling this API, you can call [common.isFeatureSupported](./js-apis-enterprise-common.md#commonisfeaturesupported) (with common.ManagedFeature.LOCAL_HOTA_DOMAIN as the input parameter) to check whether the device supports the local HOTA domain feature.

HOTA domain usage process:
1. The enterprise administrator calls [systemManager.setLocalHotaDomain](#systemmanagersetlocalhotadomain) through the MDM application to set the local HOTA domain of the device and specify the upgrade package download server.
2. When the device performs a HOTA upgrade, the system finds and downloads the upgrade package based on the locally configured HOTA domain to complete the upgrade.
3. The enterprise administrator can call [systemManager.getLocalHotaDomain](#systemmanagergetlocalhotadomain) to query the currently configured local HOTA domain of the device and verify whether the configuration is correct.
4. To restore the default system upgrade server, call this API and pass an empty string to restore the domain to the default domain.

Application scenarios:
- Intranet upgrade: In an enterprise intranet environment where the public network upgrade server cannot be accessed, the administrator specifies the domain of the enterprise intranet HOTA upgrade server, so that the device can obtain upgrade packages from the intranet server.
- Upgrade server change: After the enterprise upgrade server is migrated or replaced, the administrator resets the local HOTA domain name to ensure that the device obtains the upgrade package from the new server.
- Upgrade server failover: When the enterprise upgrade server fails, the administrator can switch to the backup upgrade server domain name to ensure the continuity of the upgrade service.

> **NOTE**
> 
> When the upgrade policy is set to prohibit upgrades through the [systemManager.setOtaUpdatePolicy](#systemmanagersetotaupdatepolicy) API, the device prohibits OTA upgrades. In this scenario, the local HOTA domain name set does not take effect.
>
> In a multi-MDM application scenario, the [Configuration](../../mdm/mdm-kit-multi-mdm.md#rule-3-latest-configuration-precedence) rule is followed.

The domain passed in must comply with the domain name naming rules. The validation rules are as follows:
1. The length cannot exceed 64 characters.
2. IP addresses and localhost are not supported.
3. The domain name must start with https\://.
4. The domain name must match the regular expression: ^(?:\[a-zA-Z0-9\](?:\[a-zA-Z0-9.-\]*\[a-zA-Z0-9\])?\\.)+\[a-zA-Z\]{2,}$. This regular expression does not participate in validating the https\:// part.
5. Passing an empty string restores the domain name to the default domain name. The empty string is not subject to the preceding validation rules.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences:**: This API can be properly called on PCs/2-in-1 devices. If it is called on other device types, error code 801 is returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                        |
| ----- | -------------------------------------- | ---- | ------- |
| domain | string | Yes | Local HOTA domain. For details about the validation rules, see the API description. |

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device. |
| 9200002 | The administrator application does not have permission to manage the device. |
| 9200012 | Parameter verification failed. |
| 9200016 | Service timeout. |
| 9200018 | This device is not an enterprise device. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 801     | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { common, systemManager } from '@kit.MDMKit';

// Replace it based on the actual situation.
let domain: string = "https://www.hotaExample.com";
// Before calling this API, query whether the device supports the local HOTA domain name feature.
let isSupported: boolean = common.isFeatureSupported(common.ManagedFeature.LOCAL_HOTA_DOMAIN);
if (isSupported) {
  try {
    systemManager.setLocalHotaDomain(domain);
    console.info('Succeeded in setting local HOTA domain.');
  } catch (err) {
    console.error(`Failed to set local HOTA domain. Code is ${err.code}, message is ${err.message}`);
  }
} else {
  console.info('The local HOTA domain feature is not supported.');
}
```

## systemManager.getLocalHotaDomain

getLocalHotaDomain(): string

Obtains the local HOTA (Huawei Over-the-Air) domain of the device. This API is applicable to scenarios where there is a need to query the local HOTA domain configured on the current device.

**Application scenarios**
- Configuration verification: Before an upgrade or after an upgrade exception, query the local HOTA domain to confirm whether the current upgrade server configuration of the device is correct.
- Batch management: Enterprise administrators can query the local HOTA domain configuration of each device in batches through the MDM platform to centrally control the upgrade direction of devices.

**Since:** 26.0.1

> **NOTE**
>
> In multi-MDM application scenarios, the [configuration](../../mdm/mdm-kit-multi-mdm.md#rule-3-latest-configuration-precedence) rule is followed.

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences:** This interface can be normally called on PC/2in1 enterprise devices, and returns an empty string on other devices.

**Model restriction:** This interface can be used only in the stage model.

**Return value**

| Type   | Description                                |
| ------ | ----------------------------------- |
| string | Local HOTA domain name. If the device does not support this API, an empty string is returned as the default value. |

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200016  | Service timeout. |
| 9200018  | This device is not an enterprise device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { systemManager } from '@kit.MDMKit';

try {
  let domain: string = systemManager.getLocalHotaDomain();
  console.info(`Succeeded in getting local HOTA domain: ${domain}`);
} catch (err) {
  console.error(`Failed to get local HOTA domain. Code is ${err.code}, message is ${err.message}`);
}
```

## systemManager.addDisallowedNearLinkProtocols<sup>20+</sup>

addDisallowedNearLinkProtocols(admin: Want, protocols: Array&lt;NearLinkProtocol&gt;, accountId: number): void

Adds a list of NearLink protocols that are not allowed to be used for a specified user. NearLink Kit provides a low-power, high-speed short-range communication service that supports connection and data interaction between NearLink devices. <!--RP3--><!--RP3End-->This API does not take effect for system services and system applications such as the keyboard and stylus.

> **NOTE**
>
> In a multi-MDM application scenario, the [merge](../../mdm/mdm-kit-multi-mdm.md#rule-4-policy-merging) rule is followed.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices. If it is called on other device types, error code 801 is returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                  |
| protocols  | Array&lt;[NearLinkProtocol](#nearlinkprotocol20)&gt;               | Yes  | NearLink protocol list.|
| accountId | number                                                 | Yes  | User ID, which must be greater than or equal to 0.<br>**accountId** can be obtained via APIs such as [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1).|


**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).


| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |


**Example**

```ts
import { systemManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// Replace with actual values.
let protocols: systemManager.NearLinkProtocol[] = [systemManager.NearLinkProtocol.SSAP,
  systemManager.NearLinkProtocol.DATA_TRANSFER];

// Replace with actual values.
let accountId: number = 100;

try {
  systemManager.addDisallowedNearLinkProtocols(wantTemp, protocols, accountId);
  console.info('Succeeded in adding the disabled Starlink protocol list for the specified user.');
} catch (err) {
  console.error(`Failed to add the disabled Starlink protocol list for the specified user. Code is ${err.code}, message is ${err.message}`);
}
```

## systemManager.removeDisallowedNearLinkProtocols<sup>20+</sup>

removeDisallowedNearLinkProtocols(admin: Want, protocols: Array&lt;NearLinkProtocol&gt;, accountId: number): void

Removes the list of disallowed NearLink protocols for a specified user. After successful removal, the specified user can use the removed NearLink protocols for communication again, restoring the corresponding protocol connection capabilities. Use cases: In enterprise device management scenarios, administrators can use this API to remove previously set NearLink protocol disabling policies, allowing users to resume communication between devices via NearLink protocols. This is suitable for scenarios where there is a need to restore NearLink communication capabilities for specific users, helping enterprise administrators flexibly adjust NearLink protocol access permissions of user devices to meet communication requirements in different business scenarios.


> **NOTE**
>
> In a multi-MDM application scenario, the [merge](../../mdm/mdm-kit-multi-mdm.md#rule-4-policy-merging) rule is followed.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices. If it is called on other device types, error code 801 is returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                  |
| protocols  | Array&lt;[NearLinkProtocol](#nearlinkprotocol20)&gt;               | Yes  | NearLink protocol list.|
| accountId | number                                                 | Yes  | User ID, which must be greater than or equal to 0.<br>**accountId** can be obtained via APIs such as [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1).|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. | 
| 9200012  | Parameter verification failed. |                
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { systemManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// Replace with actual values.
let protocols: systemManager.NearLinkProtocol[] = [systemManager.NearLinkProtocol.SSAP,
  systemManager.NearLinkProtocol.DATA_TRANSFER];

// Replace with actual values.
let accountId: number = 100;
try {
  systemManager.removeDisallowedNearLinkProtocols(wantTemp, protocols, accountId);
  console.info('Succeeded in removing the disabled Starlink protocol list for the specified user.');
} catch (err) {
  console.error(`Failed to remove the disabled Starlink protocol list for the specified user. Code is ${err.code}, message is ${err.message}`);
}
```

## systemManager.getDisallowedNearLinkProtocols<sup>20+</sup>

getDisallowedNearLinkProtocols(admin: Want, accountId: number): Array&lt;NearLinkProtocol&gt;

Obtains the list of disallowed NearLink protocols for a specified user. This API is applicable to scenarios where there is a need to query the current NearLink protocol access restrictions for a user, helping enterprise administrators verify whether the policy has been correctly applied or obtain the current configuration before making policy adjustments.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices. If it is called on other device types, error code 801 is returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type                                                   | Mandatory| Description                                                        |
| ------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                  |
| accountId | number                                                 | Yes  | User ID, which must be greater than or equal to 0.<br>**accountId** can be obtained via APIs such as [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1).|

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| Array&lt;[NearLinkProtocol](#nearlinkprotocol20)&gt;          | List of disallowed NearLink protocols for a specified user.|

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
import { systemManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// Replace with actual values.
let accountId: number = 100;

try {
  let result: systemManager.NearLinkProtocol[] = systemManager.getDisallowedNearLinkProtocols(wantTemp, accountId);
  console.info(`Succeeded in querying the disabled Starlink protocol list for the specified user: ${result}`);
} catch (err) {
  console.error(`Failed to query the disabled Starlink protocol list for the specified user. Code is ${err.code}, message is ${err.message}`);
}
```

## systemManager.setInstallLocalEnterpriseAppEnabled<sup>20+</sup>

setInstallLocalEnterpriseAppEnabled(admin: Want, isEnable: boolean): void

Sets whether local installation of enterprise applications is supported. When local installation is enabled, users can install enterprise applications (signing certificate distribution type: **enterprise_normal**) by double-tapping their installation packages on enterprise PCs/2-in-1 devices with the local installation capability.<!--RP8--><!--RP8End-->

> **NOTE**
>
> In a multi-MDM application scenario, the [strictest control](../../mdm/mdm-kit-multi-mdm.md#rule-1-security-first) rule is followed. If any MDM application sets support for local installation of enterprise applications, the combined policy is to support local installation of enterprise applications.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices but returns error code 801 on other devices.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type                                 | Mandatory | Description|
| ----- | ----------------------------------- | ---- | ------- |
| admin | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes| EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| isEnable | boolean | Yes| Whether local installation of enterprise applications is supported. The value **true** indicates that the local installation of enterprise applications is supported, and the value **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                     |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device. |
| 9200002 | The administrator application does not have permission to manage the device. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts

import { systemManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let isEnable: boolean = true;
try {
  systemManager.setInstallLocalEnterpriseAppEnabled(wantTemp, isEnable);
  console.info('Succeeded in setting InstallLocalEnterpriseAppEnabled.');
} catch (err) {
  console.error(`Failed to set installLocalEnterpriseAppEnabled. Code is ${err.code}, message is ${err.message}`);
}
```

## systemManager.getInstallLocalEnterpriseAppEnabled<sup>20+</sup>

getInstallLocalEnterpriseAppEnabled(admin: Want | null): boolean

Queries whether local installation of enterprise applications is supported. This API is applicable to scenarios where you need to verify whether the local installation of enterprise applications is enabled on a device, helping enterprise administrators confirm the policy configuration status and ensure that the device can install enterprise applications properly.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices but returns error code 801 on other devices.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description                  |
| ------ | ------------------------------------------------------- | ---- | ---------------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.<br>Before API version 24, this API can be called to check whether local installation of enterprise applications is supported. If the device has multiple MDM applications, you can pass **admin** to query the corresponding policies. Since API version 24, **admin** can be set to **null**. In this case, the policies that actually take effect on the device are returned.|

**Return value**

| Type  | Description                               |
| ------ | ----------------------------------- |
| boolean | Whether local installation of enterprise applications is supported. The value **true** indicates that local installation is supported, and the value **false** indicates the opposite.|

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
import { systemManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let isEnable: boolean = systemManager.getInstallLocalEnterpriseAppEnabled(wantTemp);
  console.info('Succeeded in getting installLocalEnterpriseAppEnabled.');
} catch (err) {
  console.error(`Failed to get installLocalEnterpriseAppEnabled. Code is ${err.code}, message is ${err.message}`);
}
```
  

## systemManager.setAutoUnlockAfterReboot<sup>20+</sup>

setAutoUnlockAfterReboot(admin: Want, isAllowed: boolean): void

Sets automatic unlocking upon device reboot. This setting takes effect only on devices without a screen lock password. This API is applicable to enterprise unattended devices or scenarios where services need to be quickly restored through a restart, avoiding device downtime caused by manual unlocking, thereby improving device operation and maintenance efficiency and service continuity.

> **NOTE**
>
> In a multi-MDM application scenario, the [strictest control](../../mdm/mdm-kit-multi-mdm.md#rule-1-security-first) rule is followed. If any MDM application sets automatic unlock after device restart, the combined policy is automatic unlock after device restart.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices. If it is called on other device types, error code 801 is returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type                                 | Mandatory  | Description     |
| ----- | ----------------------------------- | ---- | ------- |
| admin | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes   | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| isAllowed | boolean | Yes| The value **true** indicates that the device is automatically unlocked after reboot, and the value **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                     |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device. |
| 9200002 | The administrator application does not have permission to manage the device. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { systemManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let isAllowed: boolean = true;
try {
  systemManager.setAutoUnlockAfterReboot(wantTemp, isAllowed);
  console.info('Succeeded in setting setAutoUnlockAfterReboot.');
} catch (err) {
  console.error(`Failed to set auto unlock after reboot. Code is ${err.code}, message is ${err.message}`);
}
```

## systemManager.getAutoUnlockAfterReboot<sup>20+</sup>

getAutoUnlockAfterReboot(admin: Want): boolean

Obtains whether the device automatically unlocks after restart. This API is applicable to scenarios where you need to verify whether the device restart unlock policy is correctly configured, helping enterprise administrators confirm the device automatic unlock status.

This API queries the policy set by the corresponding enterprise device management application by passing in a Want. To query the policy that actually takes effect, use the [systemManager.getAutoUnlockAfterReboot](#systemmanagergetautounlockafterreboot) API.

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences:** This API can be properly called on PC/2in1 devices. If it is called on other device types, error code 801 is returned.

**Model restriction** This API can be used only in the stage model.

**Parameters**

| Name | Type                                                    | Mandatory | Description                   |
| ------ | ------------------------------------------------------- | ---- | ---------------------- |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes   | Enterprise device management extension component. The Want must contain the abilityName of the enterprise device management extension capability and the bundleName of the application.|

**Return value**

| Type   | Description                                |
| ------ | ----------------------------------- |
| boolean | true indicates that the device is automatically unlocked after restart; false indicates the opposite. |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { systemManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace it based on the actual situation.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let result: boolean = systemManager.getAutoUnlockAfterReboot(wantTemp);
  console.info(`Succeeded in getting auto unlock after reboot. result: ${result}`);
} catch (err) {
  console.error(`Failed to get auto unlock after reboot. Code is ${err.code}, message is ${err.message}`);
}
```


## systemManager.getAutoUnlockAfterReboot

getAutoUnlockAfterReboot(admin: Want | null): boolean

Checks whether the device is automatically unlocked upon reboot. This API is applicable to scenarios where there is a need to verify whether the device reboot unlock policy is correctly configured, helping enterprise administrators confirm the status of the automatic device unlock function.

**Since:** 26.0.0

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices. If it is called on other device types, error code 801 is returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description                  |
| ------ | ------------------------------------------------------- | ---- | ---------------------- |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | Yes   | Enterprise device management extension component. The Want must contain the abilityName of the enterprise device management extension capability and the bundleName of the application.<br>When multiple MDM applications exist on the device, passing Want queries the policy set by the corresponding enterprise device management application, and passing null queries the policy that actually takes effect.|

**Return value**

| Type  | Description                               |
| ------ | ----------------------------------- |
| boolean | The value **true** indicates the device is automatically unlocked after reboot, and the value **false** indicates the opposite.|

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
import { systemManager } from '@kit.MDMKit';

try {
  // Replace the parameters based on the actual situation.
  systemManager.getAutoUnlockAfterReboot(null);
  console.info('Succeeded in getting auto unlock after reboot.');
} catch (err) {
  console.error(`Failed to get auto unlock after reboot. Code is ${err.code}, message is ${err.message}`);
}
```
## systemManager.addKeyEventPolicies<sup>23+</sup>

addKeyEventPolicies(admin: Want, keyPolicies: Array&lt;KeyEventPolicy&gt;): void

Adds a key event handling policy. When the system triggers a key event, if the event matches the delivered key event policy, the MDM app will be notified via the [EnterpriseAdminExtensionAbility.onKeyEvent](js-apis-EnterpriseAdminExtensionAbility.md#onkeyevent23) callback, with the key event information of the matched policy carried in the callback. 

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be properly called on phones and tablets. If it is called on other device types, error code 801 is returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description                  |
| ------ | ------------------------------------------------------- | ---- | ---------------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| keyPolicies     | Array&lt;[KeyEventPolicy](#keyeventpolicy23)&gt; | Yes  | Key policy. Physical keys (power key, volume up, and volume down) and navigation keys (back, home, and recently opened) are supported. Physical keys can be combined into a combination key, but navigation keys cannot. For details about the combination key event response, see the key event callback [onKeyEvent](js-apis-EnterpriseAdminExtensionAbility.md#onkeyevent23).|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200010  | A conflict policy has been configured. |
| 9200012  | Parameter verification failed. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { systemManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

let keypolicy: Array<systemManager.KeyEventPolicy> = [
  {
    "keyCode": systemManager.KeyCode.POWER,
    "keyPolicy": systemManager.KeyPolicy.CUSTOM
  },
  {
    "keyCode": systemManager.KeyCode.VOLUME_UP,
    "keyPolicy": systemManager.KeyPolicy.CUSTOM
  }
];

try {
  systemManager.addKeyEventPolicies(wantTemp, keypolicy);
  console.info('Succeeded in adding key event policies.');
} catch (err) {
  console.error(`Failed to add key event policies. Code is ${err.code}, message is ${err.message}`);
}
```

## systemManager.removeKeyEventPolicies<sup>23+</sup>

removeKeyEventPolicies(admin: Want, keyCodes: Array&lt;KeyCode&gt;): void

Removes a key event handling policy. After the deletion is successful, the system restores the default handling behavior for the specified key event. This API is applicable to scenarios where there is a need to restore the default key behavior, helping enterprise administrators flexibly adjust device key response policies to meet the needs of different business scenarios.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be properly called on phones and tablets. If it is called on other device types, error code 801 is returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description                  |
| ------ | ------------------------------------------------------- | ---- | ---------------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| keyCodes    | Array&lt;[KeyCode](#keycode23)&gt; | Yes  | Key code. You can remove multiple key policies at a time. Removing an unsupported key will report error code 9200012.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { systemManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

let keyCodes: Array<systemManager.KeyCode> = [
  systemManager.KeyCode.POWER, systemManager.KeyCode.VOLUME_UP
];

try {
  systemManager.removeKeyEventPolicies(wantTemp, keyCodes);
  console.info('Succeeded in removing key event policies.');
} catch (err) {
  console.error(`Failed to remove key event policies. Code is ${err.code}, message is ${err.message}`);
}
```

## systemManager.getKeyEventPolicies<sup>23+</sup>

getKeyEventPolicies(admin: Want): Array&lt;KeyEventPolicy&gt;

Obtains the key event handling policy. This API is applicable to scenarios where you need to query the current key event handling policy configuration. It helps enterprise administrators verify whether the policy is correctly delivered, or obtain the current configuration before making policy adjustments.

This API queries the policy set by the corresponding enterprise device management application by passing in a Want. To query the policy that actually takes effect, use the [systemManager.getKeyEventPolicies](#systemmanagergetkeyeventpolicies) API.

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences:** This API can be properly called on Phone and Tablet devices. If it is called on other device types, error code 801 is returned.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type                                                    | Mandatory | Description                   |
| ------ | ------------------------------------------------------- | ---- | ---------------------- |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes   | Enterprise device management extension component. The Want must contain the abilityName of the device management extension capability and the bundleName of the application. |

**Return value**

| Type   | Description                                |
| ------ | ----------------------------------- |
| Array&lt;[KeyEventPolicy](#keyeventpolicy23)&gt; | List of currently configured key event policies. |

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { systemManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace it based on the actual situation.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let result: Array<systemManager.KeyEventPolicy> = [];
try {
  result = systemManager.getKeyEventPolicies(wantTemp);
  console.info('Succeeded in getting key event policies.');
} catch (err) {
  console.error(`Failed to get key event policies. Code is ${err.code}, message is ${err.message}`);
}
```


## systemManager.getKeyEventPolicies

getKeyEventPolicies(admin: Want | null): Array&lt;KeyEventPolicy&gt;

Obtains the key event handling policy. This API is applicable to scenarios where you need to query the current key event handling policy configuration. It helps enterprise administrators verify whether the policy has been correctly applied or obtain the current configuration before making policy adjustments.

**Since:** 26.0.0

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be properly called on phones and tablets. If it is called on other device types, error code 801 is returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description                  |
| ------ | ------------------------------------------------------- | ---- | ---------------------- |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | Yes   | Enterprise device management extension component. The Want must contain the abilityName of the device management extension capability and the bundleName of the application.<br>When multiple MDM applications exist on the device, passing a Want queries the policy set by the corresponding enterprise device management application, while passing null queries the policy that actually takes effect.|

**Return value**

| Type  | Description                               |
| ------ | ----------------------------------- |
| Array&lt;[KeyEventPolicy](#keyeventpolicy23)&gt; | List of currently configured key event policies.|

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
import { systemManager } from '@kit.MDMKit';

let result: Array<systemManager.KeyEventPolicy> = [];
try {
  // Replace the parameters based on the actual situation.
  result = systemManager.getKeyEventPolicies(null);
  console.info('Succeeded in getting key event policies.');
} catch (err) {
  console.error(`Failed to get key event policies. Code is ${err.code}, message is ${err.message}`);
}
```
## systemManager.startCollectLog<sup>23+</sup>

startCollectLog(admin: Want): Promise&lt;void&gt;

Starts to collect faultlog logs of the [FaultType](../apis-performance-analysis-kit/js-apis-faultLogger.md#faulttype) type that have been generated on the device and stored on the hard disk. It does not support collecting faultlog logs that are not stored on the hard disk, application service logs, or system running logs. This API uses a promise to return the result.

- After the API is called, the system starts a log collection task. The API returns a response immediately after the task is started. The task may fail due to system performance constraints.
- Upon task completion, the MDM app is notified via the [EnterpriseAdminExtensionAbility.onLogCollected](js-apis-EnterpriseAdminExtensionAbility.md#onlogcollected23) callback. The system mounts the collected log files to the MDM app sandbox path, enabling the MDM app to read the logs within the callback.
- If the log collection task takes more than 5 minutes, the [EnterpriseAdminExtensionAbility.onLogCollected](js-apis-EnterpriseAdminExtensionAbility.md#onlogcollected23) callback returns a task execution failure message.
- After the app obtains the logs, you are advised to call [systemManager.finishLogCollected](#systemmanagerfinishlogcollected23) to remove the collected logs.

> **NOTE**
>
> In a multi-MDM application scenario, multiple MDM applications are allowed to call this API. Logs collected by different MDM applications under different users are stored separately and do not affect each other. Only one MDM application is allowed to start a log collection task at a time. If this API is called before the task is completed, error code 9201009 is returned. After the task is completed, other MDM applications are allowed to call this API.

**Required permissions**: ohos.permission.ENTERPRISE_READ_LOG

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices. If it is called on other device types, error code 801 is returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description                  |
| ------ | ------------------------------------------------------- | ---- | ---------------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|

**Return value**

| Type  | Description                               |
| ------ | ----------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. When a log collection task fails to be created, an error object is thrown.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9201009  | Collecting logs, please try again later. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { systemManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

systemManager.startCollectLog(wantTemp).then(() => {
  console.info('Succeeded in starting collect log');
}).catch((err: BusinessError) => {
  console.error(`Failed to start collect log. Code: ${err.code}, message: ${err.message}`);
});
```

## systemManager.finishLogCollected<sup>23+</sup>

finishLogCollected(admin: Want): void

Deletes the device logs collected by the current MDM app under the current user.

> **NOTE**
> 
> After an application calls [startCollectLog](#systemmanagerstartcollectlog23) to start collecting logs, when the [EnterpriseAdminExtensionAbility.onLogCollected](js-apis-EnterpriseAdminExtensionAbility.md#onlogcollected23) callback is received, it is recommended to copy or process the logs immediately and call this API to delete the collected logs.
> 
> If this API is not called, the device logs occupy system storage space, but this does not affect the next call to [startCollectLog](#systemmanagerstartcollectlog23) to start a log collection task.

**Required permissions**: ohos.permission.ENTERPRISE_READ_LOG

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices. If it is called on other device types, error code 801 is returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description                  |
| ------ | ------------------------------------------------------- | ---- | ---------------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|

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
import { Want } from '@kit.AbilityKit';
import { systemManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  systemManager.finishLogCollected(wantTemp);
  console.info('Succeeded in finishing log collected.');
} catch (err) {
  console.error(`Failed to finish log collected. Code is ${err.code}, message is ${err.message}`);
}
```

## systemManager.setActivationLockDisabled<sup>24+</sup>

setActivationLockDisabled(admin: Want, isDisabled: boolean, credential?: string): Promise&lt;void&gt;

Disables or enables the device activation lock. This API uses a promise to return the result. After the device activation lock is disabled, the Find Device feature cannot be used. This feature is applicable only to specific devices<!--RP5--><!--RP5End-->

> **NOTE**
>
> In a multi-MDM application scenario, the [configuration](../../mdm/mdm-kit-multi-mdm.md#rule-3-latest-configuration-precedence) rule is followed.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices. If it is called on other device types, error code 801 is returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description                  |
| ------ | ------------------------------------------------------- | ---- | ---------------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| isDisabled | boolean | Yes| Whether to disable the activation lock. The value **true** indicates yes, and the value **false** indicates no.|
| credential | string | No| Credential for disabling the activation lock. To disable the activation lock, you must set this parameter to a valid credential<!--RP6--><!--RP6End-->. Leave this parameter empty when enabling the activation lock.|

**Return value**

| Type  | Description                               |
| ------ | ----------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. An error object is thrown when the activation lock fails to be enabled or disabled.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 9200016  | Service timeout. |
| 9201011  | The credential of the activation lock is invalid. |
| 9201012  | Failed to enable or disable the activation lock. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { systemManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let credential: string = "XXX";
let isDisabled: boolean = true;
systemManager.setActivationLockDisabled(wantTemp, isDisabled, credential).then(() => {
  console.info('Succeeded in setting activation lock status.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set activation lock status. Code: ${err.code}, message: ${err.message}`);
});
```

## systemManager.isActivationLockDisabled<sup>24+</sup>

isActivationLockDisabled(admin: Want): Promise&lt;boolean&gt;

Obtains the disabled state of the device activation lock. This API uses a promise to return the result. It is applicable to scenarios where the state of the device activation lock feature needs to be verified, helping enterprise administrators confirm the security configuration of the device, especially when the activation lock state needs to be known during device transfer or recycling.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices. If it is called on other device types, error code 801 is returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description                  |
| ------ | ------------------------------------------------------- | ---- | ---------------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|

**Return value**

| Type                  | Description                     |
| --------------------- | ------------------------- |
| Promise&lt;boolean&gt; | Promise used to return whether the device activation lock is disabled. The value **true** indicates that the device activation lock is disabled and the Find Device function cannot be used. The value **false** indicates that the device activation lock is enabled and the Find Device function is available.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200016  | Service timeout. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { systemManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

systemManager.isActivationLockDisabled(wantTemp).then(result => {
  console.info(`Succeeded in getting activation lock status: ${JSON.stringify(result)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set activation lock status. Code: ${err.code}, message: ${err.message}`);
});
```

## systemManager.setInstallLocalEnterpriseAppEnabledForAccount<sup>24+</sup>

setInstallLocalEnterpriseAppEnabledForAccount(admin: Want, isEnable: boolean, accountId: number): void

Sets whether local installation of enterprise applications is supported for a specified user. After the policy of supporting local enterprise application installation is delivered to a PC/2-in-1 enterprise device that has the local installation capability, the user can double-click an enterprise application installation package on the desktop or in the Files application to install it.<!--RP8--><!--RP8End-->

Only enterprise applications signed with the **enterprise_normal** or **enterprise_mdm** signature type are supported.

> **NOTE**
>
> A PC/2-in-1 enterprise device supports local installation of enterprise applications for the current user if any of the following conditions is met:
>
> 1. The offline installer has been enabled through [setInstallLocalEnterpriseAppEnabled](#systemmanagersetinstalllocalenterpriseappenabled20).
> 2. The current user has been set to support local installation of enterprise applications through this API.
>
> 3. In a multi-MDM application scenario, the [strictest control](../../mdm/mdm-kit-multi-mdm.md#rule-1-security-first) rule is followed. If any MDM application sets support for local installation of enterprise applications, the combined policy is to support local installation of enterprise applications.
<!--RP7--><!--RP7End-->

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices but returns error code 801 on other devices.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type                                 | Mandatory | Description|
| ----- | ----------------------------------- | ---- | ------- |
| admin | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes| EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| isEnable | boolean | Yes| Whether local installation of enterprise applications is supported. The value **true** indicates that the local installation of enterprise applications is supported, and the value **false** indicates the opposite.|
| accountId | number                                                 | Yes  | User ID, which must be greater than or equal to 0.<br>**accountId** can be obtained via APIs such as [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1).|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                     |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device. |
| 9200002 | The administrator application does not have permission to manage the device. |
| 9200012 | Parameter verification failed. |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 801     | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts

import { systemManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let isEnable: boolean = true;
let accountId: number = 100;
try {
  systemManager.setInstallLocalEnterpriseAppEnabledForAccount(wantTemp, isEnable, accountId);
  console.info('Succeeded in setting InstallLocalEnterpriseAppEnabledForAccount.');
} catch (err) {
  console.error(`Failed to set installLocalEnterpriseAppEnabledForAccount. Code is ${err.code}, message is ${err.message}`);
}
```

## systemManager.getInstallLocalEnterpriseAppEnabledForAccount<sup>24+</sup>

getInstallLocalEnterpriseAppEnabledForAccount(admin: Want | null, accountId: number): boolean

Queries whether a specified user supports local installation of enterprise applications. It is applicable to scenarios where the state of the local installation of enterprise applications feature for a specific user needs to be verified, helping enterprise administrators confirm the policy configuration state and ensure that users can install enterprise applications normally.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices but returns error code 801 on other devices.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description                  |
| ------ | ------------------------------------------------------- | ---- | ---------------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.<br>If the device has multiple MDM applications, you can pass **admin** to query the corresponding policies. If **null** is passed, the policies that actually take effect on the device are returned.|
| accountId | number                                                 | Yes  | User ID, which must be greater than or equal to 0.<br>**accountId** can be obtained via APIs such as [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1).|

**Return value**

| Type  | Description                               |
| ------ | ----------------------------------- |
| boolean | Whether local installation of enterprise applications is supported. The value **true** indicates that local installation is supported, and the value **false** indicates the opposite. When **admin** is set to **null**, this API checks whether local installation of enterprise applications is supported.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012 | Parameter verification failed. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { systemManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let accountId: number = 100;
try {
  let isEnable: boolean = systemManager.getInstallLocalEnterpriseAppEnabledForAccount(wantTemp, accountId);
  console.info('Succeeded in getting installLocalEnterpriseAppEnabled.');
} catch (err) {
  console.error(`Failed to get installLocalEnterpriseAppEnabled. Code is ${err.code}, message is ${err.message}`);
}
```

## systemManager.addAllowedPrinterIPAddressesForDevice

addAllowedPrinterIPAddressesForDevice(ipAddresses: Array&lt;string&gt;): void

Adds an IP-based network printer whitelist policy for the current device. After this policy is set, only network printers whose IP addresses are in the whitelist are allowed to print, and network printers not in the whitelist cannot print. Before calling this API, you can call [common.isFeatureSupported](./js-apis-enterprise-common.md#commonisfeaturesupported) (with common.ManagedFeature.PRINTER_IP_ADDRESS_POLICY as the input parameter) to check whether the device supports the printer IP address policy feature.
- If the whitelist has been set through [addAllowedPrinterIPAddressesForAccount](#systemmanageraddallowedprinteripaddressesforaccount) before this API is called, a policy conflict (9200010) is reported.
- If the printer function has been disabled through [restrictions.setDisallowedPolicy](js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicydeprecated) or the printing function of the current user has been disabled through [restrictions.setDisallowedPolicyForAccount](js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicyforaccountdeprecated), the policy can still be set successfully when this API is called, but the printing function remains disabled.
- After the whitelist is added for the device, you can remove it through [removeAllowedPrinterIPAddressesForDevice](#systemmanagerremoveallowedprinteripaddressesfordevice). When the whitelist is empty, all network printers are not governed by this policy.

> **NOTE**
>
> In a multi-MDM application scenario, the [merge](../../mdm/mdm-kit-multi-mdm.md#rule-4-policy-merging) rule is followed.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences** This interface can be called normally on PC/2-in-1 devices, and returns error code 801 on other devices.

**Model restriction:** This interface can be used only in the stage model.

**Parameters**

| Name   | Type                                                    | Mandatory | Description                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| ipAddresses  | Array&lt;string&gt;               | Yes   | IP addresses (IPv4 and IPv6; only complete standard-format addresses are allowed). A maximum of 100 IP addresses can be set (if 60 IP addresses have already been set in the whitelist, at most 40 more can be set). |


**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).


| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200010  | A conflict policy has been configured.|
| 9200012  | Parameter verification failed. |
| 9200016  | Service timeout. |
| 9200019  | The policy list has exceeded the limit. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |


**Example**

```ts
import { common, systemManager } from '@kit.MDMKit';

// Replace it based on the actual situation.
const ipArray: Array<string> = ['192.1.1.1', '2001:0db8:0000:0000:0000:0000:1428:57ab'];
// Before calling this API, query whether the device supports the printer IP address policy feature.
let isSupported: boolean = common.isFeatureSupported(common.ManagedFeature.PRINTER_IP_ADDRESS_POLICY);
if (isSupported) {
  try {
    systemManager.addAllowedPrinterIPAddressesForDevice(ipArray);
    console.info('Succeeded in adding the allowed printer IP Addresses for the device.');
  } catch (err) {
    console.error(`Failed to add the allowed printer IP Addresses for the device. Code is ${err.code}, message is ${err.message}`);
  }
} else {
  console.info('The printer IP address policy feature is not supported.');
}
```

## systemManager.removeAllowedPrinterIPAddressesForDevice

removeAllowedPrinterIPAddressesForDevice(ipAddresses: Array&lt;string&gt;): void

Removes network printers from the whitelist managed based on IP for the current device. After successful removal, when the whitelist is empty, no network printer is governed by this policy; when the whitelist is not empty, network printers whose IP addresses have been removed from the whitelist cannot print. Before calling this API, you can call [common.isFeatureSupported](./js-apis-enterprise-common.md#commonisfeaturesupported) (with common.ManagedFeature.PRINTER_IP_ADDRESS_POLICY as the input parameter) to check whether the device supports the printer IP address policy feature.

> **NOTE**
>
> In the multi-MDM application scenario, the [merge](../../mdm/mdm-kit-multi-mdm.md#rule-4-policy-merging) rule is followed.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences:** This API can be called normally on PC/2-in-1 devices, and returns error code 801 on other devices.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name   | Type                                                    | Mandatory | Description                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| ipAddresses  | Array&lt;string&gt;               | Yes   | IP address (IPv4 and IPv6; only complete standard-format addresses are allowed). |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. | 
| 9200012  | Parameter verification failed. |
| 9200016  | Service timeout. |                
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { common, systemManager } from '@kit.MDMKit';

// Replace it based on the actual situation.
const ipArray: Array<string> = ['192.1.1.1', '2001:0db8:0000:0000:0000:0000:1428:57ab'];
// Before calling this API, query whether the device supports the printer IP address policy feature.
let isSupported: boolean = common.isFeatureSupported(common.ManagedFeature.PRINTER_IP_ADDRESS_POLICY);
if (isSupported) {
  try {
    systemManager.removeAllowedPrinterIPAddressesForDevice(ipArray);
    console.info('Succeeded in removing the allowed printer IP Addresses for the device.');
  } catch (err) {
    console.error(`Failed to remove the allowed printer IP Addresses for the device. Code is ${err.code}, message is ${err.message}`);
  }
} else {
  console.info('The printer IP address policy feature is not supported.');
}
```

## systemManager.getAllowedPrinterIPAddressesForDevice

getAllowedPrinterIPAddressesForDevice(queryPolicy?: common.QueryPolicy): Array&lt;string&gt;

Obtains the whitelist of network printers managed based on IP addresses on the device.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences:** This interface can normally return the whitelist array on PC/2-in-1 devices, and returns an empty array on other devices.

**Model restriction:** This interface can be used only in the stage model.

**Parameters**

| Name  | Type                                                    | Mandatory | Description                                                         |
| ------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| queryPolicy   | [common.QueryPolicy](js-apis-enterprise-common.md#querypolicy) | No   | Policy to obtain. The type can be SELF or ALL. If this parameter is not passed, it is equivalent to SELF.                                   |

**Return value**

| Type    | Description                                                         |
| ------- | ------------------------------------------------------------ |
| Array&lt;string&gt;          | Whitelist of network printers managed based on IP addresses. |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200016  | Service timeout. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { common, systemManager } from '@kit.MDMKit';

try {
  let result: string[] = systemManager.getAllowedPrinterIPAddressesForDevice(common.QueryPolicy.ALL);
  console.info(`Succeeded in querying the allowed printer IP Addresses for the device.`);
} catch (err) {
  console.error(`Failed to query the allowed printer IP Addresses for the device. Code is ${err.code}, message is ${err.message}`);
}
```
## systemManager.addAllowedPrinterIPAddressesForAccount

addAllowedPrinterIPAddressesForAccount(ipAddresses: Array&lt;string&gt;): void

Adds an IP-based network printer allowlist policy for the current user. After this policy is set, only network printers whose IP addresses are in the allowlist are allowed to print, and network printers whose IP addresses are not in the allowlist cannot print. Before calling this API, you can call [common.isFeatureSupported](./js-apis-enterprise-common.md#commonisfeaturesupported) (with the input parameter common.ManagedFeature.PRINTER_IP_ADDRESS_POLICY) to check whether the device supports the printer IP address policy feature.
- If this API is called after the allowlist has been set through [addAllowedPrinterIPAddressesForDevice](#systemmanageraddallowedprinteripaddressesfordevice), a policy conflict (9200010) is reported.
- If this API is called after the printer function has been disabled through [restrictions.setDisallowedPolicy](js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicydeprecated) or the printing function of the current user has been disabled through [restrictions.setDisallowedPolicyForAccount](js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicyforaccountdeprecated), the policy can be set successfully, but the printing function remains disabled.
- After the allowlist is added for the current user, you can remove it through [removeAllowedPrinterIPAddressesForAccount](#systemmanagerremoveallowedprinteripaddressesforaccount). When the allowlist is empty, all network printers are not governed by this policy.
- If you need to add an IP-based network printer allowlist policy for the current device, refer to [addAllowedPrinterIPAddressesForDevice](#systemmanageraddallowedprinteripaddressesfordevice).

> **NOTE**
>
> In multi-MDM application scenarios, the [merge](../../mdm/mdm-kit-multi-mdm.md#rule-4-policy-merging) rule is followed.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences:** This interface can be normally called on PC/2in1 devices, and returns error code 801 on other devices.

**Model restriction:** This interface can only be used in the Stage model.


**Parameters:**

| Name   | Type                                                    | Mandatory | Description                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| ipAddresses  | Array&lt;string&gt;               | Yes   | IP addresses (IPv4 and IPv6, only complete standard-format addresses are allowed). A maximum of 100 IP addresses can be set (if 60 IP addresses have already been set in the whitelist, at most 40 more can be set).|


**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).


| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200010  | A conflict policy has been configured.|
| 9200012  | Parameter verification failed. |
| 9200016  | Service timeout. |
| 9200019  | The policy list has exceeded the limit. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |


**Example**

```ts
import { common, systemManager } from '@kit.MDMKit';

// Replace it based on the actual situation.
const ipArray: Array<string> = ['192.1.1.1', '2001:0db8:0000:0000:0000:0000:1428:57ab'];

// Before calling this API, query whether the device supports the printer IP address policy feature.
let isSupported: boolean = common.isFeatureSupported(common.ManagedFeature.PRINTER_IP_ADDRESS_POLICY);
if (isSupported) {
  try {
    systemManager.addAllowedPrinterIPAddressesForAccount(ipArray);
    console.info('Succeeded in adding the allowed printer IP Addresses for current user.');
  } catch (err) {
    console.error(`Failed to add the allowed printer IP Addresses for current user. Code is ${err.code}, message is ${err.message}`);
  }
} else {
  console.info('The printer IP address policy feature is not supported.');
}
```

## systemManager.removeAllowedPrinterIPAddressesForAccount

removeAllowedPrinterIPAddressesForAccount(ipAddresses: Array&lt;string&gt;): void

Removes network printers from the whitelist managed based on IP for the current user. After successful removal, when the whitelist is empty, no network printer is subject to this policy; when the whitelist is not empty, network printers whose IP addresses have been removed from the whitelist cannot print. Before calling this API, you can call [common.isFeatureSupported](./js-apis-enterprise-common.md#commonisfeaturesupported) (with common.ManagedFeature.PRINTER_IP_ADDRESS_POLICY as the input parameter) to check whether the device supports the printer IP address policy feature.

> **NOTE**
>
> In a multi-MDM application scenario, the [merge](../../mdm/mdm-kit-multi-mdm.md#rule-4-policy-merging) rule is followed.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences:** This API can be called normally on PC/2-in-1 devices, and returns error code 801 on other devices.

**Model restriction:** This API can be used only in the stage model.


**Parameters**

| Name   | Type                                                    | Mandatory | Description                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| ipAddresses  | Array&lt;string&gt;               | Yes   | IP address (IPv4 and IPv6; only complete standard-format addresses are allowed). |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. | 
| 9200012  | Parameter verification failed. | 
| 9200016  | Service timeout. |               
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { common, systemManager } from '@kit.MDMKit';

// Replace it based on the actual situation.
const ipArray: Array<string> = ['192.1.1.1', '2001:0db8:0000:0000:0000:0000:1428:57ab'];
// Before calling this API, query whether the device supports the printer IP address policy feature.
let isSupported: boolean = common.isFeatureSupported(common.ManagedFeature.PRINTER_IP_ADDRESS_POLICY);
if (isSupported) {
  try {
    systemManager.removeAllowedPrinterIPAddressesForAccount(ipArray);
    console.info('Succeeded in removing the allowed printer IP Addresses for current user.');
  } catch (err) {
    console.error(`Failed to remove the allowed printer IP Addresses for current user. Code is ${err.code}, message is ${err.message}`);
  }
} else {
  console.info('The printer IP address policy feature is not supported.');
}
```

## systemManager.getAllowedPrinterIPAddressesForAccount

getAllowedPrinterIPAddressesForAccount(queryPolicy?: common.QueryPolicy): Array&lt;string&gt;

Obtains the whitelist of network printers managed by IP for the current user.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences** This interface can normally return the whitelist array on PC/2-in-1 devices, and returns an empty array on other devices.

**Model restriction:** This interface can be used only in the stage model.

**Parameters**

| Name  | Type                                                    | Mandatory | Description                                                         |
| ------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| queryPolicy   | [common.QueryPolicy](js-apis-enterprise-common.md#querypolicy) | No   | Policy to obtain. The type is SELF or ALL. If not passed, it is equivalent to SELF.                                   |

**Return value**

| Type    | Description                                                         |
| ------- | ------------------------------------------------------------ |
| Array&lt;string&gt;          | Whitelist of network printers managed based on IP for the current user. |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200016  | Service timeout. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { common, systemManager } from '@kit.MDMKit';

try {
  let result: string[] = systemManager.getAllowedPrinterIPAddressesForAccount(common.QueryPolicy.SELF);
  console.info(`Succeeded in querying the allowed printer IP Addresses for current user.`);
} catch (err) {
  console.error(`Failed to query the allowed printer IP Addresses for current user. Code is ${err.code}, message is ${err.message}`);
}
```

## systemManager.createExactTimer

createExactTimer(config: ExactTimerConfig): Promise&lt;number&gt;

Creates an exact timer. This API is applicable to scenarios where an enterprise device needs to execute tasks at precise times, such as scheduled inspection, scheduled data reporting, and scheduled policy delivery, helping enterprise administrators automate the scheduled execution of device tasks. This API uses a promise to return the result asynchronously.

> **NOTE**
>
> 1. This API must be used together with [systemManager.destroyExactTimer](#systemmanagerdestroyexacttimer); otherwise, memory leaks may occur.
>
> 2. When the device management application is deactivated or its process is terminated, the EDM service automatically destroys all timers created by the device management application.
>
> 3. If the name of the timer to be created is the same as that of an existing timer, the previous timer with the same name is automatically stopped and destroyed, and the newly created timer is assigned a new timer ID that differs from the ID of the destroyed timer.
>
> 4. A single device management application can create at most 5 timers that take effect simultaneously. When the upper limit is exceeded, error code 9201053 is returned.
>
> 5. When an application process runs in the background for a long time, it may be frozen or terminated by the system, causing the timer to be destroyed. You can call [addFreezeExemptedApps](./js-apis-enterprise-applicationManager.md#applicationmanageraddfreezeexemptedapps22) to add the application to the freeze-exemption list to avoid this issue.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences:** This API can be called normally on Phone and Tablet devices, and returns error code 801 on other devices.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type                                                    | Mandatory | Description                   |
| ------ | ------------------------------------------------------- | ---- | ---------------------- |
| config  | [ExactTimerConfig](#exacttimerconfig) | Yes   | Initial configuration of the timer, including whether it is a repeating timer, the trigger interval, the callback, and the name. |

**Return value**

| Type   | Description                                |
| ------ | ----------------------------------- |
| Promise&lt;number&gt; | Promise object that returns the timer ID. |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 9200016  | Service timeout. |
| 9201053  | The number of timers has reached the upper limit. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { systemManager } from '@kit.MDMKit';
import { BusinessError } from '@kit.BasicServicesKit';

let config: systemManager.ExactTimerConfig = {
  name: 'timer1',
  repeat: true,
  interval: 5000,
  callback: () => {
    console.info('Timer expired.');
  }
};
systemManager.createExactTimer(config).then((timerId: number) => {
  console.info(`Succeeded in creating exact timer, timerId: ${timerId}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to create exact timer. Code: ${err.code}, message: ${err.message}`);
});
```

## systemManager.startExactTimer

startExactTimer(timer: number, triggerTime: number): Promise&lt;void&gt;

Starts an exact timer. When the timer expires, the callback configured when the timer was created is triggered. For a repeating timer, after the trigger time is reached, the callback is triggered periodically at the configured interval. For a one-shot timer, the callback is triggered once after the trigger time is reached. This API is applicable to the scenario of starting scheduled tasks. This API uses a promise to return the result asynchronously.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences:** This interface can be called normally on Phone and Tablet devices, and returns error code 801 on other devices.

**Model restriction:** This interface can be used only in the stage model.

**Parameters**

| Name | Type                                                    | Mandatory | Description                   |
| ------ | ------------------------------------------------------- | ---- | ---------------------- |
| timer  | number | Yes   | Timer ID, obtained through [systemManager.createExactTimer](#systemmanagercreateexacttimer). |
| triggerTime  | number | Yes   | Timer trigger time, in milliseconds. This value is the elapsed time since system startup at the target trigger moment. It must be the elapsed time since the current system startup plus the expected delay. For example, to trigger the timer after 5 seconds, obtain the elapsed time since the current system startup through [systemDateTime.getUptime](../apis-basic-services-kit/js-apis-date-time.md#systemdatetimegetuptime10) (passing in [TimeType.STARTUP](../apis-basic-services-kit/js-apis-date-time.md#timetype10)), and then add 5s. |

**Return value**

| Type   | Description                                |
| ------ | ----------------------------------- |
| Promise&lt;void&gt; | Promise object that returns no result. If the timer fails to start, an error object is thrown. |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 9200016  | Service timeout. |
| 9201054  | The specified timer does not exist or does not belong to the current administrator. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { systemManager } from '@kit.MDMKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { systemDateTime } from '@kit.BasicServicesKit';

// Replace it based on the actual situation. The timerId is obtained from the createExactTimer API.
let timerId: number = 1;
// Trigger the timer after 10 seconds.
let triggerTime: number = systemDateTime.getUptime(systemDateTime.TimeType.STARTUP) + 10000;
systemManager.startExactTimer(timerId, triggerTime).then(() => {
  console.info('Succeeded in starting exact timer.');
}).catch((err: BusinessError) => {
  console.error(`Failed to start exact timer. Code: ${err.code}, message: ${err.message}`);
});
```

## systemManager.stopExactTimer

stopExactTimer(timer: number): Promise&lt;void&gt;

Stops an exact timer. After the timer is stopped, its callback will no longer be triggered, but the timer resources will not be released. The timer can be restarted through the [systemManager.startExactTimer](#systemmanagerstartexacttimer) API. This API is applicable to the scenario of pausing a scheduled task. This API uses a promise to return the result asynchronously.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences** This API can be called normally on phones and tablets, and returns error code 801 on other devices.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type                                                    | Mandatory | Description                   |
| ------ | ------------------------------------------------------- | ---- | ---------------------- |
| timer  | number | Yes   | Timer ID, obtained through the [systemManager.createExactTimer](#systemmanagercreateexacttimer) API. |

**Return value**

| Type   | Description                                |
| ------ | ----------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. If stopping the timer fails, an error object is thrown. |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200016  | Service timeout. |
| 9201054  | The specified timer does not exist or does not belong to the current administrator. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { systemManager } from '@kit.MDMKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Replace it based on the actual situation. The timerId is obtained from the createExactTimer API.
let timerId: number = 1;
systemManager.stopExactTimer(timerId).then(() => {
  console.info('Succeeded in stopping exact timer.');
}).catch((err: BusinessError) => {
  console.error(`Failed to stop exact timer. Code: ${err.code}, message: ${err.message}`);
});
```

## systemManager.destroyExactTimer

destroyExactTimer(timer: number): Promise&lt;void&gt;

Destroys an exact timer. After the timer is destroyed, its resources are released and its ID becomes invalid, so it can no longer be used to start or stop the timer. This API is applicable to scenarios where the timer task is no longer needed, helping enterprise administrators release system resources in a timely manner. This API uses an asynchronous callback to return the result.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences:** This interface can be called normally on Phone and Tablet devices, and returns error code 801 on other devices.

**Model restriction:** This interface can be used only in the stage model.

**Parameters**

| Name | Type                                                    | Mandatory | Description                   |
| ------ | ------------------------------------------------------- | ---- | ---------------------- |
| timer  | number | Yes   | Timer ID, obtained by [systemManager.createExactTimer](#systemmanagercreateexacttimer). |

**Return value**

| Type   | Description                                |
| ------ | ----------------------------------- |
| Promise&lt;void&gt; | Promise object that returns no result. Throws an error object if the timer fails to be destroyed. |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200016  | Service timeout. |
| 9201054  | The specified timer does not exist or does not belong to the current administrator. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { systemManager } from '@kit.MDMKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Replace it based on the actual situation. The timerId is obtained from the createExactTimer API.
let timerId: number = 1;
systemManager.destroyExactTimer(timerId).then(() => {
  console.info('Succeeded in destroying exact timer.');
}).catch((err: BusinessError) => {
  console.error(`Failed to destroy exact timer. Code: ${err.code}, message: ${err.message}`);
});
```

## systemManager.setVolumeDegree

setVolumeDegree(volumeType: AudioVolumeType, degree: number): void

Sets the volume of the specified volume type for the current user. This API is applicable to the scenario where an enterprise uniformly manages device volume, for example, adjusting the media playback volume of terminal devices in batches.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can be used only in the stage model.

**Parameters**

| Name       | Type                                 | Mandatory | Description                                                         |
| ---------- | ------------------------------------ | --------- | ------------------------------------------------------------ |
| volumeType | [AudioVolumeType](#audiovolumetype) | Yes       | Volume type. |
| degree     | number                               | Yes       | Volume value, ranging from 0 to 100. If the value is out of this range, error code 9200012 is returned. When earphones are worn, due to safety regulations, if the set value exceeds the maximum value required by the current device safety regulations, the value is set to the maximum value required by the current safety regulations, and a system dialog box is triggered to remind the user. For PC/2-in-1 devices, this dialog box is not displayed. |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                |
| ------------- | ------------------------------------------------------------ |
| 201           | Permission verification failed. The application does not have the permission required to call the API. |
| 9200001       | The application is not an administrator application of the device. |
| 9200002       | The administrator application does not have permission to manage the device. |
| 9200012       | Parameter verification failed.                               |
| 9200016       | Service timeout.                                             |

**Example**

```ts
import { systemManager } from '@kit.MDMKit';

// Replace it based on the actual situation.
let volumeType: systemManager.AudioVolumeType = systemManager.AudioVolumeType.STREAM_MUSIC;
let degree: number = 50;
try {
  systemManager.setVolumeDegree(volumeType, degree);
  console.info('Succeeded in setting volume degree.');
} catch (err) {
  console.error(`Failed to set volume degree. Code is ${err.code}, message is ${err.message}`);
}
```

## systemManager.getVolumeDegree

getVolumeDegree(volumeType: AudioVolumeType): number

Obtains the volume of the specified volume type for the current user. This is applicable to the scenario where an enterprise device management application confirms the current volume state of the device before delivering a volume policy.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| ---------- | ------------------------------------ | ---- | ------------------------------------------------------------ |
| volumeType | [AudioVolumeType](#audiovolumetype) | Yes | Volume type. |

**Return value**

| Type   | Description                                                         |
| ------ | ------------------------------------------------------------ |
| number | Volume value of the specified volume type. The value ranges from 0 to 100.                     |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed.                               |
| 9200016  | Service timeout.                                             |

**Example**

```ts
import { systemManager } from '@kit.MDMKit';

// Replace it based on the actual situation.
let volumeType: systemManager.AudioVolumeType = systemManager.AudioVolumeType.STREAM_MUSIC;
try {
  let degree: number = systemManager.getVolumeDegree(volumeType);
  console.info(`Succeeded in getting volume degree, degree is ${degree}.`);
} catch (err) {
  console.error(`Failed to get volume degree. Code is ${err.code}, message is ${err.message}`);
}
```

## SystemUpdateInfo

Represents information about the system version to update.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can be used only in the stage model.

| Name               | Type    | Read-Only | Optional| Description           |
| ----------------- | ------ | --- | --- |------------- |
| versionName       | string | No  | No|System version to update.  |
| firstReceivedTime | number | No  | No|Time when the system update package is received for the first time, in seconds.|
| packageType       | string | No  | No|Type of the system update package to update. The value can be **normal** or **patch**. |

## OtaUpdatePolicy

Represents an OTA update policy.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can be used only in the stage model.

| Name        | Type    | Read-Only| Optional| Description                           |
| ----------- | --------| ---- | -----| -------------------------- |
| policyType        | [PolicyType](#policytype)   | No  | No| Type of the update policy.|
| version | string   | No  | No|Version of the software to update.|
| latestUpdateTime        | number   | No  | Yes| Latest update time (timestamp).|
| delayUpdateTime | number   | No  | Yes| Period for which the update is postponed, in hours.|
| installStartTime        | number   | No  | Yes| Start time (timestamp) of the installation window.|
| installEndTime | number   | No  | Yes| End time (timestamp) of the installation window.|
| disableSystemOtaUpdate<sup>20+</sup> | boolean   | No  | Yes| Whether to disable public network upgrade. The value **true** indicates that public network upgrade is disabled, and the value **false** indicates the opposite. If this field is used as an input parameter of [systemManager.setOtaUpdatePolicy](#systemmanagersetotaupdatepolicy), the default value can be retained. The current configuration can be obtained via the [systemManager.getOtaUpdatePolicy](#systemmanagergetotaupdatepolicy) API. After public network upgrade is disabled, you can perform intranet upgrade.<!--RP4--><!--RP4End--> |

## PolicyType

Enumerates the update policy types.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can be used only in the stage model.

| Name               | Value | Description   |
| ----------------- | ---- | ----- |
| DEFAULT | 0 | Default upgrade policy. Periodically reminds the user to upgrade through a dialog box. The period starts from 24 hours and gradually extends. |
| PROHIBIT  | 1 | Prohibit updates.|
| UPDATE_TO_SPECIFIC_VERSION | 2 | Forced upgrade policy. The latest update time (latestUpdateTime) parameter must be specified. 1. If the device is not upgraded when the time remaining before the latest update time is more than 48 hours, a reminder dialog box appears once every 24 hours. 2. If the device is not upgraded when the time remaining before the latest update time is less than 48 hours, a reminder to install the upgrade appears periodically every X hours. The message is displayed in the notification center and cannot be removed. 3. If the device is still not upgraded after the latest update time, a forced upgrade reminder appears during idle time.  |
| WINDOWS | 3 | Upgrade policy within a specified time window. The time window parameters (installStartTime and installEndTime) must be specified. The time window must be longer than 5 minutes. 1. Configure the time window [A, B], obtain a random upgrade time C within the window, and automatically upgrade when the idle condition is met at time C. 2. Configure the time window [A, B], obtain a random upgrade time C within the window. If the idle condition is not met at time C and B - C is more than half an hour, refresh a random time D between C and B, and automatically upgrade when the idle condition is met at time D. 3. Configure the time window [A, B], obtain a random upgrade time C within the window. If the idle condition is not met at time C and B - C is more than half an hour, refresh a random time D between C and B. If the idle condition is not met at time D, check again after 24 hours, that is, postpone the window task to the next [A, B] window. 4. Configure the time window [A, B], obtain a random upgrade time C within the window. If the idle condition is not met at time C and B - C is less than or equal to half an hour, check again after 24 hours, that is, postpone the window task to the next [A, B] window. |
| POSTPONE | 4 | Postpone updates. After the time specified by **delayUpdateTime** is over, the default update policy is used.|

## UpdatePackageInfo

Represents information about the system update packages.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can be used only in the stage model.

| Name               | Type    | Read-Only | Optional| Description           |
| ----------------- | ------ | --- | ---- |------------- |
| version       | string | No  | No| Version of the system update package.  |
| packages | Array&lt;[Package](#package)&gt; | No  | No| Details about the system update packages.|
| description       | [PackageDescription](#packagedescription) | No  | Yes| Description of the system update packages. |
| authInfo<sup>19+</sup> | string | No| Yes| Authentication information of the system update package.|

## Package

Represents the details about a system update package.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can be used only in the stage model.

| Name               | Type    | Read-Only | Optional| Description           |
| ----------------- | ------ | --- | --- | ------------- |
| type       | [PackageType](#packagetype) | No  | No|  Type of the system update package.  |
| path | string | No  | No| Path of the system update package. If **fd** is specified, pass in the update package name here.|
| fd       | number | No  | Yes| File descriptor (FD) of the system update package. Currently, you cannot pass in **path** only. The **fd** parameter must also be passed in. |

## PackageDescription

Represents the description of a system update package.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can only be used in the Stage model.

| Name               | Type    | Read-Only | Optional| Description           |
| ----------------- | ------ | --- | --- | ------------- |
| notify       | [NotifyDescription](#notifydescription) | No  | Yes| Update notification defined by an enterprise.  |

## NotifyDescription

Represents the update notification defined by an enterprise.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can only be used in the Stage model.

| Name               | Type    | Read-Only |  Optional| Description           |
| ----------------- | ------ | --- | ---- | ------------- |
| installTips       | string | No  | Yes| Update tips provided by the enterprise.  |
| installTipsDetail       | string | No  | Yes| Details about the update tips customized by the enterprise.  |

## UpdateResult

Represents the update result information.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can only be used in the Stage model.

| Name               | Type  | Read-Only | Optional  | Description           |
| ----------------- | ------ | ------ | ------ | ------------- |
| version       | string |  No| No|Current version of the system.  |
| status       | [UpdateStatus](#updatestatus) | No| No| System update status.  |
| errorInfo       | [ErrorInfo](#errorinfo) | No| No| Error information.  |

## ErrorInfo

Represents the update error information.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can only be used in the Stage model.

| Name               | Type    | Read-Only | Optional| Description           |
| ----------------- | ------ | ------ | ------ | ------------- |
| code       | number | No| No| Error code.  |
| message       | string | No| No| Error message.  |

## PackageType

Enumerates the update package types.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can only be used in the Stage model.

| Name               | Value | Description   |
| ----------------- | ---- | ----- |
| FIRMWARE | 1 | Firmware.|

## UpdateStatus

Enumerates the system update statuses.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can only be used in the Stage model.

| Name              | Value | Description   |
| -----------------  | ---- | ----- |
| NO_UPDATE_PACKAGE  | -4 | The system update package of the specified version does not exist.|
| UPDATE_WAITING     | -3 | The system update package is waiting to be installed.|
| UPDATING           | -2 | The system update is being performed.|
| UPDATE_FAILURE     | -1 | The update failed.|
| UPDATE_SUCCESS     | 0 | The update is successful.|

## NearLinkProtocol<sup>20+</sup>

Enumerates NearLink protocols.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

| Name              | Value | Description   |
| -----------------  | ---- | ----- |
| SSAP   | 0 |  SparkLink Service Access Protocol (SSAP).<!--RP1--><!--RP1End--> |
| DATA_TRANSFER      | 1 | Data transfer protocol.<!--RP2--><!--RP2End--> |

## KeyEventPolicy<sup>23+</sup>

Enumerates key event handling policies. When a key event occurs, only the keys for which the key event handling policy has been delivered are intercepted. For key events where no handling policy has been delivered, the system executes its original response logic.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

| Name               | Type    | Read-Only | Optional| Description           |
| ----------------- | ------ | ------ | ------ | ------------- |
| keyCode       | [KeyCode](#keycode23) | No| No| Key code.  |
| keyPolicy       | [KeyPolicy](#keypolicy23) | No| No| Key policy.  |

## KeyCode<sup>23+</sup>

Key code. The [addKeyEventPolicies](#systemmanageraddkeyeventpolicies23), [removeKeyEventPolicies](#systemmanagerremovekeyeventpolicies23), [getKeyEventPolicies](#systemmanagergetkeyeventpolicies23), and [onKeyEvent](js-apis-EnterpriseAdminExtensionAbility.md#onkeyevent23) APIs map key codes to the corresponding physical keys on the device.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

| Name              | Value | Description   |
| -----------------  | ---- | ----- |
| POWER    | 0 |  Power key|
| VOLUME_UP       | 1 | Volume up|
| VOLUME_DOWN       | 2 | Volume down|
| BACK       | 3 | Navigation key - back|
| HOME       | 4 | Navigation key - home|
| RECENT       | 5 | Navigation key - recently opened|

## KeyPolicy<sup>23+</sup>

Enumerates key policies. This refers to the system behavior triggered after the key code delivered by the MDM app matches the system key event.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

| Name              | Value | Description   |
| -----------------  | ---- | ----- |
| INTERCEPTION     | 0 |  Intercepts messages. After this parameter is set, only the current key event is intercepted. The system does not process the event, and the key callback API does not respond to the key event. For example, after the power key interception policy is delivered, pressing the power key does not respond, the device cannot be powered off or locked, and only the power key event in the power-on state is affected. When the device is powered off, the power key can be used to power on the device.|
| CUSTOM        | 1 | Intercepts and forwards messages. When this policy is configured, the system intercepts the current key event and does not process the event. In addition, the [EnterpriseAdminExtensionAbility.onKeyEvent](js-apis-EnterpriseAdminExtensionAbility.md#onkeyevent23) callback API is used to notify the MDM app of the key event, which does not block the processing of other events.|

## KeyEvent<sup>23+</sup>

Enumerates key events. When the [EnterpriseAdminExtensionAbility.onKeyEvent](js-apis-EnterpriseAdminExtensionAbility.md#onkeyevent23) key event callback is triggered, the current key event information is transferred.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

| Name               | Type    | Read-Only | Optional| Description           |
| ----------------- | ------ | ------ | ------ | ------------- |
| keyCode       | [KeyCode](#keycode23) | No| No| Key code.  |
| keyAction       | [KeyAction](#keyaction23) | No| No| Key action.  |
| actionTime       | number | No| No| Time when the key action occurs. The value is a microsecond-level timestamp after the system is powered on. For long-press key events, this parameter remains unchanged in subsequent key events. Apps can use this timestamp to determine whether the event is a long-press event and execute the corresponding long-press event logic accordingly.  |
| keyItems       | Array&lt;[KeyItem](#keyitem23)&gt; | No| No| Information about other keys that are being pressed when the current key event occurs.  |

## KeyAction<sup>23+</sup>

Enumerates key actions.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

| Name              | Value | Description   |
| -----------------  | ---- | ----- |
| UNKNOWN      | -1 |  Any key action other than press and release.|
| DOWN         | 0 | Key press.|
| UP          | 1 | Key release.|

## KeyItem<sup>23+</sup>

Enumerates other key information. This refers to the information of other keys that have been pressed when the current [KeyCode](#keycode23) event occurs.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

| Name               | Type    | Read-Only | Optional| Description           |
| ----------------- | ------ | ------ | ------ | ------------- |
| keyCode       | [KeyCode](#keycode23) | No| No| Key code.  |
| pressed       | boolean  | No| No| Key action. It indicates whether the key is pressed: **true** for pressed; **false** for released. |
| downTime      | number | No| No| Time when the key action occurs. The value is a microsecond-level timestamp after the system is powered on. Navigation keys do not support combination expansion, so their occurrence time is displayed as 0.|

## ExactTimerConfig

Defines the initialization configuration of an exact timer. It serves as the input parameter of [systemManager.createExactTimer](#systemmanagercreateexacttimer) and is used to configure the timer name, whether to trigger cyclically, the trigger interval, and the expiration callback.

**Since:** 26.0.1

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can be used only in the Stage model.

### Attributes

**Since:** 26.0.1

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can be used only in the stage model.

| Name                | Type     | Read-only  | Optional | Description            |
| ----------------- | ------ | ------ | ------ | ------------- |
| name       | string | No | No | Timer name. The maximum length is 64 bytes and it cannot be empty.   |
| repeat       | boolean | No | No | Whether it is a repeating timer. true indicates a repeating timer, and false indicates a one-shot timer.   |
| interval       | number | No | No | Timer trigger interval. For a repeating timer, the minimum value of interval is 1000 ms and the maximum value is 86400000 ms. For a one-shot timer, the value is 0. Unit: millisecond (ms).   |

### callback

callback(): void

Callback invoked when the timer expires.

**Since:** 26.0.1

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can be used only in the stage model.

## AudioVolumeType

Enumerates the volume types. The volume type to set or query is specified through the [setVolumeDegree](#systemmanagersetvolumedegree) and [getVolumeDegree](#systemmanagergetvolumedegree) APIs.

**Since:** 26.1.0

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can be used only in the stage model.

| Name         | Value | Description |
| ------------ | ----- | ----------- |
| STREAM_MUSIC | 1     | Media volume. |