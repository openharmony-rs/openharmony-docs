# @ohos.util.LightWeightMap (非线性容器LightWeightMap)  
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong; @lijin1039-->
<!--Designer: @Malzahar; @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

LightWeightMap可用于存储具有关联关系的key-value键值对集合，存储元素中key值唯一，每个key对应一个value。

LightWeightMap依据泛型定义，采用轻量级结构，初始默认容量大小为8，每次扩容大小为原始容量的两倍。

集合中key值的查找依赖于hash算法，通过一个数组存储hash值，然后映射到其他数组中的key值及value值。

LightWeightMap和[HashMap](js-apis-hashmap.md)都是用来存储键值对的集合，但LightWeightMap占用内存更小。


**推荐使用场景：** 当需要存取key-value键值对时，推荐使用占用内存更小的LightWeightMap。

文档中使用了泛型，涉及以下泛型标记符：
- K：Key，键<br>
- V：Value，值

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 容器类使用静态语言实现，限制了存储位置和属性，不支持自定义属性和方法。

## 规格限制

当LightWeightMap存入的key为number类型且值大于INT32_MAX或小于INT32_MIN时，针对LightWeightMap的操作，其结果可能与预期不一致。

这是因为，当key为number类型且值大于INT32_MAX或小于INT32_MIN时，存储结构会发生改变。

例如在以下示例针对key的计算中，1758783600000大于INT32_MAX，此时会通过TaggedDouble存储；1758783600小于INT32_MIN，此时会通过TaggedInt存储。由于以上存储方式的差异，当对其进行hash算法即会计算出不同的hash值，从而导致映射结果不同，产生与预期不一致的现象。

```ts
let mp = new LightWeightMap<number, number>();
let key = 1758783600000 / 1000;  // 1758783600000 > INT32_MAX
mp.set(key, 1001);
console.info("result:", mp.hasKey(1758783600));  // result: false 
console.info("result:", mp.hasKey(key));  // result: true
```

## 导入模块

```ts
import { LightWeightMap } from '@kit.ArkTS';
```

## LightWeightMap

### 属性

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| length | ArkTS-Dyn: number <br> ArkTS-Sta: int | 是 | 否 | LightWeightMap的元素个数。 |


### constructor

constructor()

LightWeightMap的构造函数。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200012 | The LightWeightMap's constructor cannot be directly invoked. |

**示例：**

ArkTS-Dyn示例：

```ts
let lightWeightMap = new LightWeightMap<string, number>();
```

ArkTS-Sta示例：

```ts
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
```


### isEmpty

isEmpty(): boolean

判断LightWeightMap是否为空。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 为空返回true，不为空返回false。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The isEmpty method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
const lightWeightMap = new LightWeightMap<string, number>();
let result = lightWeightMap.isEmpty();
console.info("result:", result);  // result: true
```

ArkTS-Sta示例：

```ts
const lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
let result = lightWeightMap.isEmpty();
console.info("result:", result);  // result: true
```


### hasAll

hasAll(map: LightWeightMap<K, V>): boolean

判断LightWeightMap中是否包含指定map中的所有元素。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| map | LightWeightMap<K, V> | 是 | 比较对象。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 包含所有元素返回true，否则返回false。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The hasAll method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let map = new LightWeightMap<string, number>();
map.set("sparrow", 356);
let result = lightWeightMap.hasAll(map); 
console.info("result = ", result); // result = true
```

ArkTS-Sta示例：

```ts
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let map = new LightWeightMap<string, int>();
map.set("sparrow", 356);
let result = lightWeightMap.hasAll(map);
console.info("result = ", result); // result = true
```


### hasKey

hasKey(key: K): boolean

判断LightWeightMap中是否包含指定key。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| key | K | 是 | 指定key。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 包含指定key返回true，否则返回false。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The hasKey method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
let result = lightWeightMap.hasKey("squirrel");
console.info("result:", result);  // result: true
```

ArkTS-Sta示例：

```ts
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
let result = lightWeightMap.hasKey("squirrel");
```


### hasValue

hasValue(value: V): boolean

判断LightWeightMap中是否包含指定value。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | V | 是 | 指定元素。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 包含指定元素返回true，否则返回false。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The hasValue method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
let result = lightWeightMap.hasValue(123);
console.info("result:", result);  // result: true
```

ArkTS-Sta示例：

```ts
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
let result = lightWeightMap.hasValue(123);
console.info("result:", result);  // result: true
```

### increaseCapacityTo

ArkTS-Dyn: increaseCapacityTo(minimumCapacity: number): void

ArkTS-Sta: increaseCapacityTo(minimumCapacity: int): void

将当前LightWeightMap扩容至指定容量。如果传入的容量值大于或等于当前LightWeightMap中的元素个数，将容量变更为新容量，小于则不会变更。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| minimumCapacity | ArkTS-Dyn: number <br> ArkTS-Sta: int | 是 | 需要容纳的元素数量。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The increaseCapacityTo method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.increaseCapacityTo(10);
```

ArkTS-Sta示例：

```ts
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.increaseCapacityTo(10);
```

### get

get(key: K): V

获取指定key所对应的value。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[get](#get23)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| key | K | 是 | 指定key。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| V | 返回key映射的value值。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The get method cannot be bound. |

**示例：**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.get("sparrow");
console.info("result:", result);  // result: 356
```

### get<sup>23+</sup>

get(key: K): V \| undefined

获取指定key所对应的value值。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[get](#get)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| key | K | 是 | 指定key。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| V \| undefined | 返回key映射的value值，不存在返回undefined。 |

**示例：**

```ts
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.get("sparrow");
console.info("result:", result);  // result: 356
```

### getIndexOfKey

ArkTS-Dyn: getIndexOfKey(key: K): number

ArkTS-Sta: getIndexOfKey(key: K): int

查找key元素首次出现的下标值，如果未找到返回-1。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| key | K | 是 | 被查找的元素。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn: number <br> ArkTS-Sta: int | 返回key元素首次出现的下标值，查找失败返回-1。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The getIndexOfKey method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.getIndexOfKey("sparrow");
console.info("result:", result);  // result: 0
```

ArkTS-Sta示例：

```ts
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.getIndexOfKey("sparrow");
console.info("result:", result);  // result: 0
```


### getIndexOfValue

ArkTS-Dyn: getIndexOfValue(value: V): number

ArkTS-Sta: getIndexOfValue(value: V): int

查找value元素首次出现的下标值，如果未找到则返回-1。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | V | 是 | 被查找的元素。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn: number <br> ArkTS-Sta: int | 返回value元素首次出现的下标值，查找失败返回-1。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The getIndexOfValue method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.getIndexOfValue(123);
console.info("result:", result);  // result: 1
```

ArkTS-Sta示例：

```ts
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.getIndexOfValue(123);
console.info("result:", result);  // result: 1
```


### getKeyAt

getKeyAt(index: number): K

查找指定下标的元素键值对中key值，如果未找到则返回undefined。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[getKeyAt](#getkeyat23)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| index | number | 是 | 所查找的下标。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| K | 返回该下标对应的元素键值对中key值。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of index is out of range. |
| 10200011 | The getKeyAt method cannot be bound. |

**示例：**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.getKeyAt(1);
console.info("result:", result);  // result: squirrel
```

### getKeyAt<sup>23+</sup>

getKeyAt(index: int): K | undefined

查找指定下标的元素键值对中key值，否则返回undefined。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[getKeyAt](#getkeyat)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| index | int | 是 | 所查找的下标。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| K \| undefined | 返回该下标对应的元素键值对中key值。如果没找到则返回undefined。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of index is out of range. |

**示例：**

```ts
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.getKeyAt(1);
console.info("result:", result);  // result: squirrel
```


### setAll

setAll(map: LightWeightMap<K, V>): void

将一个LightWeightMap中的所有元素组添加到另一个LightWeightMap中。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| map | LightWeightMap<K, V> | 是 | 提供添加元素的LightWeightMap。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The setAll method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let map = new LightWeightMap<string, number>();
map.setAll(lightWeightMap);   // 将lightWeightMap中所有的元素添加到map中
let result = map.get("sparrow");
console.info("result:", result);  // result: 356
```

ArkTS-Sta示例：

```ts
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let map: LightWeightMap<string, int> = new LightWeightMap<string, int>();
map.setAll(lightWeightMap); // 将lightWeightMap中所有的元素添加到map中
let result = map.get("sparrow");
console.info("result:", result);  // result: 356
```


### set
set(key: K, value: V): Object

向LightWeightMap中添加或更新一组数据。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| key | K | 是 | 添加或更新成员数据的键名。 |
| value | V | 是 | 添加或更新成员数据的值。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Object | 返回添加或更新数据后的LightWeightMap。|

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The set method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
let lightWeightMap = new LightWeightMap<string, number>();
let result = lightWeightMap.set("squirrel", 123);
console.info("result:", result);  // result: squirrel:123
```

ArkTS-Sta示例：

```ts
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
let result = lightWeightMap.set("squirrel", 123);
console.info("result:", result);  // result: squirrel:123
```


### remove

remove(key: K): V

删除指定key映射的元素。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[remove](#remove23)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| key | K | 是 | 指定key。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| V | 返回删除元素的值。|

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The remove method cannot be bound. |

**示例：**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.remove("sparrow");
console.info("result:", result);  // result: 356
```

### remove<sup>23+</sup>

remove(key: K): V \| undefined

删除并返回指定key映射的元素。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[remove](#remove)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| key | K | 是 | 指定key。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| V \| undefined | 返回删除元素的值，key不存在则返回undefined。 |

**示例：**

```ts
let lightWeightMap: LightWeightMap<string, number> = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
lightWeightMap.remove("sparrow");
console.info("result:", result);  // result: 356
```

### removeAt

ArkTS-Dyn: removeAt(index: number): boolean

ArkTS-Sta: removeAt(index: int): boolean

删除指定下标对应的元素。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| index | ArkTS-Dyn: number <br> ArkTS-Sta: int | 是 | 指定下标。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 成功删除元素返回true，否则返回false。|

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The removeAt method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.removeAt(1);
console.info("result:", result);  // result: true
```

ArkTS-Sta示例：

```ts
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.removeAt(1);
console.info("result:", result);  // result: true
```


### setValueAt

ArkTS-Dyn: setValueAt(index: number, newValue: V): boolean

ArkTS-Sta: setValueAt(index: int, newValue: V): boolean

替换指定下标对应键值对中的值。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| index | ArkTS-Dyn: number <br> ArkTS-Sta: int | 是 | 指定下标。需要小于等于int32_max即2147483647。 |
| newValue | V | 是 | 替换键值对中的值。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 成功替换返回true，否则返回false。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of index is out of range. |
| 10200011 | The setValueAt method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
lightWeightMap.setValueAt(1, 3546);
console.info("result:", lightWeightMap.get("squirrel"));  // result: 3546
```

ArkTS-Sta示例：

```ts
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
lightWeightMap.setValueAt(1, 3546);
console.info("result:", lightWeightMap.get("squirrel"));  // result: 3546
```


### getValueAt

getValueAt(index: number): V

获取指定下标对应键值对中的值。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[getValueAt](#getvalueat23)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| index | number | 是 | 指定下标。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| V | 返回指定下标对应键值对中的值。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of index is out of range. |
| 10200011 | The getValueAt method cannot be bound. |

**示例：**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.getValueAt(1);
console.info("result:", result);  // result: 123
```

### getValueAt<sup>23+</sup>

getValueAt(index: int): V | undefined

获取指定下标对应键值对中的元素。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[getValueAt](#getvalueat)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| index | int | 是 | 指定下标。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| V \| undefined | 返回指定下标对应键值对中的元素,如果没有则返回undefined。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of index is out of range. |

**示例：**

```ts
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.getValueAt(1);
console.info("result:", result);  // result: 123
```


### clear

clear(): void

清除LightWeightMap中的所有元素，并将length置为0。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The clear method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
lightWeightMap.clear();
let result = lightWeightMap.isEmpty();
console.info("result:", result);  // result: true
```

ArkTS-Sta示例：

```ts
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
lightWeightMap.clear();
let result = lightWeightMap.isEmpty();
console.info("result:", result);  // result: true
```


### keys

keys(): IterableIterator&lt;K&gt;

返回包含此映射中所有的键的新迭代器对象。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| IterableIterator&lt;K&gt; | 返回一个迭代器。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The keys method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let keys = lightWeightMap.keys();
for (let key of keys) {
  console.info("key:", key);
}
// key: sparrow
// key: squirrel
```

ArkTS-Sta示例：

```ts
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let iter = lightWeightMap.keys();
let temp: IteratorResult<string> = iter.next();
while(!temp.done) {
  console.info("value:" + temp.value);
  temp = iter.next();
}
// key: sparrow
// key: squirrel
```


### values

values(): IterableIterator&lt;V&gt;

返回包含此映射中所有键值的新迭代器对象。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| IterableIterator&lt;V&gt; | 返回一个迭代器。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The values method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let values = lightWeightMap.values();
for (let value of values) {
  console.info("value:", value);
}
// value: 356
// value: 123
```

ArkTS-Sta示例：

```ts
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let iter = lightWeightMap.values();
let temp: IteratorResult<int> = iter.next();
while(!temp.done) {
  console.info("value:" + temp.value);
  temp = iter.next();
}
// value: 356
// value: 123
```


### forEach

forEach(callbackFn: (value?: V, key?: K, map?: LightWeightMap<K, V>) => void, thisArg?: Object): void

通过回调函数来遍历实例对象上的元素及其下标。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[forEach](#foreach23)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callbackFn | function | 是 | 回调函数。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值，默认值为当前实例对象。 |

callbackFn的参数说明：
| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | V | 否 | 当前遍历到的元素键值对的值，默认值为首个键值对的值。 |
| key | K | 否 | 当前遍历到的元素键值对的键，默认值为首个键值对的键。 |
| map | LightWeightMap<K, V> | 否 | 当前调用forEach方法的实例对象，默认值为当前实例对象。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The forEach method cannot be bound. |

**示例：**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("sparrow", 123);
lightWeightMap.set("gull", 357);
lightWeightMap.forEach((value: number, key: string) => {
  console.info("value:" + value, "key:" + key);
});
// value:123 key:sparrow
// value:357 key:gull
```

```ts
// 不建议在forEach中使用set、setValueAt、remove、removeAt方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。
let lightWeightMap = new LightWeightMap<string, number>();
for(let i = 0; i < 10; i++) {
  lightWeightMap.set("sparrow" + i, 123);
}
for(let i = 0; i < 10; i++) {
  lightWeightMap.remove("sparrow" + i);
}
```

### forEach<sup>23+</sup>

forEach(callbackFn: LightWeightMapCbFn\<K, V\>): void

通过回调函数来遍历实例对象上的元素以及元素对应的下标。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[forEach](#foreach)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callbackFn | [LightWeightMapCbFn\<K, V\>](#lightweightmapcbfnk-v23) | 是 | 回调函数。 |

**示例：**

```ts
import { LightWeightMapCbFn } from '@kit.ArkTS';

let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("sparrow", 123);
lightWeightMap.set("test", 987);
lightWeightMap.set("gull", 357);
let lightWeightMapCb: LightWeightMapCbFn<string, int> = (value: int, key: string, map: LightWeightMap<string, int>) => {
  console.info("value: " + value, " key: " + key);
};
lightWeightMap.forEach(lightWeightMapCb);
// value:123 key:sparrow
// value:357 key:gull
```

### entries

entries(): IterableIterator<[K, V]>

返回包含此映射中所有键值对的新迭代器对象。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| IterableIterator<[K, V]> | 返回一个迭代器。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The entries method cannot be bound. |

**示例：**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let iter = lightWeightMap.entries();
let temp: IteratorResult<Object[]> = iter.next();
while(!temp.done) {
  console.info("key:" + temp.value[0]);
  console.info("value:" + temp.value[1]);
  temp = iter.next();
}
```
```ts
// 不建议在entries中使用set、setValueAt、remove、removeAt方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。
let lightWeightMap = new LightWeightMap<string, number>();
for(let i = 0; i < 10; i++) {
  lightWeightMap.set("sparrow" + i, 123);
}
for(let i = 0; i < 10; i++) {
  lightWeightMap.remove("sparrow" + i);
}
```

ArkTS-Dyn示例：

```ts
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let iter = lightWeightMap.entries();
let temp: IteratorResult<[string, int]> = iter.next();
while(!temp.done) {
  console.info("key:" + temp.value![0]);
  console.info("value:" + temp.value![1]);
  temp = iter.next();
}
```
```ts
// 不建议在entries中使用set、setValueAt、remove、removeAt方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
for(let i = 0; i < 10; i++) {
  lightWeightMap.set("sparrow" + i, 123);
}
for(let i = 0; i < 10; i++) {
  lightWeightMap.remove("sparrow" + i);
}
```

### toString

toString(): String

将此映射中包含的键值对拼接成字符串并返回。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| String | 返回一个字符串。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The toString method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.toString();
console.info("result:", result);  // result: sparrow:356,squirrel:123
```

ArkTS-Sta示例：

```ts
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.toString();
console.info("result:", result);  // result: sparrow:356,squirrel:123
```

### [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;[K, V]&gt;

返回一个迭代器，迭代器的每一项都是一个JavaScript对象。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[$_iterator](#_iterator23)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| IterableIterator<[K, V]> | 返回一个迭代器。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The Symbol.iterator method cannot be bound. |

**示例：**

```ts
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);

// 使用方法一：
for (let item of lightWeightMap) {
  console.info("key:", item[0]);
  console.info("value:", item[1]);
}
// key: sparrow
// value: 356
// key: squirrel
// value: 123

// 使用方法二：
let iter = lightWeightMap[Symbol.iterator]();
let temp: IteratorResult<Object[]> = iter.next();
while(!temp.done) {
  console.info("key:", temp.value[0]);
  console.info("value:", temp.value[1]);
  temp = iter.next();
}
// key: sparrow
// value: 356
// key: squirrel
// value: 123
```

```ts
// 不建议在Symbol.iterator中使用set、setValueAt、remove、removeAt方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。
let lightWeightMap = new LightWeightMap<string, number>();
for(let i = 0; i < 10; i++) {
  lightWeightMap.set("sparrow" + i, 123);
}
for(let i = 0; i < 10; i++) {
  lightWeightMap.remove("sparrow" + i);
}
```

### $_iterator<sup>23+</sup>

\$_iterator\(): IterableIterator&lt;[K, V]&gt;

返回一个迭代器，迭代器的每一项都是一个JavaScript对象，并返回该对象。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[Symbol.iterator](#symboliterator)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| IterableIterator<[K, V]> | 返回一个迭代器。 |

**示例：**

```ts
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);

// 使用方法一：
for (let item of lightWeightMap) {
  console.info("key:" + item[0]);
  console.info("value:" + item[1]);
}

// 使用方法二：
let iter = lightWeightMap.$_iterator();
let temp: IteratorResult<[string, int]> = iter.next();
while(!temp.done) {
  console.info("key:" + temp.value![0]);
  console.info("value:" + temp.value![1]);
  temp = iter.next();
}
```

### LightWeightMapCbFn\<K, V\><sup>23+</sup>

type LightWeightMapCbFn\<K, V\> = (value: V, key: K, map: LightWeightMap\<K, V\>) => void

LightWeightMap中forEach方法的回调函数。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | V | 是 | 当前遍历到的元素键值对的值。 |
| key | K | 是 | 当前遍历到的元素键值对的键。 |
| map | [LightWeightMap\<K, V\>](#lightweightmap) | 是 | 当前调用[forEach](#foreach23)方法的实例对象。 |