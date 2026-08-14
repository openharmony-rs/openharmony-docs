# setProcDumpInSharedOOM

## setProcDumpInSharedOOM

```TypeScript
function setProcDumpInSharedOOM(enable: boolean): void
```

将转储的堆快照由线程级改为进程级。 > **注意** > > 要想转储进程级的堆快照，调用该接口并传参true、进程OOM时发生的是SharedHeap OOM，两个条件缺一不可。 > > 该接口不影响其他场景下转储的堆快照内容。如：不会影响dumpJsRawHeapData的结果。 > > 该接口在应用的生命周期内可被多次调用，但仅最后一次调用的执行结果会生效。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-hidebug-function setProcDumpInSharedOOM(enable: boolean): void--><!--Device-hidebug-function setProcDumpInSharedOOM(enable: boolean): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 当进程发生SharedHeap OOM时，系统将依据该进程在其生命周期中最后一次调用该接口所记录的信息，转储相应级别的堆快照。 true：进程级。 false：线程级。 默认值：false。 |

## 示例

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

hidebug.setProcDumpInSharedOOM(true);
```

