# LRUCache

```TypeScript
class LRUCache<K, V>
```

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

返回键值对形式的二维数组。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-LRUCache-[Symbol.iterator](): IterableIterator<[K, V]>--><!--Device-LRUCache-[Symbol.iterator](): IterableIterator<[K, V]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[K, V]&gt; | 返回一个键值对形式的二维数组。 |

**示例**

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

删除值后执行后续操作，这些操作由开发者自行实现。本接口会在删除操作时被调用，如[get<sup>9+</sup>](#get)、[put<sup>9+</sup>](#put)、[remove<sup>9+</sup>](#remove)、[clear<sup>9+</sup>](#clear)、[updateCapacity<sup>9+</sup>](#updatecapacity)接口。

> **说明：** 
> 
> 若此回调方法在[clear<sup>9+</sup>](#clear)、
> [updateCapacity<sup>9+</sup>](#updatecapacity)接口调用之后触发执行，传入的key和value参数
> 类型为MapIterator，可参照示例二进行后续操作。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-LRUCache-afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void--><!--Device-LRUCache-afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEvict | boolean | 是 | 当因容量不足而调用该方法时，参数值设置为true，其他情况设置为false。 |
| key | K | 是 | 表示删除的键。 |
| value | V | 是 | 表示删除的值。 |
| newValue | V | 是 | 如果已调用put方法并且要添加的键已经存在，则参数值是关联的新值。其他情况下参数值为空。 |

## clear

```TypeScript
clear(): void
```

清除当前缓冲区中的键值对，并触发afterRemoval回调方法执行后续操作。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-LRUCache-clear(): void--><!--Device-LRUCache-clear(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例**

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

默认构造函数用于创建一个新的LRUCache实例，默认容量为64。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-LRUCache-constructor(capacity?: number)--><!--Device-LRUCache-constructor(capacity?: number)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capacity | number | 否 | 要创建的缓存的容量。默认值为 **64**，最大值为 **2147483647**。<br>**适用版本：** 12 |

**示例**

```TypeScript
let lruCache = new util.LRUCache<number, number>();
```

## contains

```TypeScript
contains(key: K): boolean
```

检查当前缓存是否包含指定的键。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-LRUCache-contains(key: K): boolean--><!--Device-LRUCache-contains(key: K): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 要检查的键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果缓存包含指定的键，则返回true；否则返回false。 |

**示例**

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

如果在缓存中未匹配到键，则执行后续操作，参数表示未匹配的键，返回与键关联的值，默认返回undefined。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-LRUCache-createDefault(key: K): V--><!--Device-LRUCache-createDefault(key: K): V-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 表示未匹配的键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | 返回与键关联的值。 |

**示例**

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

返回一个迭代器对象，用于按插入顺序遍历当前对象中的所有键值对（[key, value]）。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-LRUCache-entries(): IterableIterator<[K, V]>--><!--Device-LRUCache-entries(): IterableIterator<[K, V]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[K, V]&gt; | 返回一个迭代器对象，用于按插入顺序遍历当前缓冲区中的所有键值对[key, value]。 |

**示例**

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

返回键对应的值。当键不在缓存中时，通过[createDefault<sup>9+</sup>](#createdefault)接口创建，若createDefault创建的值不为undefined时，此时会调用[afterRemoval<sup>9+</sup>](#afterremoval)接口，返回createDefault创建的值。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-LRUCache-get(key: K): V | undefined--><!--Device-LRUCache-get(key: K): V | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 要查询的键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V &#124; undefined | 如果指定的键存在于缓冲区中，则返回与键关联的值；否则返回createDefault创建的值。 |

**示例**

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

获取当前缓存的容量。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-LRUCache-getCapacity(): number--><!--Device-LRUCache-getCapacity(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回当前缓冲区的容量。 |

**示例**

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

获取对象创建的次数。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-LRUCache-getCreateCount(): number--><!--Device-LRUCache-getCreateCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回创建对象的次数。 |

**示例**

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

获取查询值匹配成功的次数。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-LRUCache-getMatchCount(): number--><!--Device-LRUCache-getMatchCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回查询值匹配成功的次数。 |

**示例**

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

获取查询值不匹配的次数。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-LRUCache-getMissCount(): number--><!--Device-LRUCache-getMissCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回查询值不匹配的次数。 |

**示例**

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

获取将值添加到缓存的次数。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-LRUCache-getPutCount(): number--><!--Device-LRUCache-getPutCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回将值添加到缓冲区的次数。 |

**示例**

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

获取缓存键值对的回收次数。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-LRUCache-getRemovalCount(): number--><!--Device-LRUCache-getRemovalCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回缓冲区键值对回收的次数。 |

**示例**

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

检查缓存是否为空。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-LRUCache-isEmpty(): boolean--><!--Device-LRUCache-isEmpty(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果缓存不包含任何值，则返回true；否则返回false。 |

**示例**

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

获取当前缓存中所有键，从最近最少访问到最近访问的顺序列表。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-LRUCache-keys(): K[]--><!--Device-LRUCache-keys(): K[]-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| K[] | 返回当前缓冲区中所有键的列表，顺序为从最近最少访问（Least Recent）到最近访问（Most Recent）。 |

**示例**

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

将键值对添加到缓存，返回与添加的键关联的值。当缓存中值的总数超过容量时，执行删除操作。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-LRUCache-put(key: K, value: V): V--><!--Device-LRUCache-put(key: K, value: V): V-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 要添加的键。 |
| value | V | 是 | 指示与要添加的键关联的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | 返回与添加的键关联的值。如果键或值为空，则抛出此异常。 |

**示例**

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

从当前缓存中删除指定的键及其关联的值，并返回键关联的值。如果指定的键不存在，则返回undefined。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-LRUCache-remove(key: K): V | undefined--><!--Device-LRUCache-remove(key: K): V | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 要删除的键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V &#124; undefined | 返回与已删除键关联的值；如果key不存在，则返回undefined，如果key为null，则抛出异常。 |

**示例**

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

返回对象的字符串表示，格式为LRUCache[ maxSize = 缓存区最大值, hits = 查询匹配成功次数, misses = 查询匹配失败次数, hitRate = 查询匹配率 ]。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-LRUCache-toString(): string--><!--Device-LRUCache-toString(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回对象的字符串表示形式。 |

**示例**

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

更新缓存容量为指定值，如果newCapacity小于或等于0，则抛出异常。当缓存中值的总数大于指定容量时，会执行删除操作。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-LRUCache-updateCapacity(newCapacity: number): void--><!--Device-LRUCache-updateCapacity(newCapacity: number): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newCapacity | number | 是 | 指示要为缓冲区自定义的容量，取值范围为[0, 2147483647]。 |

**示例**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.updateCapacity(100);
```

## values

```TypeScript
values(): V[]
```

获取当前缓存中所有值，从最近最少访问到最近访问的顺序列表。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-LRUCache-values(): V[]--><!--Device-LRUCache-values(): V[]-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V[] | 返回当前缓冲区中所有值的列表，顺序为从最近最少访问（Least Recent）到最近访问（Most Recent）。 |

**示例**

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

当前缓存中值的总数。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-LRUCache-length: number--><!--Device-LRUCache-length: number-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.put(2, 10);
pro.put(1, 8);
let result = pro.length;
console.info('result = ' + result);
// 输出结果：result = 2
```
