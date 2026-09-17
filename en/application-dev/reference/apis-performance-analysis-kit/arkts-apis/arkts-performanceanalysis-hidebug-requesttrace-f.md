# requestTrace

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## requestTrace

```TypeScript
function requestTrace(config: RequestTraceConfig): Promise<string>
```

Obtains the trace information of the current process, including the application tag, image window tag, CPU scheduling, and binder kernel information. This API uses a promise to return the result.

A maximum of three .sys files returned by trace collection can be stored in the directory. If the number of .sys files is greater than or equal to three, error code 11400120 is reported when the API is called again.

This API cannot be used in the input method applications.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [RequestTraceConfig](arkts-performanceanalysis-hidebug-requesttraceconfig-i.md) | Yes | Trace collection configuration information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the application sandbox path of the .sys trace file. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [11400104](../errorcode-hiviewdfx-hidebug-cpuusage.md#11400104-abnormal-cpu-usage) | Remote service exception. |
| [11400120](../errorcode-hiviewdfx-hidebug-trace.md#11400120-trace-file-storage-limit-reached) | Trace storage limit reached. |
| [11400302](../errorcode-hiviewdfx-hidebug-trace.md#11400302-trace-collection-exceeds-the-resource-quota) | Resource unavailable. |

**Examples**

```TypeScript
import { hidebug, hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  hidebug.requestTrace({
    identifier: "trace_name",
    bufferSizeKb: 1024,
    durationMs: 1000,
    reserved: 0,
  }).then((tracePath: string) => {
    hilog.info(0x0000, 'hidebug', `tracePath: ${tracePath}`)
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'hidebug', `error code: ${err.code}, message: ${err.message}`)
  })
} catch (error) {
  hilog.error(0x0000, 'hidebug', `error code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`)
}
```
