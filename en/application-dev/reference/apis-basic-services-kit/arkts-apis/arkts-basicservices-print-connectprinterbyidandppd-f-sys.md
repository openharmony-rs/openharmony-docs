# connectPrinterByIdAndPpd (System API)

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## connectPrinterByIdAndPpd

```TypeScript
function connectPrinterByIdAndPpd(printerId: string, protocol: string, ppdName: string): Promise<void>
```

Connect a printer by the printer ID and ppd.

**Since:** 24

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**Model restriction:** This API can be used only in the stage model.

<!--Device-print-function connectPrinterByIdAndPpd(printerId: string, protocol: string, ppdName: string): Promise<void>--><!--Device-print-function connectPrinterByIdAndPpd(printerId: string, protocol: string, ppdName: string): Promise<void>-End-->

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| printerId | string | Yes | Indicates the printer ID of the printer to be connected. |
| protocol | string | Yes | Indicates the protocol of the printer to be connected. |
| ppdName | string | Yes | Indicates the PPD name of the printer to be connected. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application. |
| [13100003](../errorcode-print.md#13100003-print-service-exception) | Add the printer to system failed. |
