# @ohos.util.Deque

Deque（double-ended queue）基于循环队列的数据结构实现，支持两端元素的插入和删除。Deque同时具备先进先出以及先进后出的特点，可根据操作端的不同同时作为队列和栈使用。当现有容量不足以容纳新插入的元素时，Deque会动态调整容量，每次扩容两倍，无需手动预设容量。
 Deque和[Queue](arkts-arkts-util-queue-queue-c.md)相比，Deque允许在两端执行插入和删除操作，Queue只能在头部删除元素，尾部插入元素。
 与[ArrayList](arkts-arkts-util-arraylist-arraylist-c.md)相比，它们都支持在两端插入和删除元素，但Deque不支持中间插入。Deque在头部插入删除元素的效率高于ArrayList，而ArrayList随机访问元素的效率高于Deque。
 **推荐使用场景：** 需要在集合两端频繁增删元素时，推荐使用Deque。
 文档中使用了泛型，涉及以下泛型标记符：
 - T：Type，类型
 > **说明**
 >
 > - 容器类使用静态语言实现，限制了内部存储方式和所支持的属性，不支持自定义属性和方法。


## 导入模块

```TypeScript
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Deque](arkts-arkts-util-deque-deque-c.md) | Deque（number-ended queue）基于循环队列的数据结构实现，支持两端元素的插入和删除。Deque同时具备先进先出以及先进后出的特点，可根据操作端的不同同时作为队列和栈使用。当现有容量不足以容纳新插入的元素时，Deque会动态调整容量，每次扩容两倍，无需手动预设容量。 |
