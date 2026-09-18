# notifyWatermarkComplete

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## notifyWatermarkComplete

```TypeScript
function notifyWatermarkComplete(jobId: string, result: WatermarkHandleResult): void
```

Notify watermark complete.

**Since:** 24

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_PRINT

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| jobId | string | Yes | Indicates the job ID.<br>Print job ID in preview. |
| result | [WatermarkHandleResult](arkts-basicservices-print-watermarkhandleresult-e.md) | Yes | Indicates the result.<br>Watermark processing results. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';

let watermarkCallback: print.WatermarkCallback = (jobId: string, fd: number) => {
    console.info('Watermark callback triggered, jobId: ' + jobId + ', fd: ' + fd);

    try {
        // Notify the system that the watermark processing is successful.
        print.notifyWatermarkComplete(jobId, print.WatermarkHandleResult.WATERMARK_HANDLE_SUCCESS);
        console.info('notifyWatermarkComplete success');
    } catch (error) {
        console.error(`Failed to notifyWatermarkComplete. Code: ${error.code}, message: ${error.message}`);
    }
};

try {
    print.registerWatermarkCallback(watermarkCallback);
    console.info('registerWatermarkCallback success');
} catch (error) {
    console.error(`Failed to registerWatermarkCallback. Code: ${error.code}, message: ${error.message}`);
}
```
