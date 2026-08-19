# getVMRuntimeStat

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getVMRuntimeStat

```TypeScript
function getVMRuntimeStat(item: string): long
```

根据参数获取指定的系统GC统计信息。

**起始版本：** 23

<!--Device-hidebug-function getVMRuntimeStat(item: string): long--><!--Device-hidebug-function getVMRuntimeStat(item: string): long-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| item | string | 是 | 所需统计信息的类型。可获取的统计信息类型如下： "ark.gc.gc-count"：当前线程的GC次数。 "ark.gc.gc-time"：当前线程触发的GC总耗时，以ms为单位。 "ark.gc.gc-bytes-allocated"：当前线程Ark虚拟机已分配的内存大小，以B为单位。 "ark.gc.gc-bytes-freed"：当前线程GC成功回收的内存，以B为单位。 "ark.gc.fullgc-longtime-count"：当前线程超长fullGC次数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 系统GC统计信息，根据传入的参数，返回相应的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Possible causes: 1. Invalid parameter, a string parameter required. 2. Invalid parameter, unknown property. |

**示例**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  console.info(`gc-count: ${hidebug.getVMRuntimeStat('ark.gc.gc-count')}`);
  console.info(`gc-time: ${hidebug.getVMRuntimeStat('ark.gc.gc-time')}`);
  console.info(`gc-bytes-allocated: ${hidebug.getVMRuntimeStat('ark.gc.gc-bytes-allocated')}`);
  console.info(`gc-bytes-freed: ${hidebug.getVMRuntimeStat('ark.gc.gc-bytes-freed')}`);
  console.info(`fullgc-longtime-count: ${hidebug.getVMRuntimeStat('ark.gc.fullgc-longtime-count')}`);
} catch (error) {
  console.error(`error code: ${(error as BusinessError).code}, error msg: ${(error as BusinessError).message}`);
}
```

