# @ohos.enterprise.restrictions (Restrictions)
<!--Kit: MDM Kit-->
<!--Subsystem: Customization-->
<!--Owner: @huanleima-->
<!--Designer: @liuzuming-->
<!--Tester: @lpw_work-->
<!--Adviser: @Brilliantry_Rui-->

This **restrictions** module provides APIs for disallowing general features of devices. You can globally disable or enable the features such as Bluetooth, HDC, USB, and Wi-Fi.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - The APIs of this module can be called only by a device administrator application that is enabled. For details, see [MDM Kit Development](../../mdm/mdm-kit-guide.md).

## Modules to Import

```ts
import { restrictions } from '@kit.MDMKit';
```

## restrictions.setDisallowedPolicy

setDisallowedPolicy(admin: Want, feature: string, disallow: boolean): void

Disallows a feature.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS or ohos.permission.PERSONAL_MANAGE_RESTRICTIONS<sup>15+</sup>

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                      |
| feature  | string                                                  | Yes  | For features that can be set, see Table 1.<br> **NOTE**<br>Since API version 15, applications granted with the ohos.permission.PERSONAL_MANAGE_RESTRICTIONS permission and [activated as device administrator applications](./js-apis-enterprise-adminManager.md#adminmanagerstartadminprovision15) can set the following features: **bluetooth**, **hdc**, **microphone**, **usb**, **wifi**, **tethering**, and **camera**<!--RP3--><!--RP3End-->.|
| disallow | boolean                                                 | Yes  | Whether to disallow the feature. The value **true** means to disallow the feature; the value **false** means the opposite.                       |

**Table 1 Supported features**
|Feature|Description|
|--------------|---------------------|
|bluetooth|Device Bluetooth capability. If a Bluetooth device blocklist or trustlist is configured via [addDisallowedBluetoothDevices](js-apis-enterprise-bluetoothManager.md#bluetoothmanageradddisallowedbluetoothdevices20) or [addAllowedBluetoothDevices](js-apis-enterprise-bluetoothManager.md#bluetoothmanageraddallowedbluetoothdevices), disabling Bluetooth via this API takes priority. The blocklist or trustlist will only take effect after Bluetooth is re-enabled.|
|modifyDateTime|Device capability to modify system time.|
|printer|Device printing capability, which is supported only on PCs/2-in-1 devices for API versions earlier than 23, and on PCs/2-in-1 devices, smartphones, and tablets for API version 23 and later versions. Disabling printing via this API overrides the [setDisallowedPolicyForAccount](#restrictionssetdisallowedpolicyforaccount14) setting for specific users.|
|hdc|Capability for other devices to connect to and debug this device via HDC. Disabling this capability prevents external devices from connecting or debugging via HDC.|
|microphone|Device microphone capability.|
|fingerprint|Device fingerprint authentication capability. Calling this API will trigger a policy conflict if fingerprint authentication has already been disabled for a user via [setDisallowedPolicyForAccount](#restrictionssetdisallowedpolicyforaccount14).|
|usb|Device USB capability. Disabling this capability prohibits the use of external USB devices (the device cannot act as a USB host to connect external devices).<br>A policy conflict occurs in the following scenarios:<br>1. A list of allowed USB devices has been configured via the [addAllowedUsbDevices](js-apis-enterprise-usbManager.md#usbmanageraddallowedusbdevices) API.<br>2. USB storage device access policy has been set to read-only or disabled via the [setUsbStorageDeviceAccessPolicy](js-apis-enterprise-usbManager.md#usbmanagersetusbstoragedeviceaccesspolicy) API.<br>3. Specific USB device types have been blocked via the [addDisallowedUsbDevices](js-apis-enterprise-usbManager.md#usbmanageradddisallowedusbdevices14) API.<br>4. USB storage write access has been disabled for specific users via the [setDisallowedPolicyForAccount](#restrictionssetdisallowedpolicyforaccount14) API.|
|wifi|Device Wi-Fi capability.|
|tethering<sup>14+</sup>|Network tethering capability (the ability to share the device's internet connection with other devices, that is, hotspot sharing).|
|inactiveUserFreeze<sup>14+</sup>|Inactive user operation capability, currently supported only on PC/2-in-1 devices. When the system switches to the enterprise space user, the personal space users are inactive users.|
|camera<sup>14+</sup>|Device camera capability.|
|mtpClient<sup>18+</sup>|Media Transfer Protocol (MTP) client capability (including read and write capabilities), currently supported only on PC/2-in-1 devices. MTP enables linear access to media files on mobile devices. A policy conflict occurs if this API is used to disable MTP client capability after MTP client write access has been disabled for specific users via [setDisallowedPolicyForAccount](#restrictionssetdisallowedpolicyforaccount14).|
|mtpServer<sup>18+</sup>|MTP server capability.|
|sambaClient<sup>20+</sup>|Samba client capability, currently supported only on PC/2-in-1 devices. <br>Samba is a free software that implements the SMB protocol on Linux and UNIX systems, consisting of both server and client programs. <br>Server Messages Block (SMB) is a communication protocol for sharing files and printers over the local area network (LAN), enabling access to shared file systems, printers, and other resources between devices on the same LAN. As a client/server protocol, SMB allows clients to access shared resources hosted on servers.|
|sambaServer<sup>20+</sup>|Samba server capability, currently supported only on PC/2-in-1 devices.|
|backupAndRestore<sup>20+</sup>|Backup and restore capability. If this feature is disabled, the **Settings** > **System** > **Backup & Restore** and **Settings** > **Cloud** options will become unavailable. Currently, this feature is supported only on smartphones and tablets. To completely disable the backup and restore capability, you are advised to call [applicationManager.addDisallowedRunningBundlesSync](./js-apis-enterprise-applicationManager.md#applicationmanageradddisallowedrunningbundlessync) to disable applications with this feature, such as Backup & Restore, HiSuite, and Cloud.|
|maintenanceMode<sup>20+</sup>|Device maintenance mode capability.|
|mms<sup>20+</sup>|Multimedia Messaging Service (MMS) capability to receive and send multimedia messages. Currently, this feature is supported only on smartphones and tablets.|
|sms<sup>20+</sup>|Short Messaging Service (SMS) capability to receive and send SMS messages. Currently, this feature is supported only on smartphones and tablets.|
|mobileData<sup>20+</sup>|Cellular data capability, which is supported only on smartphones and tablets.|
|airplaneMode<sup>20+</sup>|Airplane mode capability, which is supported only on smartphones and tablets.|
|vpn<sup>20+</sup>|Virtual Private Network (VPN) capability.|
|notification<sup>20+</sup>|Device notification capability. Disabling this feature prevents system applications and third-party applications from displaying notifications. The notification capability of system services is not affected.|
|nfc<sup>20+</sup>|Near Field Communication (NFC) capability.|
|privateSpace<sup>20+</sup>|Privacy space creation capability, which is supported only on smartphones and tablets. This setting does not affect existing private spaces.|
|telephoneCall<sup>20+</sup>|Call capability. Disabling this feature blocks incoming or outgoing calls. Currently, this feature is supported only on smartphones and tablets.|
|appClone<sup>21+</sup>|[Application clone capability](../../quick-start/app-clone.md). When this feature is disabled, new application clones cannot be created. This feature is invalid for the application clone that has been created.|
|externalStorageCard<sup>21+</sup> |External storage capability. Disabling this feature prohibits the use of external storage and unmounts currently connected external storage. If files are in use during unmounting, unmounting may fail with error code 9200013.<br>After external storage is disabled and then enabled again, you need to manually reconnect the external storage.|
|randomMac<sup>21+</sup>|Random MAC address capability for Wi-Fi connections. When this feature is disabled, only the device's physical MAC address can be used for Wi-Fi connections.|
|unmuteDevice<sup>22+</sup>|Device audio playback capability. When this feature is disabled, media playback will be muted, while [cellular calls](../../media/audio/audio-call-overview.md) remain unaffected.|
|hdcRemote<sup>22+</sup>|Capability of the device to debug other devices through HDC. Currently, this feature can be set only for PCs/2-in-1 devices. Disabling this capability prevents debugging smartphones, tablets, PCs, smart watches, and other devices via HDC.|
|virtualService<sup>23+</sup>|Device virtualization service capability, which refers to the system capability of running other operating system platforms (such as Linux and Windows) through virtualization technology by leveraging the redundancy of the device's hardware resources. If this capability is disabled, it is recommended to uninstall all applications related to the virtualization service and prohibit their reinstallation.|
<!--RP1--><!--RP1End-->

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200013  | The enterprise management policy has been successfully set, but the function has not taken effect in real time. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace parameters with actual values.
  restrictions.setDisallowedPolicy(wantTemp, 'printer', true);
  console.info('Succeeded in setting printer disabled');
} catch (err) {
  console.error(`Failed to set printer disabled. Code is ${err.code}, message is ${err.message}`);
}
```

## restrictions.getDisallowedPolicy

getDisallowedPolicy(admin: Want \| null, feature: string): boolean

Queries whether a feature is disabled.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS or ohos.permission.PERSONAL_MANAGE_RESTRICTIONS<sup>15+</sup>

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type                                                   | Mandatory| Description                                                        |
| ------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                      |
| feature | string                                                  | Yes  | For features that can be queried, see Table 2.<br> **NOTE**<br>Since API version 15, applications granted with the ohos.permission.PERSONAL_MANAGE_RESTRICTIONS permission and [activated as device administrator applications](./js-apis-enterprise-adminManager.md#adminmanagerstartadminprovision15) can obtain the following features: **bluetooth**, **hdc**, **microphone**, **usb**, **wifi**, **tethering**, and **camera**<!--RP4--><!--RP4End-->.|

**Table 2 Features that can be queried**
|Feature|Description|
|--------------|---------------------|
|bluetooth|Device Bluetooth capability.|
|modifyDateTime|Device capability to modify system time.|
|printer|Device printing capability, which is supported only on PCs/2-in-1 devices for API versions earlier than 23, and on PCs/2-in-1 devices, smartphones, and tablets for API version 23 and later versions.|
|hdc|Capability for other devices to connect to and debug this device via HDC.|
|microphone|Device microphone capability.|
|fingerprint|Device fingerprint authentication capability.|
|usb|Device USB capability. Disabling this capability prohibits the use of external USB devices (the device cannot act as a USB host to connect external devices).|
|wifi|Device Wi-Fi capability.|
|tethering<sup>14+</sup>|Network tethering capability (the ability to share the device's internet connection with other devices, that is, hotspot sharing).|
|inactiveUserFreeze<sup>14+</sup>|Inactive user operation capability, currently supported only on PC/2-in-1 devices. When the system switches to the enterprise space user, the personal space users are inactive users.|
|camera<sup>14+</sup>|Device camera capability.|
|mtpClient<sup>18+</sup>|Media Transfer Protocol (MTP) client capability (including read and write capabilities), currently supported only on PC/2-in-1 devices. MTP allows users to linearly access media files on mobile devices.|
|mtpServer<sup>18+</sup>|MTP server capability.|
|sambaClient<sup>20+</sup>|Samba client capability, currently supported only on PC/2-in-1 devices. <br>Samba is a free software that implements the SMB protocol on Linux and UNIX systems, consisting of both server and client programs. <br>Server Messages Block (SMB) is a communication protocol for sharing files and printers over the local area network (LAN), enabling access to shared file systems, printers, and other resources between devices on the same LAN. As a client/server protocol, SMB allows clients to access shared resources hosted on servers.|
|sambaServer<sup>20+</sup>|Samba server capability, currently supported only on PC/2-in-1 devices.|
|backupAndRestore<sup>20+</sup>|Backup and restore capability. If this feature is disabled, the **Settings** > **System** > **Backup & Restore** and **Settings** > **Cloud** options will become unavailable. Currently, this feature is supported only on smartphones and tablets.|
|maintenanceMode<sup>20+</sup>|Device maintenance mode capability.|
|mms<sup>20+</sup>|Multimedia Messaging Service (MMS) capability to receive and send multimedia messages. Currently, this feature is supported only on smartphones and tablets.|
|sms<sup>20+</sup>|Short Messaging Service (SMS) capability to receive and send SMS messages. Currently, this feature is supported only on smartphones and tablets.|
|mobileData<sup>20+</sup>|Cellular data capability, which is supported only on smartphones and tablets.|
|airplaneMode<sup>20+</sup>|Airplane mode capability, which is supported only on smartphones and tablets.|
|vpn<sup>20+</sup>|Virtual Private Network (VPN) capability.|
|notification<sup>20+</sup>|Device notification capability.|
|nfc<sup>20+</sup>|Near Field Communication (NFC) capability.|
|privateSpace<sup>20+</sup>|Privacy space creation capability, which is supported only on smartphones and tablets.|
|telephoneCall<sup>20+</sup>|Call capability. Disabling this feature blocks incoming or outgoing calls. Currently, this feature is supported only on smartphones and tablets.|
|appClone<sup>21+</sup>|[Application clone capability](../../quick-start/app-clone.md). When this feature is disabled, new application clones cannot be created.|
|externalStorageCard<sup>21+</sup> |External storage capability.|
|randomMac<sup>21+</sup>|Random MAC address capability for Wi-Fi connections.|
|unmuteDevice<sup>22+</sup>|Device audio playback capability. When this feature is disabled, media playback will be muted, while [cellular calls](../../media/audio/audio-call-overview.md) remain unaffected.|
|hdcRemote<sup>22+</sup>|Capability of the device to debug other devices through HDC. Currently, this feature can be set only for PCs/2-in-1 devices.|
|virtualService<sup>23+</sup>|Device virtualization service capability.|
<!--RP2--><!--RP2End-->

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | The value **true** means the feature is disallowed; the value **false** means the opposite.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace parameters with actual values.
  let result: boolean = restrictions.getDisallowedPolicy(wantTemp, 'printer');
  console.info(`Succeeded in querying whether the printing function is disabled. Disabled status: ${result}`);
} catch (err) {
  console.error(`Failed to get printer disabled status. Code is ${err.code}, message is ${err.message}`);
}
```

## restrictions.setDisallowedPolicyForAccount<sup>14+</sup>

setDisallowedPolicyForAccount(admin: Want, feature: string, disallow: boolean, accountId: number): void

Disallows a feature for a specified user.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                  |
| feature  | string                                                  | Yes  | Feature to set.<br>- **fingerprint**: device fingerprint authentication capability. Currently, this feature is supported only on PCs/2-in-1 devices. The rules for using this parameter are as follows:<br>1. If this capability has been disabled through the [setDisallowedPolicy](#restrictionssetdisallowedpolicy) API, using **setDisallowedPolicyForAccount** will throw a policy conflict.<br>2. When **setDisallowedPolicyForAccount** is used to disable or enable the device fingerprint authentication capability for a specified user, any subsequent action via the [setDisallowedPolicy](#restrictionssetdisallowedpolicy) API will override the previous setting. If [setDisallowedPolicy](#restrictionssetdisallowedpolicy) enables the capability, all users gain access to the device fingerprint authentication.<br>- **print**<sup>20+</sup>: device printing capability, which is supported only on PCs/2-in-1 devices for API versions earlier than 23, and on PCs/2-in-1 devices, smartphones, and tablets for API version 23 and later versions. If printing is disabled via this API, it remains disabled for specific users even if the [setDisallowedPolicy](#restrictionssetdisallowedpolicy) API is used to enable it for those users.<br>- **mtpClient**<sup>20+</sup>: Media Transfer Protocol (MTP) client capability (write only). Currently, this feature is supported only on PCs/2-in-1 devices. MTP allows users to linearly access media files on mobile devices. A policy conflict error will occur if this API is used to disable MTP client capability after MTP client write access has been disabled for specific users via the [setDisallowedPolicy](#restrictionssetdisallowedpolicy) API.<br>- **usbStorageDeviceWrite**<sup>20+</sup>: USB storage device write permission. This feature is supported only on PCs/2-in-1 devices.<!--RP5--><!--RP5End--><br>  If the USB storage device write permission of a user is disabled via this API in any of the following situations, a policy conflict will be reported:<br>  1. The device USB capability has been disabled via the [setDisallowedPolicy](#restrictionssetdisallowedpolicy) API.<br>  2. USB storage device access policy has been set to read-only or disabled via the [setUsbStorageDeviceAccessPolicy](js-apis-enterprise-usbManager.md#usbmanagersetusbstoragedeviceaccesspolicy) API.<br>  3. Storage USB devices have been disabled via the [addDisallowedUsbDevices](js-apis-enterprise-usbManager.md#usbmanageradddisallowedusbdevices14) API.<br>- **diskRecoveryKey**<sup>20+</sup>: recovery [key export](../../security/UniversalKeystoreKit/huks-export-key-arkts.md) capability. Currently, this feature is supported only on 2-in-1 devices.<br>- **sudo**<sup>20+</sup>: superuser do (execution with superuser privileges). Currently, this feature is supported only on PCs/2-in-1 devices. If this feature is disabled, neither enterprise spaces nor personal spaces can perform operations with superuser privileges.<br>- **distributedTransmissionOutgoing**<sup>20+</sup>: one-way data transmission between devices (only data transmission to other devices is supported).|
| disallow | boolean                                                 | Yes  | Whether to disallow the feature. The value **true** means to disallow the feature; the value **false** means the opposite.                       |
| accountId | number                                                 | Yes  | User ID, which must be greater than or equal to 0.<br>You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9) to obtain the user ID.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | the administrator application does not have permission to manage the device. |
| 9200010  | A conflict policy has been configured.                       |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace parameters with actual values.
  restrictions.setDisallowedPolicyForAccount(wantTemp, 'fingerprint', true, 100);
  console.info('Succeeded in setting fingerprint disabled');
} catch (err) {
  console.error(`Failed to set fingerprint disabled. Code is ${err.code}, message is ${err.message}`);
}
```

## restrictions.getDisallowedPolicyForAccount<sup>14+</sup>

getDisallowedPolicyForAccount(admin: Want | null, feature: string, accountId: number): boolean

Obtains the status of a feature for a specified user.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type                                                   | Mandatory| Description                                                        |
| ------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                  |
| feature | string                                                  | Yes  | Feature to set.<br>- **fingerprint**: device fingerprint authentication capability. Currently, this feature is supported only on PCs/2-in-1 devices. Note that when [setDisallowedPolicyForAccount](#restrictionssetdisallowedpolicyforaccount14) is used to disable or enable the device fingerprint authentication capability for a specified user, any subsequent action via the [setDisallowedPolicy](#restrictionssetdisallowedpolicy) API will override the previous setting. The value **false** will be returned.<br>- **mtpClient**<sup>20+</sup>: Media Transfer Protocol (MTP) client capability (write only). Currently, this feature is supported only on PCs/2-in-1 devices. MTP allows users to linearly access media files on mobile devices.<br>- **usbStorageDeviceWrite**<sup>20+</sup>: USB storage device write permission. This feature is supported only on PCs/2-in-1 devices.<br>- **diskRecoveryKey**<sup>20+</sup>: recovery [key export](../../security/UniversalKeystoreKit/huks-export-key-arkts.md) capability. Currently, this feature is supported only on 2-in-1 devices.<br>- **sudo**<sup>20+</sup>: superuser do (execution with superuser privileges). Currently, this feature is supported only on PCs/2-in-1 devices. If this feature is disabled, neither enterprise spaces nor personal spaces can perform operations with superuser privileges.<br>- **distributedTransmissionOutgoing**<sup>20+</sup>: one-way data transmission between devices (only data transmission to other devices is supported).<br>- **print**<sup>20+</sup>: device printing capability, which is supported only on PCs/2-in-1 devices for API versions earlier than 23, and on PCs/2-in-1 devices, smartphones, and tablets for API version 23 and later versions. If printing is disabled via the [setDisallowedPolicy](#restrictionssetdisallowedpolicy) API, it remains disabled even if the [setDisallowedPolicyForAccount](#restrictionssetdisallowedpolicyforaccount14) API is used to enable it for specific users.|
| accountId | number                                                 | Yes  | User ID, which must be greater than or equal to 0.<br>You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9) to obtain the user ID.|

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | The value **true** means the feature is disabled; the value **false** means the opposite.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | the administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace parameters with actual values.
  let result: boolean = restrictions.getDisallowedPolicyForAccount(wantTemp, 'fingerprint', 100);
  console.info(`Succeeded in querying is the fingerprint function disabled : ${result}`);
} catch (err) {
  console.error(`Failed to set fingerprint disabled. Code is ${err.code}, message is ${err.message}`);
}
```

## restrictions.addDisallowedListForAccount<sup>14+</sup>

addDisallowedListForAccount(admin: Want, feature: string, list: Array\<string>, accountId: number): void

Adds a list of applications that are not allowed to use a feature for a specified user.  

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                  |
| feature  | string                                                  | Yes  | Feature to set.<br>- **snapshotSkip**: screen snapshot capability.|
| list | Array\<string>                                                 | Yes  | List of content such as the bundle names.                     |
| accountId | number                                                 | Yes  | User ID, which must be greater than or equal to 0.<br>You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9) to obtain the user ID.|

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
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let valueList:Array<string> = ["com.xx.aa.", "com.xx.bb"];
try {
  // Replace parameters with actual values.
  restrictions.addDisallowedListForAccount(wantTemp, 'snapshotSkip', valueList, 100);
  console.info('Succeeded in adding disallowed snapshotSkip feature');
} catch (err) {
  console.error(`Failed to add disallowed snapshotSkip feature. Code is ${err.code}, message is ${err.message}`);
}
```

## restrictions.removeDisallowedListForAccount<sup>14+</sup>

removeDisallowedListForAccount(admin: Want, feature: string, list: Array\<string>, accountId: number): void

Removes the list of applications that are not allowed to use a feature for a specified user.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                  |
| feature  | string                                                  | Yes  | Feature to set.<br>- **snapshotSkip**: screen snapshot capability.|
| list | Array\<string>                                                 | Yes  | List of content such as the bundle names.                      |
| accountId | number                                                 | Yes  | User ID, which must be greater than or equal to 0.<br>You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9) to obtain the user ID.|

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
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let valueList:Array<string> = ["com.xx.aa.", "com.xx.bb"];
try {
  // Replace parameters with actual values.
  restrictions.removeDisallowedListForAccount(wantTemp, 'snapshotSkip', valueList, 100);
  console.info('Succeeded in removing disallowed snapshotSkip feature');
} catch (err) {
  console.error(`Failed to remove disallowed snapshotSkip feature. Code is ${err.code}, message is ${err.message}`);
}
```

## restrictions.getDisallowedListForAccount<sup>14+</sup>

getDisallowedListForAccount(admin: Want, feature: string, accountId: number): Array\<string>

Obtains the list of applications that are not allowed to use a feature for a specified user.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type                                                   | Mandatory| Description                                                        |
| ------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                  |
| feature | string                                                  | Yes  | Feature to set.<br>- **snapshotSkip**: screen snapshot capability.|
| accountId | number                                                 | Yes  | User ID, which must be greater than or equal to 0.<br>You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9) to obtain the user ID.|

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| Array\<string> | List of applications that have been added by the user and for which a certain feature is disabled.|

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
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace parameters with actual values.
  let result: Array<string> = restrictions.getDisallowedListForAccount(wantTemp, 'snapshotSkip', 100);
  console.info('Succeeded in querying disallowed list for account');
} catch (err) {
  console.error(`Failed to query disallowed list for account. Code is ${err.code}, message is ${err.message}`);
}
```

## restrictions.setUserRestriction<sup>20+</sup>

setUserRestriction(admin: Want, settingsItem: string, restricted: boolean): void

Sets restrictions on user behaviors.

**Required permissions**: ohos.permission.ENTERPRISE_SET_USER_RESTRICTION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                  |
| settingsItem  | string                                                  | Yes  | User behavior.<br>- **setApn**: APN configuration, currently supported only on smartphones and tablets.<br>- **powerLongPress**: capability to open the power menu by long-pressing the power button. Currently, only smartphones and tablets are supported.<br>- **setEthernetIp**: Ethernet IP address configuration, currently supported only on PCs/2-in-1 devices.<br>- **setDeviceName**: device name configuration, currently supported only on PCs/2-in-1 devices, smartphones, and tablets. When it is disabled, the device name cannot be modified in the following settings: **About**, **Bluetooth**, and **More connectivity options** > **NearLink** on PCs/2-in-1 devices, and **About**, **Bluetooth**, and **Personal hotspot** on smartphones and tablets.<br>- **setBiometricsAndScreenLock**: screen lock password configuration, currently supported only on PCs/2-in-1 devices, smartphones, and tablets.|
| restricted | boolean                                                 | Yes  | Whether to disable the action. The value **true** means to disable the action, and **false** means the opposite.                      |

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { restrictions } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace parameters with actual values.
  restrictions.setUserRestriction(wantTemp, 'setApn', true);
  console.info('Succeeded in restricting from setting apn');
} catch (err) {
  console.error(`Failed to restrict from setting apn. Code is ${err.code}, message is ${err.message}`);
}
```
## restrictions.getUserRestricted<sup>20+</sup>

getUserRestricted(admin: Want, settingsItem: string): boolean

Obtains the disabled status of a setting item.


**Required permissions**: ohos.permission.ENTERPRISE_SET_USER_RESTRICTION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type                                                   | Mandatory| Description                                                        |
| ------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                  |
| settingsItem | string                                             | Yes  | Setting item.<br>- **setEthernetIp**: Ethernet IP address configuration, currently supported only on PCs/2-in-1 devices.<br>- **setDeviceName**: device name configuration, currently supported only on PCs/2-in-1 devices, smartphones, and tablets. When it is disabled, the device name cannot be modified in the following settings: **About**, **Bluetooth**, and **More connectivity options** > **NearLink** on PCs/2-in-1 devices, and **About**, **Bluetooth**, and **Personal hotspot** on smartphones and tablets.<br>- **setBiometricsAndScreenLock**: screen lock password configuration, currently supported only on PCs/2-in-1 devices, smartphones, and tablets.|

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Disabled status of the specified setting item. The value **true** means the item is disabled; the value **false** means the opposite.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { restrictions } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace input parameters with actual values.
  let result: boolean = restrictions.getUserRestricted(wantTemp, 'setEthernetIp');
  console.info('Succeeded in getting user restricted');
} catch (err) {
  console.error(`Failed to get user restricted. Code is ${err.code}, message is ${err.message}`);
}
```

## restrictions.setUserRestrictionForAccount<sup>23+</sup>

setUserRestrictionForAccount(admin: Want, settingsItem: string, accountId: int, restricted: boolean): void

Sets restrictions on specified user behaviors.

**Required permissions**: ohos.permission.ENTERPRISE_SET_USER_RESTRICTION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                  |
| settingsItem  | string                                                  | Yes  | User behavior.<br>- **modifyWallpaper**: Modify the wallpaper, including the lock screen wallpaper and home screen wallpaper.|
| accountId | number                                                 | Yes  | User ID, which must be greater than or equal to 0.<br>You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9) to obtain the user ID.                      |
| restricted | boolean                                                 | Yes  | Whether to disable the action. The value **true** means to disable the action, and **false** means the opposite.                      |

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { restrictions } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let userId = 100;
let settingsItem: string = "modifyWallpaper";
try {
  restrictions.setUserRestrictionForAccount(wantTemp, settingsItem, userId, true);
  console.info('Succeeded in restricting from setting modifyWallpaper');
} catch (err) {
  console.error(`Failed to restrict from setting modifyWallpaper. Code is ${err.code}, message is ${err.message}`);
}
```
## restrictions.getUserRestrictedForAccount<sup>23+</sup>

getUserRestrictedForAccount(admin: Want | null, settingsItem: string, accountId: int): boolean

Obtains the disabled status of a setting item for a specified user.


**Required permissions**: ohos.permission.ENTERPRISE_SET_USER_RESTRICTION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type                                                   | Mandatory| Description                                                        |
| ------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                  |
| settingsItem | string                                             | Yes  | Setting item.<br>- **modifyWallpaper**: Modify the wallpaper, including the lock screen wallpaper and home screen wallpaper.|
| accountId | number                                                 | Yes  | User ID, which must be greater than or equal to 0.<br>You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9) to obtain the user ID.                      |


**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Disabled status of the specified setting item. The value **true** means the item is disabled; the value **false** means the opposite.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { restrictions } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// Replace with actual values.
let userId = 100;
let settingsItem: string = "modifyWallpaper";
try {
  let result: boolean = restrictions.getUserRestrictedForAccount(wantTemp, settingsItem, userId);
  console.info(`Succeeded in getting user restricted: ${result}`);
} catch (err) {
  console.error(`Failed to get user restricted. Code is ${err.code}, message is ${err.message}`);
}
```
