# @ohos.util.LightWeightSet

LightWeightSet可用于存储一系列值的集合，存储元素中value唯一。
 LightWeightSet依据泛型定义，采用轻量级结构，初始默认容量大小为8，每次扩容为原始容量的两倍。
 集合中value值的查找依赖于hash算法，通过一个数组存储hash值，然后根据hash值映射到对应的存储位置获取value。
 LightWeightSet和[HashSet](arkts-arkts-util-hashset-hashset-c.md)都是用于存储元素的集合类型，但LightWeightSet的占用内存更小。
 **推荐使用场景：** 当需要存储一组唯一元素、对数据进行去重、或需要基于hash快速查找元素时，推荐使用LightWeightSet。
 相比HashSet，LightWeightSet占用内存更小，适合内存敏感场景下的小规模数据存储与查找。
 文档中使用了泛型，涉及以下泛型标记符：
 - T：Type，表示LightWeightSet中存储元素的类型。
 > **说明：**
 >
 > - 容器类使用静态语言实现，限制了存储位置和属性，不支持自定义属性和方法。
 规格限制：当LightWeightSet存入的value为number类型且值大于INT32_MAX（2147483647）或小于INT32_MIN（-2147483648）时，
 针对LightWeightSet的操作，其结果可能与预期不一致。这是因为，当value为number类型且值大于INT32_MAX或小于INT32_MIN时，存储结构会发生改变。
 例如在以下示例中，针对value的计算，1758783600000大于INT32_MAX，此时会通过TaggedDouble存储；1758783600在INT32范围内，此时会通过TaggedInt存储。
 由于以上存储方式的差异，当对其进行hash算法即会计算出不同的hash值，从而导致映射结果不同，产生与预期不一致的现象。


## 导入模块

```TypeScript
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [LightWeightSet](arkts-arkts-util-lightweightset-lightweightset-c.md) | LightWeightSet可用于存储一系列值，存储元素中value唯一。 |
