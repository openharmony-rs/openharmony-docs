# HashMap

HashMap底层采用数组、链表和红黑树实现，支持高效查询、插入和删除。HashMap实例中的元素为键值对的映射，每个键必须唯一且只能对应一个值。

**起始版本：** 8

<!--Device-unnamed-declare class HashMap<K, V>--><!--Device-unnamed-declare class HashMap<K, V>-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { HashMap } from '@kit.ArkTS';
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<[K, V]>
```

返回一个迭代器，迭代器的每一项都是一个JavaScript对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HashMap-[Symbol.iterator](): IterableIterator<[K, V]>--><!--Device-HashMap-[Symbol.iterator](): IterableIterator<[K, V]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[K, V]&gt; | @throws { BusinessError } 10200011 - The Symbol.iterator method cannot be bound. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The Symbol.iterator method cannot be bound. |

**示例：**

```TypeScript
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
hashMap.set("sparrow", 356);

// 使用方法一：
for (let item of hashMap) {
  console.info("key:", item[0]);
  console.info("value:", item[1]);
}
// key: squirrel
// value: 123
// key: sparrow
// value: 356

// 使用方法二：
let iter = hashMap[Symbol.iterator]();
let temp: IteratorResult<Object[]> = iter.next();
while (!temp.done) {
  console.info("key:", temp.value[0]);
  console.info("value:", temp.value[1]);
  temp = iter.next();
}
// key: squirrel
// value: 123
// key: sparrow
// value: 356

```

```TypeScript
// 不建议在Symbol.iterator中使用set、remove方法，因其可能导致迭代过程中的状态异常，建议使用for循环来进行安全的插入与删除操作。
let hashMap = new HashMap<string, number>();
for (let i = 0; i < 10; i++) {
  hashMap.set("sparrow" + i, 123);
}

for (let i = 0; i < 10; i++) {
  hashMap.remove("sparrow" + i);
}

```

## clear

```TypeScript
clear(): void
```

清除HashMap中的所有元素，并将length置为0。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HashMap-clear(): void--><!--Device-HashMap-clear(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The clear method cannot be bound. |

**示例：**

```TypeScript
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
hashMap.set("sparrow", 356);
hashMap.clear();
let result = hashMap.isEmpty();
console.info("result:", result);  // result: true

```

## constructor

```TypeScript
constructor()
```

HashMap的构造函数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HashMap-constructor()--><!--Device-HashMap-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The HashMap's constructor cannot be directly invoked. |

**示例：**

```TypeScript
let hashMap = new HashMap<string, number>();

```

## entries

```TypeScript
entries(): IterableIterator<[K, V]>
```

返回包含此映射中包含的键值对的新迭代器对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HashMap-entries(): IterableIterator<[K, V]>--><!--Device-HashMap-entries(): IterableIterator<[K, V]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[K, V]&gt; | 返回一个迭代器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The entries method cannot be bound. |

**示例：**

```TypeScript
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
hashMap.set("sparrow", 356);
let iter = hashMap.entries();
let temp: IteratorResult<Object[]> = iter.next();
while (!temp.done) {
  console.info("key:" + temp.value[0]);
  console.info("value:" + temp.value[1]);
  temp = iter.next();
}

```

```TypeScript
// 不建议在entries中使用set、remove方法，因其可能导致迭代过程中的状态异常，建议使用for循环来进行安全的插入与删除操作。
let hashMap = new HashMap<string, number>();
for (let i = 0; i < 10; i++) {
  hashMap.set("sparrow" + i, 123);
}

for (let i = 0; i < 10; i++) {
  hashMap.remove("sparrow" + i);
}

```

## forEach

```TypeScript
forEach(callbackFn: (value?: V, key?: K, map?: HashMap<K, V>) => void, thisArg?: Object): void
```

在遍历过程中对每个元素调用一次回调函数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HashMap-forEach(callbackFn: (value?: V, key?: K, map?: HashMap<K, V>) => void, thisArg?: Object): void--><!--Device-HashMap-forEach(callbackFn: (value?: V, key?: K, map?: HashMap<K, V>) => void, thisArg?: Object): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value?: V, key?: K, map?: HashMap&lt;K, V&gt;) =&gt; void | 是 | 回调函数。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值，默认值为当前实例对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The forEach method cannot be bound. |

**示例：**

```TypeScript
let hashMap = new HashMap<string, number>();
hashMap.set("sparrow", 123);
hashMap.set("gull", 357);
hashMap.forEach((value: number, key: string) => {
  console.info("value: " + value, "key: " + key);
});
// value: 123 key: sparrow
// value: 357 key: gull

```

```TypeScript
// 不建议在forEach中使用set、remove方法，因其可能导致迭代过程中的状态异常，建议使用for循环来进行安全的插入与删除操作。
let hashMap = new HashMap<string, number>();
for (let i = 0; i < 10; i++) {
  hashMap.set("sparrow" + i, 123);
}

for (let i = 0; i < 10; i++) {
  hashMap.remove("sparrow" + i);
}

```

## get

```TypeScript
get(key: K): V
```

获取指定key对应的value，不存在返回undefined。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HashMap-get(key: K): V--><!--Device-HashMap-get(key: K): V-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 查找的指定key。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | 返回key映射的value值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The get method cannot be bound. |

**示例：**

```TypeScript
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
hashMap.set("sparrow", 356);
let result = hashMap.get("sparrow");
console.info("result:", result);  // result: 356

```

## hasKey

```TypeScript
hasKey(key: K): boolean
```

判断此HashMap中是否包含指定key。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HashMap-hasKey(key: K): boolean--><!--Device-HashMap-hasKey(key: K): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 指定Key。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 包含指定Key返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The hasKey method cannot be bound. |

**示例：**

```TypeScript
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
let result = hashMap.hasKey("squirrel");
console.info("result:", result);  // result: true

```

## hasValue

```TypeScript
hasValue(value: V): boolean
```

判断此HashMap中是否包含指定value。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HashMap-hasValue(value: V): boolean--><!--Device-HashMap-hasValue(value: V): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | V | 是 | 指定value。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 包含指定的value返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The hasValue method cannot be bound. |

**示例：**

```TypeScript
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
let result = hashMap.hasValue(123);
console.info("result:", result);  // result: true

```

## isEmpty

```TypeScript
isEmpty(): boolean
```

判断该HashMap是否为空。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HashMap-isEmpty(): boolean--><!--Device-HashMap-isEmpty(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 为空返回true，不为空返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The isEmpty method cannot be bound. |

**示例：**

```TypeScript
let hashMap = new HashMap<string, number>();
let result = hashMap.isEmpty();
console.info("result:", result);  // result: true

```

## keys

```TypeScript
keys(): IterableIterator<K>
```

返回新迭代器对象，包含此映射中所有的键。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HashMap-keys(): IterableIterator<K>--><!--Device-HashMap-keys(): IterableIterator<K>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;K&gt; | 返回一个迭代器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The keys method cannot be bound. |

**示例：**

```TypeScript
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
hashMap.set("sparrow", 356);
let keys = hashMap.keys();
for (let key of keys) {
  console.info("key:" + key);
}
// key:squirrel
// key:sparrow

```

## remove

```TypeScript
remove(key: K): V
```

删除指定key所对应元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HashMap-remove(key: K): V--><!--Device-HashMap-remove(key: K): V-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 指定key。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | 返回删除元素的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The remove method cannot be bound. |

**示例：**

```TypeScript
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
hashMap.set("sparrow", 356);
let result = hashMap.remove("sparrow");
console.info("result:", result);  // result: 356

```

## replace

```TypeScript
replace(key: K, newValue: V): boolean
```

用于替换指定键对应的值。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HashMap-replace(key: K, newValue: V): boolean--><!--Device-HashMap-replace(key: K, newValue: V): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 依据key指定替换的元素。 |
| newValue | V | 是 | 替换成员数据的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否成功对已有数据进行替换，成功返回true，失败返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The replace method cannot be bound. |

**示例：**

```TypeScript
let hashMap = new HashMap<string, number>();
hashMap.set("sparrow", 123);
let result = hashMap.replace("sparrow", 357);
console.info("result:", result);  // result: true

```

## set

```TypeScript
set(key: K, value: V): Object
```

向HashMap中添加或更新一组数据。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HashMap-set(key: K, value: V): Object--><!--Device-HashMap-set(key: K, value: V): Object-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 添加或更新成员数据的键名。 |
| value | V | 是 | 添加或更新成员数据的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | 返回添加或更新后的HashMap。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The set method cannot be bound. |

**示例：**

```TypeScript
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
console.info("result:", hashMap.get("squirrel"));  // result: 123

```

## setAll

```TypeScript
setAll(map: HashMap<K, V>): void
```

将一个HashMap中的所有元素组添加到另一个HashMap中。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HashMap-setAll(map: HashMap<K, V>): void--><!--Device-HashMap-setAll(map: HashMap<K, V>): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| map | [HashMap](arkts-arkts-util-hashmap-hashmap-c.md)&lt;K, V&gt; | 是 | 被添加元素的HashMap。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The setAll method cannot be bound. |

**示例：**

```TypeScript
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
hashMap.set("sparrow", 356);
let newHashMap = new HashMap<string, number>();
newHashMap.set("newMap", 99);
hashMap.setAll(newHashMap);
let result = hashMap.hasKey("newMap");
console.info("result:", result);  // result: true

```

## values

```TypeScript
values(): IterableIterator<V>
```

返回新迭代器对象，包含此映射中所有键对应的值。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HashMap-values(): IterableIterator<V>--><!--Device-HashMap-values(): IterableIterator<V>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;V&gt; | 返回一个迭代器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The values method cannot be bound. |

**示例：**

```TypeScript
let hashMap = new HashMap<string, number>();
hashMap.set("squirrel", 123);
hashMap.set("sparrow", 356);
let values = hashMap.values();
for (let value of values) {
  console.info("value:", value);
}
// value: 123
// value: 356

```

## length

```TypeScript
length: number
```

HashMap的元素个数。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HashMap-length: number--><!--Device-HashMap-length: number-End-->

**系统能力：** SystemCapability.Utils.Lang

