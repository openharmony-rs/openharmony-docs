# @ohos.util.HashMap

HashMap底层采用数组、链表和红黑树实现，支持高效查询、插入和删除。HashMap存储内容基于键值对映射，不允许重复的key，且一个key只能对应一个value。
 HashMap和[TreeMap](arkts-arkts-util-treemap-treemap-c.md)相比，HashMap依据键的hashCode（哈希码）存取数据，访问速度较快，但不保证键的有序性。而TreeMap是有序存储和访问，查询效率较低。
 [HashSet](arkts-arkts-util-hashset-hashset-c.md)基于HashMap实现。HashMap的输入参数由key、value两个值组成。在HashSet中，只对value对象进行存储和管理。
 **推荐使用场景：** 需要快速存取、删除以及插入键值对数据时，推荐使用HashMap。典型应用场景包括数据缓存、键值查找表、配置参数管理等。
 文档中使用了泛型，包含以下泛型参数：<br>
 - K：Key，键<br>
 - V：Value，值
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
| [HashMap](arkts-arkts-util-hashmap-hashmap-c.md) | HashMap底层采用数组、链表和红黑树实现，支持高效查询、插入和删除。HashMap存储内容基于键值对映射，不允许重复的key，且一个key只能对应一个value。 |
