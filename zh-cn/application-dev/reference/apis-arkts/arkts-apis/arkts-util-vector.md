# @ohos.util.Vector

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Vector](arkts-arkts-util-vector-vector-c.md) | Vector是一种线性数据结构，底层基于数组实现，解决了需要动态扩容、高效随机访问的数据存储问题。 当Vector的内存用尽时，会自动分配更大的连续内存区，将原先的元素复制到新的内存区，并释放旧的内存区。 使用Vector能够高效快速地访问元素，其2倍扩容策略减少了频繁的内存重分配，同时丰富的操作接口提供了更灵活的数据管理能力。 Vector和[ArrayList](arkts-arkts-util-arraylist-arraylist-c.md#arraylist)相似，都是基于数组实现，但Vector提供了更多操作数组的接口。 它们都可以动态调整容量，但Vector每次扩容增加1倍，ArrayList只扩容0.5倍。 **推荐使用场景：** 当需要频繁按索引随机访问元素且数据量较大时，推荐使用Vector来存取数据。 文档中使用了泛型，涉及以下泛型标记符： - T：Type，类 |

