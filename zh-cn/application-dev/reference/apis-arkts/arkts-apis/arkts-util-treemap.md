# @ohos.util.TreeMap

TreeMap可用于存储具有关联关系的key-value键值对集合，存储元素中key值唯一，每个key对应一个value。
 TreeMap底层使用红黑树实现，可以利用二叉树特性查找键值对，查找、插入和删除操作的时间复杂度为O(log n)。key值有序存储，可以实现高效的有序遍历。
 TreeMap和[HashMap](arkts-arkts-util-hashmap-hashmap-c.md)相比，HashMap依据键的hashCode存取数据，访问速度较快但不保证键的顺序；而TreeMap基于红黑树有序存取，访问效率较低，但支持有序遍历、范围查询和首末键及相邻键查找等有序操作。
 **推荐使用场景：** 需要对键值对进行有序存储和访问的场景，例如范围查询、有序遍历和键邻近查找等。
 文档中使用了泛型，涉及以下泛型标记符：
 - K：Key，键
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
| [TreeMap](arkts-arkts-util-treemap-treemap-c.md) | TreeMap可用于存储具有关联关系的key-value键值对集合，存储元素中key值唯一，每个key对应一个value。 TreeMap底层使用红黑树实现，可以利用二叉树特性查找键值对，查找、插入和删除操作的时间复杂度为O(log n)。key值有序存储，可以实现高效的有序遍历。 |
