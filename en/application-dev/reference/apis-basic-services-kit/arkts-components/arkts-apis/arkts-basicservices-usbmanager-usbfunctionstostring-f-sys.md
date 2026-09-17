# usbFunctionsToString (System API)

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## usbFunctionsToString

```TypeScript
function usbFunctionsToString(funcs: FunctionType): string
```

Converts the USB function list in the numeric mask format to a string in Device mode. This API is applicable to scenarios where the USB function state needs to be displayed or saved as a string, for example, recording the current function configuration in logs or displaying the current function on the UI.

**Since:** 9

**Deprecated since:** 12

**Substitutes:** [getStringFromFunctions](arkts-basicservices-usbmanager-getstringfromfunctions-f-sys.md)(funcs: FunctionType)

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| funcs | [FunctionType](arkts-basicservices-usbmanager-functiontype-e-sys.md) | Yes | Numeric mask of the function list. Multiple functions can be combined through bitwise operations. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Function list in string format after conversion. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
