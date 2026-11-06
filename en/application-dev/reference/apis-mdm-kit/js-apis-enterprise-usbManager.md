# @ohos.enterprise.usbManager (USB Management)
<!--Kit: MDM Kit-->
<!--Subsystem: Customization-->
<!--Owner: @huanleima; @weizai16-->
<!--Designer: @hp_guo-->
<!--Tester: @lpw_work-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=a894d7980411a2984f50dafd44488a2990ac825c translatedAt=2026-11-03T05:37:19.760Z pushedAt=2026-11-03T12:08:25.564Z nl=1 -->

The **usbManager** module provides APIs for USB management.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.
>
> The APIs of this module are open only to device management applications. Before calling the APIs, you must activate a device management application. For details, see [MDM Kit Development Guide](../../mdm/mdm-kit-guide.md).
>
> Global universal restriction policies are provided by restrictions. To globally disable USB, see [@ohos.enterprise.restrictions (Restriction Policies)](js-apis-enterprise-restrictions.md).

## Modules to Import

```ts
import { usbManager } from '@kit.MDMKit';
```

## usbManager.addAllowedUsbDevices

addAllowedUsbDevices(admin: Want, usbDeviceIds: Array\<UsbDeviceId>): void

Adds allowed USB devices.

**Use cases:**
- Restrict access to only specific USB devices in enterprise security management scenarios.
- Enable device administrators to precisely control which USB devices can be recognized and used.
- Work with the [removeAllowedUsbDevices](#usbmanagerremoveallowedusbdevices) API to implement dynamic management of USB devices.

A policy conflict is reported when this API is called in the following scenarios:

1. The USB capability or the USB-to-serial capability of the device has been disabled via [setDisallowedPolicy](js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicydeprecated).
2. The USB storage device access policy has been disabled using the [setUsbStorageDeviceAccessPolicy](#usbmanagersetusbstoragedeviceaccesspolicy) API.
3. Disallowed USB device types have been added using the [addDisallowedUsbDevices](#usbmanageradddisallowedusbdevices14) API.
4. Disallowed USB device types have been added via [addDisallowedPermissiveUsbDevices](#usbmanageradddisallowedpermissiveusbdevices).
5. External storage device mount interception has been enabled via [setExternalStorageInterceptEnable](#usbmanagersetexternalstorageinterceptenable).

> **NOTE**
>
> In the multi-MDM application scenario, the [merge](../../mdm/mdm-kit-multi-mdm.md#rule-4-policy-merging) rule is followed.

**Required permission**: ohos.permission.ENTERPRISE_MANAGE_USB

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                                   | Mandatory| Description                                                        |
| ------------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin        | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                      |
| usbDeviceIds | Array<[UsbDeviceId](#usbdeviceid)>                      | Yes  | USB device IDs, which can be obtained through [getDevices](../apis-basic-services-kit/js-apis-usbManager.md#usbmanagergetdevices). The maximum number of USB devices is 1,000. If there are already 300 USB device IDs, only 700 more can be added.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200007 | The system ability works abnormally. |
| 9200010  | A conflict policy has been configured.                       |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { usbManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let usbDeviceIds: Array<usbManager.UsbDeviceId> = [{
    vendorId: 1,
    productId: 1
  }];
  usbManager.addAllowedUsbDevices(wantTemp, usbDeviceIds);
  console.info(`Succeeded in adding allowed USB devices.`);
} catch (err) {
  console.error(`Failed to add allowed USB devices. Code: ${err.code}, message: ${err.message}`);
}
```

## usbManager.removeAllowedUsbDevices

removeAllowedUsbDevices(admin: Want, usbDeviceIds: Array\<UsbDeviceId>): void

Removes allowed USB devices.

**Use cases:**
- Revoke access permissions for certain USB devices in enterprise security management scenarios.
- Enable device administrators to dynamically adjust the list of allowed USB devices.
- Remove USB devices from the trustlist when they are no longer needed or pose a security risk.

> **NOTE**
>
> In the multi-MDM application scenario, the [merge](../../mdm/mdm-kit-multi-mdm.md#rule-4-policy-merging) rule is followed.

**Required permission**: ohos.permission.ENTERPRISE_MANAGE_USB

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                                   | Mandatory| Description                                                        |
| ------------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin        | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                      |
| usbDeviceIds | Array<[UsbDeviceId](#usbdeviceid)>                      | Yes  | USB device IDs, which can be obtained through [getDevices](../apis-basic-services-kit/js-apis-usbManager.md#usbmanagergetdevices).|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { usbManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it based on the actual situation.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let usbDeviceIds: Array<usbManager.UsbDeviceId> = [{
    vendorId: 1,
    productId: 1
  }];
  usbManager.removeAllowedUsbDevices(wantTemp, usbDeviceIds);
  console.info(`Succeeded in removing allowed USB devices.`);
} catch (err) {
  console.error(`Failed to remove allowed USB devices. Code: ${err.code}, message: ${err.message}`);
}
```

## usbManager.getAllowedUsbDevices

getAllowedUsbDevices(admin: Want): Array\<UsbDeviceId>

Obtains the allowed USB device list. General use cases: before modifying a policy, retrieve the existing policy for evaluation; the management page needs to display the current USB storage device access control status.

This interface queries the policy set by the corresponding enterprise device management application by passing in Want. To query the policy that actually takes effect, use the [usbManager.getAllowedUsbDevices](#usbmanagergetallowedusbdevices-1) interface.

**Required permission:** ohos.permission.ENTERPRISE_MANAGE_USB

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This API can be used only in the stage model.


**Parameters**

| Name| Type                                                   | Mandatory| Description                                  |
| ------ | ------------------------------------------------------- | ---- | -------------------------------------- |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes   | Enterprise device management extension component. The Want must include the abilityName of the enterprise device management extension capability and the bundleName of the host application.|

**Return value**

| Type                              | Description                     |
| ---------------------------------- | ------------------------- |
| Array<[UsbDeviceId](#usbdeviceid)> | Array of device IDs in the allowed USB device list. |

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
import { usbManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let result: Array<usbManager.UsbDeviceId> = usbManager.getAllowedUsbDevices(wantTemp);
  console.info(`Succeeded in getting allowed USB devices. Result: ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get allowed USB devices. Code: ${err.code}, message: ${err.message}`);
}
```


## usbManager.getAllowedUsbDevices

getAllowedUsbDevices(admin: Want | null): Array\<UsbDeviceId>

Obtains the allowed USB device list. General use cases: before modifying a policy, obtain the existing policy for evaluation; the management UI needs to display the current USB storage device access control status.

**Since:** 26.0.0

**Required permission**: ohos.permission.ENTERPRISE_MANAGE_USB

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description                                  |
| ------ | ------------------------------------------------------- | ---- | -------------------------------------- |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | Yes   | Enterprise Device Management extension component. The Want must include the abilityName of the Enterprise Device Management extension capability and the bundleName of the host application.<br>When multiple MDM applications exist on the device, passing Want queries the policy set by the corresponding Enterprise Device Management application, and passing null queries the policy that actually takes effect.|

**Return value**

| Type                              | Description                     |
| ---------------------------------- | ------------------------- |
| Array<[UsbDeviceId](#usbdeviceid)> | Array of device IDs in the USB device trustlist.|

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
import { usbManager } from '@kit.MDMKit';

try {
  // Replace the parameters based on the actual situation.
  let result: Array<usbManager.UsbDeviceId> = usbManager.getAllowedUsbDevices(null);
  console.info(`Succeeded in getting allowed USB devices. Result: ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get allowed USB devices. Code: ${err.code}, message: ${err.message}`);
}
```
## usbManager.setUsbStorageDeviceAccessPolicy

setUsbStorageDeviceAccessPolicy(admin: Want, usbPolicy: UsbPolicy): void

Sets the USB storage device (baseClass = 0x08) access policy.

> **NOTE**
> Before calling the interface, ensure that read and write operations on the USB storage device have been suspended to guarantee operational stability and data integrity. Otherwise, unexpected exceptions may occur.
>
> In scenarios with multiple MDM applications, the [strictest control](../../mdm/mdm-kit-multi-mdm.md#rule-1-security-first) rule applies. The strict priority is: disabled > read-only > read-write.

A policy conflict occurs when you set the USB storage device access policy to read, write, or read-only in the following scenarios:

1. The USB capability of the device has been disabled via [setDisallowedPolicy](js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicydeprecated).
2. The USB storage device has been disallowed to use through [addDisallowedUsbDevices](#usbmanageradddisallowedusbdevices14).
3. The USB storage write capability has been disabled for specific users via [setDisallowedPolicyForAccount](js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicyforaccountdeprecated).
4. External storage device mount interception has been enabled through the [setExternalStorageInterceptEnable](#usbmanagersetexternalstorageinterceptenable) interface.

A policy conflict is reported if the USB storage device access policy is disabled by calling this API in the following scenarios:

1. The USB capability of the device has been disabled via [setDisallowedPolicy](js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicydeprecated).
2. The available USB devices have been added through [addAllowedUsbDevices](#usbmanageraddallowedusbdevices).
3. The USB storage write capability has been disabled for specific users via [setDisallowedPolicyForAccount](js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicyforaccountdeprecated).
4. External storage device mount interception has been enabled through the [setExternalStorageInterceptEnable](#usbmanagersetexternalstorageinterceptenable) interface.

You can disable a USB storage device by calling this API or [addDisallowedUsbDevices](#usbmanageradddisallowedusbdevices14). The latter is recommended.

**Required permissions**: 

- Before API version 26.0.0: ohos.permission.ENTERPRISE_MANAGE_USB
- Since API version 26.0.0: ohos.permission.ENTERPRISE_MANAGE_USB or ohos.permission.PERSONAL_MANAGE_RESTRICTIONS (The application is activated as a built-in device administrator application via the [adminManager.startAdminProvision](./js-apis-enterprise-adminManager.md#adminmanagerstartadminprovision15) API.)

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name   | Type                                                   | Mandatory| Description                                  |
| --------- | ------------------------------------------------------- | ---- | -------------------------------------- |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| usbPolicy | [UsbPolicy](#usbpolicy)                                 | Yes  | Access policy of the USB storage device.                 |

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200007 | The system ability works abnormally. |
| 9200010  | A conflict policy has been configured.                       |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { usbManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let policy: usbManager.UsbPolicy = usbManager.UsbPolicy.DISABLED;
  usbManager.setUsbStorageDeviceAccessPolicy(wantTemp, policy);
  console.info(`Succeeded in setting USB storage device access policy.`);
} catch (err) {
  console.error(`Failed to set USB storage device access policy. Code: ${err.code}, message: ${err.message}`);
}
```

## usbManager.getUsbStorageDeviceAccessPolicy

getUsbStorageDeviceAccessPolicy(admin: Want): UsbPolicy

Obtains the USB storage device (baseClass = 0x08) access policy.

This interface queries the policy set by the corresponding enterprise device management application by passing in Want. To query the policy that actually takes effect, use the [usbManager.getUsbStorageDeviceAccessPolicy](#usbmanagergetusbstoragedeviceaccesspolicy-1) interface.

**Required permissions**:
 - Before API version 26.0.0: ohos.permission.ENTERPRISE_MANAGE_USB
 - From API version 26.0.0: ohos.permission.ENTERPRISE_MANAGE_USB or ohos.permission.PERSONAL_MANAGE_RESTRICTIONS (the application calls the [adminManager.startAdminProvision](./js-apis-enterprise-adminManager.md#adminmanagerstartadminprovision15) interface to activate itself as a self-owned device management application).

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.


**Parameters**

| Name| Type                                                   | Mandatory| Description                                  |
| ------ | ------------------------------------------------------- | ---- | -------------------------------------- |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes   | Enterprise device management extension component. The Want must include the abilityName of the enterprise device management extension capability and the bundleName of the host application.|

**Return value**

| Type                   | Description                 |
| ----------------------- | --------------------- |
| [UsbPolicy](#usbpolicy) | Access policy of the USB storage device. The value **READ_WRITE** indicates that the USB storage device can be read and written. The value **READ_ONLY** indicates that the USB storage device can only be read. The value **DISABLED** indicates that access to the USB storage device cannot be accessed.|

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
import { usbManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let result: usbManager.UsbPolicy = usbManager.getUsbStorageDeviceAccessPolicy(wantTemp);
  console.info(`Succeeded in getting USB storage device access policy. Result: ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get USB storage device access policy. Code: ${err.code}, message: ${err.message}`);
}
```


## usbManager.getUsbStorageDeviceAccessPolicy

getUsbStorageDeviceAccessPolicy(admin: Want | null): UsbPolicy

Obtains the access policy of USB storage devices (baseClass = 0x08).

**Since:** 26.0.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_USB or ohos.permission.PERSONAL_MANAGE_RESTRICTIONS (when the application calls [adminManager.startAdminProvision](./js-apis-enterprise-adminManager.md#adminmanagerstartadminprovision15) to become a self-provisioned device management application).

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can be used only in the stage model.

**Parameters**

| Name | Type                                                    | Mandatory | Description                                   |
| ------ | ------------------------------------------------------- | ---- | -------------------------------------- |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | Yes   | Enterprise device management extension component. The Want must include the abilityName of the enterprise device management extension capability and the bundleName of the host application.<br>When multiple MDM applications exist on the device, passing Want queries the policy set by the corresponding enterprise device management application, and passing null queries the policy that actually takes effect.|

**Return value**

| Type                    | Description                  |
| ----------------------- | --------------------- |
| [UsbPolicy](#usbpolicy) | USB storage device access policy. READ_WRITE indicates that both read and write access to USB storage devices is allowed; READ_ONLY indicates that only read access to USB storage devices is allowed and write access is prohibited; DISABLED indicates that access to USB storage devices is completely prohibited. |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { usbManager } from '@kit.MDMKit';

try {
  // Replace the parameters based on the actual situation.
  let result: usbManager.UsbPolicy = usbManager.getUsbStorageDeviceAccessPolicy(null);
  console.info(`Succeeded in getting USB storage device access policy. Result: ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get USB storage device access policy. Code: ${err.code}, message: ${err.message}`);
}
```
## usbManager.addDisallowedUsbDevices<sup>14+</sup>

addDisallowedUsbDevices(admin: Want, usbDevices: Array\<UsbDeviceType>): void

Adds disallowed USB device types. General use cases: In enterprise security management scenarios, specific types of USB devices need to be disabled; preventing data leakage: disabling USB storage device types; device administrators need to prohibit the use of certain types of USB devices according to security policies; used together with [removeDisallowedUsbDevices](#usbmanagerremovedisallowedusbdevices14) to implement dynamic management of USB device types.

> **NOTE**
>
> It is recommended to use the [addDisallowedPermissiveUsbDevices](#usbmanageradddisallowedpermissiveusbdevices) API.
>
> In multi-MDM application scenarios, the [Policy merging](../../mdm/mdm-kit-multi-mdm.md#rule-4-policy-merging) rule is followed.

A policy conflict is reported when this API is called in the following scenarios:

1. The USB capability of the device has been disabled via [setDisallowedPolicy](js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicydeprecated).
2. The available USB devices have been added through [addAllowedUsbDevices](#usbmanageraddallowedusbdevices).
3. The USB storage write capability has been disabled for specific users via [setDisallowedPolicyForAccount](js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicyforaccountdeprecated).
4. Disallowed USB device types have been added via [addDisallowedPermissiveUsbDevices](#usbmanageradddisallowedpermissiveusbdevices).
5. The external storage device mount interception has been enabled through the [setExternalStorageInterceptEnable](#usbmanagersetexternalstorageinterceptenable) API.

**Required permission**: ohos.permission.ENTERPRISE_MANAGE_USB

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name    | Type                                                   | Mandatory| Description                                                        |
| ---------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin      | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                      |
| usbDevices | Array<[UsbDeviceType](#usbdevicetype14)>                | Yes  | Array of the USB devices to be added, which can be obtained through [getDevices](../apis-basic-services-kit/js-apis-usbManager.md#usbmanagergetdevices). The maximum number of USB devices is 200. If there are already 100 USB device IDs, only 100 more can be added.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200010  | A conflict policy has been configured.                       |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { usbManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let usbDevices: Array<usbManager.UsbDeviceType> = [{
    baseClass: 8,
    subClass: 0,
    protocol: 0,
    descriptor: usbManager.Descriptor.INTERFACE
  }];
  usbManager.addDisallowedUsbDevices(wantTemp, usbDevices);
  console.info(`Succeeded in adding disallowed USB devices.`);
} catch (err) {
  console.error(`Failed to add disallowed USB devices. Code: ${err.code}, message: ${err.message}`);
}
```

## usbManager.removeDisallowedUsbDevices<sup>14+</sup>

removeDisallowedUsbDevices(admin: Want, usbDevices: Array\<UsbDeviceType>): void

Removes the disallowed USB device types.

**Use cases:**
- Lifts the restriction on certain USB device types in enterprise security management scenarios.
- Enable device administrators to dynamically adjust the list of disallowed USB device types.
- Remove USB device types from the blocklist when they no longer pose a security risk.

> **NOTE**
>
> In multi-MDM application scenarios, the [Policy merging](../../mdm/mdm-kit-multi-mdm.md#rule-4-policy-merging) rule is followed.

**Required permission**: ohos.permission.ENTERPRISE_MANAGE_USB

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name    | Type                                                   | Mandatory| Description                                                        |
| ---------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin      | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                      |
| usbDevices | Array<[UsbDeviceType](#usbdevicetype14)>                | Yes  | Array of the USB devices to be removed, which can be obtained through [getDevices](../apis-basic-services-kit/js-apis-usbManager.md#usbmanagergetdevices).|

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
import { usbManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let usbDevices: Array<usbManager.UsbDeviceType> = [{
    baseClass: 8,
    subClass: 0,
    protocol: 0,
    descriptor: usbManager.Descriptor.INTERFACE
  }];
  usbManager.removeDisallowedUsbDevices(wantTemp, usbDevices);
  console.info(`Succeeded in removing disallowed USB devices.`);
} catch (err) {
  console.error(`Failed to remove disallowed USB devices. Code: ${err.code}, message: ${err.message}`);
}
```

## usbManager.getDisallowedUsbDevices<sup>14+</sup>

getDisallowedUsbDevices(admin: Want): Array\<UsbDeviceType>

Obtains the USB device types whose use is prohibited. General use cases: a device administrator needs to view the current list of USB device types whose use is prohibited; before modifying the prohibited list, the existing list must be obtained for comparison; the management interface needs to display the current USB device type prohibition policy configuration.

This interface queries the policy set by the corresponding enterprise device management application by passing in a Want. To query the policy that actually takes effect, use [usbManager.getDisallowedUsbDevices](#usbmanagergetdisallowedusbdevices).

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_USB

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can be used only in the stage model.


**Parameters**

| Name | Type                                                    | Mandatory| Description                                   |
| ------ | ------------------------------------------------------- | ---- | -------------------------------------- |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes   | Enterprise device management extension component. The Want must include the abilityName of the enterprise device management extension capability and the bundleName of the host application.|

**Return value**

| Type                                     | Description                    |
| ---------------------------------------- | ----------------------- |
| Array<[UsbDeviceType](#usbdevicetype14)> | USB device types whose use is prohibited. |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                |
| ------------- | ------------------------------------------------------------ |
| 9200001       | The application is not an administrator application of the device. |
| 9200002       | The administrator application does not have permission to manage the device. |
| 201           | Permission verification failed. The application does not have the permission required to call the API. |
| 401           | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { usbManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it based on the actual situation.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let result: Array<usbManager.UsbDeviceType> = usbManager.getDisallowedUsbDevices(wantTemp);
  console.info(`Succeeded in getting disallowed USB devices. Result: ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get disallowed USB devices. Code: ${err.code}, message: ${err.message}`);
}
```


## usbManager.getDisallowedUsbDevices

getDisallowedUsbDevices(admin: Want | null): Array\<UsbDeviceType>

Obtains the types of USB devices that are prohibited from use. General use cases: a device administrator needs to view the current list of prohibited USB device types; before modifying the disallowed list, the existing list must be obtained for comparison; the management interface needs to display the current USB device type prohibition policy configuration.

**Since:** 26.0.0

**Required permission**: ohos.permission.ENTERPRISE_MANAGE_USB

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description                                  |
| ------ | ------------------------------------------------------- | ---- | -------------------------------------- |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | Yes   | Enterprise device management extension component. The Want must include the abilityName of the enterprise device management extension capability and the bundleName of the host application.<br>When multiple MDM applications exist on the device, passing Want queries the policy set by the corresponding enterprise device management application, and passing null queries the policy that actually takes effect.|

**Return value**

| Type                                    | Description                   |
| ---------------------------------------- | ----------------------- |
| Array<[UsbDeviceType](#usbdevicetype14)> | Disallowed USB device types obtained.|

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
import { usbManager } from '@kit.MDMKit';

try {
  // Replace the parameters based on the actual situation.
  let result: Array<usbManager.UsbDeviceType> = usbManager.getDisallowedUsbDevices(null);
  console.info(`Succeeded in getting disallowed USB devices. Result: ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get disallowed USB devices. Code: ${err.code}, message: ${err.message}`);
}
```
## usbManager.addDisallowedPermissiveUsbDevices

addDisallowedPermissiveUsbDevices(admin: Want, usbDevices: Array\<PermissiveUsbDeviceType>): void

Adds disallowed USB device types. Unlike the [addDisallowedUsbDevices](#usbmanageradddisallowedusbdevices14) API, this API does not require matching based on the [defined-class-codes](https://www.usb.org/defined-class-codes) standard. This API takes effect immediately on connected USB devices without requiring re-plugging. For example, if a USB wired headset is in normal use and this API is called to disable it, the headset will become unavailable immediately.

A policy conflict is reported when this API is called in the following scenarios:

1. Disallowed USB device types have been added using the [addDisallowedUsbDevices](#usbmanageradddisallowedusbdevices14) API.
2. The USB capability of the device has been disabled via [setDisallowedPolicy](js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicydeprecated).
3. The available USB devices have been added through [addAllowedUsbDevices](#usbmanageraddallowedusbdevices).
4. The USB storage write capability has been disabled for specific users via [setDisallowedPolicyForAccount](js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicyforaccountdeprecated).
5. External storage device mount interception has already been enabled by calling the [setExternalStorageInterceptEnable](#usbmanagersetexternalstorageinterceptenable) interface.

**Since:** 26.0.0

> **NOTE**
>
> In a multi-MDM application scenario, the [merging](../../mdm/mdm-kit-multi-mdm.md#rule-4-policy-merging) rule is followed.

**Required permission**: ohos.permission.ENTERPRISE_MANAGE_USB

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name    | Type                                                    | Mandatory| Description|
| ---------- | ------------------------------------------------------- | ---- | ---- |
| admin      | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| usbDevices | Array\<[PermissiveUsbDeviceType](#permissiveusbdevicetype)> | Yes  | Array of USB device types to be added. Partial field matching is supported. The array can have a maximum of 1000 elements. If there are already 500 USB device IDs in the array, only 500 more can be added.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200010  | A conflict policy has been configured.                       |
| 9200012  | Parameter verification failed.                               |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { usbManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  // Disable USB storage devices (use the actual USB device type parameter).
  let usbDevices1: Array<usbManager.PermissiveUsbDeviceType> = [{
    baseClass: 8
  }];
  usbManager.addDisallowedPermissiveUsbDevices(wantTemp, usbDevices1);

  // Disable USB wired headsets (use the actual USB device type parameter).
  let usbDevices2: Array<usbManager.PermissiveUsbDeviceType> = [{
    baseClass: 0,
    subClass: 0,
    protocol: 0,
    descriptor: usbManager.Descriptor.DEVICE
  }];
  usbManager.addDisallowedPermissiveUsbDevices(wantTemp, usbDevices2);

  // Disable USB wired keyboard input (use the actual USB device type parameter).
  let usbDevices3: Array<usbManager.PermissiveUsbDeviceType> = [{
    baseClass: 3,
    subClass: 1,
    protocol: 1,
    descriptor: usbManager.Descriptor.INTERFACE
  }];
  usbManager.addDisallowedPermissiveUsbDevices(wantTemp, usbDevices3);
  console.info(`Succeeded in adding disallowed permissive USB devices.`);
} catch (err) {
  console.error(`Failed to add disallowed permissive USB devices. Code: ${err.code}, message: ${err.message}`);
}
```

## usbManager.removeDisallowedPermissiveUsbDevices

removeDisallowedPermissiveUsbDevices(admin: Want, usbDevices: Array\<PermissiveUsbDeviceType>): void

Removes the USB device types that have been disallowed via [addDisallowedPermissiveUsbDevices](#usbmanageradddisallowedpermissiveusbdevices). The removed USB device types can be used normally.

**Since:** 26.0.0

> **NOTE**
>
> In a multi-MDM application scenario, the [merging](../../mdm/mdm-kit-multi-mdm.md#rule-4-policy-merging) rule is followed.

**Required permission**: ohos.permission.ENTERPRISE_MANAGE_USB

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name    | Type                                                      | Mandatory| Description|
| ---------- | --------------------------------------------------------- | ---- | ----- |
| admin      | [Want](../apis-ability-kit/js-apis-app-ability-want.md)   | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| usbDevices | Array\<[PermissiveUsbDeviceType](#permissiveusbdevicetype)> | Yes  | Array of USB device types to be removed.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed.                               |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { usbManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let usbDevices: Array<usbManager.PermissiveUsbDeviceType> = [{
    baseClass: 8
  }];
  usbManager.removeDisallowedPermissiveUsbDevices(wantTemp, usbDevices);
  console.info(`Succeeded in removing disallowed permissive USB devices.`);
} catch (err) {
  console.error(`Failed to remove disallowed permissive USB devices. Code: ${err.code}, message: ${err.message}`);
}
```

## usbManager.getDisallowedPermissiveUsbDevices

getDisallowedPermissiveUsbDevices(admin: Want | null): Array\<PermissiveUsbDeviceType>

Obtains the USB device types that have been disallowed via [addDisallowedPermissiveUsbDevices](#usbmanageradddisallowedpermissiveusbdevices).

**Since:** 26.0.0

**Required permission**: ohos.permission.ENTERPRISE_MANAGE_USB

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description|
| ------ | ------------------------------------------------------- | ---- | ----- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. If the value is null, the disallowed USB device types on the current device are to be obtained.|

**Return value**

| Type                                                    | Description                        |
| -------------------------------------------------------- | ---------------------------- |
| Array\<[PermissiveUsbDeviceType](#permissiveusbdevicetype)> | Array of disallowed USB device types.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { usbManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let result: Array<usbManager.PermissiveUsbDeviceType> = usbManager.getDisallowedPermissiveUsbDevices(wantTemp);
  console.info(`Succeeded in getting disallowed permissive USB devices. Result: ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get disallowed permissive USB devices. Code: ${err.code}, message: ${err.message}`);
}
```

## usbManager.getUsbSerialNumber

getUsbSerialNumber(busNum: number, devAddress: number): string

Obtains the serial number of a USB device.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_USB

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can be used only in the stage model.

**Parameters**

| Name | Type                                                    | Mandatory | Description |
| ------ | ------------------------------------------------------- | ---- | ----- |
| busNum  | number | Yes   | Bus number of the USB device, which can be obtained through the [getDevices](../apis-basic-services-kit/js-apis-usbManager.md#usbmanagergetdevices) interface. |
| devAddress  | number | Yes   | Address of the USB device, which can be obtained through the [getDevices](../apis-basic-services-kit/js-apis-usbManager.md#usbmanagergetdevices) interface. |

**Return value**

| Type                                                     | Description                         |
| -------------------------------------------------------- | ---------------------------- |
| string | Serial number of the USB device. |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 9200016  | Service timeout. |
| 9201055  | Failed to obtain the USB serial number. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { usbManager } from '@kit.MDMKit';
import { usbManager as baseUsbManager } from '@kit.BasicServicesKit';

// Obtain the list of USB devices connected to the host device.
let devicesList: Array<baseUsbManager.USBDevice> = baseUsbManager.getDevices();
console.info(`devicesList = ${devicesList}`);

// Select the target USB device (the first device is used as an example here), and take busNum and devAddress as input parameters.
let device: baseUsbManager.USBDevice = devicesList[0];

try {
  let result: string = usbManager.getUsbSerialNumber(device.busNum, device.devAddress);
  console.info(`Succeeded in getting USB serial number. Result: ${result}`);
} catch (err) {
  console.error(`Failed to get USB serial number. Code: ${err.code}, message: ${err.message}`);
}
```

## usbManager.addAllowedOpticalDiscDriveBurnUsbDevices

addAllowedOpticalDiscDriveBurnUsbDevices(usbDevices: Array\<UsbDevice>): Promise\<void>

Adds external USB optical disc drive burning devices to the allowed list. A maximum of 10000 allowed list entries can be added in a single call. Adding devices does not affect devices that are currently burning discs. The policy takes effect immediately, and optical disc drive burning can be controlled without re-plugging the optical disc drive device. After the allowed list is added, only the device types in the allowed list are permitted to burn discs. When the allowed list of optical disc drive burning devices is empty, optical disc drive burning is not controlled. This API uses an asynchronous callback to return the result.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_USB

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences:** This interface can be called normally on PC/2-in-1 devices, and returns error code 801 on other devices.

**Model restriction:** This interface can be used only in the stage model.

**Parameters**

| Name       | Type                              | Mandatory | Description                                                         |
| ---------- | --------------------------------- | --------- | ----------------------------------------------------------- |
| usbDevices | Array\<[UsbDevice](#usbdevice)>   | Yes   | Array of external USB optical disc drive devices to be added. The maximum array length is 10000, and the array cannot be empty.   |

**Return value**

| Type           | Description                         |
| -------------- | ---------------------------- |
| Promise\<void> | Promise that returns no value.    |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Possible causes:<br>1. The hardware does not support the capability.<br>2. The chip does not support the capability.<br>3. A dependent service feature is not supported. |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed.                               |
| 9200016  | Service timeout.                                             |
| 9200019  | The policy list has exceeded the limit.                      |

**Example**

```ts
import { usbManager } from '@kit.MDMKit';
import { BusinessError } from '@kit.BasicServicesKit';

let usbDevices: Array<usbManager.UsbDevice> = [{
  vendorId: 1234,
  productId: 5678,
  serial: 'SN123456789'
}];
usbManager.addAllowedOpticalDiscDriveBurnUsbDevices(usbDevices).then(() => {
  console.info('Succeeded in adding allowed optical disc drive burn USB devices.');
}).catch((err: BusinessError) => {
  console.error(`Failed to add allowed optical disc drive burn USB devices. Code is ${err.code}, message is ${err.message}`);
});
```

## usbManager.removeAllowedOpticalDiscDriveBurnUsbDevices

removeAllowedOpticalDiscDriveBurnUsbDevices(usbDevices: Array\<UsbDevice>): Promise\<void>

Removes devices from the allowed list of external USB optical disc drive burning devices. A maximum of 10000 entries can be removed at a time. Devices currently performing optical disc drive burning are not affected during removal. The policy takes effect immediately, and optical disc drive burning can be controlled without re-plugging the optical disc drive device. After removal, the removed device types are no longer allowed to burn. When the allowed list of optical disc drive burning devices is empty, optical disc drive burning is not controlled. This API uses a promise to return the result asynchronously.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_USB

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior difference:** This interface can be called normally on PC/2in1 devices, and returns error code 801 on other devices.

**Model restriction:** This interface can be used only in the stage model.

**Parameters**

| Name     | Type                              | Mandatory | Description                                                         |
| ---------- | --------------------------------- | ---- | ------------------------------------------------------------ |
| usbDevices | Array\<[UsbDevice](#usbdevice)>   | Yes   | Array of USB devices to remove. The maximum length of the array is 10000, and it cannot be empty.       |

**Return value**

| Type           | Description                         |
| -------------- | ----------------------------------- |
| Promise\<void> | Promise object that returns no value. |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Possible causes:<br>1. The hardware does not support the capability.<br>2. The chip does not support the capability.<br>3. A dependent service feature is not supported. |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed.                               |
| 9200016  | Service timeout.                                             |
| 9200019  | The policy list has exceeded the limit.                      |

**Example**

```ts
import { usbManager } from '@kit.MDMKit';
import { BusinessError } from '@kit.BasicServicesKit';

let usbDevices: Array<usbManager.UsbDevice> = [{
  vendorId: 1234,
  productId: 5678,
  serial: 'SN123456789'
}];
usbManager.removeAllowedOpticalDiscDriveBurnUsbDevices(usbDevices).then(() => {
  console.info('Succeeded in removing allowed optical disc drive burn USB devices.');
}).catch((err: BusinessError) => {
  console.error(`Failed to remove allowed optical disc drive burn USB devices. Code is ${err.code}, message is ${err.message}`);
});
```

## usbManager.getAllowedOpticalDiscDriveBurnUsbDevices

getAllowedOpticalDiscDriveBurnUsbDevices(queryPolicy?: common.QueryPolicy): Promise\<Array\<UsbDevice>>

Obtains the allowed list of external USB optical disc drive burn devices. This list can be used to evaluate the existing allowed list before modifying the policy, or to display the current allowed list status in the management UI. This API uses an asynchronous callback to return the result.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_USB

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can be used only in the stage model.

**Parameters**

| Name        | Type                                              | Mandatory | Description                                                         |
| ----------- | ------------------------------------------------- | --------- | ------------------------------------------------------------ |
| queryPolicy | [common.QueryPolicy](./js-apis-enterprise-common.md#querypolicy) | No   | Query policy. The query policy is specified by queryPolicy. The default value is common.QueryPolicy.SELF, which means to query the policy set by the current device management application. When common.QueryPolicy.ALL is passed in, the policy set on the current device can be queried.|

**Return value**

| Type                                       | Description                                       |
| ------------------------------------------ | ------------------------------------------ |
| Promise\<Array\<[UsbDevice](#usbdevice)>> | Promise object that returns an array of USB devices supporting CD/DVD burning. |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200016  | Service timeout.                                             |

**Example**

```ts
import { usbManager, common } from '@kit.MDMKit';
import { BusinessError } from '@kit.BasicServicesKit';

usbManager.getAllowedOpticalDiscDriveBurnUsbDevices(common.QueryPolicy.SELF).then((result: Array<usbManager.UsbDevice>) => {
  console.info(`Succeeded in getting allowed optical disc drive burn USB devices. Result: ${JSON.stringify(result)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get allowed optical disc drive burn USB devices. Code is ${err.code}, message is ${err.message}`);
});
```

## usbManager.setExternalStorageInterceptEnable

setExternalStorageInterceptEnable(enable: boolean): void

Sets the enable status of external storage device mount interception. After interception is successfully enabled, already mounted external storage devices are not affected. Newly inserted external storage devices will no longer be mounted automatically, and the [usbManager.setExternalStorageDeviceMountPolicy](#usbmanagersetexternalstoragedevicemountpolicy) interface must be called to mount them. After interception is disabled, unmounted external storage devices must be re-inserted before they can be mounted successfully. Intercepted external storage devices support only the types corresponding to [common.DiskType](./js-apis-enterprise-common.md#disktype).

> **NOTE**
>
> In a multi-MDM application scenario, the [strictest control](../../mdm/mdm-kit-multi-mdm.md#rule-1-security-first) rule is followed. As long as any MDM application enables interception, the system keeps interception enabled.

In the following cases, enabling external storage device mount interception (enable is true) reports a policy conflict:

1. A prohibited USB device type has already been added through the [addDisallowedPermissiveUsbDevices](#usbmanageradddisallowedpermissiveusbdevices) interface.
2. A prohibited USB device type has already been added through the [addDisallowedUsbDevices](#usbmanageradddisallowedusbdevices14) interface.
3. The device USB capability has already been disabled through the [setDisallowedPolicy](js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicydeprecated) interface.
4. An allowed USB device list has already been added through the [addAllowedUsbDevices](#usbmanageraddallowedusbdevices) interface.
5. The USB storage device write capability of a user has already been disabled through the [setDisallowedPolicyForAccount](js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicyforaccountdeprecated) interface.
6. The USB storage device access policy has been set to disabled through the [setUsbStorageDeviceAccessPolicy](#usbmanagersetusbstoragedeviceaccesspolicy) interface.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_USB

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can be used only in the stage model.

**Parameters**

| Name   | Type    | Mandatory | Description                                                         |
| ------ | ------- | --------- | ------------------------------------------------------------ |
| enable | boolean | Yes       | Whether to enable external storage device mount interception. The value **true** means to enable it, and **false** means to disable it. |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200010  | A conflict policy has been configured.                       |
| 9200016  | Service timeout.                                             |

**Example:**

```ts
import { usbManager } from '@kit.MDMKit';

try {
  usbManager.setExternalStorageInterceptEnable(true);
  console.info(`Succeeded in setting external storage intercept enable.`);
} catch (err) {
  console.error(`Failed to set external storage intercept enable. Code: ${err.code}, message: ${err.message}`);
}
```

## usbManager.isExternalStorageInterceptEnable

isExternalStorageInterceptEnable(queryPolicy?: common.QueryPolicy): boolean

Queries the enabled status of external storage device mount interception. This API can be used to query the current status before calling [setExternalStorageInterceptEnable](#usbmanagersetexternalstorageinterceptenable) to set interception, or to display the current interception status in the management UI.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_USB

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can be used only in the stage model.

**Parameters**

| Name        | Type                                              | Mandatory | Description                                                         |
| ----------- | ------------------------------------------------- | --------- | ------------------------------------------------------------ |
| queryPolicy | [common.QueryPolicy](./js-apis-enterprise-common.md#querypolicy) | No        | Query policy. Specifies the query policy through queryPolicy. The default value is common.QueryPolicy.SELF, which means querying the policy set by the current device management application. When common.QueryPolicy.ALL is passed in, the policy set on the current device can be queried. The value true indicates that external storage device mount interception is enabled; the value false indicates that it is not enabled. |

**Return value**

| Type    | Description                                                  |
| ------- | ------------------------------------------------------------ |
| boolean | true indicates that external storage device mount interception is enabled; false indicates that it is not enabled. |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Common Error Codes](../errorcode-universal.md).

| ID | Error Message                                                |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200016  | Service timeout.                                             |

**Example**

```ts
import { usbManager, common } from '@kit.MDMKit';

try {
  let result: boolean = usbManager.isExternalStorageInterceptEnable(common.QueryPolicy.SELF);
  console.info(`Succeeded in querying external storage intercept enable. Result: ${result}`);
} catch (err) {
  console.error(`Failed to query external storage intercept enable. Code: ${err.code}, message: ${err.message}`);
}
```

## usbManager.setExternalStorageDeviceMountPolicy

setExternalStorageDeviceMountPolicy(volumeId: string, policy: MountPolicy): void

Sets the mount policy for an external storage device, which can be mounted or unmounted. For an external storage device of the optical disc drive type ([common.DiskType](./js-apis-enterprise-common.md#disktype) is CD_DVD_BD), regardless of whether read-write mount ([MountPolicy](#mountpolicy).MOUNT_READ_WRITE) or read-only mount ([MountPolicy](#mountpolicy).MOUNT_READ_ONLY) is set, only read-only mount takes effect.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_USB

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can be used only in the stage model.

**Parameters**

| Name     | Type                          | Mandatory | Description                                                         |
| -------- | ----------------------------- | --------- | ------------------------------------------------------------ |
| volumeId | string                        | Yes       | Volume ID, which can be obtained through the [getExternalStorageDeviceInfos](#usbmanagergetexternalstoragedeviceinfos) interface. |
| policy   | [MountPolicy](#mountpolicy)   | Yes       | Mount policy.                                                   |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                |
| ------------- | ------------------------------------------------------------ |
| 201           | Permission verification failed. The application does not have the permission required to call the API. |
| 9200001       | The application is not an administrator application of the device. |
| 9200002       | The administrator application does not have permission to manage the device. |
| 9200012       | Parameter verification failed.                               |
| 9200016       | Service timeout.                                             |
| 9201056       | Invalid external storage mount policy.                       |

**Example**

```ts
import { usbManager } from '@kit.MDMKit';

try {
  // Replace the volume ID based on the actual situation.
  let volumeId: string = 'public:123456,1';
  let policy: usbManager.MountPolicy = usbManager.MountPolicy.MOUNT_READ_WRITE;
  usbManager.setExternalStorageDeviceMountPolicy(volumeId, policy);
  console.info(`Succeeded in setting external storage device mount policy.`);
} catch (err) {
  console.error(`Failed to set external storage device mount policy. Code: ${err.code}, message: ${err.message}`);
}
```

## usbManager.getExternalStorageDeviceInfos

getExternalStorageDeviceInfos(): Array\<common.ExternalStorageDeviceInfo>

Obtains the external storage device information of the current device. Before calling [setExternalStorageDeviceMountPolicy](#usbmanagersetexternalstoragedevicemountpolicy) to set the mount policy, you can call this API to obtain the volume ID and mount status of the external storage device. You can also display the list of currently connected external storage devices on the management UI. Returns an array of external storage device information, including the device type, mount path, volume ID, mount status, vendor ID, product ID, and serial number.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_USB

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can be used only in the stage model.

**Return value**

| Type                                                              | Description                         |
| ----------------------------------------------------------------- | ---------------------------- |
| Array\<[common.ExternalStorageDeviceInfo](./js-apis-enterprise-common.md#externalstoragedeviceinfo)> | Array of external storage device information.       |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200016  | Service timeout.                                             |

**Example**

```ts
import { usbManager, common } from '@kit.MDMKit';

try {
  let result: Array<common.ExternalStorageDeviceInfo> = usbManager.getExternalStorageDeviceInfos();
  console.info(`Succeeded in getting external storage device infos. Result: ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get external storage device infos. Code: ${err.code}, message: ${err.message}`);
}
```

## UsbDeviceId

Represents the USB device identity information.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can only be used in the stage model.

| Name     | Type  | Read-Only| Optional| Description    |
| --------- | ------ | ---- | ---- | -------- |
| vendorId  | number | No  | No| Vendor ID.|
| productId | number | No  | No| Product ID.|

## UsbDeviceType<sup>14+</sup>

Represents the USB device type information.

You can obtain the list of USB devices connected to the host device through the [getDevices](../apis-basic-services-kit/js-apis-usbManager.md#usbmanagergetdevices) API, and then find the type of the current device in the returned list.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can only be used in the stage model.

| Name      | Type                       | Read-Only| Optional| Description                                                        |
| ---------- | --------------------------- | ---- | ---- | ------------------------------------------------------------ |
| baseClass  | number                      | No  | No| Type code.<br>First, determine the type of descriptor to pass in based on this value. If the descriptor is **DEVICE**, this field takes the value of the **USBDevice.clazz** field; if the descriptor is **INTERFACE**, this field takes the value of the **USBDevice.configs.interfaces.clazz** field.<br>If the field value is 255 (indicating the device's type code is a vendor-defined code), calling the [addDisallowedUsbDevices](#usbmanageradddisallowedusbdevices14) or [removeDisallowedUsbDevices](#usbmanagerremovedisallowedusbdevices14) API to enable or disable the device will not take effect. If the field value is not defined in [defined-class-codes](https://www.usb.org/defined-class-codes), calling the [addDisallowedUsbDevices](#usbmanageradddisallowedusbdevices14) or [removeDisallowedUsbDevices](#usbmanagerremovedisallowedusbdevices14) API to enable or disable the device will also not take effect.|
| subClass   | number                      | No  | No| Subtype code.<br>First, determine the type of descriptor to pass in based on the value of baseClass. If the descriptor is **DEVICE**, this field takes the value of the **USBDevice.subClass** field; if the descriptor is **INTERFACE**, this field takes the value of the **USBDevice.configs.interfaces.subClass** field.<br>If the field value is 255 (indicating that the subtype code of the device is a vendor-defined code), calling the [addDisallowedUsbDevices](#usbmanageradddisallowedusbdevices14) or [removeDisallowedUsbDevices](#usbmanagerremovedisallowedusbdevices14) API to enable or disable the device will not take effect. If the field value is not defined in [defined-class-codes](https://www.usb.org/defined-class-codes), calling the [addDisallowedUsbDevices](#usbmanageradddisallowedusbdevices14) or [removeDisallowedUsbDevices](#usbmanagerremovedisallowedusbdevices14) API to enable or disable the device will also not take effect.|
| protocol   | number                      | No  | No| Protocol code.<br>First, determine the type of descriptor to pass in based on the value of baseClass. If the descriptor is **DEVICE**, this field takes the value of the **USBDevice.protocol** field; if the descriptor is **INTERFACE**, this field takes the value of the **USBDevice.configs.interfaces.protocol** field.<br>If the field value is 255 (indicating the device's protocol code is a vendor-defined code), calling the [addDisallowedUsbDevices](#usbmanageradddisallowedusbdevices14) or [removeDisallowedUsbDevices](#usbmanagerremovedisallowedusbdevices14) API to enable or disable the device will not take effect. If the field value is not defined in [defined-class-codes](https://www.usb.org/defined-class-codes), calling the [addDisallowedUsbDevices](#usbmanageradddisallowedusbdevices14) or [removeDisallowedUsbDevices](#usbmanagerremovedisallowedusbdevices14) API to enable or disable the device will also not take effect.|
| descriptor | [Descriptor](#descriptor14) | No  | No| USB descriptor.<br>If the value of **USBDevice.clazz** is **0**, you need to find the value of **USBDevice.configs.interfaces.clazz** in the Base Class column in [defined-class-codes](https://www.usb.org/defined-class-codes). The Descriptor Usage column in the row where the search result is located indicates the descriptor type to be transferred. If the value of Descriptor Usage is **Both**, both types can be transferred. If device-level disabling is required, transfer **DEVICE**. If interface-level disabling is required, transfer **INTERFACE**.<br>If the value of **USBDevice.clazz** is **255** (indicating the device's type code is a vendor-defined code), calling the [addDisallowedUsbDevices](#usbmanageradddisallowedusbdevices14) or [removeDisallowedUsbDevices](#usbmanagerremovedisallowedusbdevices14) API to enable or disable the device will not take effect. If the value of **USBDevice.clazz** is another value, search for the value in the Base Class column of [defined-class-codes](https://www.usb.org/defined-class-codes). The Descriptor Usage column in the row where the search result is located indicates the descriptor type to be transferred. If the value of Descriptor Usage is **Both**, both types can be transferred. If device-level disabling is required, transfer **DEVICE**. If interface-level disabling is required, transfer **INTERFACE**.|

## UsbPolicy

Enumerates the USB storage device access policies.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can only be used in the stage model.

| Name      | Value  | Description      |
| ---------- | ---- | ---------- |
| READ_WRITE | 0    | Read and write.|
| READ_ONLY  | 1    | Read only.    |
| DISABLED   | 2    | Disabled.    |

## Descriptor<sup>14+</sup>

Enumerates USB descriptors.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can only be used in the stage model.

| Name     | Value  | Description        |
| --------- | ---- | ------------ |
| INTERFACE | 0    | Interface descriptor.|
| DEVICE    | 1    | Device descriptor.|

## PermissiveUsbDeviceType

USB device type information. Partial field matching is supported.

- Compared with [UsbDeviceType](#usbdevicetype14), the **subClass**, **protocol**, and **descriptor** parameters in this API are optional, allowing for more flexible USB device disabling policies.

- Only the matching based on the **baseClass** parameter is supported.

- Multiple parameters can be configured. All parameters must be satisfied simultaneously for a match.

- You can obtain the list of USB devices connected to the host device through the [getDevices](../apis-basic-services-kit/js-apis-usbManager.md#usbmanagergetdevices) API, and then find the type of the current device in the returned list.

**Since:** 26.0.0

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can only be used in the stage model.

| Name      | Type                       | Read-Only| Optional| Description                                                        |
| ---------- | --------------------------- | ---- | ---- | ------------------------------------------------------------ |
| baseClass  | number                      | No  | No  | Type code. The value range is [0, 255].<br>If **descriptor** is **DEVICE**, this parameter takes the value of the **USBDevice.clazz** parameter; if **descriptor** is **INTERFACE**, this parameter takes the value of the **USBDevice.configs.interfaces.clazz** parameter.|
| subClass   | number                      | No  | Yes  | Subtype code. The value range is [0, 255].<br>If **descriptor** is **DEVICE**, this parameter takes the value of the **USBDevice.subClass** parameter; if **descriptor** is **INTERFACE**, this parameter takes the value of the **USBDevice.configs.interfaces.subClass** parameter.|
| protocol   | number                      | No  | Yes  | Protocol code. The value range is [0, 255].<br>If **descriptor** is **DEVICE**, this parameter takes the value of the **USBDevice.protocol** parameter; if **descriptor** is **INTERFACE**, this parameter takes the value of the **USBDevice.configs.interfaces.protocol** parameter.|
| descriptor | [Descriptor](#descriptor14) | No  | Yes  | USB descriptor.<br>If **USBDevice.clazz** is **0**, locate the value of **USBDevice.configs.interfaces.clazz** in the **Base Class** column of the [defined-class-codes](https://www.usb.org/defined-class-codes) table. The **Descriptor Usage** column of the corresponding row indicates the descriptor type to be passed. (If **Descriptor Usage** is **Both**, either type can be passed. You can pass **DEVICE** for device-level disabling, or **INTERFACE** for interface-level disabling.) If **USBDevice.clazz** is other than **0**, locate that value in the **Base Class** column of the [defined-class-codes](https://www.usb.org/defined-class-codes) table. The **Descriptor Usage** column of the corresponding row indicates the descriptor type to be passed. (If **Descriptor Usage** is **Both**, either type can be passed. Pass **DEVICE** for device-level disabling, or **INTERFACE** for interface-level disabling.)|

## UsbDevice

Defines the identification information of an external optical disc drive device.

**Since:** 26.0.1

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can be used only in the stage model.

| Name      | Type   | Read-only | Optional | Description     |
| --------- | ------ | ---- | ---- | -------- |
| vendorId  | number | No   | No | Vendor ID. |
| productId | number | No   | No | Product ID. |
| serial    | string | No   | Yes | Serial number. |

## MountPolicy

Enumerates the mount policies for external storage devices.

**Since:** 26.0.1

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This interface can be used only in the Stage model.

| Name             | Value | Description           |
| ---------------- | ----- | --------------------- |
| MOUNT_READ_WRITE | 0     | Mounted with read and write permissions. |
| MOUNT_READ_ONLY  | 1     | Mounted in read-only mode. |
| UNMOUNT          | 2     | Unmounted. |