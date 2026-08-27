# getPss

## 导入模块

```TypeScript
```

## getPss

```TypeScript
function getPss() : bigint
```

获取应用进程实际使用的物理内存大小。接口实现方式：读取/proc/{pid}/smaps_rollup节点中的Pss与SwapPss值并求和。

> **注意**：
> 
> 由于/proc/{pid}/smaps_rollup的读取耗时较长，建议不要在主线程中使用该接口，可通过[@ohos.taskpool](../../apis-arkts/arkts-apis/arkts-taskpool.md)或
> [@ohos.worker](../../apis-arkts/arkts-apis/arkts-arkts-worker-n.md)开启异步线程以避免应用出现卡顿。

**起始版本：** 8

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | 返回应用进程实际使用的物理内存大小，单位为KB。 |

**示例**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let pss: bigint = hidebug.getPss();
console.info(`pss = ${pss}`);
```
