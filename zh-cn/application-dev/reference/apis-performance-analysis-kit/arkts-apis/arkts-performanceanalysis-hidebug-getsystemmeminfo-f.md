# getSystemMemInfo

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getSystemMemInfo

```TypeScript
function getSystemMemInfo(): SystemMemInfo
```

获取系统内存信息。读取/proc/meminfo节点的数据。

**起始版本：** 23

<!--Device-hidebug-function getSystemMemInfo(): SystemMemInfo--><!--Device-hidebug-function getSystemMemInfo(): SystemMemInfo-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SystemMemInfo](arkts-performanceanalysis-hidebug-systemmeminfo-i.md) | 系统内存信息。 |

**示例**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let systemMemInfo: hidebug.SystemMemInfo = hidebug.getSystemMemInfo();

console.info(`totalMem: ${systemMemInfo.totalMem}, freeMem: ${systemMemInfo.freeMem}, ` +
  `availableMem: ${systemMemInfo.availableMem}`);
```

