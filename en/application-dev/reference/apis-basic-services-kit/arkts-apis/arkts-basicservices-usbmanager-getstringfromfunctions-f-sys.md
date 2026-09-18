# getStringFromFunctions (System API)

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## getStringFromFunctions

```TypeScript
function getStringFromFunctions(funcs: FunctionType): string
```

Converts the USB function list in the numeric mask format to a string in Device mode. This API is applicable to scenarios where the USB function state needs to be displayed or saved as a string, for example, recording the current function configuration in logs or displaying the current function on the UI.

**Since:** 12

**Required permissions:** ohos.permission.MANAGE_USB_CONFIG

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| funcs | [FunctionType](arkts-basicservices-usbmanager-functiontype-e-sys.md) | Yes | Numeric mask of the function list. Multiple functions can be combined through bitwise operations. Some function values are not supported currently. For details, see [FunctionType](arkts-basicservices-usbmanager-functiontype-e-sys.md). |

**Return value:**

| Type | Description |
| --- | --- |
| string | Function list in string format after conversion. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 18 and later |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied. Normal application do not have permission to use system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |
