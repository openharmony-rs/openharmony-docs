# getGraphicsMemorySummary

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getGraphicsMemorySummary

```TypeScript
function getGraphicsMemorySummary(interval?: number): Promise<GraphicsMemorySummary>
```

Obtains the GPU memory data of an application. This API uses a promise to return the result.

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| interval | number | No | Validity period of the cached GPU memory data, in seconds. Default value: **300** The value ranges from 2 to 3600. If the input value is out of the value range, the default value will be used.<br>If the cached GPU memory data exists for a period longer than the value of this parameter, the latest GPU memory data is obtained and the cache value is updated. Otherwise, the cache value is directly obtained. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[GraphicsMemorySummary](arkts-performanceanalysis-hidebug-graphicsmemorysummary-i.md)&gt; | Promise used to return the GPU memory data of the application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [11400104](../errorcode-hiviewdfx-hidebug-cpuusage.md#11400104-abnormal-cpu-usage) | Failed to get the application memory due to a remote exception. |

**Examples**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

hidebug.getGraphicsMemorySummary().then((ret: hidebug.GraphicsMemorySummary) => {
  console.info(`get graphicsMemory gl: ${ret.gl} graph: ${ret.graph}.`)
}).catch((error: BusinessError) => {
  console.error(`error code: ${error.code}, error msg: ${error.message}.`);
})
```
