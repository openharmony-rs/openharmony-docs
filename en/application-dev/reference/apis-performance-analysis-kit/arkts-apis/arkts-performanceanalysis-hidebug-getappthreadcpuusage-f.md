# getAppThreadCpuUsage

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getAppThreadCpuUsage

```TypeScript
function getAppThreadCpuUsage(): ThreadCpuUsage[]
```

Obtains the CPU usage of application threads.

> **NOTE:** 
> 
> This API involves cross-process communication and takes a long time. To avoid performance problems, you are
> advised not to call this API in the main thread.

**Since:** 12

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Return value:**

| Type | Description |
| --- | --- |
| [ThreadCpuUsage](arkts-performanceanalysis-hidebug-threadcpuusage-i.md)[] | CPU usage of all threads of the current application process. |

**Examples**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let appThreadCpuUsage: hidebug.ThreadCpuUsage[] = hidebug.getAppThreadCpuUsage();
for (let i = 0; i < appThreadCpuUsage.length; i++) {
  console.info(`threadId=${appThreadCpuUsage[i].threadId}, cpuUsage=${appThreadCpuUsage[i].cpuUsage}`);
}
```
