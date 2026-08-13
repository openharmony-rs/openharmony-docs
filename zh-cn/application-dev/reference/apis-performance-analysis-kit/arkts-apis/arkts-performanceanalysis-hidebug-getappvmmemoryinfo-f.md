# getAppVMMemoryInfo

## getAppVMMemoryInfo

```TypeScript
function getAppVMMemoryInfo(): VMMemoryInfo
```

获取VM内存相关信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-hidebug-function getAppVMMemoryInfo(): VMMemoryInfo--><!--Device-hidebug-function getAppVMMemoryInfo(): VMMemoryInfo-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [VMMemoryInfo](arkts-performanceanalysis-hidebug-vmmemoryinfo-i.md) | 返回VM内存信息。 |

## 示例

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let vmMemory: hidebug.VMMemoryInfo = hidebug.getAppVMMemoryInfo();
console.info(`totalHeap = ${vmMemory.totalHeap}, heapUsed = ${vmMemory.heapUsed},` +
  `allArraySize = ${vmMemory.allArraySize}` );
```

