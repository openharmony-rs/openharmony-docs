# getFunctionsFromString (System API)

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## getFunctionsFromString

```TypeScript
function getFunctionsFromString(funcs: string): number
```

Converts the USB function list in the string format to a numeric mask in Device mode. This API can be used to convert the USB function list in the string format in the configuration file or input by the user to a numeric mask used internally by the system, so that USB functions can be set by calling APIs such as **setDeviceFunctions**.

**Since:** 12

**Required permissions:** ohos.permission.MANAGE_USB_CONFIG

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| funcs | string | Yes | Function list in string format. The options are as follows: **none**, **acm**, **ecm**, **hdc**, **mtp**, **ptp**, **rndis**, **midi**, **audio_source**, and **ncm**. Multiple functions can be separated by commas (,). |

**Return value:**

| Type | Description |
| --- | --- |
| number | Numeric mask of the function list after conversion. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 18 and later |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied. Normal application do not have permission to use system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |
