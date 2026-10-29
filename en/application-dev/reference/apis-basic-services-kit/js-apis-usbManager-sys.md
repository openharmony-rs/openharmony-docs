# @ohos.usbManager (USB Manager) (System API)

<!--Kit: Basic Services Kit-->
<!--Subsystem: USB-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->

This module provides USB device management functions, including USB device list query, bulk data transfer, control transfer, and permission control on the host side as well as port management, and function switch and query on the device side. This module can be used to exchange data with USB peripherals, manage USB device permissions, and dynamically switch the USB device mode. As a system interface, this module provides the system-level permission control mechanism, USB function configuration capabilities on the device, and port role management capability. It helps the system app implement flexible USB device management and meet USB communication requirements in different service scenarios.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.usbManager (USB Manager)](js-apis-usbManager.md).

## Modules to Import

```ts
import { usbManager } from '@kit.BasicServicesKit';
```

## usbFunctionsFromString<sup>(deprecated)</sup>

usbFunctionsFromString(funcs: string): number

Converts the USB function list in the string format to a numeric mask in Device mode. This API can be used to convert the USB function list in the string format in the configuration file or input by the user to a numeric mask used internally by the system, so that USB functions can be set by calling APIs such as **setDeviceFunctions**.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. You are advised to use [getFunctionsFromString](#getfunctionsfromstring12) instead.

**System API**: This is a system API.

**System capability**: SystemCapability.USB.USBManager

**Parameters**

| Name| Type  | Mandatory| Description                  |
| ------ | ------ | ---- | ---------------------- |
| funcs  | string | Yes  | Function list in the string format. The options are as follows: **none**, **acm**, **ecm**, **hdc**, **mtp**, **ptp**, **rndis**, **midi**, **audio_source**, and **ncm**. Multiple functions can be separated by commas (,). If an invalid string is passed, an exception will be thrown.|

**Return value**

| Type  | Description              |
| ------ | ------------------ |
| number | Numeric mask of the function list after conversion.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                                               |
| -------- | ------------------------------------------------------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
// Define the USB function list in the string format.
let funcs: string = 'acm';
// Convert the string to a numeric mask.
let ret: number = usbManager.usbFunctionsFromString(funcs);
```

## usbFunctionsToString<sup>(deprecated)</sup>

usbFunctionsToString(funcs: FunctionType): string

Converts the USB function list in the numeric mask format to a string in Device mode. This API is applicable to scenarios where the USB function state needs to be displayed or saved as a string, for example, recording the current function configuration in logs or displaying the current function on the UI.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. You are advised to use [getStringFromFunctions](#getstringfromfunctions12) instead.

**System API**: This is a system API.

**System capability**: SystemCapability.USB.USBManager

**Parameters**

| Name| Type                         | Mandatory| Description             |
| ------ | ----------------------------- | ---- | ----------------- |
| funcs  | [FunctionType](#functiontype) | Yes  | Numeric mask of the function list. Multiple functions can be combined through bitwise operations.|

**Return value**

| Type  | Description                          |
| ------ | ------------------------------ |
| string | Function list in string format after conversion.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                                               |
| -------- | ------------------------------------------------------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
// Define the USB function type combination.
let funcs: usbManager.FunctionType = usbManager.FunctionType.ACM | usbManager.FunctionType.ECM;
// Convert the numeric mask into a string.
let ret: string = usbManager.usbFunctionsToString(funcs);
```

## setCurrentFunctions<sup>(deprecated)</sup>

setCurrentFunctions(funcs: FunctionType): Promise\<void\>

Sets the current USB function list in Device mode. This API uses a promise to return the result. After this API is successfully called, the USB functions of the device will be switched to the specified function list. This API is applicable to scenarios where the system app needs to dynamically switch the USB functions of the device and configure the working mode of the device.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. You are advised to use [setDeviceFunctions](#setdevicefunctions12) instead.

**System API**: This is a system API.

**System capability**: SystemCapability.USB.USBManager

**Parameters**

| Name| Type                         | Mandatory| Description             |
| ------ | ----------------------------- | ---- | ----------------- |
| funcs  | [FunctionType](#functiontype) | Yes  | Numeric mask of the function list. Multiple functions can be combined through bitwise operations.|

**Return value**

| Type               | Description         |
| ------------------- | ------------- |
| Promise\<void\> | Promise used to return the result. If the API is called successfully, no value is returned. If the call fails, an exception is thrown.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [USB Error Codes](errorcode-usb.md).

| ID| Error Message                                                                                               |
| -------- | ------------------------------------------------------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 14400002 | Permission denied. The HDC is disabled by the system. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
// Set the USB function type to HDC.
let funcs: usbManager.FunctionType = usbManager.FunctionType.HDC;
// Asynchronously set the current USB function.
usbManager.setCurrentFunctions(funcs).then(() => {
  console.info('usb setCurrentFunctions successfully.');
}).catch((err: BusinessError) => {
  console.error(`usb setCurrentFunctions failed. Code: ${err.code}, message: ${err.message}`);
});
```

## getCurrentFunctions<sup>(deprecated)</sup>

getCurrentFunctions(): FunctionType

Obtains the numeric mask combination for the USB function list in Device mode. This API can be used to check the USB function state, confirm the function configuration, or compare the status before and after function switching. When the developer mode is disabled, **undefined** is returned if no device is connected. Check whether the return value of the API is empty.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. You are advised to use [getDeviceFunctions](#getdevicefunctions12) instead.

**System API**: This is a system API.

**System capability**: SystemCapability.USB.USBManager

**Return value**

| Type                         | Description                             |
| ----------------------------- | --------------------------------- |
| [FunctionType](#functiontype) | Numeric mask combination for the USB function list. When the developer mode is disabled and no device is connected, **undefined** is returned. Check whether the return value is empty.|

**Example**

```ts
// Obtain the numeric mask of the USB function.
let ret: usbManager.FunctionType = usbManager.getCurrentFunctions();
```

## getPorts<sup>(deprecated)</sup>

getPorts(): Array\<USBPort\>

Obtains the list of all physical USB ports. This API can be used to enumerate USB ports, perform port management, diagnose the device connection status, or query the port configuration information. When the developer mode is disabled, **undefined** is returned if no device is connected. Check whether the return value of the API is empty.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. You are advised to use [getPortList](#getportlist12) instead.

**System API**: This is a system API.

**System capability**: SystemCapability.USB.USBManager

**Return value**

| Type                      | Description                 |
| -------------------------- | --------------------- |
| Array<[USBPort](#usbport)> | List of physical USB ports.|

**Example**

```ts
// Obtain all USB ports.
let ret: Array<usbManager.USBPort> = usbManager.getPorts();
```

## getSupportedModes<sup>(deprecated)</sup>

getSupportedModes(portId: number): PortModeType

Obtains the mask combination for the supported mode list of a given USB port. This method is applicable when the system app needs to query the USB-C port capabilities to determine whether a specific mode (such as UFP, DFP, or DRP) is supported. The return value is the mask combination of **PortModeType**. You can determine whether the port supports a specific mode using bitwise operations. The **PortModeType** values are as follows: **NONE (0)**: no mode; **UFP (1)**: upstream port mode, **dataRole** is **DEVICE**; **DFP (2)**: downstream port mode, **dataRole** is **HOST**; **DRP (3)**: dual-role mode, which can switch between **UFP** and **DFP**; **NUM_MODES (4)**: not supported currently. You can determine whether the port supports the combination of power roles and data transfer roles based on the return value.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. You are advised to use [getPortSupportModes](#getportsupportmodes12) instead.

**System API**: This is a system API.

**System capability**: SystemCapability.USB.USBManager

**Parameters**

| Name| Type  | Mandatory| Description    |
| ------ | ------ | ---- | -------- |
| portId | number | Yes  | USB port number. The value is a non-negative integer, which can be obtained from the port list returned by [getPortList](#getportlist12).|

**Return value**

| Type                         | Description                      |
| ----------------------------- | -------------------------- |
| [PortModeType](#portmodetype) | Mask combination for the supported mode list.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                                               |
| -------- | ------------------------------------------------------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
// Obtain the modes supported by port 0.
let ret: usbManager.PortModeType = usbManager.getSupportedModes(0);
```

## setPortRoles<sup>(deprecated)</sup>

setPortRoles(portId: number, powerRole: PowerRoleType, dataRole: DataRoleType): Promise\<void\>

Sets the roles of a specified port, including **powerRole** (for charging) and **dataRole** (for data transfer). This API uses a promise to return the result. After this API is successfully called, the port role will be switched to the specified role. This API can be used to dynamically switch the role of a USB port. When developer mode is disabled, the operation may fail if no device is connected. In this case, an exception is thrown.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. You are advised to use [setPortRoleTypes](#setportroletypes12) instead.

**System API**: This is a system API.

**System capability**: SystemCapability.USB.USBManager

**Parameters**

| Name   | Type                           | Mandatory| Description            |
| --------- | ------------------------------- | ---- | ---------------- |
| portId    | number                          | Yes  | USB port number. The value is a non-negative integer, which can be obtained from the port list returned by [getPortList](#getportlist12).|
| powerRole | [PowerRoleType](#powerroletype) | Yes  | Power role type. The options are **NONE**, **SOURCE** (providing power), and **SINK** (requiring external power supply).|
| dataRole  | [DataRoleType](#dataroletype)   | Yes  | Data transfer role. The options are **NONE**, **HOST**, and **DEVICE**.|

**Return value**

| Type               | Description         |
| ------------------- | ------------- |
| Promise\<void\> | Promise used to return the result. If the API is called successfully, no value is returned. If the call fails, an exception is thrown.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                                               |
| -------- | ------------------------------------------------------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
import {BusinessError} from '@kit.BasicServicesKit';
// Specify a port number.
let portId: number = 1;
// Set the port roles. Set powerRole to SOURCE and dataRole to HOST.
usbManager.setPortRoles(portId, usbManager.PowerRoleType.SOURCE, usbManager.DataRoleType.HOST).then(() => {
    console.info('usb setPortRoles successfully.');
}).catch((err: BusinessError) => {
    console.error(`usb setPortRoles failed. Code: ${err.code}, message: ${err.message}`);
});
```

## addDeviceAccessRight<sup>12+</sup>

addDeviceAccessRight(tokenId: string, deviceName: string): boolean

Adds the authorization for the app to access the device. System applications are granted the device access permission by default, and calling this API will not revoke the permission. This API can be used by system settings apps or device management apps to grant third-party apps the permission to access USB devices. The authorization takes effect immediately and is stored persistently. It remains valid even after the device is rebooted. The authorization applies to the specified USB device instance. Multiple apps can obtain the access permission for the same device at the same time.

[usbManager.requestRight](js-apis-usbManager.md#usbmanagerrequestright) triggers a dialog box to request user authorization. **addDeviceAccessRight** does not trigger a dialog box but directly adds the device access permission for the app.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_USB_CONFIG (available only for system applications) System apps can request this permission by specifying the **requestPermissions** field in the configuration file. For details, see [Open system_grant Permissions](../../security/AccessToken/permissions-for-all.md).

**System capability**: SystemCapability.USB.USBManager

**Parameters**

| Name    | Type  | Mandatory| Description           |
| ---------- | ------ | ---- | --------------- |
| tokenId    | string | Yes  | Unique ID of an app, which can be obtained using [bundleManager.getBundleInfoForSelf](../apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetbundleinfoforself).|
| deviceName | string | Yes  | Device name, in the format of **bus-port**, for example, **1-1**. The value can be found in the device list obtained using the [getDevices](js-apis-usbManager.md#usbmanagergetdevices) API.|

**Return value**

| Type   | Description                                                                     |
| ------- | ------------------------------------------------------------------------- |
| boolean | Permission addition result. The value **true** indicates that the access permission is added successfully; and the value **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                                               |
| -------- | ------------------------------------------------------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. <br>Applicable version: 18+|
| 202      | Permission denied. Normal application do not have permission to use system api. |
| 801      | Capability not supported.  <br>Applicable version: 18+|

**Example**

```ts
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
// Example device name. For primary use, obtain the device list by calling usbManager.getDevices() and then obtain the deviceName field from the device object.
let deviceName: string = '1-1';
// Define the tokenId variable.
let tokenId: string = '';
  // Add the USB device access permission for a specified app.
try {
  // Obtain the bundle information flag.
  let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_DEFAULT;
  // Asynchronously obtain the bundle information of the current app.
  bundleManager.getBundleInfoForSelf(bundleFlags).then((bundleInfo) => {
    console.info('testTag', 'getBundleInfoForSelf successfully. Data:', JSON.stringify(bundleInfo));
    // Obtain the access token ID of the app.
    let token = bundleInfo.appInfo.accessTokenId;
    tokenId = token.toString();
    // Add the device access permission.
    if (usbManager.addDeviceAccessRight(tokenId, deviceName)) {
      console.info(`Succeed in adding right`);
    }
  }).catch((err : BusinessError) => {
    console.error(`testTag getBundleInfoForSelf failed. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  console.error(`testTag failed. Code: ${err.code}, message: ${err.message}`);
}
```

## getFunctionsFromString<sup>12+</sup>

getFunctionsFromString(funcs: string): number

Converts the USB function list in the string format to a numeric mask in Device mode. This API can be used to convert the USB function list in the string format in the configuration file or input by the user to a numeric mask used internally by the system, so that USB functions can be set by calling APIs such as **setDeviceFunctions**.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_USB_CONFIG (available only for system applications) System apps can request this permission by specifying the **requestPermissions** field in the configuration file. For details, see [Open system_grant Permissions](../../security/AccessToken/permissions-for-all.md).

**System capability**: SystemCapability.USB.USBManager

**Parameters**

| Name| Type  | Mandatory| Description                  |
| ------ | ------ | ---- | ---------------------- |
| funcs  | string | Yes  | Function list in string format. The options are as follows: **none**, **acm**, **ecm**, **hdc**, **mtp**, **ptp**, **rndis**, **midi**, **audio_source**, and **ncm**. Multiple functions can be separated by commas (,).|

**Return value**

| Type  | Description              |
| ------ | ------------------ |
| number | Numeric mask of the function list after conversion.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                       |
| -------- | ------------------------------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. <br>Applicable version: 18+|
| 202      | Permission denied. Normal application do not have permission to use system api. |
| 801      | Capability not supported.  <br>Applicable version: 18+|

**Example**

```ts
// Define the USB function list in the string format.
let funcs: string = 'acm';
// Convert the string to a numeric mask.
let ret: number = usbManager.getFunctionsFromString(funcs);
```

## getStringFromFunctions<sup>12+</sup>

getStringFromFunctions(funcs: FunctionType): string

Converts the USB function list in the numeric mask format to a string in Device mode. This API is applicable to scenarios where the USB function state needs to be displayed or saved as a string, for example, recording the current function configuration in logs or displaying the current function on the UI.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_USB_CONFIG (available only for system applications) System apps can request this permission by specifying the **requestPermissions** field in the configuration file. For details, see [Open system_grant Permissions](../../security/AccessToken/permissions-for-all.md).

**System capability**: SystemCapability.USB.USBManager

**Parameters**

| Name| Type                         | Mandatory| Description             |
| ------ | ----------------------------- | ---- | ----------------- |
| funcs  | [FunctionType](#functiontype) | Yes  | Numeric mask of the function list. Multiple functions can be combined through bitwise operations. Some function values are not supported currently. For details, see [FunctionType](#functiontype).|

**Return value**

| Type  | Description                          |
| ------ | ------------------------------ |
| string | Function list in string format after conversion.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                                               |
| -------- | ------------------------------------------------------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. <br>Applicable version: 18+|
| 202      | Permission denied. Normal application do not have permission to use system api. |
| 801      | Capability not supported.  <br>Applicable version: 18+|

**Example**

```ts
// Define the USB function type combination.
let funcs: usbManager.FunctionType = usbManager.FunctionType.ACM | usbManager.FunctionType.ECM;
// Convert the numeric mask into a string.
let ret: string = usbManager.getStringFromFunctions(funcs);
```

## setDeviceFunctions<sup>12+</sup>

setDeviceFunctions(funcs: FunctionType): Promise\<void\>

Sets the current USB function list in Device mode. This API uses a promise to return the result. After this API is successfully called, the USB functions of the device will be switched to the specified function list. Some USB functions may not be supported by the current device. Before setting the USB functions, you are advised to query the list of functions supported by the device. When developer mode is disabled, the operation may fail if no device is connected. In this case, an exception is thrown. Function switching triggers re-enumeration of the USB devices, and the connected host may need to re-identify the device. Multiple functions can be set through bitwise operations. However, some functions may be mutually exclusive or have different priorities. For details about the restrictions, see the device specifications. The function setting may fail due to device incompatibility, insufficient permissions, or system restrictions. For details, see the error code description.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_USB_CONFIG (available only for system applications) System apps can request this permission by specifying the **requestPermissions** field in the configuration file. For details, see [Open system_grant Permissions](../../security/AccessToken/permissions-for-all.md).

**System capability**: SystemCapability.USB.USBManager

**Parameters**

| Name| Type                         | Mandatory| Description             |
| ------ | ----------------------------- | ---- | ----------------- |
| funcs  | [FunctionType](#functiontype) | Yes  | Numeric mask of the function list. Multiple functions can be combined through bitwise operations. Some functions may not be supported by the current device. For details, see [FunctionType](#functiontype).|

**Return value**

| Type               | Description         |
| ------------------- | ------------- |
| Promise\<void\> | Promise used to return the result. If the API is called successfully, no value is returned. If the call fails, an exception is thrown.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [USB Error Codes](errorcode-usb.md).

| ID| Error Message                                                                                               |
| -------- | ------------------------------------------------------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. <br>Applicable version: 18+|
| 202      | Permission denied. Normal application do not have permission to use system api. |
| 801      | Capability not supported.  <br>Applicable version: 18+|
| 14400002 | Permission denied. The HDC is disabled by the system. |
| 14400006 | Unsupported operation. The function is not supported. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
// Set the USB function type to HDC.
let funcs: usbManager.FunctionType = usbManager.FunctionType.HDC;
// Asynchronously set the device function.
usbManager.setDeviceFunctions(funcs).then(() => {
    console.info('usb setDeviceFunctions successfully.');
}).catch((err : BusinessError) => {
    console.error(`usb setDeviceFunctions failed. Code: ${err.code}, message: ${err.message}`);
});
```

## getDeviceFunctions<sup>12+</sup>

getDeviceFunctions(): FunctionType

Obtains the numeric mask combination for the USB function list in Device mode. This API can be used to check the USB function state, confirm the function configuration, or compare the status before and after function switching. When the developer mode is disabled, **undefined** is returned if no device is connected. Check whether the return value of the API is empty.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_USB_CONFIG (available only for system applications) System apps can request this permission by specifying the **requestPermissions** field in the configuration file. For details, see [Open system_grant Permissions](../../security/AccessToken/permissions-for-all.md).

**System capability**: SystemCapability.USB.USBManager

**Return value**

| Type                         | Description                             |
| ----------------------------- | --------------------------------- |
| [FunctionType](#functiontype) | Numeric mask combination for the USB function list.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                       |
| -------- | ------------------------------------------------------------------------------- |
| 201      | Permission verification failed. The application does not have the permission required to call the API. <br>Applicable version: 18+|
| 202      | Permission denied. Normal application do not have permission to use system api. |
| 801      | Capability not supported.  <br>Applicable version: 18+|

**Example**

```ts
// Obtain the numeric mask of the USB function.
let ret: usbManager.FunctionType = usbManager.getDeviceFunctions();
```

## getPortList<sup>12+</sup>

getPortList(): Array\<USBPort\>

Obtains the list of all physical USB ports. This API can be used to enumerate USB ports, perform port management, diagnose the device connection status, or query the port configuration information. When the developer mode is disabled, **undefined** is returned if no device is connected. Check whether the return value of the API is empty.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_USB_CONFIG (available only for system applications) System apps can request this permission by specifying the **requestPermissions** field in the configuration file. For details, see [Open system_grant Permissions](../../security/AccessToken/permissions-for-all.md).

**System capability**: SystemCapability.USB.USBManager

**Return value**

| Type                      | Description                 |
| -------------------------- | --------------------- |
| Array<[USBPort](#usbport)> | List of physical USB ports.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                                               |
| -------- | ------------------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed. The application does not have the permission required to call the API.  <br>Applicable version: 18+|
| 202      | Permission denied. Normal application do not have permission to use system api. |
| 801      | Capability not supported.  <br>Applicable version: 18+|

**Example**

```ts
// Obtain the USB port list.
let ret: Array<usbManager.USBPort> = usbManager.getPortList();
```

## getPortSupportModes<sup>12+</sup>

getPortSupportModes(portId: number): PortModeType

Obtains the mask combination for the supported mode list of a given USB port. This method is applicable when the system app needs to query the USB-C port capabilities to determine whether a specific mode (such as UFP, DFP, or DRP) is supported. When the developer mode is disabled, **undefined** is returned if no device is connected. Check whether the return value of the API is empty. For details about the enumerated values, see [PortModeType](#portmodetype).

> **NOTE**
>
> The initial APIs of this module are supported since API version 12.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_USB_CONFIG (available only for system applications) System apps can request this permission by specifying the **requestPermissions** field in the configuration file. For details, see [Open system_grant Permissions](../../security/AccessToken/permissions-for-all.md).

**System capability**: SystemCapability.USB.USBManager

**Parameters**

| Name| Type  | Mandatory| Description    |
| ------ | ------ | ---- | -------- |
| portId | number | Yes  | USB port number. The value can be obtained from the port list returned by [getPortList](#getportlist12).|

**Return value**

| Type                         | Description                      |
| ----------------------------- | -------------------------- |
| [PortModeType](#portmodetype) | Mask combination for the supported mode list.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [USB Error Codes](errorcode-usb.md).

| ID| Error Message                                                                                               |
| -------- | ------------------------------------------------------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 201      | Permission verification failed. The application does not have the permission required to call the API.  <br>Applicable version: 18+|
| 202      | Permission denied. Normal application do not have permission to use system api. |
| 801      | Capability not supported.  <br>Applicable version: 18+|

**Example**

```ts
// Obtain the supported mode of port 0.
let ret: usbManager.PortModeType = usbManager.getPortSupportModes(0);
```

## setPortRoleTypes<sup>12+</sup>

setPortRoleTypes(portId: number, powerRole: PowerRoleType, dataRole: DataRoleType): Promise\<void\>

Sets the role types of a specified port, including **powerRole** (for charging) and **dataRole** (for data transfer). This API uses a promise to return the result. After the API is successfully called, the power role and data transfer role of the port are switched to the specified roles. This API can be used to dynamically switch the role of a USB port. When developer mode is disabled, the operation may fail if no device is connected. In this case, an exception is thrown. For details about role constraints, see [USBPortStatus](#usbportstatus).

**Suggestions**
- You are advised to call [getPortList](#getportlist12) to obtain the port list and obtain a valid port ID.
- You are advised to call [getPortSupportModes](#getportsupportmodes12) to query the modes supported by the port and ensure that the configured role is supported.
- If the configured role is not supported by the port, the API call fails and error code 14400003 is returned.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_USB_CONFIG (available only for system applications) System apps can request this permission by specifying the **requestPermissions** field in the configuration file. For details, see [Open system_grant Permissions](../../security/AccessToken/permissions-for-all.md).

**System capability**: SystemCapability.USB.USBManager

**Parameters**

| Name   | Type                           | Mandatory| Description            |
| --------- | ------------------------------- | ---- | ---------------- |
| portId    | number                          | Yes  | Port number. The value can be obtained from the port list returned by [getPortList](#getportlist12).|
| powerRole | [PowerRoleType](#powerroletype) | Yes  | Power role type. The options are **NONE**, **SOURCE** (providing power), and **SINK** (requiring external power supply).|
| dataRole  | [DataRoleType](#dataroletype)   | Yes  | Data transfer role. The options are **NONE**, **HOST**, and **DEVICE**.|

**Return value**

| Type               | Description         |
| ------------------- | ------------- |
| Promise\<void\> | Promise used to return the result. If the API is called successfully, no value is returned. If the call fails, an exception is thrown.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [USB Error Codes](errorcode-usb.md).

| ID| Error Message                                                                                               |
| -------- | ------------------------------------------------------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 201      | Permission verification failed. The application does not have the permission required to call the API.  <br>Applicable version: 18+|
| 202      | Permission denied. Normal application do not have permission to use system api. |
| 801      | Capability not supported.  <br>Applicable version: 18+|
| 14400003 | Unsupported operation. The current device does not support port role switching. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Specify a port number.
let portId: number = 1;
// Set the port role types. Set powerRole to SOURCE and dataRole to HOST.
usbManager.setPortRoleTypes(portId, usbManager.PowerRoleType.SOURCE, usbManager.DataRoleType.HOST).then(() => {
  console.info('usb setPortRoleTypes successfully.');
}).catch((err : BusinessError) => {
  console.error(`usb setPortRoleTypes failed. Code: ${err.code}, message: ${err.message}`);
});
```

## addAccessoryRight<sup>14+</sup>

addAccessoryRight(tokenId: number, accessory: USBAccessory): void

Adds the permission to apps for accessing USB accessories. This API can be used by system apps to grant third-party apps the permission to access USB accessories. **usbManager.requestAccessoryRight** triggers a dialog box to request user authorization. **addAccessoryRight** does not trigger a dialog box but directly adds the device accessory access permission for the app. The authorization takes effect immediately and is stored persistently. It remains valid even after the device is rebooted. The authorization applies to the specified USB device accessory instance. Multiple apps can obtain the access permission for the same accessory at the same time. Unlike **requestAccessoryRight**, **addAccessoryRight** does not require user interaction and is suitable for scenarios where the system app automatically grants authorization.

> **NOTE**
>
> This API is supported since API version 14.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_USB_CONFIG (available only for system applications) System apps can request this permission by specifying the **requestPermissions** field in the configuration file. For details, see [Open system_grant Permissions](../../security/AccessToken/permissions-for-all.md).

**System capability**: SystemCapability.USB.USBManager

**Parameters**

| Name   | Type        | Mandatory| Description                    |
| --------- | ------------ | ---- | ------------------------ |
| tokenId   | number       | Yes  | Unique ID of an app, which can be obtained using [bundleManager.getBundleInfoForSelf](../apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetbundleinfoforself).|
| accessory | [USBAccessory](js-apis-usbManager.md#usbaccessory14) | Yes  | USB accessory object, including the accessory ID and attributes. You can obtain the accessory list by calling [getAccessoryList](js-apis-usbManager.md#usbmanagergetaccessorylist14). For details about the field definition, see [USBAccessory](js-apis-usbManager.md#usbaccessory14).|

**Return value**

| Type     | Description         |
| --------- | ------------- |
| void      | No value is returned. If the API is called successfully, the app is granted with the permission to access the USB accessories. If the call fails, an exception is thrown.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [USB Error Codes](errorcode-usb.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | The permission check failed. |
| 202      | Permission denied. Normal application do not have permission to use system api. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801      | Capability not supported.  <br>Applicable version: 18+|
| 14400004 | Service exception. Possible causes: 1. No accessory is plugged in. |
| 14400005 | Database operation exception. |

**Example**

```ts
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
async function addAccessoryRightExample() {
  // Add the USB accessory access permission for a specified app.
  try {
    // Obtain the USB accessory list.
    let accList: usbManager.USBAccessory[] = usbManager.getAccessoryList();
    if (accList.length === 0) {
      console.error('No USB accessory found');
      return;
    }
    // Set the bundle information flag.
    let flags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_APPLICATION |
    bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY;
    // Asynchronously obtain the bundle information of the current app.
    let bundleInfo = await bundleManager.getBundleInfoForSelf(flags);
    // Obtain the token ID of the app.
    let tokenId: number = bundleInfo.appInfo.accessTokenId;
    // Add the USB accessory access permission for the app.
    usbManager.addAccessoryRight(tokenId, accList[0]);
    console.info('addAccessoryRight success');
  } catch (error) {
    console.error(`addAccessoryRight error ${error.code}, message is ${error.message}`);
  }
}
```

## USBPort

Represents a USB port.

**System API**: This is a system API.

**System capability**: SystemCapability.USB.USBManager

| Name          | Type                           | Read-Only| Optional| Description                               |
| -------------- | ------------------------------- | ---- | ---- | ----------------------------------- |
| id             | number                          | No  | No  | Unique identifier of a USB port.                  |
| supportedModes | [PortModeType](#portmodetype)   | No  | No  | Numeric mask combination for the supported mode list. **status.currentMode** must be supported.|
| status         | [USBPortStatus](#usbportstatus) | No  | No  | USB port role information. **currentMode** must be within the range of **supportedModes**.|

## USBPortStatus

Enumerates USB port roles. **currentMode** indicates the current USB mode of the port. The value must be within the range of **supportedModes** of the USB port. **currentPowerRole** indicates the current power role, and **currentDataRole** indicates the current data transfer role. These fields are generally set as follows: In DFP mode, **dataRole** is **HOST**, and **powerRole** is **SOURCE**. In UFP mode, **dataRole** is **DEVICE**, and **powerRole** is **SINK**. The port status change is subject to hardware and system constraints. Some mode or role combinations may not be supported.

**System API**: This is a system API.

**System capability**: SystemCapability.USB.USBManager

| Name            | Type  | Read-Only| Optional| Description                  |
| ---------------- | ------ | ---- | ---- | ---------------------- |
| currentMode      | number | No  | No  | Current USB mode. For details, see [PortModeType](#portmodetype).       |
| currentPowerRole | number | No  | No  | Current power role of the device. For details, see [PowerRoleType](#powerroletype).    |
| currentDataRole  | number | No  | No  | Current data transfer role of the device. For details, see [DataRoleType](#dataroletype).|

## FunctionType

Enumerates USB device function types.

**System API**: This is a system API.

**System capability**: SystemCapability.USB.USBManager

| Name        | Value | Description      |
| ------------ | --- | ---------- |
| NONE         | 0   | No function.|
| ACM          | 1   | Abstract control model (ACM) with serial port communication function, which is used to simulate serial port devices.|
| ECM          | 2   | Ethernet control model (ECM) with Ethernet control function, which is used for network sharing. |
| HDC          | 4   | HarmonyOS device connector (HDC). |
| MTP          | 8   | Media transfer protocol (MTP).|
| PTP          | 16  | Picture transfer protocol (PTP).|
| RNDIS        | 32  | Remote network driver interface specification (RNDIS), which is used for network sharing (not supported currently).|
| MIDI         | 64  | Musical instrument digital interface (MIDI), which is used for communication with MIDI devices (not supported currently).|
| AUDIO_SOURCE | 128 | Audio source, which is used for audio data transfer (not supported currently).|
| NCM          | 256 | Network control model (NCM), which is used for high-speed network sharing (not supported currently). |

## PortModeType

Enumerates USB port mode types.

**System API**: This is a system API.

**System capability**: SystemCapability.USB.USBManager

| Name     | Value| Description                                                |
| --------- | -- | ---------------------------------------------------- |
| NONE      | 0  | None                                                |
| UFP       | 1  | Upstream facing port, which functions as the sink of power supply.                            |
| DFP       | 2  | Downstream facing port, which functions as the source of power supply.                            |
| DRP       | 3  | Dynamic reconfiguration port (DRP), which can function as the DFP (host) or UFP (device). It is not supported currently.|
| NUM_MODES | 4  | Not supported currently.                                        |

## PowerRoleType

Enumerates power role types.

**System API**: This is a system API.

**System capability**: SystemCapability.USB.USBManager

| Name  | Value| Description      |
| ------ | -- | ---------- |
| NONE   | 0  | None      |
| SOURCE | 1  | Power supply for external devices.|
| SINK   | 2  | External power supply.|

## DataRoleType

Enumerates data role types.

**System API**: This is a system API.

**System capability**: SystemCapability.USB.USBManager

| Name  | Value| Description        |
| ------ | -- | ------------ |
| NONE   | 0  | None        |
| HOST   | 1  | USB host.|
| DEVICE | 2  | USB device.|
