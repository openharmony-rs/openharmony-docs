# MultithreadingDetectionOptions

多线程安全检测功能参数配置。

**起始版本：** 26.0.0

<!--Device-util-interface MultithreadingDetectionOptions--><!--Device-util-interface MultithreadingDetectionOptions-End-->

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

## abort

```TypeScript
abort?: boolean
```

若 abort 为 **true**，应用将崩溃；若 abort 为 **false**，应用将不崩溃。默认值为 **true**。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MultithreadingDetectionOptions-abort?: boolean--><!--Device-MultithreadingDetectionOptions-abort?: boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## frequency

```TypeScript
frequency?: number
```

多线程安全检测的采样频率。 该值必须为整数，最小为 **100**，最大为 **2147483647**（默认 **100**）。 该值应为整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MultithreadingDetectionOptions-frequency?: number--><!--Device-MultithreadingDetectionOptions-frequency?: number-End-->

**系统能力：** SystemCapability.Utils.Lang

## interval

```TypeScript
interval?: number
```

多线程安全检测的时间间隔（分钟）。 只有距离上次检测的时间超过此间隔时才会再次上报错误。 该值必须为 [0,1440] 范围内的整数（默认 5min）。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MultithreadingDetectionOptions-interval?: number--><!--Device-MultithreadingDetectionOptions-interval?: number-End-->

**系统能力：** SystemCapability.Utils.Lang

