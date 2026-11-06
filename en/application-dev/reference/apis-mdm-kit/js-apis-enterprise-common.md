# @ohos.enterprise.common (Common Module)
<!--Kit: MDM Kit-->
<!--Subsystem: Customization-->
<!--Owner: @huanleima; @weizai16-->
<!--Designer: @hp_guo-->
<!--Tester: @lpw_work-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=a894d7980411a2984f50dafd44488a2990ac825c translatedAt=2026-11-03T04:57:33.963Z pushedAt=2026-11-03T12:08:25.520Z nl=1 -->

This module provides common capabilities frequently used in MDM Kit, including enum types, data structs, and management control feature query APIs.

**Use cases:**
In enterprise device administrator application development, the types and APIs defined in this module are used in scenarios such as configuring device management policies, managing application instances, handling application installation results, listening for policy changes, and querying whether a device supports a specified management control feature. These types and APIs provide unified parameter and return value standards for the submodules in MDM Kit.

**Benefits:**
Standardized type definitions simplify the development process of enterprise device administrator applications, improve code maintainability and type safety, and reduce type-related runtime errors.

> **NOTE**
>
> The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { common } from '@kit.MDMKit';
```

## ManagedPolicy

Enumerates enterprise device management policies.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

| Name        | Value| Description                           |
| ----------- | -------- | ------------------------------- |
| DEFAULT | 0  | Default policy with no restrictions applied.|
| DISALLOW | 1  | Policy that disallows extensions from external sources to run.|
| FORCE_OPEN | 2  | Policy that forcibly enables extensions from external sources to run.|

## ApplicationInstance

Defines application instance data.

It is used as an input parameter in the [addUserNonStopApps](./js-apis-enterprise-applicationManager.md#applicationmanageraddusernonstopapps22), [removeUserNonStopApps](./js-apis-enterprise-applicationManager.md#applicationmanagerremoveusernonstopapps22), [addFreezeExemptedApps](./js-apis-enterprise-applicationManager.md#applicationmanageraddfreezeexemptedapps22), and [removeFreezeExemptedApps](./js-apis-enterprise-applicationManager.md#applicationmanagerremovefreezeexemptedapps22) APIs.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

| Name         | Type                            | Read-Only| Optional| Description                                                       |
| ------------- | --------------------------------| ---- | -----| ------------------------------------------------------ |
| appIdentifier          | string       | No  | No| [Unique identifier](../apis-ability-kit/js-apis-bundleManager-bundleInfo.md#signatureinfo) of an application. You can call the [bundleManager.getBundleInfo](../apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetbundleinfo14-2) API to obtain **bundleInfo.signatureInfo.appIdentifier**.          |
| accountId        | number       | No  | No| Account ID. The value is an integer greater than or equal to 0.<br> You can obtain the account ID by calling the [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) API.           |
| appIndex        | number       | No  | No| Index of the application clone. The value is an integer greater than or equal to 0.<br> You can obtain the index by calling the [getAppCloneIdentity](../apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetappcloneidentity14) API.          |

## InstallationResult

An object that holds the application installation result.

This object is used as a callback parameter in [EnterpriseAdminExtensionAbility.onMarketAppInstallResult](./js-apis-EnterpriseAdminExtensionAbility.md#onmarketappinstallresult22).

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

| Name         | Type                            | Read-Only| Optional| Description                                                       |
| ------------- | --------------------------------| ---- | -----| ------------------------------------------------------ |
| result        | [Result](#result)       | No  | No| Application installation result. **SUCCESS** indicates that the application is successfully installed and can be properly used. **FAIL** indicates that the application fails to be installed and is unavailable.           |
| message        | string       | No  | No| Application installation result message.          |

## Result

Enumerates application installation results.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

| Name        | Value| Description                           |
| ----------- | -------- | ------------------------------- |
| SUCCESS | 0  | The application is installed successfully.|
| FAIL | -1  | The application fails to be installed.|

## EnterpriseAdminExtensionContext<sup>23+</sup>

type EnterpriseAdminExtensionContext = _EnterpriseAdminExtensionContext.default

**EnterpriseAdminExtensionContext** is the context of [EnterpriseAdminExtensionAbility](js-apis-EnterpriseAdminExtensionAbility.md) and inherits from [ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md).

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| _EnterpriseAdminExtensionContext.default | Context [EnterpriseAdminExtensionContext](js-apis-application-EnterpriseAdminExtensionContext.md) of the EnterpriseAdminExtensionAbility component.|

## StartupScene<sup>24+</sup>

Startup wizard completion scenario. When the initial switch to a sub-user (only on PCs), OTA upgrade, and first-time startup wizard are complete, the device system calls the [onStartupGuideCompleted](./js-apis-EnterpriseAdminExtensionAbility.md#onstartupguidecompleted24) API to notify the device administrator application.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

| Name        | Value| Description                           |
| ----------- | -------- | ------------------------------- |
| USER_SETUP | 0  | A sub-user is switched to for the first time and the startup wizard for the sub-user is complete (only on PCs). The callback will not be triggered when the sub-user is switched again.|
| OTA | 1  | The OTA upgrade is complete.|
| DEVICE_PROVISION | 2  | The initial startup wizard is complete.|

## PolicyChangedEvent

Defines the policy change event.

This API is used as a callback input parameter of [onAdminPolicyChanged](./js-apis-EnterpriseAdminExtensionAbility.md#onadminpolicychanged).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

| Name         | Type                            | Read-Only| Optional| Description                                                       |
| ------------- | --------------------------------| ---- | -----| ------------------------------------------------------ |
| bundleName          | string       | No  | No| App bundle name.          |
| functionName        | string       | No  | No| API name. For example, if the [setPasswordPolicy](./js-apis-enterprise-securityManager.md#securitymanagersetpasswordpolicy) API is called, the value of this parameter is **setPasswordPolicy**.           |
| parameters        | string       | No  | No| Input parameter value (excluding the **admin** parameter) when an API is called. The value is a JSON string. For example, if the [setPasswordPolicy](./js-apis-enterprise-securityManager.md#securitymanagersetpasswordpolicy) API is called, the return value of this parameter is **{"policy":{"complexityRegex":"^(?=.\*[a-zA-Z])(?=.\*\\\\d).{8},$","validityPeriod":1808309786000,"additionalDescription":"It must contain at least eight characters, including digits and letters.** **"}}**.           |
| time        | number       | No  | No| Timestamp when an API is called, in milliseconds.          |

## DiskType

Enumerates the disk types of external storage devices.

**Since:** 26.0.1

**Model restriction:** This API can only be used in the Stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

| Name      | Value | Description            |
| --------- | ----- | ---------------------- |
| SD_CARD   | 1     | SD card type.          |
| USB_FLASH | 2     | USB flash drive type.  |
| CD_DVD_BD | 3     | Optical disc type.     |

## ExternalStorageDeviceInfo

Provides information about an external storage device. This API is currently used as the return value in the [usbManager.getExternalStorageDeviceInfos](./js-apis-enterprise-usbManager.md#usbmanagergetexternalstoragedeviceinfos) API and as the callback input parameter in the [EnterpriseAdminExtensionAbility.onUnmountExternalStorageDevice](./js-apis-EnterpriseAdminExtensionAbility.md#onunmountexternalstoragedevice) API.

**Since:** 26.0.1

**Model restriction:** This API can only be used in the Stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

| Name        | Type                  | Read-only | Optional | Description                                                         |
| ----------- | --------------------- | ---- | ---- | ------------------------------------------------------------ |
| type        | [DiskType](#disktype) | No   | No   | Disk type.                                                   |
| devicePath  | string                | No   | No   | Mount path.                                                   |
| volumeId    | string                | No   | No   | Volume ID.                                                       |
| mountStatus | boolean               | No   | No   | Mount status. The value **true** indicates that the device is mounted, and **false** indicates that it is not mounted.         |
| vendorId    | number                | No   | No   | Vendor ID.                                                     |
| productId   | number                | No   | No   | Product ID.                                                     |
| serial      | string                | No   | No   | Serial number.                                                     |

## QueryPolicy

Enumerates the policies to obtain.

**Since:** 26.0.1

**Model restriction:** This API can only be used in the Stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

| Name         | Value | Description                            |
| ----------- | -------- | ------------------------------- |
| SELF | 0  | Policies set by the current Admin. |
| ALL | 1  | Policies set by all Admins. |

## ManagedFeature

Enumerates the management control features.

**Since:** 26.0.1

**Model restriction:** This API can only be used in the Stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

| Name                    | Value | Description                              |
| ----------------------- | -------- | --------------------------------- |
| LOCAL_HOTA_DOMAIN       | 0  | Local HOTA (Huawei Over-the-Air) domain name.    |
| USER_EXTEND_CREDENTIAL  | 1  | Extended identity authentication credential.                |
| DEVICE_SECURITY_LEVEL   | 2  | Device security level.              |
| PRINTER_IP_ADDRESS_POLICY | 3 | Printer IP address policy.          |
| OPTICAL_DISC_DRIVE_BURN | 4 | Optical disc drive burning.          |
| EXACT_TIMER | 5 | Exact timer.          |
| EXEMPTION_RESOURCE | 6 | Resource exemption.          |
| X_KEY | 7 | X key.          |
| SYSTEM_ROLLBACK | 8 | System rollback.          |
| SUPER_PRIVACY | 9 | Super privacy mode.          |

## common.isFeatureSupported

isFeatureSupported(feature: ManagedFeature): boolean

Queries whether a management control feature is supported. This API is intended for enterprise device management applications to check whether the current device supports a specific feature before calling device-form-related management control APIs, so as to perform differentiated service processing and avoid calling related APIs on unsupported devices.

**Since:** 26.0.1

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This API can only be used in the Stage model.

**Parameters**

| Name    | Type                                        | Required | Description                    |
| ------- | ------------------------------------------- | -------- | ------------------------------ |
| feature | [ManagedFeature](#managedfeature)           | Yes      | Management control feature.    |

**Return value**

| Type    | Description                                                       |
| ------- | ----------------------------------------------------------------- |
| boolean | true if the feature is supported; false otherwise.                |

**Example:**

```ts
import { common, systemManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it based on the actual situation.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace it based on the actual situation.
let domain: string = "https://www.hotaExample.com";
// Before calling the API, use this API to query whether the device supports the local HOTA domain name feature.
let isSupported: boolean = common.isFeatureSupported(common.ManagedFeature.LOCAL_HOTA_DOMAIN);
if (isSupported) {
  try {
    systemManager.setLocalHotaDomain(wantTemp, domain);
    console.info('Succeeded in setting local HOTA domain.');
  } catch (err) {
    console.error(`Failed to set local HOTA domain. Code is ${err.code}, message is ${err.message}`);
  }
} else {
  console.info('The local HOTA domain feature is not supported.');
}
```
