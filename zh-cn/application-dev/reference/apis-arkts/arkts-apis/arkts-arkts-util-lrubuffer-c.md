# LruBuffer

```TypeScript
class LruBuffer<K, V>
```

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

返回一个键值对形式的二维数组。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [Symbol.iterator]

<!--Device-LruBuffer-[Symbol.iterator](): IterableIterator<[K, V]>--><!--Device-LruBuffer-[Symbol.iterator](): IterableIterator<[K, V]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[K, V]&gt; | 返回一个键值对形式的二维数组。 |

**示例**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
let result = pro[Symbol.iterator]();
```

## afterRemoval

```TypeScript
afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void
```

删除值后执行后续操作。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [afterRemoval](arkts-arkts-util-lrucache-c.md#afterremoval)

<!--Device-LruBuffer-afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void--><!--Device-LruBuffer-afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEvict | boolean | 是 | 因容量不足而调用该方法时，参数值为true，其他情况为false。 |
| key | K | 是 | 表示删除的键。 |
| value | V | 是 | 表示删除的值。 |
| newValue | V | 是 | 如果已调用put方法并且要添加的键已经存在，则参数值是关联的新值。其他情况下参数值为空。 |

**示例**

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

清除当前缓冲区中的键值对，后续调用[afterRemoval](#afterremoval)方法执行操作。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [clear](arkts-arkts-util-lrucache-c.md#clear)

<!--Device-LruBuffer-clear(): void--><!--Device-LruBuffer-clear(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例**

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

构造函数用于创建一个新的LruBuffer实例，默认容量为64。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [constructor](arkts-arkts-util-lrucache-c.md#constructor)

<!--Device-LruBuffer-constructor(capacity?: number)--><!--Device-LruBuffer-constructor(capacity?: number)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capacity | number | 否 | 指示要为缓冲区自定义的容量，取值范围为[0, 2147483647]，默认值为64。 |

**示例**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
```

## contains

```TypeScript
contains(key: K): boolean
```

检查当前缓冲区是否包含指定的键。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [contains](arkts-arkts-util-lrucache-c.md#contains)

<!--Device-LruBuffer-contains(key: K): boolean--><!--Device-LruBuffer-contains(key: K): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 表示要检查的键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果缓冲区包含指定的键，则返回true；否则返回false。 |

**示例**

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

当缓冲区中未匹配到指定键时，执行后续处理逻辑，参数表示未匹配到的键，返回与该键关联的值，默认返回undefined。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [createDefault](arkts-arkts-util-lrucache-c.md#createdefault)

<!--Device-LruBuffer-createDefault(key: K): V--><!--Device-LruBuffer-createDefault(key: K): V-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 表示丢失的键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | 返回与键关联的值。 |

**示例**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
let result = pro.createDefault(50);
```

## entries

```TypeScript
entries(): IterableIterator<[K, V]>
```

允许迭代包含在这个对象中的所有键值对。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [entries](arkts-arkts-util-lrucache-c.md#entries)

<!--Device-LruBuffer-entries(): IterableIterator<[K, V]>--><!--Device-LruBuffer-entries(): IterableIterator<[K, V]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[K, V]&gt; | 返回一个可迭代数组。 |

**示例**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
let result = pro.entries();
```

## get

```TypeScript
get(key: K): V | undefined
```

返回键对应的值。当键不在缓冲区中时，返回undefined。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [get](arkts-arkts-util-lrucache-c.md#get)

<!--Device-LruBuffer-get(key: K): V | undefined--><!--Device-LruBuffer-get(key: K): V | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 要查询的键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V &#124; undefined | 如果指定的键存在于缓冲区中，则返回与键关联的值；否则返回undefined。 |

**示例**

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

获取当前缓冲区的容量。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getCapacity](arkts-arkts-util-lrucache-c.md#getcapacity)

<!--Device-LruBuffer-getCapacity(): number--><!--Device-LruBuffer-getCapacity(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回当前缓冲区的容量。 |

**示例**

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

获取createDefault()返回值的次数。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getCreateCount](arkts-arkts-util-lrucache-c.md#getcreatecount)

<!--Device-LruBuffer-getCreateCount(): number--><!--Device-LruBuffer-getCreateCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回createDefault()返回值的次数。 |

**示例**

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

获取查询值匹配成功的次数。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getMatchCount](arkts-arkts-util-lrucache-c.md#getmatchcount)

<!--Device-LruBuffer-getMatchCount(): number--><!--Device-LruBuffer-getMatchCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回查询值匹配成功的次数。 |

**示例**

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

获取查询值不匹配的次数。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getMissCount](arkts-arkts-util-lrucache-c.md#getmisscount)

<!--Device-LruBuffer-getMissCount(): number--><!--Device-LruBuffer-getMissCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回查询值不匹配的次数。 |

**示例**

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

获取将值添加到缓冲区的次数。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getPutCount](arkts-arkts-util-lrucache-c.md#getputcount)

<!--Device-LruBuffer-getPutCount(): number--><!--Device-LruBuffer-getPutCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回将值添加到缓冲区的次数。 |

**示例**

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

获取从缓冲区中逐出值的次数。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getRemovalCount](arkts-arkts-util-lrucache-c.md#getremovalcount)

<!--Device-LruBuffer-getRemovalCount(): number--><!--Device-LruBuffer-getRemovalCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回从缓冲区中驱逐的次数。 |

**示例**

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

检查当前缓冲区是否为空。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isEmpty](arkts-arkts-util-lrucache-c.md#isempty)

<!--Device-LruBuffer-isEmpty(): boolean--><!--Device-LruBuffer-isEmpty(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果当前缓冲区不包含任何值，则返回true；否则返回false。 |

**示例**

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

获取当前缓冲区中所有键从最近访问到最近最少访问的升序列表。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [keys](arkts-arkts-util-lrucache-c.md#keys)

<!--Device-LruBuffer-keys(): K[]--><!--Device-LruBuffer-keys(): K[]-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| K[] | 按升序返回当前缓冲区中所有键的列表，从最近访问到最近最少访问。 |

**示例**

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

将键值对添加到缓冲区。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [put](arkts-arkts-util-lrucache-c.md#put)

<!--Device-LruBuffer-put(key: K, value: V): V--><!--Device-LruBuffer-put(key: K, value: V): V-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 要添加的键。 |
| value | V | 是 | 指示与要添加的键关联的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | 返回与添加的键关联的值；如果要添加的键已经存在，则返回原始值，如果键或值为空，则抛出此异常。 |

**示例**

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

删除当前缓冲区中指定的键及其关联的值。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [remove](arkts-arkts-util-lrucache-c.md#remove)

<!--Device-LruBuffer-remove(key: K): V | undefined--><!--Device-LruBuffer-remove(key: K): V | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 要删除的键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V &#124; undefined | 返回一个包含已删除键值对的Optional对象；如果key不存在，则返回一个空的Optional对象，如果key为null，则抛出异常。 |

**示例**

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

返回对象的字符串表示形式。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [toString](arkts-arkts-util-lrucache-c.md#tostring)

<!--Device-LruBuffer-toString(): string--><!--Device-LruBuffer-toString(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回对象的字符串表示形式。 |

**示例**

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

将缓冲区容量更新为指定容量，如果newCapacity小于或等于0，则抛出异常。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [updateCapacity](arkts-arkts-util-lrucache-c.md#updatecapacity)

<!--Device-LruBuffer-updateCapacity(newCapacity: number): void--><!--Device-LruBuffer-updateCapacity(newCapacity: number): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newCapacity | number | 是 | 指示要为缓冲区自定义的容量，取值范围为[0, 2147483647]。 |

**示例**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.updateCapacity(100);
```

## values

```TypeScript
values(): V[]
```

获取当前缓冲区中所有值从最近访问到最近最少访问的顺序列表。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [values](arkts-arkts-util-lrucache-c.md#values)

<!--Device-LruBuffer-values(): V[]--><!--Device-LruBuffer-values(): V[]-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V[] | 按从最近访问到最近最少访问的顺序返回当前缓冲区中所有值的列表。 |

**示例**

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

当前缓冲区中值的总数。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [length](arkts-arkts-util-lrucache-c.md#length)

<!--Device-LruBuffer-length: number--><!--Device-LruBuffer-length: number-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例**

```TypeScript
let pro : util.LruBuffer<number,number>= new util.LruBuffer();
pro.put(2,10);
pro.put(1,8);
let result = pro.length;
console.info("result = " + result);
// 输出结果：result = 2
```
