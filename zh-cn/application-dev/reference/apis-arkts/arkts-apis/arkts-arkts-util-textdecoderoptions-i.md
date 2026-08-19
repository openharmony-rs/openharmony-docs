# TextDecoderOptions

描述解码相关的选项，包含 **fatal** 和 **ignoreBOM**。

**起始版本：** 11

<!--Device-util-interface TextDecoderOptions--><!--Device-util-interface TextDecoderOptions-End-->

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

## fatal

```TypeScript
fatal?: boolean
```

是否显示致命错误。值为 **true** 表示显示致命错误，值为 **false** 表示相反的情况。默认值为 **false**。

**类型：** boolean

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextDecoderOptions-fatal?: boolean--><!--Device-TextDecoderOptions-fatal?: boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## ignoreBOM

```TypeScript
ignoreBOM?: boolean
```

是否忽略 BOM。值为 **true** 表示忽略 BOM，值为 **false** 表示相反的情况。默认值为 **false**。

**类型：** boolean

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextDecoderOptions-ignoreBOM?: boolean--><!--Device-TextDecoderOptions-ignoreBOM?: boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

