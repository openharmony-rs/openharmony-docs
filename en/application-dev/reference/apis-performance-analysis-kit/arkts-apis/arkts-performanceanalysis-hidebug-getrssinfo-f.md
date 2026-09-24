# getRssInfo

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getRssInfo

```TypeScript
function getRssInfo(): RssInfo
```

Obtains the physical memory usage of the application process. Reads data from the **\/proc/{pid}/status** node.

> **NOTE:** 
> 
> Reading the /proc/{pid}/status node takes a short time. The value obtained by this API is slightly different from
> the **rss** value obtained by the [hidebug.getAppNativeMemInfo](arkts-performanceanalysis-hidebug-getappnativememinfo-f.md) API. However,
> this API is more lightweight. To avoid frame loss or frame freezing, you are advised to use this API.

**Since:** 24

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Return value:**

| Type | Description |
| --- | --- |
| [RssInfo](arkts-performanceanalysis-hidebug-rssinfo-i.md) | Physical memory information about the application process. |

**Examples**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let rssInfo: hidebug.RssInfo = hidebug.getRssInfo();
console.info(`rss: ${rssInfo.rss}, swapRss: ${rssInfo.swapRss}`);
```
