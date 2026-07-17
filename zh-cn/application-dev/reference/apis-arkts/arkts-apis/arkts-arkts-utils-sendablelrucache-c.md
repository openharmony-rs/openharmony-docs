# SendableLruCache

用于存储近期最少使用的Sendable对象的缓冲区。

**起始版本：** 18

**装饰器类型：** @Sendable

<!--Device-utils-class SendableLruCache<K, V>--><!--Device-utils-class SendableLruCache<K, V>-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { ArkTSUtils } from '@kit.ArkTS';
```

## clear

```TypeScript
clear(): void
```

清除SendableLruCache中的所有键值对。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-clear(): void--><!--Device-SendableLruCache-clear(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

## constructor

```TypeScript
constructor(capacity?: number)
```

默认构造函数。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-constructor(capacity?: number)--><!--Device-SendableLruCache-constructor(capacity?: number)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capacity | number | 否 | SendableLruCache的容量。 |

## contains

```TypeScript
contains(key: K): boolean
```

检查SendableLruCache中是否包含指定的键。如果存在，返回true；否则返回false。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-contains(key: K): boolean--><!--Device-SendableLruCache-contains(key: K): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 要检查的键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查的结果。 |

## entries

```TypeScript
entries(): IterableIterator<[K, V]>
```

返回SendableLruCache中每个元素的键值对的可迭代对象。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-entries(): IterableIterator<[K, V]>--><!--Device-SendableLruCache-entries(): IterableIterator<[K, V]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator<[K, V]> | 新的可迭代迭代器对象。 |

## get

```TypeScript
get(key: K): V | undefined
```

获取SendableLruCache中与指定键关联的值。

**起始版本：** 18

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
| V | 如果指定的键存在于缓冲区中，则返回与键关联的值；否则返回undefined。 |

## getCapacity

```TypeScript
getCapacity(): number
```

获取SendableLruCache的容量。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-getCapacity(): number--><!--Device-SendableLruCache-getCapacity(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | SendableLruCache的容量。 |

## getCreateCount

```TypeScript
getCreateCount(): number
```

获取SendableLruCache中createDefault的调用次数。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-getCreateCount(): number--><!--Device-SendableLruCache-getCreateCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | createDefault的调用次数。 |

## getMatchCount

```TypeScript
getMatchCount(): number
```

获取SendableLruCache中查询值匹配的次数。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-getMatchCount(): number--><!--Device-SendableLruCache-getMatchCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 查询值匹配的次数。 |

## getMissCount

```TypeScript
getMissCount(): number
```

获取SendableLruCache中查询值不匹配的次数。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-getMissCount(): number--><!--Device-SendableLruCache-getMissCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 查询值不匹配的次数。 |

## getPutCount

```TypeScript
getPutCount(): number
```

获取将值添加到SendableLruCache的次数。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-getPutCount(): number--><!--Device-SendableLruCache-getPutCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 值被添加的次数。 |

## getRemoveCount

```TypeScript
getRemoveCount(): number
```

获取SendableLruCache中值被移除的次数。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-getRemoveCount(): number--><!--Device-SendableLruCache-getRemoveCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 值被移除的次数。 |

## isEmpty

```TypeScript
isEmpty(): boolean
```

检查SendableLruCache是否为空。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-isEmpty(): boolean--><!--Device-SendableLruCache-isEmpty(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果SendableLruCache为空则返回true，否则返回false。 |

## keys

```TypeScript
keys(): K[]
```

返回SendableLruCache中所有键的列表。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-keys(): K[]--><!--Device-SendableLruCache-keys(): K[]-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| K[] | 所有键的数组。 |

## put

```TypeScript
put(key: K, value: V): V
```

将键值对添加到SendableLruCache中。

**起始版本：** 18

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
| V | 返回与添加的键关联的值，或如果键已存在则返回原始值。 |

## remove

```TypeScript
remove(key: K): V | undefined
```

从SendableLruCache中移除指定的键及其关联值。

**起始版本：** 18

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
| V | 被删除的值或undefined。 |

## toString

```TypeScript
toString(): string
```

返回对象的字符串表示形式。返回字符串格式是：SendableLruCache[ maxSize = (maxSize), hits = (hitCount),misses = (missCount), hitRate = (hitRate) ]。(maxSize)表示缓存区最大值，(hitCount)表示查询值匹配成功的次数，(missCount)表示查询值匹配失败的次数，(hitRate)表示查询值匹配率。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-toString(): string--><!--Device-SendableLruCache-toString(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 包含所有元素的新字符串。 |

## updateCapacity

```TypeScript
updateCapacity(newCapacity: number): void
```

更新SendableLruCache的容量。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-updateCapacity(newCapacity: number): void--><!--Device-SendableLruCache-updateCapacity(newCapacity: number): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newCapacity | number | 是 | SendableLruCache的新容量。 |

## values

```TypeScript
values(): V[]
```

返回SendableLruCache中所有值的列表。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-values(): V[]--><!--Device-SendableLruCache-values(): V[]-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V[] | 所有值的数组。 |

## length

```TypeScript
readonly length: number
```

SendableLruCache的长度。

**类型：** number

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SendableLruCache-readonly length: number--><!--Device-SendableLruCache-readonly length: number-End-->

**系统能力：** SystemCapability.Utils.Lang

