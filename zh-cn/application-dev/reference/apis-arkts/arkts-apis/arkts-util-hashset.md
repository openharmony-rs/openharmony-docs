# @ohos.util.HashSet

HashSet是一种非线性容器，用于存储不重复的元素集合，支持高效的元素增删和存在性判断。HashSet基于[HashMap](arkts-arkts-util-hashmap-hashmap-c.md)实现，仅操作元素的值对象，不涉及键的概念。
 HashSet和[TreeSet](arkts-arkts-util-treeset-treeset-c.md)相比，HashSet中的数据按Hash值分布存储，因此元素的插入顺序与遍历时的顺序可能不一致，
 而TreeSet则是按照元素的自然排序或者自定义比较器进行有序存储。这两种集合中的元素都不允许重复，HashSet允许插入null值，
 TreeSet不建议插入null值，会影响排序结果。
 **推荐使用场景：** 当需要确保集合中元素不重复，或需要去除已有集合中的重复元素时，推荐使用HashSet；也可利用HashSet基于哈希的O(1)查找特性进行高效的元素存在性判断。
 文档中使用了泛型，涉及以下泛型标记符：
 - T：Type，类型
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
| [HashSet](arkts-arkts-util-hashset-hashset-c.md) | HashSet是一种非线性容器，用于存储不重复的元素集合，支持高效的元素增删和存在性判断。HashSet基于HashMap实现，仅操作元素的值对象，不涉及键的概念。 |
