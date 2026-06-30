# Map
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

Map是一种用于存储键值对的数据结构。本模块提供高效的数据存储与访问能力，包括键值对的增删改查、遍历操作等。当需要建立唯一键与对应值的映射关系时，可使用本模块接口实现快速数据检索。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
>
> - 本模块首批接口从API version 24开始支持。

## ReadonlyMap\<K, V>

ReadonlyMap是一个接口，它定义了一个只读的键值对集合所需要包含的接口，描述了如何读取一个Map结构的数据，但不包含任何会修改该数据的方法。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 名称 | 类型 | 只读 | 可选 | 说明                         |
| ---- | ---- | ---- | ---- | ---------------------------- |
| size | int  | 是   | 否   | 返回Map中唯一key的数量。 |

### get

get(key: K): V | undefined

获取key对应的value值，不存在返回undefined。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明           |
| ------ | ---- | ---- | -------------- |
| key    | K    | 是   | 要查找的key。 |

**返回值：**

| 类型          | 说明                   |
| ------------- | ---------------------- |
| V\| undefined | 返回key映射的value值。 |

**示例：**

```ts
const map:ReadonlyMap<string,int> = new Map<string,int>([["a",1]]);
const value1=map.get("a");
console.info(value1); // 1
const value2=map.get("b");
console.info(value2); // undefined
```

### has

has(key: K): boolean

判断是否存在对应的key。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明           |
| ------ | ---- | ---- | -------------- |
| key    | K    | 是   | 要查找的key。 |

**返回值：**

| 类型    | 说明                                         |
| ------- | -------------------------------------------- |
| boolean | 判断是否包含指定元素。`true`表示包含，`false`表示不包含。 |

**示例：**

```ts
const map:ReadonlyMap<string,int> = new Map<string,int>([["a",1]]);
console.info(map.has("a")); // true
```

### forEach

forEach(callbackfn: (value: V, key: K, map: ReadonlyMap\<K, V>) => void)

在遍历过程中对每个元素调用一次回调函数，遍历顺序为元素插入顺序，使用callbackfn异步回调。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名     | 类型                                                                          | 必填 | 说明                                           |
| ---------- | ----------------------------------------------------------------------------- | ---- | ---------------------------------------------- |
| callbackfn | (value: V, key: K, map: [ReadonlyMap\<K, V>](#readonlymapk-v)) => void<br /> | 是   | 遍历时执行的回调函数，遍历顺序为元素插入顺序。 |

**示例：**

```ts
const map:ReadonlyMap<string,int> = new Map<string,int>([["a",1],["b",2]]);
map.forEach((value, key) => {
  console.info(`${key} = ${value}`);
});
// a = 1
// b = 2
```

### keys

keys(): IterableIterator\<K>

返回新迭代器对象，包含此映射中所有的键。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型             | 说明                                                                           |
| ---------------- | ------------------------------------------------------------------------------ |
| IterableIterator | 该方法返回一个迭代器对象，通过这个迭代器可以按插入顺序逐个检索映射中的所有键。 |

**示例：**

```ts
const map:ReadonlyMap<string,int> = new Map<string,int>([["a",1],["b",2]]);
const iter = map.keys();
console.info(iter.next().value); // a
console.info(iter.next().value); // b
```

### values

values(): IterableIterator\<V>

返回新迭代器对象，包含此映射中所有键对应的值。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型             | 说明                                                                           |
| ---------------- | ------------------------------------------------------------------------------ |
| IterableIterator | 该方法返回一个迭代器对象，通过这个迭代器可以按插入顺序逐个检索映射中的所有值。 |

**示例：**

```ts
const map:ReadonlyMap<string,int> = new Map<string,int>([["a",1],["b",2]]);
const iter = map.values();
console.info(iter.next().value); // 1
console.info(iter.next().value); // 2
```

### entries

entries(): IterableIterator\<[K, V]>

返回包含此映射中包含的键值对的新迭代器对象。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型                     | 说明                                                                               |
| ------------------------ | ---------------------------------------------------------------------------------- |
| IterableIterator\<[K, V]> | 该方法返回一个迭代器对象，通过这个迭代器可以按插入顺序逐个检索映射中的所有键值对。 |

**示例：**

```ts
const map:ReadonlyMap<string,int> = new Map<string,int>([["a",1],["b",2]]);
const iter = map.entries();
console.info(iter.next().value); // a,1
console.info(iter.next().value); // b,2
```

## MapIterator\<K, V, R>

Map的迭代器接口，用于按顺序遍历元素。实例由`keys`、`values`和`entries`等接口返回。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### next

next(): IteratorResult\<R>

返回下一个迭代器对象。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型           | 说明             |
| -------------- | ---------------- |
| IteratorResult | 下一个迭代结果。 |

**示例：**

```ts
const map = new Map<string, int>([["a", 1]]);
const iter = map.keys();
console.info(iter.next().value);
```

### $_iterator

$_iterator(): IterableIterator\<R>

返回一个迭代器，迭代器的每一项都是一个对象，并返回该对象。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型             | 说明             |
| ---------------- | ---------------- |
| IterableIterator | 返回自身迭代器。 |

**示例：**

```ts
const map = new Map<string, int>([["a", 1]]);
const iter = map.keys();
for (const key of iter) {
  console.info(key);
}
```

## Map\<K, V>

可读可写的Map实现，继承ReadonlyMap接口，支持插入、删除和清空。

**系统能力：** SystemCapability.Utils.Lang

### 属性

**系统能力：** SystemCapability.Utils.Lang

| 名称 | 类型 | 只读 | 可选 | 说明                         |
| ---- | ---- | ---- | ---- | ---------------------------- |
| size | int  | 是   | 否   | 返回Map中唯一key的数量。 |

### constructor

constructor(entries?: Iterable\<[K, V]> | readonly ((readonly [K, V]) | null | undefined)[] | null)

Map的构造函数。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名  | 类型                                                                           | 必填 | 说明                                             |
| ------- | ------------------------------------------------------------------------------ | ---- | ------------------------------------------------ |
| entries | Iterable\<[K, V]>\| readonly ((readonly [K, V]) \| null \| undefined)[] \| null | 否   | 可迭代的键值对集合以及只读数组（包含可能的空值）。 |

**返回值：**

| 类型        | 说明              |
| ----------- | ----------------- |
| Map\<K, V> | 新建的Map实例。 |

```ts
const map: Map<string, int> = new Map<string, int>([["a", 1], ["b", 2]]);
const map1 = new Map<string, int>(map.entries());
console.info(map1.get("a")); // 1
```

### constructor

constructor(map: Map\<K, V>)

从另一个Map拷贝内容，构造一个新的Map。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型        | 必填 | 说明           |
| ------ | ----------- | ---- | -------------- |
| map    | Map\<K, V> | 是   | 要拷贝的Map。 |

**返回值：**

| 类型        | 说明              |
| ----------- | ----------------- |
| Map\<K, V> | 新建的Map实例。 |

**示例：**

```ts
const map1 = new Map<string, int>([["a", 1], ["b", 2]]);
const map2 = new Map<string, int>(map1);
console.info(map2.get("b")); // 2
```

### constructor

constructor(entries: Array\<[K, V]>)

使用键值对数组构造Map。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名  | 类型          | 必填 | 说明         |
| ------- | ------------- | ---- | ------------ |
| entries | Array\<[K, V]> | 是   | 键值对数组。 |

**返回值：**

| 类型        | 说明              |
| ----------- | ----------------- |
| Map\<K, V> | 新建的Map实例。 |

**示例：**

```ts
const arr: Array<[string, int]> = [["a", 1], ["b", 2]];
const map = new Map<string, int>(arr);
console.info(map.get("a")); // 1
```

### constructor

constructor(bucketsCount: int)

通过指定桶数量构造空Map。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名       | 类型 | 必填 | 说明       |
| ------------ | ---- | ---- | ---------- |
| bucketsCount | int  | 是   | 初始桶数。 |

**返回值：**

| 类型        | 说明              |
| ----------- | ----------------- |
| Map\<K, V> | 新建的Map实例。 |

**示例：**

```ts
const map = new Map<string, double>(32); // 初始桶数为32
map.set("a", 100);
console.info(map.get("a")); // 100
```

### set

set(key: K, val: V): this

向Map中添加或更新一组数据。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明           |
| ------ | ---- | ---- | -------------- |
| key    | K    | 是   | 要插入的key。 |
| val    | V    | 是   | 对应的值。     |

**返回值：**

| 类型 | 说明                                |
| ---- | ----------------------------------- |
| this | 返回当前Map对象（支持链式调用）。 |

**示例：**

```ts
const map = new Map<string, int>();
map.set("a", 1).set("b", 2);
```

### get

get(key: K): V | undefined

获取指定key对应的value，不存在返回undefined。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明           |
| ------ | ---- | ---- | -------------- |
| key    | K    | 是   | 要查找的key。 |

**返回值：**

| 类型 | 说明                   |
| ---- | ---------------------- |
| V \| undefined | 返回key映射的value值，若不存在则为undefined。 |

**示例：**

```ts
const map = new Map<string, int>();
map.set("a", 1);
console.info(map.get("a")); // 1
console.info(map.get("b")); // undefined
```

### get

get(key: K, def: V): V

获取指定key映射的value值，不存在返回默认值def。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明                            |
| ------ | ---- | ---- | ------------------------------- |
| key    | K    | 是   | 要查找的key。                  |
| def    | V    | 否   | 如果key不存在时返回的默认值。 |

**返回值：**

| 类型 | 说明                                        |
| ---- | ------------------------------------------- |
| V    | 返回与key对应的值，若不存在则返回默认值。 |

**示例：**

```ts
const map = new Map<string, int>();
map.set("a", 1);
console.info(map.get("a")); // 1
console.info(map.get("b",2)); // 2
```

### has

has(key: K): boolean

判断此Map中是否包含指定key。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明           |
| ------ | ---- | ---- | -------------- |
| key    | K    | 是   | 要查找的key。 |

**返回值：**

| 类型    | 说明                                 |
| ------- | ------------------------------------ |
| boolean | 判断是否包含指定元素。`true`表示包含，`false`表示不包含。 |

**示例：**

```ts
const map = new Map<string, int>();
map.set("a", 1);
console.info(map.has("a"));//true
console.info(map.has("b"));//false
```

### delete

delete(key: K): boolean

删除指定key所对应元素。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明           |
| ------ | ---- | ---- | -------------- |
| key    | K    | 是   | 要删除的key。 |

**返回值：**

| 类型    | 说明                            |
| ------- | ------------------------------- |
| boolean | 判断是否删除成功。`true`表示删除成功，`false`表示删除失败。 |

**示例：**

```ts
const map = new Map<string, int>();
map.set("a", 1);
console.info(map.delete("a")); // true
console.info(map.get("a")); // undefined
```

### clear

clear()

清除Map中的所有元素，并将size置为0。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**示例：**

```ts
const map = new Map<string, int>();
map.set("a", 1);
map.set("b", 2);
map.clear();
console.info(map.get("a")); // undefined
console.info(map.get("b")); // undefined
console.info(map.size); // 0
```

### keys

keys(): IterableIterator\<K>

返回新迭代器对象，包含此映射中所有的键。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型                  | 说明                                                                           |
| --------------------- | ------------------------------------------------------------------------------ |
| IterableIterator\<K> | 该方法返回一个迭代器对象，通过这个迭代器可以按插入顺序逐个检索映射中的所有键。 |

**示例：**

```ts
const map = new Map<string, int>();
map.set("a", 1);
map.set("b", 2);
const iter = map.keys();
console.info(iter.next().value); // a
console.info(iter.next().value); // b
```

### values

values(): IterableIterator\<V>

返回新迭代器对象，包含此映射中所有键对应的值。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型                  | 说明                                                                           |
| --------------------- | ------------------------------------------------------------------------------ |
| IterableIterator\<V> | 该方法返回一个迭代器对象，通过这个迭代器可以按插入顺序逐个检索映射中的所有值。 |

**示例：**

```ts
const map = new Map<string, int>();
map.set("a", 1);
map.set("b", 2);
const iter = map.values();
console.info(iter.next().value); // 1
console.info(iter.next().value); // 2
```

### entries

entries(): IterableIterator\<[K, V]>

返回包含此映射中包含的键值对的新迭代器对象。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型                     | 说明                                                                               |
| ------------------------ | ---------------------------------------------------------------------------------- |
| IterableIterator\<[K, V]> | 该方法返回一个迭代器对象，通过这个迭代器可以按插入顺序逐个检索映射中的所有键值对。 |

**示例：**

```ts
const map = new Map<string, int>();
map.set("a", 1);
map.set("b", 2);
const iter = map.entries();
console.info(iter.next().value); // a,1
console.info(iter.next().value); // b,2
```

### forEach

forEach(callbackfn: (value: V, key: K, map: Map\<K, V>) => void)

在遍历过程中对每个元素调用一次回调函数。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名     | 类型                                         | 必填 | 说明                                       |
| ---------- | -------------------------------------------- | ---- | ------------------------------------------ |
| callbackfn | (value: V, key: K, map: [Map\<K, V>](#mapk-v)) => void | 是   | 按插入顺序对集合的每个值执行一次回调函数。 |

**示例：**

```ts
const map = new Map<string, int>();
map.set("a", 1);
map.set("b", 2);
map.forEach((value, key) => {
  console.info(`${key} = ${value}`);
});
// a = 1
// b = 2
```

### toString

toString(): string

将Map的元素按插入顺序转换成字符串返回。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型   | 说明                        |
| ------ | --------------------------- |
| string | 返回Map的字符串表示形式。 |

**示例：**

```ts
const map = new Map<string, int>();
map.set("a", 1);
map.set("b", 2);
console.info(map.toString()); // a,1,b,2
```

## Record\<K, V>

继承自Map\<K, V>，限制了key类型，仅支持数字类型、字符串类型、基于整数的枚举、基于长整型的枚举、基于字符串的枚举。

**系统能力：** SystemCapability.Utils.Lang

### $_get

$_get(key: K): V | undefined

获取指定key对应的value，不存在返回undefined。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明           |
| ------ | ---- | ---- | -------------- |
| key    | K    | 是   | 要查找的key。 |

**返回值：**

| 类型          | 说明                             |
| ------------- | -------------------------------- |
| V\| undefined | 返回值，若不存在则为undefined。 |

**示例：**

```ts
const record = new Record<string, int>();
record.$_set("a", 1);
console.info(record.$_get("a")); // 1
```

### $_set

$_set(key: K, value: V)

向Record中添加或更新一组数据。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明           |
| ------ | ---- | ---- | -------------- |
| key    | K    | 是   | 要设置的key。 |
| value  | V    | 是   | 要设置的值。   |

**示例：**

```ts
const record = new Record<string, int>();
record.$_set("a", 1);
console.info(record.$_get("a")); // 1
```
