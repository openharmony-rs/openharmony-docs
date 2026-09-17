# analyzePrintEvents (System API)

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## analyzePrintEvents

```TypeScript
function analyzePrintEvents(printerId: string, eventType: string): Promise<string>
```

Analyze print events.

**Since:** 24

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| printerId | string | Yes | Indicates the printer ID.<br>Printer ID to be analyzed. |
| eventType | string | Yes | Indicates the avant type.<br>Event types to be analyzed. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | the promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application. |
