# onPrinterInfoQuery (System API)

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## onPrinterInfoQuery

```TypeScript
function onPrinterInfoQuery(callback: PrinterInfoQueryCallback): void
```

Register event callback for the printer info queried.

**Since:** 24

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [PrinterInfoQueryCallback](arkts-basicservices-print-printerinfoquerycallback-t-sys.md) | Yes | The callback function for the printer info queried.<br>The callback function for the printer info queried. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application. |
