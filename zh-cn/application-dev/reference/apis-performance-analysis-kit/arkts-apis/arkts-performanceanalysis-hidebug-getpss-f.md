# getPss

## getPss

```TypeScript
function getPss() : bigint
```

获取应用进程实际使用的物理内存大小。接口实现方式：读取/proc/{pid}/smaps_rollup节点中的Pss与SwapPss值并求和。 > **注意** > > 由于/proc/{pid}/smaps_rollup的读取耗时较长，建议不要在主线程中使用该接口，可通过@ohos.taskpool或@ohos.worker开启异步线程以避免应用出现卡顿。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-hidebug-function getPss() : bigint--><!--Device-hidebug-function getPss() : bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | 返回应用进程实际使用的物理内存大小，单位为KB。 |

## 示例

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let pss: bigint = hidebug.getPss();
console.info(`pss = ${pss}`);
```

