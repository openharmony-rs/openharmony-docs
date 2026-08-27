# @ohos.util.List

List底层通过单向链表实现，每个节点有一个指向后一个元素的引用。查询元素必须从头遍历，因此查询效率低，但插入和删除效率高。List允许元素为null。
 List和[LinkedList](arkts-arkts-util-linkedlist-linkedlist-c.md)相比，LinkedList是双向链表，可以快速地在头尾进行增删，而List是单向链表，不支持双向操作。
 > **注意：**
 >
 > 在List中使用\[index\]的方式获取元素可能导致未定义结果，推荐使用get()方法。
 **推荐使用场景：** 当需要频繁的插入删除元素且需要使用单向链表时，推荐使用List。
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
| [List](arkts-arkts-util-list-list-c.md) | List底层通过单向链表实现，每个节点有一个指向后一个元素的引用。查询元素必须从头遍历，因此查询效率低，但插入和删除效率高。List允许元素为null。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ListComparatorFn](arkts-arkts-listcomparatorfn-t.md) | List中sort方法的回调函数。 |
