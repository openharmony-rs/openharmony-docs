# getSystemCpuUsage

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getSystemCpuUsage

```TypeScript
function getSystemCpuUsage(): number
```

Obtains the CPU usage of the system.

> **NOTE:** 
> 
> This API involves cross-process communication and takes a long time. To avoid performance problems, you are
> advised not to call this API in the main thread.

**Since:** 12

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Return value:**

| Type | Description |
| --- | --- |
| number | CPU usage of the system. For example, if the CPU usage is **50%**, **0.5** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [11400104](../errorcode-hiviewdfx-hidebug-cpuusage.md#11400104-abnormal-cpu-usage) | The status of the system CPU usage is abnormal. |

**Examples**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  console.info(`getSystemCpuUsage: ${hidebug.getSystemCpuUsage()}`)
} catch (error) {
  console.error(`error code: ${(error as BusinessError).code}, error msg: ${(error as BusinessError).message}`);
}
```
