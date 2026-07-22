# LightWeightSet

LightWeightSet可用于存储一系列值的集合，存储元素中value值唯一。

**起始版本：** 8

<!--Device-unnamed-declare class LightWeightSet<T>--><!--Device-unnamed-declare class LightWeightSet<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { LightWeightSet } from '@kit.ArkTS';
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<T>
```

返回一个迭代器，迭代器的每一项都是一个JavaScript对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-[Symbol.iterator](): IterableIterator<T>--><!--Device-LightWeightSet-[Symbol.iterator](): IterableIterator<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;T&gt; | @throws { BusinessError } 10200011 - The Symbol.iterator method cannot be bound. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The Symbol.iterator method cannot be bound. |

**示例：**

```TypeScript
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");

// 使用方法一：
for (let value of lightWeightSet) {
  console.info("value:", value);
}
// value: sparrow
// value: squirrel

// 使用方法二：
let symbolIterator = lightWeightSet[Symbol.iterator]();
let iteratorResult: IteratorResult<string> = symbolIterator.next();
while (!iteratorResult.done) {
  console.info("value:", iteratorResult.value);
  iteratorResult = symbolIterator.next();
}
// value: sparrow
// value: squirrel

```

```TypeScript
// 不建议在Symbol.iterator中使用add、remove、removeAt方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。
let lightWeightSet = new LightWeightSet<string>();
for (let i = 0; i < 10; i++) {
  lightWeightSet.add(i + "123");
}
for (let i = 0; i < 10; i++) {
  lightWeightSet.remove(i + "123");
}

```

## add

```TypeScript
add(obj: T): boolean
```

向容器中添加数据。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-add(obj: T): boolean--><!--Device-LightWeightSet-add(obj: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | T | 是 | 添加的成员数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 成功添加元素返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The add method cannot be bound. |

**示例：**

```TypeScript
// 向容器中添加元素
let lightWeightSet = new LightWeightSet<string>();
let result = lightWeightSet.add("squirrel");
console.info("result:", result);  // result: true

```

## addAll

```TypeScript
addAll(set: LightWeightSet<T>): boolean
```

将另一个容器的所有元素组添加到当前容器。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-addAll(set: LightWeightSet<T>): boolean--><!--Device-LightWeightSet-addAll(set: LightWeightSet<T>): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| set | [LightWeightSet](arkts-arkts-util-lightweightset-lightweightset-c.md)&lt;T&gt; | 是 | 提供添加元素的LightWeightSet。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 成功添加元素返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The addAll method cannot be bound. |

**示例：**

```TypeScript
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
let set = new LightWeightSet<string>();
set.add("gull");
// 将另一个容器的所有元素添加到当前容器
lightWeightSet.addAll(set);
let result = lightWeightSet.has("gull");
console.info("result:", result);  // result: true

```

## clear

```TypeScript
clear(): void
```

清除容器中的所有元素，并将length置为0。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-clear(): void--><!--Device-LightWeightSet-clear(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The clear method cannot be bound. |

**示例：**

```TypeScript
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
// 清除容器中的所有元素
lightWeightSet.clear();
let result = lightWeightSet.isEmpty();
console.info("result:", result);  // result: true

```

## constructor

```TypeScript
constructor()
```

LightWeightSet的构造函数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-constructor()--><!--Device-LightWeightSet-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The LightWeightSet's constructor cannot be directly invoked. |

**示例：**

```TypeScript
// 创建LightWeightSet实例
let lightWeightSet = new LightWeightSet<number | string>();

```

## entries

```TypeScript
entries(): IterableIterator<[T, T]>
```

返回包含此映射中包含的键值对的新迭代器对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-entries(): IterableIterator<[T, T]>--><!--Device-LightWeightSet-entries(): IterableIterator<[T, T]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[T, T]&gt; | 返回一个迭代器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The entries method cannot be bound. |

**示例：**

```TypeScript
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
let entryIterator = lightWeightSet.entries();
for (let item of entryIterator) {
  console.info("value:", item[1])
}
// value: sparrow
// value: squirrel

```

```TypeScript
// 不建议在entries中使用add、remove、removeAt方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。
let lightWeightSet = new LightWeightSet<string>();
for(let i = 0; i < 10; i++) {
  lightWeightSet.add(i + "123");
}
for(let i = 0; i < 10; i++) {
  lightWeightSet.remove(i + "123");
}

```

## equal

```TypeScript
equal(obj: Object): boolean
```

判断此容器与obj的构成元素是否相同。
> **说明**  
>  
> 此接口从API version 8开始支持，从API version 12开始废弃。无替代接口。

**起始版本：** 8

**废弃版本：** 12

<!--Device-LightWeightSet-equal(obj: Object): boolean--><!--Device-LightWeightSet-equal(obj: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | Object | 是 | 比较对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当obj为仅含string或number的LightWeightSet或数组，且对象内部元素构成相同时，返回true；其他情况返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The equal method cannot be bound. |

**示例：**

```TypeScript
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
let comparisonArray = ["sparrow", "squirrel"];
// 判断此容器与obj的构成元素是否相同
let result = lightWeightSet.equal(comparisonArray);
console.info("result:", result);  // result: true

```

## forEach

```TypeScript
forEach(callbackFn: (value?: T, key?: T, set?: LightWeightSet<T>) => void, thisArg?: Object): void
```

通过回调函数来遍历LightWeightSet实例对象上的元素以及元素对应的下标。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-forEach(callbackFn: (value?: T, key?: T, set?: LightWeightSet<T>) => void, thisArg?: Object): void--><!--Device-LightWeightSet-forEach(callbackFn: (value?: T, key?: T, set?: LightWeightSet<T>) => void, thisArg?: Object): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value?: T, key?: T, set?: LightWeightSet&lt;T&gt;) =&gt; void | 是 | 回调函数。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值，默认值为当前实例对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The forEach method cannot be bound. |

**示例：**

```TypeScript
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("sparrow");
lightWeightSet.add("gull");
// 通过回调函数遍历LightWeightSet中的元素
lightWeightSet.forEach((value: string, key: string) => {
  console.info("value:" + value, "key:" + key);
});
// value:gull key:gull
// value:sparrow key:sparrow

```

```TypeScript
// 不建议在forEach函数中使用add、remove、removeAt方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。
let lightWeightSet = new LightWeightSet<string>();
for (let i = 0; i < 10; i++) {
  lightWeightSet.add(i + "123");
}
for (let i = 0; i < 10; i++) {
  lightWeightSet.remove(i + "123");
}

```

## getIndexOf

```TypeScript
getIndexOf(key: T): number
```

获取指定key所对应的下标。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-getIndexOf(key: T): int--><!--Device-LightWeightSet-getIndexOf(key: T): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | T | 是 | 查找的指定key。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 在lightWeightSet中指定数据的下标。若lightWeightSet中没有要查找的元素，则返回一个负值。表示目标哈希值应该插入的位置，插入位置是从1开始计数的，负号表示这是一个插入位置而不是索引。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getIndexOf method cannot be bound. |

**示例：**

```TypeScript
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
// 获取指定元素的下标
let result = lightWeightSet.getIndexOf("sparrow");
console.info("result:", result);  // result: 0

```

## getValueAt

```TypeScript
getValueAt(index: number): T
```

获取容器中指定下标对应的元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-getValueAt(index: number): T--><!--Device-LightWeightSet-getValueAt(index: number): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 指定下标。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回指定下标对应的元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getValueAt method cannot be bound. |

**示例：**

```TypeScript
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
// 获取指定下标对应的元素
let result = lightWeightSet.getValueAt(1);
console.info("result:", result);  // result: squirrel

```

## has

```TypeScript
has(key: T): boolean
```

判断容器中是否包含指定的key。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-has(key: T): boolean--><!--Device-LightWeightSet-has(key: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | T | 是 | 指定key。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 包含指定key时返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The has method cannot be bound. |

**示例：**

```TypeScript
let lightWeightSet = new LightWeightSet<number>();
lightWeightSet.add(123);
// 判断容器中是否包含指定元素
let result = lightWeightSet.has(123);
console.info("result:", result);  // result: true

```

## hasAll

```TypeScript
hasAll(set: LightWeightSet<T>): boolean
```

判断容器中是否包含指定set中的所有元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-hasAll(set: LightWeightSet<T>): boolean--><!--Device-LightWeightSet-hasAll(set: LightWeightSet<T>): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| set | [LightWeightSet](arkts-arkts-util-lightweightset-lightweightset-c.md)&lt;T&gt; | 是 | 比较对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 包含所有元素时返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The hasAll method cannot be bound. |

**示例：**

```TypeScript
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
let set = new LightWeightSet<string>();
set.add("sparrow");
// 判断容器中是否包含指定set中的所有元素
let result = lightWeightSet.hasAll(set);
console.info("result:", result);  // result: true

```

## increaseCapacityTo

```TypeScript
increaseCapacityTo(minimumCapacity: number): void
```

将当前LightWeightSet扩容至指定容量。如果传入的容量值大于或等于当前LightWeightSet中的元素个数，将容量变更为新容量，小于则不会变更。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-increaseCapacityTo(minimumCapacity: int): void--><!--Device-LightWeightSet-increaseCapacityTo(minimumCapacity: int): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| minimumCapacity | number | 是 | 需要容纳的元素数量。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The increaseCapacityTo method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of minimumCapacity is out of range. |

**示例：**

```TypeScript
let lightWeightSet = new LightWeightSet<string>();
// 将容器扩容至指定容量
lightWeightSet.increaseCapacityTo(10);

```

## isEmpty

```TypeScript
isEmpty(): boolean
```

判断容器是否为空。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-isEmpty(): boolean--><!--Device-LightWeightSet-isEmpty(): boolean-End-->

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
// 判断容器是否为空
const lightWeightSet = new LightWeightSet<number>();
let result = lightWeightSet.isEmpty();
console.info("result:", result);  // result: true

```

## remove

```TypeScript
remove(key: T): T
```

删除并返回指定key对应的元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-remove(key: T): T--><!--Device-LightWeightSet-remove(key: T): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | T | 是 | 指定key。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回删除元素的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The remove method cannot be bound. |

**示例：**

```TypeScript
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
// 删除并返回指定元素
let result = lightWeightSet.remove("sparrow");
console.info("result:", result);  // result: sparrow

```

## removeAt

```TypeScript
removeAt(index: number): boolean
```

删除指定下标所对应的元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-removeAt(index: int): boolean--><!--Device-LightWeightSet-removeAt(index: int): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 指定下标。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 确认是否成功删除元素，成功删除元素返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The removeAt method cannot be bound. |

**示例：**

```TypeScript
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
// 删除指定下标的元素
let result = lightWeightSet.removeAt(1);
console.info("result:", result);  // result: true

```

## toArray

```TypeScript
toArray(): Array<T>
```

获取包含此容器中所有对象的数组。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-toArray(): Array<T>--><!--Device-LightWeightSet-toArray(): Array<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 返回对应数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The toArray method cannot be bound. |

**示例：**

```TypeScript
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
// 获取包含此容器中所有对象的数组
let result = lightWeightSet.toArray();
console.info(result.toString());
// sparrow,squirrel

```

## toString

```TypeScript
toString(): String
```

获取包含容器中所有键和值的字符串。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-toString(): String--><!--Device-LightWeightSet-toString(): String-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| String | 返回对应字符串。 |

**示例：**

```TypeScript
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
// 获取包含容器中所有元素的字符串
let result = lightWeightSet.toString();
console.info("result:", result);  // result: sparrow,squirrel

```

## values

```TypeScript
values(): IterableIterator<T>
```

返回包含此映射中所有键值的新迭代器对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-values(): IterableIterator<T>--><!--Device-LightWeightSet-values(): IterableIterator<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;T&gt; | 返回一个迭代器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The values method cannot be bound. |

**示例：**

```TypeScript
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
// 获取包含所有元素的迭代器
let values = lightWeightSet.values();
for (let value of values) {
  console.info("value:", value);
}
// value: sparrow
// value: squirrel

```

## length

```TypeScript
length: number
```

LightWeightSet的元素个数。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-length: number--><!--Device-LightWeightSet-length: number-End-->

**系统能力：** SystemCapability.Utils.Lang

