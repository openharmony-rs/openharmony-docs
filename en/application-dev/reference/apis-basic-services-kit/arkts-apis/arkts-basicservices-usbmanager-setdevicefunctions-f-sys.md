# setDeviceFunctions (System API)

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## setDeviceFunctions

```TypeScript
function setDeviceFunctions(funcs: FunctionType): Promise<void>
```

Sets the current USB function list in Device mode. This API uses a promise to return the result. After this API is successfully called, the USB functions of the device will be switched to the specified function list. Some USB functions may not be supported by the current device. Before setting the USB functions, you are advised to query the list of functions supported by the device. When developer mode is disabled, the operation may fail if no device is connected. In this case, an exception is thrown. Function switching triggers re-enumeration of the USB devices, and the connected host may need to re-identify the device. Multiple functions can be set through bitwise operations. However, some functions may be mutually exclusive or have different priorities. For details about the restrictions, see the device specifications. The function setting may fail due to device incompatibility, insufficient permissions, or system restrictions. For details, see the error code description.

**Since:** 12

**Required permissions:** ohos.permission.MANAGE_USB_CONFIG

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| funcs | [FunctionType](arkts-basicservices-usbmanager-functiontype-e-sys.md) | Yes | Numeric mask of the function list. Multiple functions can be combined through bitwise operations. Some functions may not be supported by the current device. For details, see [FunctionType](arkts-basicservices-usbmanager-functiontype-e-sys.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. If the API is called successfully, no value is returned. If the call fails, an exception is thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 18 and later |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied. Normal application do not have permission to use system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |
| [14400002](../errorcode-usb.md#14400002-hdc-disabled) | Permission denied. The HDC is disabled by the system. |
| [14400006](../errorcode-usb.md#14400006-usb-device-function-unsupported) | Unsupported operation. The function is not supported. |
