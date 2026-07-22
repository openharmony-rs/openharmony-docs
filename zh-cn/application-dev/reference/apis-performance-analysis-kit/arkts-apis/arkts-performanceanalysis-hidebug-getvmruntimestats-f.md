# getVMRuntimeStats

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getVMRuntimeStats

```TypeScript
function getVMRuntimeStats(): GcStats
```

��ȡϵͳGCͳ����Ϣ��

**起始版本：** 12

<!--Device-hidebug-function getVMRuntimeStats(): GcStats--><!--Device-hidebug-function getVMRuntimeStats(): GcStats-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [GcStats](arkts-performanceanalysis-hidebug-gcstats-t.md) | ϵͳGCͳ����Ϣ�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let vMRuntimeStats: hidebug.GcStats = hidebug.getVMRuntimeStats();
console.info(`gc-count: ${vMRuntimeStats['ark.gc.gc-count']}`);
console.info(`gc-time: ${vMRuntimeStats['ark.gc.gc-time']}`);
console.info(`gc-bytes-allocated: ${vMRuntimeStats['ark.gc.gc-bytes-allocated']}`);
console.info(`gc-bytes-freed: ${vMRuntimeStats['ark.gc.gc-bytes-freed']}`);
console.info(`fullgc-longtime-count: ${vMRuntimeStats['ark.gc.fullgc-longtime-count']}`);

```

