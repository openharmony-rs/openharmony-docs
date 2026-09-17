# usbFunctionsFromString (System API)

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## usbFunctionsFromString

```TypeScript
function usbFunctionsFromString(funcs: string): number
```

Converts the USB function list in the string format to a numeric mask in Device mode. This API can be used to convert the USB function list in the string format in the configuration file or input by the user to a numeric mask used internally by the system, so that USB functions can be set by calling APIs such as **setDeviceFunctions**.

**Since:** 9

**Deprecated since:** 12

**Substitutes:** [getFunctionsFromString](arkts-basicservices-usbmanager-getfunctionsfromstring-f-sys.md)(funcs: string)

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| funcs | string | Yes | Function list in the string format. The options are as follows: **none**, **acm**, **ecm**, **hdc**, **mtp**, **ptp**, **rndis**, **midi**, **audio_source**, and **ncm**. Multiple functions can be separated by commas (,). If an invalid string is passed, an exception will be thrown. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Numeric mask of the function list after conversion. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
