# getPrivateDirty

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getPrivateDirty

```TypeScript
function getPrivateDirty() : bigint
```

获取进程的私有脏内存大小。读取/proc/{pid}/smaps_rollup中的Private_Dirty值。 > **注意** > > 由于/proc/{pid}/smaps_rollup的读取耗时较长，建议不要在主线程中使用该接口，可通过@ohos.taskpool或@ohos.worker开启异步线程以避免应用出现卡顿。

**起始版本：** 23

<!--Device-hidebug-function getPrivateDirty() : bigint--><!--Device-hidebug-function getPrivateDirty() : bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | 返回进程的私有脏内存大小，单位为KB。 |

**示例**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let privateDirty: bigint = hidebug.getPrivateDirty();
console.info(`privateDirty = ${privateDirty}`);
```

