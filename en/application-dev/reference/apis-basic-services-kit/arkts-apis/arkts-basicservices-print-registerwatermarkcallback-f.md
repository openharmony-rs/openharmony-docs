# registerWatermarkCallback

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## registerWatermarkCallback

```TypeScript
function registerWatermarkCallback(callback: WatermarkCallback): void
```

Registers an event listener for forcible watermark processing. A forcible watermark is the watermark that must be added to printed files according to enterprise management policies. In enterprise management scenarios, when a watermark (such as a company logo or confidentiality level mark) needs to be forcibly added to printed files, you can use this API to register a watermark processing callback.

**Since:** 24

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_PRINT

**Model restriction:** This API can be used only in the stage model.

<!--Device-print-function registerWatermarkCallback(callback: WatermarkCallback): void--><!--Device-print-function registerWatermarkCallback(callback: WatermarkCallback): void-End-->

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [WatermarkCallback](arkts-basicservices-print-watermarkcallback-t.md) | Yes | Callback type used to register an event listener for forcible watermark processing. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';

let watermarkCallback: print.WatermarkCallback = (jobId: string, fd: number) => {
    console.info('Watermark callback triggered, jobId: ' + jobId + ', fd: ' + fd);
};

try {
    print.registerWatermarkCallback(watermarkCallback);
    console.info('registerWatermarkCallback success');
} catch (error) {
    console.error(`Failed to registerWatermarkCallback. Code: ${error.code}, message: ${error.message}`);
}
```
