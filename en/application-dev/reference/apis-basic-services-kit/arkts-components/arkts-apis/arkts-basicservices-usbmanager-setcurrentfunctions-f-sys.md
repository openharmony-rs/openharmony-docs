# setCurrentFunctions (System API)

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## setCurrentFunctions

```TypeScript
function setCurrentFunctions(funcs: FunctionType): Promise<void>
```

Sets the current USB function list in Device mode. This API uses a promise to return the result. After this API is successfully called, the USB functions of the device will be switched to the specified function list. This API is applicable to scenarios where the system app needs to dynamically switch the USB functions of the device and configure the working mode of the device.

**Since:** 9

**Deprecated since:** 12

**Substitutes:** [setDeviceFunctions](arkts-basicservices-usbmanager-setdevicefunctions-f-sys.md)(funcs: FunctionType)

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| funcs | [FunctionType](arkts-basicservices-usbmanager-functiontype-e-sys.md) | Yes | Numeric mask of the function list. Multiple functions can be combined through bitwise operations. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. If the API is called successfully, no value is returned. If the call fails, an exception is thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [14400002](../errorcode-usb.md#14400002-hdc-disabled) | Permission denied. The HDC is disabled by the system. |
