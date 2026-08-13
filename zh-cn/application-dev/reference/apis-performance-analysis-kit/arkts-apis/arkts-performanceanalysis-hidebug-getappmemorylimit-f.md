# getAppMemoryLimit

## getAppMemoryLimit

```TypeScript
function getAppMemoryLimit(): MemoryLimit
```

获取应用程序进程的内存限制。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-hidebug-function getAppMemoryLimit(): MemoryLimit--><!--Device-hidebug-function getAppMemoryLimit(): MemoryLimit-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MemoryLimit](arkts-performanceanalysis-hidebug-memorylimit-i.md) | 应用程序进程内存限制。 |

## 示例

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let appMemoryLimit:hidebug.MemoryLimit = hidebug.getAppMemoryLimit();
console.info(`rssLimit: ${appMemoryLimit.rssLimit}, vssLimit: ${appMemoryLimit.vssLimit},` +
  `vmHeapLimit: ${appMemoryLimit.vmHeapLimit}, vmTotalHeapSize: ${appMemoryLimit.vmTotalHeapSize}`);
```

