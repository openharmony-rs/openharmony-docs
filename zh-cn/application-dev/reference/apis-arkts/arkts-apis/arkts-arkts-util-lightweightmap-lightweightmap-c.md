# LightWeightMap

LightWeightMap可用于存储具有关联关系的key-value键值对，其中key值唯一，每个key对应一个value。

**起始版本：** 23

<!--Device-unnamed-declare class LightWeightMap--><!--Device-unnamed-declare class LightWeightMap-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { LightWeightMap } from '@kit.ArkTS';
import { LightWeightMapCbFn } from '@kit.ArkTS';
```

## $_iterator

```TypeScript
$_iterator(): IterableIterator<[K, V]>
```

返回一个迭代器，迭代器的每一项都是一个包含键和值的[K, V]数组。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-$_iterator(): IterableIterator<[K, V]>--><!--Device-LightWeightMap-$_iterator(): IterableIterator<[K, V]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[K, V]&gt; | LightWeightMap的迭代器。 |

**示例**

```TypeScript
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

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<[K, V]>
```

返回一个迭代器，迭代器的每一项都是一个包含键和值的[K, V]数组。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-[Symbol.iterator](): IterableIterator<[K, V]>--><!--Device-LightWeightMap-[Symbol.iterator](): IterableIterator<[K, V]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[K, V]&gt; | 返回一个迭代器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The Symbol.iterator method cannot be bound. |

**示例**

```TypeScript
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

```TypeScript
// 不建议在Symbol.iterator中使用set、setValueAt、remove、removeAt方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。
let lightWeightMap = new LightWeightMap<string, number>();
for(let i = 0; i < 10; i++) {
  lightWeightMap.set("sparrow" + i, 123);
}
for(let i = 0; i < 10; i++) {
  lightWeightMap.remove("sparrow" + i);
}
```

## clear

```TypeScript
clear(): void
```

清除LightWeightMap中的所有元素，并将length置为0。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-clear(): void--><!--Device-LightWeightMap-clear(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The clear method cannot be bound. |

**示例**

ArkTS-Dyn示例：

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
lightWeightMap.clear();
let result = lightWeightMap.isEmpty();
console.info("result:", result);  // result: true
```

ArkTS-Sta示例：

```TypeScript
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
lightWeightMap.clear();
let result = lightWeightMap.isEmpty();
console.info("result:", result);  // result: true
```

## constructor

```TypeScript
constructor()
```

LightWeightMap的构造函数，创建一个空的LightWeightMap实例。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-constructor()--><!--Device-LightWeightMap-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The LightWeightMap's constructor cannot be directly invoked. |

**示例**

ArkTS-Dyn示例：

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
```

ArkTS-Sta示例：

```TypeScript
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
```

## entries

```TypeScript
entries(): IterableIterator<[K, V]>
```

返回包含此映射中所有键值对的新迭代器对象。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-entries(): IterableIterator<[K, V]>--><!--Device-LightWeightMap-entries(): IterableIterator<[K, V]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[K, V]&gt; | 返回包含此映射中所有键值对的迭代器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The entries method cannot be bound. |

**示例**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let iteratorResult = lightWeightMap.entries();
let temp: IteratorResult<Object[]> = iteratorResult.next();
while (!temp.done) {
  console.info("key:" + temp.value[0]);
  console.info("value:" + temp.value[1]);
  temp = iteratorResult.next();
}
```

```TypeScript
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

```TypeScript
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

```TypeScript
// 不建议在entries中使用set、setValueAt、remove、removeAt方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
for(let i = 0; i < 10; i++) {
  lightWeightMap.set("sparrow" + i, 123);
}
for(let i = 0; i < 10; i++) {
  lightWeightMap.remove("sparrow" + i);
}
```

## forEach

```TypeScript
forEach(callbackFn: (value?: V, key?: K, map?: LightWeightMap<K, V>) => void, thisArg?: Object): void
```

通过回调函数来遍历实例对象上的元素及其键值对信息。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-forEach(callbackFn: (value?: V, key?: K, map?: LightWeightMap<K, V>) => void, thisArg?: Object): void--><!--Device-LightWeightMap-forEach(callbackFn: (value?: V, key?: K, map?: LightWeightMap<K, V>) => void, thisArg?: Object): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value?: V, key?: K, map?: LightWeightMap&lt;K, V&gt;) =&gt; void | 是 | 回调函数，用于遍历LightWeightMap实例中的元素及下标。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值。当需要回调函数中的this指向非当前实例对象时传入此参数，当不需要改变this指向时可不传入。不传入时，默认值为当前实例对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The forEach method cannot be bound. |

**示例**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("sparrow", 123);
lightWeightMap.set("gull", 357);
lightWeightMap.forEach((value: number, key: string) => {
  console.info("value:" + value, "key:" + key);
});
// value:123 key:sparrow
// value:357 key:gull
```

```TypeScript
// 不建议在forEach中使用set、setValueAt、remove、removeAt方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。
let lightWeightMap = new LightWeightMap<string, number>();
for (let i = 0; i < 10; i++) {
  lightWeightMap.set("sparrow" + i, 123);
}
for (let i = 0; i < 10; i++) {
  lightWeightMap.remove("sparrow" + i);
}
```

## forEach

```TypeScript
forEach(callbackFn: LightWeightMapCbFn<K, V>): void
```

通过回调函数来遍历实例对象上的元素及其键值对信息。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-forEach(callbackFn: LightWeightMapCbFn<K, V>): void--><!--Device-LightWeightMap-forEach(callbackFn: LightWeightMapCbFn<K, V>): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | [LightWeightMapCbFn](arkts-arkts-lightweightmapcbfn-t.md)&lt;K, V&gt; | 是 | 回调函数，用于遍历LightWeightMap实例中的元素及下标。 |

**示例**

```TypeScript
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

## get

```TypeScript
get(key: K): V
```

获取指定key所对应的value。当key为number类型且值大于INT32_MAX或小于INT32_MIN时，结果可能与预期不一致。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-get(key: K): V--><!--Device-LightWeightMap-get(key: K): V-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 指定key。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | 返回key映射的value值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The get method cannot be bound. |

**示例**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.get("sparrow");
console.info("result:", result);  // result: 356
```

## get

```TypeScript
get(key: K): V | undefined
```

获取指定key所对应的value。当key为number类型且值大于INT32_MAX或小于INT32_MIN时，结果可能与预期不一致。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-get(key: K): V | undefined--><!--Device-LightWeightMap-get(key: K): V | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 指定key。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | 如果存在与key关联的值则返回该值，否则返回undefined。 |

**示例**

```TypeScript
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.get("sparrow");
console.info("result:", result);  // result: 356
```

## getIndexOfKey

```TypeScript
getIndexOfKey(key: K): int
```

查找key元素首次出现的下标值，如果未找到返回-1。当key为number类型且值大于INT32_MAX或小于INT32_MIN时，结果可能与预期不一致。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-getIndexOfKey(key: K): int--><!--Device-LightWeightMap-getIndexOfKey(key: K): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 被查找的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回key元素首次出现的下标值，查找失败返回-1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getIndexOfKey method cannot be bound. |

**示例**

ArkTS-Dyn示例：

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.getIndexOfKey("sparrow");
console.info("result:", result);  // result: 0
```

ArkTS-Sta示例：

```TypeScript
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.getIndexOfKey("sparrow");
console.info("result:", result);  // result: 0
```

## getIndexOfValue

```TypeScript
getIndexOfValue(value: V): int
```

查找指定value元素首次出现的下标值，如果未找到则返回-1。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-getIndexOfValue(value: V): int--><!--Device-LightWeightMap-getIndexOfValue(value: V): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | V | 是 | 要查找首次出现下标位置的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回value元素首次出现的下标值，查找失败返回-1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getIndexOfValue method cannot be bound. |

**示例**

ArkTS-Dyn示例：

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.getIndexOfValue(123);
console.info("result:", result);  // result: 1
```

ArkTS-Sta示例：

```TypeScript
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.getIndexOfValue(123);
console.info("result:", result);  // result: 1
```

## getKeyAt

```TypeScript
getKeyAt(index: number): K
```

查找指定下标的元素键值对中key值，如果未找到则返回undefined。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-getKeyAt(index: number): K--><!--Device-LightWeightMap-getKeyAt(index: number): K-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 所查找的下标。需要小于等于INT32_MAX即2147483647。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| K | 返回该下标对应的元素键值对中key值，如果未找到则返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getKeyAt method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

**示例**

```TypeScript
// 不建议在keys中使用set、setValueAt、remove、removeAt方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.getKeyAt(1);
console.info("result:", result);  // result: squirrel
```

## getKeyAt

```TypeScript
getKeyAt(index: int): K | undefined
```

查找指定下标的元素键值对中key值，如果未找到则返回undefined。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-getKeyAt(index: int): K | undefined--><!--Device-LightWeightMap-getKeyAt(index: int): K | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 所查找的下标。需要小于等于INT32_MAX即2147483647。 取值限定为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| K | 返回指定下标对应的key，如果下标超出范围则返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

**示例**

```TypeScript
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.getKeyAt(1);
console.info("result:", result);  // result: squirrel
```

## getValueAt

```TypeScript
getValueAt(index: number): V
```

获取指定下标对应键值对中的值。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-getValueAt(index: number): V--><!--Device-LightWeightMap-getValueAt(index: number): V-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 指定下标。需要小于等于INT32_MAX即2147483647。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | 返回指定下标对应键值对中的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getValueAt method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

**示例**

```TypeScript
// 不建议在values中使用set、setValueAt、remove、removeAt方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.getValueAt(1);
console.info("result:", result);  // result: 123
```

## getValueAt

```TypeScript
getValueAt(index: int): V | undefined
```

获取指定下标对应键值对中的值。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-getValueAt(index: int): V | undefined--><!--Device-LightWeightMap-getValueAt(index: int): V | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 要删除的元素的下标位置。取值范围：[0, length-1]，需小于等于INT32_MAX即2147483647。 取值限定为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | 返回指定下标对应的值，如果下标超出范围则返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

**示例**

```TypeScript
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.getValueAt(1);
console.info("result:", result);  // result: 123
```

## hasAll

```TypeScript
hasAll(map: LightWeightMap<K, V>): boolean
```

判断LightWeightMap中是否包含指定map中的所有元素。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-hasAll(map: LightWeightMap<K, V>): boolean--><!--Device-LightWeightMap-hasAll(map: LightWeightMap<K, V>): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| map | [LightWeightMap](arkts-arkts-util-lightweightmap-lightweightmap-c.md)&lt;K, V&gt; | 是 | 用于比较的LightWeightMap对象，判断当前实例是否包含此map中的所有元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 包含所有元素返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The hasAll method cannot be bound. |

**示例**

ArkTS-Dyn示例：

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let targetMap = new LightWeightMap<string, number>();
targetMap.set("sparrow", 356);
let result = lightWeightMap.hasAll(targetMap); 
console.info("result = ", result); // result = true
```

ArkTS-Sta示例：

```TypeScript
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let map = new LightWeightMap<string, int>();
map.set("sparrow", 356);
let result = lightWeightMap.hasAll(map);
console.info("result = ", result); // result = true
```

## hasKey

```TypeScript
hasKey(key: K): boolean
```

判断LightWeightMap中是否包含指定key。当key为number类型且值大于INT32_MAX或小于INT32_MIN时，结果可能与预期不一致，详见规格限制。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-hasKey(key: K): boolean--><!--Device-LightWeightMap-hasKey(key: K): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 指定key。当key为number类型且值大于INT32_MAX或小于INT32_MIN时，结果可能与预期不一致。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 包含指定key返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The hasKey method cannot be bound. |

**示例**

ArkTS-Dyn示例：

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
let result = lightWeightMap.hasKey("squirrel");
console.info("result:", result);  // result: true
```

ArkTS-Sta示例：

```TypeScript
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
let result = lightWeightMap.hasKey("squirrel");
```

## hasValue

```TypeScript
hasValue(value: V): boolean
```

判断LightWeightMap中是否包含指定value。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-hasValue(value: V): boolean--><!--Device-LightWeightMap-hasValue(value: V): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | V | 是 | 要判断是否包含的value。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 包含指定元素返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The hasValue method cannot be bound. |

**示例**

ArkTS-Dyn示例：

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
let result = lightWeightMap.hasValue(123);
console.info("result:", result);  // result: true
```

ArkTS-Sta示例：

```TypeScript
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
let result = lightWeightMap.hasValue(123);
console.info("result:", result);  // result: true
```

## increaseCapacityTo

```TypeScript
increaseCapacityTo(minimumCapacity: int): void
```

将当前LightWeightMap扩容至指定容量。如果传入的容量值大于或等于当前LightWeightMap中的元素个数，将容量扩容至新容量，小于则不会变更。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-increaseCapacityTo(minimumCapacity: int): void--><!--Device-LightWeightMap-increaseCapacityTo(minimumCapacity: int): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| minimumCapacity | int | 是 | 需要容纳的元素数量。取值需大于等于0，大于等于当前元素个数时扩容生效，否则不变更容量。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The increaseCapacityTo method cannot be bound. |

**示例**

ArkTS-Dyn示例：

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.increaseCapacityTo(10);
```

ArkTS-Sta示例：

```TypeScript
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.increaseCapacityTo(10);
```

## isEmpty

```TypeScript
isEmpty(): boolean
```

判断LightWeightMap是否为空。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-isEmpty(): boolean--><!--Device-LightWeightMap-isEmpty(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 为空返回true，不为空返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The isEmpty method cannot be bound. |

**示例**

ArkTS-Dyn示例：

```TypeScript
const lightWeightMap = new LightWeightMap<string, number>();
let result = lightWeightMap.isEmpty();
console.info("result:", result);  // result: true
```

ArkTS-Sta示例：

```TypeScript
const lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
let result = lightWeightMap.isEmpty();
console.info("result:", result);  // result: true
```

## keys

```TypeScript
keys(): IterableIterator<K>
```

返回包含此映射中所有的键的新迭代器对象。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-keys(): IterableIterator<K>--><!--Device-LightWeightMap-keys(): IterableIterator<K>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;K&gt; | 返回一个迭代器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The keys method cannot be bound. |

**示例**

ArkTS-Dyn示例：

```TypeScript
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

```TypeScript
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

## remove

```TypeScript
remove(key: K): V
```

删除指定key映射的元素。当key为number类型且值大于INT32_MAX或小于INT32_MIN时，结果可能与预期不一致。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-remove(key: K): V--><!--Device-LightWeightMap-remove(key: K): V-End-->

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

**示例**

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.remove("sparrow");
console.info("result:", result);  // result: 356
```

## remove

```TypeScript
remove(key: K): V | undefined
```

删除指定key映射的元素。当key为number类型且值大于INT32_MAX或小于INT32_MIN时，结果可能与预期不一致。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-remove(key: K): V | undefined--><!--Device-LightWeightMap-remove(key: K): V | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 指定key。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | 如果删除了元素则返回该元素的值，否则返回undefined。 |

**示例**

```TypeScript
let lightWeightMap: LightWeightMap<string, number> = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
lightWeightMap.remove("sparrow");
console.info("result:", result);  // result: 356
```

## removeAt

```TypeScript
removeAt(index: int): boolean
```

删除指定下标对应的元素。调用成功后，若下标有效则该位置的键值对从LightWeightMap中移除且length减少。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-removeAt(index: int): boolean--><!--Device-LightWeightMap-removeAt(index: int): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 要删除的元素的下标位置。取值范围：[0, length-1]，需小于等于INT32_MAX即2147483647。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 成功删除元素返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The removeAt method cannot be bound. |

**示例**

ArkTS-Dyn示例：

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.removeAt(1);
console.info("result:", result);  // result: true
```

ArkTS-Sta示例：

```TypeScript
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.removeAt(1);
console.info("result:", result);  // result: true
```

## set

```TypeScript
set(key: K, value: V): Object
```

向LightWeightMap中添加或更新一组数据。调用成功后，若key不存在则新增键值对且length增加，若key已存在则更新对应value值。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-set(key: K, value: V): Object--><!--Device-LightWeightMap-set(key: K, value: V): Object-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 添加或更新成员数据的键名。当key为number类型且值大于INT32_MAX或小于INT32_MIN时，结果可能与预期不一致。 |
| value | V | 是 | 添加或更新成员数据的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | 返回添加或更新后的LightWeightMap实例对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The set method cannot be bound. |

**示例**

ArkTS-Dyn示例：

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
let result = lightWeightMap.set("squirrel", 123);
console.info("result:", result);  // result: squirrel:123
```

ArkTS-Sta示例：

```TypeScript
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
let result = lightWeightMap.set("squirrel", 123);
console.info("result:", result);  // result: squirrel:123
```

## setAll

```TypeScript
setAll(map: LightWeightMap<K, V>): void
```

将一个LightWeightMap中的所有元素添加到另一个LightWeightMap中，如果目标LightWeightMap中已存在相同的key，则会更新其对应的value。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-setAll(map: LightWeightMap<K, V>): void--><!--Device-LightWeightMap-setAll(map: LightWeightMap<K, V>): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| map | [LightWeightMap](arkts-arkts-util-lightweightmap-lightweightmap-c.md)&lt;K, V&gt; | 是 | 提供添加元素的LightWeightMap。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The setAll method cannot be bound. |

**示例**

ArkTS-Dyn示例：

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let map = new LightWeightMap<string, number>();
map.setAll(lightWeightMap);   // 将lightWeightMap中所有的元素添加到map中
let result = map.get("sparrow");
console.info("result:", result);  // result: 356
```

ArkTS-Sta示例：

```TypeScript
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let map: LightWeightMap<string, int> = new LightWeightMap<string, int>();
map.setAll(lightWeightMap); // 将lightWeightMap中所有的元素添加到map中
let result = map.get("sparrow");
console.info("result:", result);  // result: 356
```

## setValueAt

```TypeScript
setValueAt(index: int, newValue: V): boolean
```

替换指定下标对应键值对中的值。调用成功后，指定下标处键值对的值将被替换为newValue。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-setValueAt(index: int, newValue: V): boolean--><!--Device-LightWeightMap-setValueAt(index: int, newValue: V): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 指定下标。需要小于等于INT32_MAX即2147483647。 |
| newValue | V | 是 | 替换键值对中的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 成功替换返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The setValueAt method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

**示例**

ArkTS-Dyn示例：

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
lightWeightMap.setValueAt(1, 3546);
console.info("result:", lightWeightMap.get("squirrel"));  // result: 3546
```

ArkTS-Sta示例：

```TypeScript
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
lightWeightMap.setValueAt(1, 3546);
console.info("result:", lightWeightMap.get("squirrel"));  // result: 3546
```

## toString

```TypeScript
toString(): String
```

将此映射中包含的键值对拼接成字符串并返回。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-toString(): String--><!--Device-LightWeightMap-toString(): String-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| String | 返回将此映射中键值对拼接而成的字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The toString method cannot be bound. |

**示例**

ArkTS-Dyn示例：

```TypeScript
let lightWeightMap = new LightWeightMap<string, number>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.toString();
console.info("result:", result);  // result: sparrow:356,squirrel:123
```

ArkTS-Sta示例：

```TypeScript
let lightWeightMap: LightWeightMap<string, int> = new LightWeightMap<string, int>();
lightWeightMap.set("squirrel", 123);
lightWeightMap.set("sparrow", 356);
let result = lightWeightMap.toString();
console.info("result:", result);  // result: sparrow:356,squirrel:123
```

## values

```TypeScript
values(): IterableIterator<V>
```

返回包含此映射中所有值的新迭代器对象。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-values(): IterableIterator<V>--><!--Device-LightWeightMap-values(): IterableIterator<V>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;V&gt; | 返回一个迭代器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The values method cannot be bound. |

**示例**

ArkTS-Dyn示例：

```TypeScript
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

```TypeScript
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

## length

```TypeScript
length: number
```

LightWeightMap的元素个数。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightMap-length: number--><!--Device-LightWeightMap-length: number-End-->

**系统能力：** SystemCapability.Utils.Lang

