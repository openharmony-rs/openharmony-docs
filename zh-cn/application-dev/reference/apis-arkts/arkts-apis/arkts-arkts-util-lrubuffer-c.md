# LruBuffer

LruBuffer 算法在缓存空间不足时使用新数据替换最不常使用的数据。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [LRUCache](arkts-arkts-util-lrucache-c.md)

<!--Device-util-class LruBuffer<K, V>--><!--Device-util-class LruBuffer<K, V>-End-->

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

**起始版本：** 8

**废弃版本：** 9

**替代接口：** iterator]

<!--Device-LruBuffer-[Symbol.iterator](): IterableIterator<[K, V]>--><!--Device-LruBuffer-[Symbol.iterator](): IterableIterator<[K, V]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator<[K, V]> | 返回以键值对形式的二维数组。 |

**示例：**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
let result = pro[Symbol.iterator]();

```

## afterRemoval

```TypeScript
afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void
```

在移除值后执行后续操作。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [afterRemoval](arkts-arkts-util-lrucache-c.md#afterremoval-1)

<!--Device-LruBuffer-afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void--><!--Device-LruBuffer-afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEvict | boolean | 是 | 容量是否不足。如果值为 **true**，则由于容量不足而调用此 API。 |
| key | K | 是 | 被移除的 key。 |
| value | V | 是 | 被移除的值。 |
| newValue | V | 是 | 如果调用了 **put()** 方法并且要添加的 key 已存在时该 key 的新值。其他情况下此参数为空。 |

**示例：**

```TypeScript
class ChildLruBuffer<K, V> extends util.LruBuffer<K, V> {
  constructor(capacity?: number) {
    super(capacity);
  }

  afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void {
    if (isEvict === true) {
      console.info('key: ' + key);
      // 输出结果：key: 11
      console.info('value: ' + value);
      // 输出结果：value: 1
      console.info('newValue: ' + newValue);
      // 输出结果：newValue: null
    }
  }
}
let lru: ChildLruBuffer<number, number> = new ChildLruBuffer(2);
lru.put(11, 1);
lru.put(22, 2);
lru.put(33, 3);

```

## clear

```TypeScript
clear(): void
```

从此缓存中清除键值对。将调用 **afterRemoval()** API 执行后续操作。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [clear](arkts-arkts-util-lrucache-c.md#clear-1)

<!--Device-LruBuffer-clear(): void--><!--Device-LruBuffer-clear(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例：**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
let result = pro.length;
pro.clear();

```

## constructor

```TypeScript
constructor(capacity?: number)
```

用于创建 **LruBuffer** 实例的构造函数。缓存的默认容量为 64。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** constructor

<!--Device-LruBuffer-constructor(capacity?: number)--><!--Device-LruBuffer-constructor(capacity?: number)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capacity | number | 否 | 要创建的缓存的容量。默认值为 **64**。 |

**示例：**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();

```

## contains

```TypeScript
contains(key: K): boolean
```

判断此缓存是否包含指定的 key。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [contains](arkts-arkts-util-lrucache-c.md#contains-1)

<!--Device-LruBuffer-contains(key: K): boolean--><!--Device-LruBuffer-contains(key: K): boolean-End-->

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
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
let result = pro.contains(20);
console.info('result = ' + result);
// 输出结果：result = false

```

## createDefault

```TypeScript
createDefault(key: K): V
```

当指定 key 的值不可用时，创建一个值。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [createDefault](arkts-arkts-util-lrucache-c.md#createdefault-1)

<!--Device-LruBuffer-createDefault(key: K): V--><!--Device-LruBuffer-createDefault(key: K): V-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 缺少值的 key。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | key 对应的值。 |

**示例：**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
let result = pro.createDefault(50);

```

## entries

```TypeScript
entries(): IterableIterator<[K, V]>
```

获取一个新的迭代器对象，该对象包含此对象中的所有键值对。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [entries](arkts-arkts-util-lrucache-c.md#entries-1)

<!--Device-LruBuffer-entries(): IterableIterator<[K, V]>--><!--Device-LruBuffer-entries(): IterableIterator<[K, V]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator<[K, V]> | 可迭代的数组。 |

**示例：**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
let result = pro.entries();

```

## get

```TypeScript
get(key: K): V | undefined
```

获取指定 key 对应的值。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [get](arkts-arkts-util-lrucache-c.md#get-1)

<!--Device-LruBuffer-get(key: K): V | undefined--><!--Device-LruBuffer-get(key: K): V | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 要查询值的 key。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | key 对应的值。如果未找到匹配项，则返回 **undefined**。 |

**示例：**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
let result  = pro.get(2);
console.info("result = " + result);
// 输出结果：result = 10

```

## getCapacity

```TypeScript
getCapacity(): number
```

获取此缓存的容量。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getCapacity](arkts-arkts-util-lrucache-c.md#getcapacity-1)

<!--Device-LruBuffer-getCapacity(): number--><!--Device-LruBuffer-getCapacity(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 缓存的容量。 |

**示例：**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
let result = pro.getCapacity();
console.info("result = " + result);
// 输出结果：result = 64

```

## getCreateCount

```TypeScript
getCreateCount(): number
```

获取 **createDefault()** 的返回值数量。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getCreateCount](arkts-arkts-util-lrucache-c.md#getcreatecount-1)

<!--Device-LruBuffer-getCreateCount(): number--><!--Device-LruBuffer-getCreateCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | **createDefault()** 的返回值数量。 |

**示例：**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(1,8);
let result = pro.getCreateCount();
console.info("result = " + result);
// 输出结果：result = 0

```

## getMatchCount

```TypeScript
getMatchCount(): number
```

获取查询值匹配的次数。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getMatchCount](arkts-arkts-util-lrucache-c.md#getmatchcount-1)

<!--Device-LruBuffer-getMatchCount(): number--><!--Device-LruBuffer-getMatchCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 查询值匹配的次数。 |

**示例：**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
pro.get(2);
let result = pro.getMatchCount();
console.info("result = " + result);
// 输出结果：result = 1

```

## getMissCount

```TypeScript
getMissCount(): number
```

获取查询值未匹配的次数。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getMissCount](arkts-arkts-util-lrucache-c.md#getmisscount-1)

<!--Device-LruBuffer-getMissCount(): number--><!--Device-LruBuffer-getMissCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 查询值未匹配的次数。 |

**示例：**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
pro.get(2);
let result = pro.getMissCount();
console.info("result = " + result);
// 输出结果：result = 0

```

## getPutCount

```TypeScript
getPutCount(): number
```

获取向此缓存添加的次数。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getPutCount](arkts-arkts-util-lrucache-c.md#getputcount-1)

<!--Device-LruBuffer-getPutCount(): number--><!--Device-LruBuffer-getPutCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 向缓存添加的次数。 |

**示例：**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
let result = pro.getPutCount();
console.info("result = " + result);
// 输出结果：result = 1

```

## getRemovalCount

```TypeScript
getRemovalCount(): number
```

获取从此缓存中移除的次数。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getRemovalCount](arkts-arkts-util-lrucache-c.md#getremovalcount-1)

<!--Device-LruBuffer-getRemovalCount(): number--><!--Device-LruBuffer-getRemovalCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 从缓存中移除的次数。 |

**示例：**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
pro.updateCapacity(2);
pro.put(50,22);
let result = pro.getRemovalCount();
console.info("result = " + result);
// 输出结果：result = 0

```

## isEmpty

```TypeScript
isEmpty(): boolean
```

判断此缓存是否为空。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isEmpty](arkts-arkts-util-lrucache-c.md#isempty-1)

<!--Device-LruBuffer-isEmpty(): boolean--><!--Device-LruBuffer-isEmpty(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果缓存不包含任何值，则返回 **true**。 |

**示例：**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
let result = pro.isEmpty();
console.info("result = " + result);
// 输出结果：result = false

```

## keys

```TypeScript
keys(): K[]
```

获取此缓存中的所有 key，按从最近最多访问到最近最少访问的顺序排列。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [keys](arkts-arkts-util-lrucache-c.md#keys-1)

<!--Device-LruBuffer-keys(): K[]--><!--Device-LruBuffer-keys(): K[]-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| K[] | 此缓存中的所有 key，按从最近最多访问到最近最少访问的顺序排列。 |

**示例：**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
let result = pro.keys();
console.info("result = " + result);
// 输出结果：result = 2

```

## put

```TypeScript
put(key: K, value: V): V
```

向此缓存添加键值对。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [put](arkts-arkts-util-lrucache-c.md#put-1)

<!--Device-LruBuffer-put(key: K, value: V): V--><!--Device-LruBuffer-put(key: K, value: V): V-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 要添加的键值对的 key。 |
| value | V | 是 | 要添加的键值对的 value。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | 添加的值。如果 key 已存在，则返回已存在的值；如果 **key** 或 **value** 传入 **null**，则抛出错误。 |

**示例：**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
let result = pro.put(2,10);
console.info("result = " + result);
// 输出结果：result = 10

```

## remove

```TypeScript
remove(key: K): V | undefined
```

从此缓存中移除指定的 key 及其对应的值。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [remove](arkts-arkts-util-lrucache-c.md#remove-1)

<!--Device-LruBuffer-remove(key: K): V | undefined--><!--Device-LruBuffer-remove(key: K): V | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 要移除的 key。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | 包含被移除键值对的 **Optional** 对象。如果 key 不存在，则返回空的 **Optional**对象；如果 **key** 传入 **null**，则抛出错误。 |

**示例：**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
let result = pro.remove(20);
console.info("result = " + result);
// 输出结果：result = undefined

```

## toString

```TypeScript
toString(): string
```

获取此缓存的字符串表示形式。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [toString](arkts-arkts-util-lrucache-c.md#tostring-1)

<!--Device-LruBuffer-toString(): string--><!--Device-LruBuffer-toString(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 此缓存的字符串表示形式。 |

**示例：**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
pro.get(2);
pro.remove(20);
let result = pro.toString();
console.info("result = " + result);
// 输出结果：result = Lrubuffer[ maxSize = 64, hits = 1, misses = 0, hitRate = 100% ]

```

## updateCapacity

```TypeScript
updateCapacity(newCapacity: number): void
```

改变缓存容量。如果新容量小于等于 **0**，则抛出异常。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [updateCapacity](arkts-arkts-util-lrucache-c.md#updatecapacity-1)

<!--Device-LruBuffer-updateCapacity(newCapacity: number): void--><!--Device-LruBuffer-updateCapacity(newCapacity: number): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newCapacity | number | 是 | 缓存的新容量。 |

**示例：**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.updateCapacity(100);

```

## values

```TypeScript
values(): V[]
```

获取此缓存中的所有值，按从最近最多访问到最近最少访问的顺序排列。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [values](arkts-arkts-util-lrucache-c.md#values-1)

<!--Device-LruBuffer-values(): V[]--><!--Device-LruBuffer-values(): V[]-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V[] | 此缓存中的所有值，按从最近最多访问到最近最少访问的顺序排列。 |

**示例：**

```TypeScript
let pro : util.LruBuffer<number|string,number|string> = new util.LruBuffer();
pro.put(2,10);
pro.put(2,"anhu");
pro.put("afaf","grfb");
let result = pro.values();
console.info("result = " + result);
// 输出结果：result = anhu,grfb

```

## length

```TypeScript
length: number
```

此缓存中值的总数。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** length

<!--Device-LruBuffer-length: number--><!--Device-LruBuffer-length: number-End-->

**系统能力：** SystemCapability.Utils.Lang

