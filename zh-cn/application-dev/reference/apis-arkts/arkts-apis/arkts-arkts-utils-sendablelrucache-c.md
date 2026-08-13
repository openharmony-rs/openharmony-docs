# SendableLruCache

SendableLruCache在缓存空间不足时，会用新数据替换近期最少使用的数据。此设计基于资源访问的考虑： 近期访问的数据可能在不久的将来再次访问，因此最少访问的数据价值最小，应优先移出缓存。 SendableLruCache支持Sendable（可跨线程安全共享的）特性，可保存Sendable对象，确保跨线程安全访问。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-utils-class SendableLruCache--><!--Device-utils-class SendableLruCache-End-->

**系统能力：** SystemCapability.Utils.Lang

## clear

```TypeScript
clear(): void
```

从当前缓存清除所有键值对。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-clear(): void--><!--Device-SendableLruCache-clear(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

## constructor

```TypeScript
constructor(capacity?: number)
```

默认构造函数用于创建一个新的SendableLruCache实例，默认容量为64。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-constructor(capacity?: number)--><!--Device-SendableLruCache-constructor(capacity?: number)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capacity | number | 否 | 指示缓存的自定义容量。不传时，默认值为64，最大值不能超过2147483647；小于等于0时会抛出异常。 建议根据实际业务数据量设置合适的容量值，以平衡缓存命中率与内存占用。 |

## contains

```TypeScript
contains(key: K): boolean
```

检查当前缓存是否包含指定的键，如果存在，返回true；否则，返回false。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-contains(key: K): boolean--><!--Device-SendableLruCache-contains(key: K): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 表示要检查的键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：缓存包含指定的键；false：缓存不包含指定的键。 |

## entries

```TypeScript
entries(): IterableIterator<[K, V]>
```

允许迭代包含在这个对象中的所有键值对，按从最近访问到最少访问的顺序排列。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-entries(): IterableIterator<[K, V]>--><!--Device-SendableLruCache-entries(): IterableIterator<[K, V]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[K, V]&gt; | 返回键值对的迭代器。 |

## get

```TypeScript
get(key: K): V | undefined
```

返回键对应的值。如果指定的键不存在于缓存中，将调用createDefault方法；若createDefault返回非undefined值，则将该键值对添加到缓存并返回该值；若createDefault返回undefined， 则返回undefined。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-get(key: K): V | undefined--><!--Device-SendableLruCache-get(key: K): V | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 要查询的键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | 如果指定的键存在于缓存中，则返回与键关联的值；否则调用createDefault方法创建值。 若createDefault返回非undefined值，则将该键值对添加到缓存中，并返回该值；若createDefault返回undefined，则最终返回undefined。 当因添加新条目导致缓存中值的数量超过容量时，将淘汰最少使用的键值对。 |

## getCapacity

```TypeScript
getCapacity(): number
```

获取当前缓存的容量。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-getCapacity(): number--><!--Device-SendableLruCache-getCapacity(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回当前缓存的容量。 |

## getCreateCount

```TypeScript
getCreateCount(): number
```

获取调用createDefault方法创建对象的次数。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-getCreateCount(): number--><!--Device-SendableLruCache-getCreateCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回使用createDefault方法创建对象的次数。 |

## getMatchCount

```TypeScript
getMatchCount(): number
```

获取查询值匹配成功的次数。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-getMatchCount(): number--><!--Device-SendableLruCache-getMatchCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回查询值匹配成功的次数。 |

## getMissCount

```TypeScript
getMissCount(): number
```

获取查询值不匹配的次数。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-getMissCount(): number--><!--Device-SendableLruCache-getMissCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回查询值不匹配的次数。 |

## getPutCount

```TypeScript
getPutCount(): number
```

获取将值添加到缓存的次数。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-getPutCount(): number--><!--Device-SendableLruCache-getPutCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回向缓存中添加值的次数。 |

## getRemoveCount

```TypeScript
getRemoveCount(): number
```

获取缓存键值对的淘汰次数。当缓存数量超过容量限制时，最少使用的键值对将被淘汰。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-getRemoveCount(): number--><!--Device-SendableLruCache-getRemoveCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回缓存键值对淘汰的次数。 |

## isEmpty

```TypeScript
isEmpty(): boolean
```

检查当前缓存是否为空。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-isEmpty(): boolean--><!--Device-SendableLruCache-isEmpty(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示当前缓存为空，不包含任何键值对；返回false表示当前缓存不为空。 |

## keys

```TypeScript
keys(): K[]
```

获取当前缓存中所有键，按从最近访问到最少访问的顺序排列。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-keys(): K[]--><!--Device-SendableLruCache-keys(): K[]-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| K[] | 返回当前缓存中所有键的列表，按从最近访问到最少访问的顺序排列。 |

## put

```TypeScript
put(key: K, value: V): V
```

将键值对添加到缓存中，并返回与添加的键关联的值。当缓存中值的数量超过容量时，将淘汰最少使用的键值对。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-put(key: K, value: V): V--><!--Device-SendableLruCache-put(key: K, value: V): V-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 要添加的键。 |
| value | V | 是 | 与要添加的键关联的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | 返回与添加的键关联的值。 |

## remove

```TypeScript
remove(key: K): V | undefined
```

从当前缓存中删除指定键及其关联值，返回该键关联的值。若键不存在，则返回undefined。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-remove(key: K): V | undefined--><!--Device-SendableLruCache-remove(key: K): V | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 要删除的键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | 返回与key关联的值；若key不存在，则返回undefined。 |

## toString

```TypeScript
toString(): string
```

返回对象的字符串表示形式，包含缓存最大容量、查询匹配成功次数、查询匹配失败次数及匹配率等信息。 返回字符串格式是：SendableLruCache[ maxSize = (maxSize), hits = (hitCount), misses = (missCount), hitRate = (hitRate) ]。 (maxSize)表示缓存最大值， (hitCount)表示查询值匹配成功的次数， (missCount)表示查询值匹配失败的次数， (hitRate)表示查询值匹配率。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-toString(): string--><!--Device-SendableLruCache-toString(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回对象的字符串表示形式，包含缓存最大容量、查询匹配成功次数、查询匹配失败次数及匹配率等信息。 |

## updateCapacity

```TypeScript
updateCapacity(newCapacity: number): void
```

将缓存容量设置为指定值。如果缓存中值的总数超过指定容量，将淘汰最少使用的键值对。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-updateCapacity(newCapacity: number): void--><!--Device-SendableLruCache-updateCapacity(newCapacity: number): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newCapacity | number | 是 | 指示要为缓存自定义的容量，最大值不能超过2147483647；小于等于0时会抛出异常。建议根据实际业务数据量设置合适的容量值，以平衡缓存命中率与内存占用。 |

## values

```TypeScript
values(): V[]
```

获取当前缓存中所有值的列表，按从最近访问到最少访问的顺序排列。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-values(): V[]--><!--Device-SendableLruCache-values(): V[]-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V[] | 返回当前缓存中所有值的列表，按从最近访问到最少访问的顺序排列。 |

## length

```TypeScript
readonly length: number
```

当前缓存中值的总数。

**类型：** number

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-readonly length: number--><!--Device-SendableLruCache-readonly length: number-End-->

**系统能力：** SystemCapability.Utils.Lang

