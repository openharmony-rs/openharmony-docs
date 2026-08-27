# @ohos.util.LinkedList

LinkedList底层通过双向链表实现，每个节点都包含对前一个元素和后一个元素的引用。查询元素时，可以从头或从尾部遍历，插入和删除效率高，查询效率低。LinkedList允许元素为null。
 LinkedList和[List](arkts-arkts-util-list-list-c.md)相比，LinkedList是双向链表，可以快速地在头尾进行增删，而List是单向链表，无法双向操作。
 LinkedList和[ArrayList](arkts-arkts-util-arraylist-arraylist-c.md)相比，LinkedList插入数据效率高于ArrayList，而ArrayList查询效率高于LinkedList。
 > **注意：**
 >
 > 在LinkedList中使用\[index\]的方式获取元素可能导致结果不可预测，推荐使用get()方法。
 **推荐使用场景：** 当需要频繁的插入删除元素且需要使用双向链表时，推荐使用LinkedList。
 文档中使用了泛型，涉及以下泛型类型参数：
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
| [LinkedList](arkts-arkts-util-linkedlist-linkedlist-c.md) | LinkedList底层通过双向链表实现，每个节点都包含对前一个元素和后一个元素的引用。查询元素时，可以从头或从尾部遍历，插入和删除效率高，查询效率低。LinkedList允许元素为null。 |
