# @ohos.util.Vector

## 导入模块

```TypeScript
import { Vector } from '@kit.ArkTS';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Vector](arkts-arkts-util-vector-vector-c.md) | Vector是基于数组实现的线性数据结构。当Vector的内存用完时，会自动分配一块更大的连续内存区域，并将所有元素复制到新内存区域，回收当前内存区域。Vector可用于高效访问元素。Vector和[ArrayList](arkts-util-arraylist.md)都是基于数组实现，但Vector提供了更多的数组操作接口。两者都可以动态调整容量，Vector每次扩容为原来的两倍，ArrayList每次扩容为原来的1.5倍。**推荐使用场景：** 当数据量较大时，推荐使用Vector。文档中使用了泛型，涉及以下泛型标记符：  - T：Type，类 > **说明**  >  > - 此模块提供的接口从API version 9开始废弃。建议使用  > [@ohos.util.ArrayList](arkts-util-arraylist.md)。 |

