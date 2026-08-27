# @ohos.util.TreeSet

TreeSet基于[TreeMap](arkts-arkts-util-treemap-treemap-c.md)实现，在TreeSet中，仅处理元素的值（value），不单独处理键（key）。
 TreeSet的每个元素在底层TreeMap中同时作为key和value存储，因此元素中value唯一且有序。
 关于TreeMap的详细实现机制，请参见[TreeMap](arkts-arkts-util-treemap-treemap-c.md)。
 TreeSet和[HashSet](arkts-arkts-util-hashset-hashset-c.md)中的元素都不允许重复。HashSet中的数据无序存放，而TreeSet是有序存放。
 HashSet允许插入null值，但TreeSet不建议插入null值，可能会影响排序结果。
 **推荐使用场景：** TreeSet适用于需要有序存储和遍历集合的场景，如：有序数据展示、排名与排序系统、
 需要获取排序相邻元素的场景或自动排序插入等。
 文档中使用了泛型，涉及以下泛型标记符：
 - T：Type，表示TreeSet中元素的类型。
 > **说明**
 >
 > - 容器类使用静态语言实现，限制了存储位置和属性，不支持自定义属性和方法。


## 导入模块

```TypeScript
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [TreeSet](arkts-arkts-util-treeset-treeset-c.md) | TreeSet基于[TreeMap](arkts-arkts-util-treemap-treemap-c.md)实现，在TreeSet中，仅处理元素的值（value），不单独处理键（key）。 TreeSet的每个元素在底层TreeMap中同时作为key和value存储，因此元素中value唯一且有序。 |
