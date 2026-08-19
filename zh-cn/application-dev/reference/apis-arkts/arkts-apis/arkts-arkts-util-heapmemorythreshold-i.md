# HeapMemoryThreshold

描述 GC 后触发已注册回调的堆内存预警阈值。

**起始版本：** 24

<!--Device-util-interface HeapMemoryThreshold--><!--Device-util-interface HeapMemoryThreshold-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { ArrayList } from '@kit.ArkTS';
import { ArrayListComparatorFn } from '@kit.ArkTS';
import { ArrayListForEachCb } from '@kit.ArkTS';
import { ArrayListReplaceCb } from '@kit.ArkTS';
import { util } from '@kit.ArkTS';
import { Deque } from '@kit.ArkTS';
import { DequeForEachCb } from '@kit.ArkTS';
import { HashMap } from '@kit.ArkTS';
import { HashMapCbFn } from '@kit.ArkTS';
import { HashSet } from '@kit.ArkTS';
import { HashSetCbFn } from '@kit.ArkTS';
import { LightWeightMap } from '@kit.ArkTS';
import { LightWeightMapCbFn } from '@kit.ArkTS';
import { LightWeightSet } from '@kit.ArkTS';
import { LightWeightSetForEachCb } from '@kit.ArkTS';
import { LinkedList } from '@kit.ArkTS';
import { LinkedListForEachCb } from '@kit.ArkTS';
import { List } from '@kit.ArkTS';
import { ListComparatorFn } from '@kit.ArkTS';
import { ListForEachCb } from '@kit.ArkTS';
import { ListReplaceCb } from '@kit.ArkTS';
import { PlainArray } from '@kit.ArkTS';
import { PlainArrayForEachCb } from '@kit.ArkTS';
import { Queue } from '@kit.ArkTS';
import { QueueForEachCb } from '@kit.ArkTS';
import { Stack } from '@kit.ArkTS';
import { StackForEachCb } from '@kit.ArkTS';
import { TreeMap } from '@kit.ArkTS';
import { TreeMapForEachCb } from '@kit.ArkTS';
import { TreeMapComparator } from '@kit.ArkTS';
import { TreeSet } from '@kit.ArkTS';
import { TreeSetForEachCb } from '@kit.ArkTS';
import { TreeSetComparator } from '@kit.ArkTS';
import { stream } from '@kit.ArkTS';
import { Vector } from '@kit.ArkTS';
import { JSON } from '@kit.ArkTS';
```

## localHeapThreshold

```TypeScript
localHeapThreshold?: number
```

该值为 70 到 95 之间的整数，表示 GC 后触发回调的 local 堆内存百分比阈值。超出此范围的值会被自动限制到有效范围内。 若未设置，则不会因 local 堆内存压力而触发回调。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HeapMemoryThreshold-localHeapThreshold?: number--><!--Device-HeapMemoryThreshold-localHeapThreshold?: number-End-->

**系统能力：** SystemCapability.Utils.Lang

## processHeapThreshold

```TypeScript
processHeapThreshold?: number
```

该值为 70 到 95 之间的整数，表示 GC 后触发回调的进程总堆内存百分比阈值。超出此范围的值会被自动限制到有效范围内。 若未设置，则不会因进程堆内存压力而触发回调。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HeapMemoryThreshold-processHeapThreshold?: number--><!--Device-HeapMemoryThreshold-processHeapThreshold?: number-End-->

**系统能力：** SystemCapability.Utils.Lang

## sharedHeapThreshold

```TypeScript
sharedHeapThreshold?: number
```

该值为 70 到 95 之间的整数，表示 GC 后触发回调的 shared 堆内存百分比阈值。超出此范围的值会被自动限制到有效范围内。 若未设置，则不会因 shared 堆内存压力而触发回调。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HeapMemoryThreshold-sharedHeapThreshold?: number--><!--Device-HeapMemoryThreshold-sharedHeapThreshold?: number-End-->

**系统能力：** SystemCapability.Utils.Lang

