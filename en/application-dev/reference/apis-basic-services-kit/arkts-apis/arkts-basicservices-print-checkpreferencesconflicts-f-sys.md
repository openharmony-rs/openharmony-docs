# checkPreferencesConflicts (System API)

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## checkPreferencesConflicts

```TypeScript
function checkPreferencesConflicts(printerId: string, changedType: string, preferences: PrinterPreferences): Promise<string[]>
```

Check preferences conflicts.

**Since:** 24

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| printerId | string | Yes | Indicates the printer ID.<br>Added printer ID in the system. |
| changedType | string | Yes | Indicates the field name that was modified on the printing interface.<br>Field names set in the print preview or preferences interface. |
| preferences | [PrinterPreferences](arkts-basicservices-print-printerpreferences-i.md) | Yes | Indicates the selected value on the printing interface.<br>The selected value on the printinginterface. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string[]&gt; | Promise that resolves with the conflicting field names. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application. |
| [13100005](../errorcode-print.md#13100005-invalid-printer) | Can not find the printer or printer's ppd file in system. |
