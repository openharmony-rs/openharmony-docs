# getPrinterDefaultPreferences (System API)

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## getPrinterDefaultPreferences

```TypeScript
function getPrinterDefaultPreferences(printerId: string): Promise<PrinterPreferences>
```

Get default preferences by printer ID.

**Since:** 24

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| printerId | string | Yes | Indicates the printer ID.<br>Added printer ID in the system. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PrinterPreferences](arkts-basicservices-print-printerpreferences-i.md)&gt; | Promise that resolves with the default preferences of the printer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application. |
| [13100005](../errorcode-print.md#13100005-invalid-printer) | Can not find the printer or printer's ppd file in system. |
