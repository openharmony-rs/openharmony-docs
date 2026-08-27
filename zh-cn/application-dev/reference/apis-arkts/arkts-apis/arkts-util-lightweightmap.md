# @ohos.util.LightWeightMap

LightWeightMap可用于存储具有关联关系的key-value键值对，其中key值唯一，每个key对应一个value。
 LightWeightMap依据泛型定义，采用轻量级结构，默认容量大小为8，每次扩容大小为原始容量的两倍。
 集合中key值的查找依赖于hash算法，通过一个数组存储hash值，然后映射到对应的key值及value值。
 LightWeightMap和[HashMap](arkts-arkts-util-hashmap-hashmap-c.md)都是用来存储键值对的容器，但LightWeightMap占用内存更小。
 **推荐使用场景：** 当需要存取key-value键值对且对内存占用较为敏感时（如需要同时维护大量小型键值对集合、运行在内存受限的环境中），推荐使用占用内存更小的LightWeightMap。
 文档中使用了泛型，包含以下泛型标记符：
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
| [LightWeightMap](arkts-arkts-util-lightweightmap-lightweightmap-c.md) | LightWeightMap可用于存储具有关联关系的key-value键值对，其中key值唯一，每个key对应一个value。 |
