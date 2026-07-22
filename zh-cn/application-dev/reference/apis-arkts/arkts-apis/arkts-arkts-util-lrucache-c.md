# LRUCache

提供在缓存已满时丢弃最近最少使用的数据以腾出空间给新元素的 API。此类使用最近最少使用（LRU）算法，该算法认为最近使用的数据可能在不久的将来再次被访问，而最少访问的数据是最不具价值的数据，应从缓存中移除。

**起始版本：** 9

<!--Device-util-class LRUCache<K, V>--><!--Device-util-class LRUCache<K, V>-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<[K, V]>
```

指定对象的默认迭代器。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LRUCache-[Symbol.iterator](): IterableIterator<[K, V]>--><!--Device-LRUCache-[Symbol.iterator](): IterableIterator<[K, V]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[K, V]&gt; | 返回以键值对形式的二维数组。 |

**示例：**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.put(2, 10);
pro.put(3, 15);

for (let value of pro) {
  console.info(value[0]+ ', '+ value[1]);
}
// 输出结果：
// 2, 10
// 3, 15

```

## afterRemoval

```TypeScript
afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void
```

在移除值后执行后续操作。后续操作必须由开发者实现。该 API 在删除操作期间会被调用，例如[get<sup>9+</sup>](arkts-arkts-util-lrucache-c.md#get)、[put<sup>9+</sup>](arkts-arkts-util-lrucache-c.md#put)、[remove<sup>9+</sup>](arkts-arkts-util-lrucache-c.md#remove)、[clear<sup>9+</sup>](arkts-arkts-util-lrucache-c.md#clear) 和[updateCapacity<sup>9+</sup>](arkts-arkts-util-lrucache-c.md#updatecapacity)。
> **NOTE**  
>  
> 如果在调用 [clear<sup>9+</sup>](arkts-arkts-util-lrucache-c.md#clear) 和  
> [updateCapacity<sup>9+</sup>](arkts-arkts-util-lrucache-c.md#updatecapacity) 后执行回调方法，并且输入的 **key** 和  
> **value** 参数为 MapIterator 类型，请参考示例 2 执行后续操作。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LRUCache-afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void--><!--Device-LRUCache-afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEvict | boolean | 是 | 容量是否不足。如果值为 **true**，则由于容量不足而调用此 API。 |
| key | K | 是 | 被移除的 key。 |
| value | V | 是 | 被移除的值。 |
| newValue | V | 是 | 如果调用了 **put()** 方法并且要添加的 key 已存在时该 key 的新值。其他情况下此参数为空。 |

## clear

```TypeScript
clear(): void
```

清除此缓存中的键值对。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LRUCache-clear(): void--><!--Device-LRUCache-clear(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例：**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.put(2, 10);
let result = pro.length;
pro.clear();
let res = pro.length;
console.info('result = ' + result);
console.info('res = ' + res);
// 输出结果：result = 1
// 输出结果：res = 0

```

## constructor

```TypeScript
constructor(capacity?: number)
```

用于创建 **LRUCache** 实例的构造函数。缓存的默认容量为 64。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LRUCache-constructor(capacity?: number)--><!--Device-LRUCache-constructor(capacity?: number)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capacity | number | 否 | 要创建的缓存的容量。默认值为 **64**，最大值为 **2147483647**。<br>**起始版本：** 12 |

**示例：**

```TypeScript
let lruCache = new util.LRUCache<number, number>();

```

## contains

```TypeScript
contains(key: K): boolean
```

判断此缓存是否包含指定的 key。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LRUCache-contains(key: K): boolean--><!--Device-LRUCache-contains(key: K): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 要检查的 key。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果缓存包含指定的 key，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.put(2, 10);
let result = pro.contains(2);
console.info('result = ' + result);
// 输出结果：result = true

```

## createDefault

```TypeScript
createDefault(key: K): V
```

在缓存中无匹配的 key 时执行后续操作，并返回与该 key 关联的值（默认为 **undefined**）。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LRUCache-createDefault(key: K): V--><!--Device-LRUCache-createDefault(key: K): V-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | key。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | key 对应的值。 |

**示例：**

```TypeScript
let pro = new util.LRUCache<number, number>();
let result = pro.createDefault(50);
console.info('result = ' + result);
// 输出结果：result = undefined

```

## entries

```TypeScript
entries(): IterableIterator<[K, V]>
```

返回一个迭代器对象，该对象按插入顺序遍历此对象中的所有键值对（[key, value]）。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LRUCache-entries(): IterableIterator<[K, V]>--><!--Device-LRUCache-entries(): IterableIterator<[K, V]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[K, V]&gt; | 可迭代的数组。 |

**示例：**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.put(2, 10);
pro.put(3, 15);
let pair = pro.entries();
for (let value of pair) {
  console.info(value[0]+ ', '+ value[1]);
}
// 输出结果：
// 2, 10
// 3, 15

```

## get

```TypeScript
get(key: K): V | undefined
```

获取 key 对应的值。如果该 key 不在缓存中，则调用[createDefault<sup>9+</sup>](arkts-arkts-util-lrucache-c.md#createdefault) 创建该 key。如果 **createDefault** 中指定的值不为 **undefined**，则调用 [afterRemoval<sup>9+</sup>](arkts-arkts-util-lrucache-c.md#afterremoval) 返回 **createDefault**中指定的值。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LRUCache-get(key: K): V | undefined--><!--Device-LRUCache-get(key: K): V | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 要查询值的 key。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | key 对应的值。如果未找到匹配项，则返回 **createDefault** 中指定的值。 |

**示例：**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.put(2, 10);
let result  = pro.get(2);
console.info('result = ' + result);
// 输出结果：result = 10

```

## getCapacity

```TypeScript
getCapacity(): number
```

获取此缓存的容量。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LRUCache-getCapacity(): number--><!--Device-LRUCache-getCapacity(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 缓存的容量。 |

**示例：**

```TypeScript
let pro = new util.LRUCache<number, number>();
let result = pro.getCapacity();
console.info('result = ' + result);
// 输出结果：result = 64

```

## getCreateCount

```TypeScript
getCreateCount(): number
```

获取创建对象的次数。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LRUCache-getCreateCount(): number--><!--Device-LRUCache-getCreateCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 创建对象的次数。 |

**示例：**

```TypeScript
// 创建新类ChildLRUCache继承LRUCache，重写createDefault方法，返回一个非undefined的值。
class ChildLRUCache extends util.LRUCache<number, number> {
  constructor() {
    super();
  }

  createDefault(key: number): number {
    return key;
  }
}
let lru = new ChildLRUCache();
lru.put(2, 10);
lru.get(3);
lru.get(5);
let res = lru.getCreateCount();
console.info('res = ' + res);
// 输出结果：res = 2

```

## getMatchCount

```TypeScript
getMatchCount(): number
```

获取查询值匹配的次数。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LRUCache-getMatchCount(): number--><!--Device-LRUCache-getMatchCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 查询值匹配的次数。 |

**示例：**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.put(2, 10);
pro.get(2);
let result = pro.getMatchCount();
console.info('result = ' + result);
// 输出结果：result = 1

```

## getMissCount

```TypeScript
getMissCount(): number
```

获取查询值未匹配的次数。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LRUCache-getMissCount(): number--><!--Device-LRUCache-getMissCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 查询值未匹配的次数。 |

**示例：**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.put(2, 10);
pro.get(2);
let result = pro.getMissCount();
console.info('result = ' + result);
// 输出结果：result = 0

```

## getPutCount

```TypeScript
getPutCount(): number
```

获取向此缓存添加的次数。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LRUCache-getPutCount(): number--><!--Device-LRUCache-getPutCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 向缓存添加的次数。 |

**示例：**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.put(2, 10);
let result = pro.getPutCount();
console.info('result = ' + result);
// 输出结果：result = 1

```

## getRemovalCount

```TypeScript
getRemovalCount(): number
```

获取此缓存中键值对被回收的次数。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LRUCache-getRemovalCount(): number--><!--Device-LRUCache-getRemovalCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 此缓存中键值对被回收的次数。 |

**示例：**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.put(2, 10);
pro.updateCapacity(2);
pro.put(50, 22);
let result = pro.getRemovalCount();
console.info('result = ' + result);
// 输出结果：result = 0

```

## isEmpty

```TypeScript
isEmpty(): boolean
```

判断此缓存是否为空。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LRUCache-isEmpty(): boolean--><!--Device-LRUCache-isEmpty(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果缓存不包含任何值，则返回 **true**。 |

**示例：**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.put(2, 10);
let result = pro.isEmpty();
console.info('result = ' + result);
// 输出结果：result = false

```

## keys

```TypeScript
keys(): K[]
```

获取此缓存中的所有 key，按从最近最少访问到最近最多访问的顺序排列。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LRUCache-keys(): K[]--><!--Device-LRUCache-keys(): K[]-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| K[] | 此缓存中所有 key 的列表，按从最近最少访问到最近最多访问的顺序排列。 |

**示例：**

```TypeScript
let pro = new util.LRUCache<number, string>();
pro.put(1, 'A');
pro.put(2, "B");
pro.put(3, 'C');
pro.put(4, 'D')
pro.put(5, 'E')
pro.put(6, 'F')
let result = pro.keys();
console.info('result = ' + result);
// 输出结果：result = 1,2,3,4,5,6
pro.get(5);
pro.get(3);
result = pro.keys();
console.info('result = ' + result);
// 输出结果：result = 1,2,4,6,5,3

```

## put

```TypeScript
put(key: K, value: V): V
```

向此缓存添加键值对，并返回与该 key 关联的值。如果缓存中的值总数大于指定容量，则执行删除操作。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LRUCache-put(key: K, value: V): V--><!--Device-LRUCache-put(key: K, value: V): V-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 要添加的键值对的 key。 |
| value | V | 是 | 要添加的键值对的 value。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | 添加的键值对的值。如果 key 或 value 为空，则抛出异常。 |

**示例：**

```TypeScript
let pro = new util.LRUCache<number, number>();
let result = pro.put(2, 10);
console.info('result = ' + result);
// 输出结果：result = 10

```

## remove

```TypeScript
remove(key: K): V | undefined
```

从此缓存中移除 key 及其关联的值，并返回与该 key 关联的值。如果 key 不存在，则返回 **undefined**。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LRUCache-remove(key: K): V | undefined--><!--Device-LRUCache-remove(key: K): V | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 要移除的 key。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | 如果 key 存在于缓存中，则返回包含被移除键值对的 **Optional** 对象；如果 key 不存在则返回 **undefined**；如果 **key** 传入 **null**，则抛出错误。 |

**示例：**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.put(2, 10);
let result = pro.remove(20);
console.info('result = ' + result);
// 输出结果：result = undefined

```

## toString

```TypeScript
toString(): string
```

获取此缓存的字符串表示形式。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LRUCache-toString(): string--><!--Device-LRUCache-toString(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 此缓存的字符串表示形式。 |

**示例：**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.put(2, 10);
pro.get(2);
pro.get(3);
console.info(pro.toString());
// 输出结果：LRUCache[ maxSize = 64, hits = 1, misses = 1, hitRate = 50% ]
// maxSize: 缓存区最大值 hits: 查询值匹配成功的次数 misses: 查询值匹配失败的次数 hitRate: 查询值匹配率

```

## updateCapacity

```TypeScript
updateCapacity(newCapacity: number): void
```

改变缓存容量。如果新容量小于等于 **0**，则抛出异常。如果缓存中的值总数大于指定容量，则执行删除操作。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LRUCache-updateCapacity(newCapacity: number): void--><!--Device-LRUCache-updateCapacity(newCapacity: number): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newCapacity | number | 是 | 缓存的新容量。最大值为 **2147483647**。 |

**示例：**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.updateCapacity(100);

```

## values

```TypeScript
values(): V[]
```

获取此缓存中的所有值，按从最近最少访问到最近最多访问的顺序排列。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LRUCache-values(): V[]--><!--Device-LRUCache-values(): V[]-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V[] | 此缓存中所有值的列表，按从最近最少访问到最近最多访问的顺序排列。 |

**示例：**

```TypeScript
let pro = new util.LRUCache<number, string>();
pro.put(1, 'A');
pro.put(2, "B");
pro.put(3, 'C');
pro.put(4, 'D')
pro.put(5, 'E')
pro.put(6, 'F')
let result = pro.values();
console.info('result = ' + result);
// 输出结果：result = A,B,C,D,E,F
pro.get(1);
pro.get(2);
result = pro.values();
console.info('result = ' + result);
// 输出结果：result = C,D,E,F,A,B

```

## length

```TypeScript
length: number
```

此缓存中值的总数。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LRUCache-length: number--><!--Device-LRUCache-length: number-End-->

**系统能力：** SystemCapability.Utils.Lang

