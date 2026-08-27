# @ohos.util.PlainArray

PlainArray可用于存储具有关联关系的key-value键值对集合，其中key值唯一且类型为number，每个key对应一个value。
 PlainArray依据泛型定义，采用轻量级结构，通过二分查找算法在集合中查找key值，并映射到其他数组中的value值。
 PlainArray和[LightWeightMap](arkts-arkts-util-lightweightmap-lightweightmap-c.md)都是用来存储键值对，且均采用轻量级结构，
 但PlainArray的key值类型仅限于number。
 **推荐使用场景：** 当需要存储key值为number类型的键值对时，可以使用PlainArray。
 文档中使用了泛型，涉及以下泛型类型参数：
 - T：Type，类型
 > **说明**
 >
 > 容器类使用静态语言实现，限制了存储位置和属性，不支持自定义属性和方法。


## 导入模块

```TypeScript
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [PlainArray](arkts-arkts-util-plainarray-plainarray-c.md) | PlainArray可用于存储具有关联关系的key-value键值对集合，其中key值唯一且类型为number，每个key对应一个value。 PlainArray依据泛型定义，采用轻量级结构。 |
