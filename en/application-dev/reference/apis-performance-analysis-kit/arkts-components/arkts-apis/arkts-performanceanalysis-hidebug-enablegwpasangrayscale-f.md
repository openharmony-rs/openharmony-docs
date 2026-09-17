# enableGwpAsanGrayscale

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## enableGwpAsanGrayscale

```TypeScript
function enableGwpAsanGrayscale(options?: GwpAsanOptions, duration?: number): void
```

Enables GWP-ASan to detect illegal behaviors in heap memory usage.

This API is used to dynamically configure and enable GWP-ASan to adapt to the custom GWP-ASan detection policy. The configuration takes effect after the application is restarted.

> **NOTE:** 
> 
> 1. If the number of GWP-ASan applications configured using this API exceeds the quota during device running, this API fails to be called and an error code is thrown. Use **try-catch** to capture exceptions to prevent the application from exiting abnormally.
> 
> 2. After the device restarts, the GWP-ASan parameters set by this API are invalid.
> 
> 3. This API involves cross-process communication and takes a long time. To avoid performance problems, you are advised not to call this API in the main thread. You can use [@ohos.taskpool](../../apis-arkts/arkts-apis/arkts-arkts-taskpool.md) or [@ohos.worker](../../apis-arkts/arkts-apis/arkts-arkts-worker-n.md) to enable asynchronous threads to avoid application frame freezing.

**Since:** 20

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [GwpAsanOptions](arkts-performanceanalysis-hidebug-gwpasanoptions-i.md) | No | GWP-ASan configuration items. If this parameter is not set, the default parameter is used. |
| duration | number | No | GWP-ASan duration, in days. The default value is 7. The value must be a positive integer greater than 0. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [11400114](../errorcode-hiviewdfx-hidebug.md#11400114-failed-to-enable-gwp-asan) | The number of GWP-ASAN applications of this device overflowed after last boot. |

**Examples**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { taskpool } from '@kit.ArkTS';
import { BusinessError } from '@kit.BasicServicesKit';

@Concurrent
function enableGwpAsanTask(): void {
  let options: hidebug.GwpAsanOptions = {
    alwaysEnabled: true,
    sampleRate: 2500,
    maxSimutaneousAllocations: 5000,
  };
  let duration: number = 4;
  hidebug.enableGwpAsanGrayscale(options, duration);
}

taskpool.execute(enableGwpAsanTask).then(() => {
  console.info(`Succeeded in enabling GWP-ASan.`);
}).catch((error: BusinessError) => {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to enable GWP-ASan. Code: ${err.code}, message: ${err.message}`);
})
```
