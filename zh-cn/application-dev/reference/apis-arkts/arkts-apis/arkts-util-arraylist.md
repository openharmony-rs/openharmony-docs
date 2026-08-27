# @ohos.util.ArrayList

ArrayList是一种线性数据结构，底层基于数组实现，解决了固定大小数组无法动态扩容的限制。ArrayList会根据实际需要动态调整容量，每次扩容增加50%。
 ArrayList和[LinkedList](arkts-arkts-util-linkedlist-linkedlist-c.md)相比，ArrayList的随机访问效率更高。但由于ArrayList的增加和删除操作可能需要对数组内其他元素进行移动，LinkedList的增加和删除操作效率更高。
 **推荐使用场景：** 当需要频繁读取或按索引随机访问集合中的元素时，推荐使用ArrayList；当需要动态管理有序数据集合且增删操作频率较低时，也推荐使用ArrayList。
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
| [ArrayList](arkts-arkts-util-arraylist-arraylist-c.md) | ArrayList是一种线性数据结构，底层基于数组实现，解决了固定大小数组无法动态扩容的限制。ArrayList会根据实际需要动态调整容量，每次扩容增加50%。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ArrayListComparatorFn](arkts-arkts-arraylistcomparatorfn-t.md) | ArrayList中sort方法的比较器类型。 |
