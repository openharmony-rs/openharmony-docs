# LightWeightSet

LightWeightSet可用于存储一系列值，存储元素中value唯一。

**起始版本：** 23

<!--Device-unnamed-declare class LightWeightSet--><!--Device-unnamed-declare class LightWeightSet-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { LightWeightSet } from '@kit.ArkTS';
import { LightWeightSetForEachCb } from '@kit.ArkTS';
```

## $_iterator

```TypeScript
$_iterator(): IterableIterator<T>
```

返回一个迭代器，迭代器的每一项都是一个JavaScript对象。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-$_iterator(): IterableIterator<T>--><!--Device-LightWeightSet-$_iterator(): IterableIterator<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;T&gt; | 返回遍历LightWeightSet中所有元素的迭代器对象，每一项为容器中的元素值。 |

**示例**

```TypeScript
let lightWeightSet: LightWeightSet<string> = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
for (let item of lightWeightSet) {
  console.info("value:" + item);
}
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<T>
```

返回一个迭代器，迭代器的每一项都是一个JavaScript对象。 不建议在Symbol.iterator中使用add、remove、removeAt方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-[Symbol.iterator](): IterableIterator<T>--><!--Device-LightWeightSet-[Symbol.iterator](): IterableIterator<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;T&gt; | 返回遍历LightWeightSet中所有元素的迭代器对象，每一项为容器中的元素值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The Symbol.iterator method cannot be bound. |

**示例**

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

向容器中添加数据。若添加的元素已存在于容器中，则不会重复添加，返回false。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-add(obj: T): boolean--><!--Device-LightWeightSet-add(obj: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | T | 是 | 添加的成员数据。若添加的值已存在于容器中，则不会重复添加。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 成功添加元素返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The add method cannot be bound. |

**示例**

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

将另一个容器的所有元素添加到当前容器。若源容器中的元素已存在于当前容器中，则跳过该元素不重复添加。

**起始版本：** 23

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
| boolean | 成功添加元素返回true，要添加的元素已存在时返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The addAll method cannot be bound. |

**示例**

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

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-clear(): void--><!--Device-LightWeightSet-clear(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The clear method cannot be bound. |

**示例**

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

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-constructor()--><!--Device-LightWeightSet-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The LightWeightSet's constructor cannot be directly invoked. |

**示例**

```TypeScript
// 创建LightWeightSet实例
let lightWeightSet = new LightWeightSet<number | string>();
```

## entries

```TypeScript
entries(): IterableIterator<[T, T]>
```

返回包含此容器中所有元素对的新迭代器对象，每个元素对由相同值组成[value, value]。 不建议在entries中使用add、remove、removeAt方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-entries(): IterableIterator<[T, T]>--><!--Device-LightWeightSet-entries(): IterableIterator<[T, T]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[T, T]&gt; | 返回包含LightWeightSet中所有键值对的迭代器对象，每一项为[key, value]结构的数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The entries method cannot be bound. |

**示例**

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

判断此容器与obj的构成元素是否相同。 > **说明：** > > 此接口从API version 8开始支持，从API version 12开始废弃。无替代接口。

**起始版本：** 8

**废弃版本：** 12

<!--Device-LightWeightSet-equal(obj: Object): boolean--><!--Device-LightWeightSet-equal(obj: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | Object | 是 | 与当前容器比较元素构成是否相同的对象，可为仅含string或number的LightWeightSet或数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当obj为仅含string或number的LightWeightSet或数组，且对象内部元素构成相同时，返回true；其他情况返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The equal method cannot be bound. |

**示例**

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

通过回调函数来遍历LightWeightSet实例对象上的元素。 不建议在forEach函数中使用add、remove、removeAt方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-forEach(callbackFn: (value?: T, key?: T, set?: LightWeightSet<T>) => void, thisArg?: Object): void--><!--Device-LightWeightSet-forEach(callbackFn: (value?: T, key?: T, set?: LightWeightSet<T>) => void, thisArg?: Object): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value?: T, key?: T, set?: LightWeightSet&lt;T&gt;) =&gt; void | 是 | 回调函数，用于遍历LightWeightSet实例对象上的元素及其下标。 callbackFn（必填）接受最多三个参数的函数。 value 当前遍历到的元素的值，默认值为首个元素的值。 key 当前遍历到的元素（与value相同），默认值为首个元素。 set 当前调用forEach方法的实例对象，默认值为当前实例对象。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值。当需要改变回调函数中的this指向时传入此参数，不需要改变this指向时可省略。不传入时默认值为当前实例对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The forEach method cannot be bound. |

**示例**

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

## forEach

```TypeScript
forEach(callbackFn: LightWeightSetForEachCb<T>): void
```

通过回调函数遍历实例对象中实际的key。 不会对已删除的key执行回调。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-forEach(callbackFn: LightWeightSetForEachCb<T>): void--><!--Device-LightWeightSet-forEach(callbackFn: LightWeightSetForEachCb<T>): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | [LightWeightSetForEachCb](arkts-arkts-lightweightsetforeachcb-t.md)&lt;T&gt; | 是 | 对每个元素执行的回调函数。 |

**示例**

```TypeScript
import { LightWeightSetForEachCb } from '@kit.ArkTS';

let lightWeightSet: LightWeightSet<string> = new LightWeightSet<string>();
lightWeightSet.add("sparrow");
lightWeightSet.add("gull");
let lightWeightSetCb: LightWeightSetForEachCb<string> = (value: string, key: string, set: LightWeightSet<string>) => {
  console.info("value: " + value, " key: " + key);
};
lightWeightSet.forEach(lightWeightSetCb);
```

## getIndexOf

```TypeScript
getIndexOf(key: T): int
```

获取指定元素所对应的下标。

**起始版本：** 23

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
| int | 在LightWeightSet中指定数据的下标。若LightWeightSet中没有要查找的元素，则返回一个负值。 表示目标哈希值应该插入的位置，插入位置是从1开始计数的，负号表示这是一个插入位置而不是索引。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getIndexOf method cannot be bound. |

**示例**

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
| index | number | 是 | 指定下标。需要小于等于INT32_MAX即2147483647。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回指定下标位置的元素值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getValueAt method cannot be bound. |

**示例**

```TypeScript
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
// 获取指定下标对应的元素
let result = lightWeightSet.getValueAt(1);
console.info("result:", result);  // result: squirrel
```

## getValueAt

```TypeScript
getValueAt(index: int): T | undefined
```

获取LightWeightSet容器中指定下标位置的对象。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-getValueAt(index: int): T | undefined--><!--Device-LightWeightSet-getValueAt(index: int): T | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 检索值的下标位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回指定下标对应的值，如果下标超出范围则返回undefined。 |

## has

```TypeScript
has(key: T): boolean
```

判断容器中是否包含指定元素。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-has(key: T): boolean--><!--Device-LightWeightSet-has(key: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | T | 是 | 指定查找的元素，用于判断容器中是否包含该元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示容器中包含指定元素，false表示容器中不包含指定元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The has method cannot be bound. |

**示例**

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

判断容器中是否包含指定set中的所有元素。当容器中存储的value为number类型且值大于INT32_MAX(2147483647)或小于INT32_MIN(-2147483648)时，判断结果可能与预期不一致，详见规格限制。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-hasAll(set: LightWeightSet<T>): boolean--><!--Device-LightWeightSet-hasAll(set: LightWeightSet<T>): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| set | [LightWeightSet](arkts-arkts-util-lightweightset-lightweightset-c.md)&lt;T&gt; | 是 | 用于判断当前容器是否包含其所有元素的目标集合。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示容器中包含目标集合中的所有元素，false表示容器中不包含目标集合中的全部元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The hasAll method cannot be bound. |

**示例**

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
increaseCapacityTo(minimumCapacity: int): void
```

将当前LightWeightSet扩容至指定容量。如果传入的容量值大于或等于当前LightWeightSet中的元素个数，将容量变更为新容量，小于则不会变更。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-increaseCapacityTo(minimumCapacity: int): void--><!--Device-LightWeightSet-increaseCapacityTo(minimumCapacity: int): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| minimumCapacity | int | 是 | 需要容纳的元素数量。若传入值小于当前元素个数，则不会变更容量。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The increaseCapacityTo method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of minimumCapacity is out of range. |

**示例**

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

**起始版本：** 23

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

**示例**

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

删除并返回指定元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-remove(key: T): T--><!--Device-LightWeightSet-remove(key: T): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | T | 是 | 指定要删除的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回删除的元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The remove method cannot be bound. |

**示例**

```TypeScript
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
// 删除并返回指定元素
let result = lightWeightSet.remove("sparrow");
console.info("result:", result);  // result: sparrow
```

## remove

```TypeScript
remove(key: T): T | undefined
```

删除LightWeightSet容器中指定Object类型的对象。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-remove(key: T): T | undefined--><!--Device-LightWeightSet-remove(key: T): T | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | T | 是 | 待删除元素的key。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 如果存在则返回被删除的值，否则返回undefined。 |

**示例**

```TypeScript
let lightWeightSet: LightWeightSet<string> = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
let result = lightWeightSet.remove("sparrow");
```

## removeAt

```TypeScript
removeAt(index: int): boolean
```

删除指定下标所对应的元素。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-removeAt(index: int): boolean--><!--Device-LightWeightSet-removeAt(index: int): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 指定下标，取值范围[0, length-1]，且需要小于等于INT32_MAX即2147483647。超出有效下标范围时返回false。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 成功删除元素返回true，指定下标不存在或超出范围时返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The removeAt method cannot be bound. |

**示例**

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

获取包含此容器中所有元素的数组。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-toArray(): Array<T>--><!--Device-LightWeightSet-toArray(): Array<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 返回包含此容器中所有元素的数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The toArray method cannot be bound. |

**示例**

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

获取包含容器中所有元素的字符串。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-toString(): String--><!--Device-LightWeightSet-toString(): String-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| String | 返回包含容器中所有元素的字符串。 |

**示例**

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

返回包含此集合中所有值的新迭代器对象。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LightWeightSet-values(): IterableIterator<T>--><!--Device-LightWeightSet-values(): IterableIterator<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;T&gt; | 返回包含LightWeightSet中所有value的迭代器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The values method cannot be bound. |

**示例**

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

