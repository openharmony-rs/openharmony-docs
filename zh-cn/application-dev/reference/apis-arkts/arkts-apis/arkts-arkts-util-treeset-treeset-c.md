# TreeSet

TreeSet基于[TreeMap](arkts-arkts-util-treemap-treemap-c.md)实现，在TreeSet中，仅处理元素的值（value），不单独处理键（key）。 TreeSet的每个元素在底层TreeMap中同时作为key和value存储，因此元素中value唯一且有序。

**起始版本：** 23

<!--Device-unnamed-declare class TreeSet--><!--Device-unnamed-declare class TreeSet-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { TreeSet } from '@kit.ArkTS';
import { TreeSetForEachCb } from '@kit.ArkTS';
import { TreeSetComparator } from '@kit.ArkTS';
```

## $_iterator

```TypeScript
$_iterator(): IterableIterator<T>
```

返回一个迭代器，每一项都是一个JavaScript对象。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-$_iterator(): IterableIterator<T>--><!--Device-TreeSet-$_iterator(): IterableIterator<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;T&gt; | TreeSet的迭代器。 |

**示例**

```TypeScript
let treeSet : TreeSet<string> = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
// 使用方法一：
for (let item of treeSet) {
  console.info("value:" + item);
}
// 使用方法二：
let iter = treeSet.$_iterator();
let temp = iter.next().value;
while(temp != undefined) {
  console.info("value:" + temp);
  temp = iter.next().value;
}
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<T>
```

返回一个迭代器，迭代器的每一项为容器中的元素值。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-[Symbol.iterator](): IterableIterator<T>--><!--Device-TreeSet-[Symbol.iterator](): IterableIterator<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;T&gt; | 返回包含TreeSet中所有元素的迭代器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The Symbol.iterator method cannot be bound. |

**示例**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
// 使用方法一：使用for...of语法遍历TreeSet
for (let item of treeSet) {
  console.info('value:' + item);
}
// value:sparrow
// value:squirrel

// 使用方法二：通过Symbol.iterator获取迭代器手动遍历
let iterator = treeSet[Symbol.iterator]();
let currentValue: IteratorResult<string> = iterator.next().value;
while (currentValue != undefined) {
  console.info('value:' + currentValue);
  currentValue = iterator.next().value;
}
// value:sparrow
// value:squirrel
```

```TypeScript
// 不建议在Symbol.iterator中使用add、remove方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。
let treeSet = new TreeSet<string>();
for (let i = 0; i < 10; i++) {
  treeSet.add('sparrow' + i);
}
for (let i = 0; i < 10; i++) {
  treeSet.remove('sparrow' + i);
}
```

## add

```TypeScript
add(value: T): boolean
```

向容器中添加指定元素。不建议插入null值，可能会影响排序结果；添加自定义类型元素时，需确保TreeSet在构造时已提供比较函数。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-add(value: T): boolean--><!--Device-TreeSet-add(value: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 向TreeSet中添加的值元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 成功添加新元素至容器返回true，当元素已存在时返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The add method cannot be bound. |

**示例**

```TypeScript
let treeSet = new TreeSet<string>();
let result = treeSet.add('squirrel');
console.info('result:', result); // result: true
```

## clear

```TypeScript
clear(): void
```

清除容器中的所有元素，并将length置为0。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-clear(): void--><!--Device-TreeSet-clear(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The clear method cannot be bound. |

**示例**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
treeSet.clear();
let result = treeSet.isEmpty();
console.info('result:', result); // result: true
```

## constructor

```TypeScript
constructor(comparator?: (firstValue: T, secondValue: T) => boolean)
```

TreeSet的构造函数，支持通过比较函数对元素进行升序或降序排序。当插入自定义类型时，必须提供比较函数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-constructor(comparator?: (firstValue: T, secondValue: T) => boolean)--><!--Device-TreeSet-constructor(comparator?: (firstValue: T, secondValue: T) => boolean)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| comparator | (firstValue: T, secondValue: T) =&gt; boolean | 否 | 用户自定义的比较函数，可通过比较关系对元素排序。默认值为null，表示不提供比较函数。 取值原则：比较函数返回值决定排序方向，返回firstValue &lt; secondValue为升序排序，返回firstValue &gt; secondValue为降序排序。 firstValue（必填）比较函数中的第一个比较元素，与secondValue比较后决定排序方向。 secondValue（必填）比较函数中的第二个比较元素，与firstValue比较后决定排序方向。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The TreeSet's constructor cannot be directly invoked. |

**示例**

```TypeScript
// 默认构造
let treeSet = new TreeSet<string | number | boolean | Object>();
```

```TypeScript
// 使用comparator firstValue < secondValue，表示期望结果为升序排序。反之firstValue > secondValue，表示为降序排序。
let treeSet: TreeSet<string> = new TreeSet<string>((firstValue: string, secondValue: string): boolean => {
  return firstValue < secondValue;
});
treeSet.add('a');
treeSet.add('c');
treeSet.add('d');
treeSet.add('b');
for (let value of treeSet) {
  console.info('value:', value);
};
// value: a
// value: b
// value: c
// value: d
```

```TypeScript
// 插入自定义类型时，必须提供比较函数。
class TestEntry {
  public id: number = 0;
}
let testEntrySet: TreeSet<TestEntry> = new TreeSet<TestEntry>((t1: TestEntry, t2: TestEntry): boolean => { return t1.id > t2.id; });
let firstEntry: TestEntry = {
  id: 0
};
let secondEntry: TestEntry = {
  id: 1
}
testEntrySet.add(firstEntry);
testEntrySet.add(secondEntry);
console.info('treeSet: ', testEntrySet.length);
```

## constructor

```TypeScript
constructor(comparator?: TreeSetComparator<T>)
```

TreeSet的构造函数，支持通过比较函数对元素进行升序或降序排序。当插入自定义类型时，必须提供比较函数。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-constructor(comparator?: TreeSetComparator<T>)--><!--Device-TreeSet-constructor(comparator?: TreeSetComparator<T>)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| comparator | [TreeSetComparator](arkts-arkts-treesetcomparator-t.md)&lt;T&gt; | 否 | 比较函数。 comparator（可选）用户自定义的比较函数。 |

**示例**

```TypeScript
// 默认构造
let treeSet : TreeSet<string | int | boolean | Object> = new TreeSet<string | int | boolean | Object>();
```

```TypeScript
import { TreeSetComparator } from '@kit.ArkTS';

// 使用comparator firstValue < secondValue，表示期望结果为升序排序。反之firstValue > secondValue，表示为降序排序。
let treeSetCb: TreeSetComparator<string> = (firstValue: string, secondValue: string): double => {
  return secondValue.compareTo(firstValue);
};
let treeSet: TreeSet<string> = new TreeSet<string>(treeSetCb);
treeSet.add("a");
treeSet.add("c");
treeSet.add("d");
treeSet.add("b");
let numbers = Array.from(treeSet.values());
for (let item of numbers) {
  console.info("TreeSet: " + item);
}
```

```TypeScript
// 当插入自定义类型时，则必须要提供比较函数。
class TestEntry{
  public id: int = 0;
}
let treeSetCb: TreeSetComparator<TestEntry> = (firstValue: TestEntry, secondValue: TestEntry): double => {
  return secondValue.compareTo(firstValue);
};
let ts1: TreeSet<TestEntry> = new TreeSet<TestEntry>(treeSetCb);
let entry1: TestEntry = {
  id: 0
};
let entry2: TestEntry = {
  id: 1
}
ts1.add(entry1);
ts1.add(entry2);
console.info("treeSet: ", ts1.length);
```

## entries

```TypeScript
entries(): IterableIterator<[T, T]>
```

返回包含此容器中元素的新迭代器对象，每个元素以[value, value]的形式返回。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-entries(): IterableIterator<[T, T]>--><!--Device-TreeSet-entries(): IterableIterator<[T, T]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[T, T]&gt; | 返回包含TreeSet中所有元素键值对的迭代器对象，每个键值对中键与值相同，均为元素本身。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The entries method cannot be bound. |

**示例**

ArkTS-Dyn示例：

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
// 获取entries迭代器
let iterator = treeSet.entries();
// 遍历迭代器获取键值对
let iterResult: IteratorResult<Object[]> = iterator.next();
while (!iterResult.done) {
  console.info('TreeSet: ' + iterResult.value[1]);
  iterResult = iterator.next();
}
// TreeSet: sparrow
// TreeSet: squirrel
```

```TypeScript
// 不建议在entries中使用add、remove方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。
let treeSet = new TreeSet<string>();
for(let i = 0; i < 10; i++) {
  treeSet.add('sparrow' + i);
}
for(let i = 0; i < 10; i++) {
  treeSet.remove('sparrow' + i);
}
```

ArkTS-Sta示例：

```TypeScript
let treeSet : TreeSet<string> = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
let it = treeSet.entries();
let t: IteratorResult<[string, string]> = it.next();
while(!t.done) {
  console.info("TreeSet: " + t.value);
  t = it.next()
}
```

```TypeScript
// 不建议在entries中使用set、remove方法，因其可能导致迭代过程中的状态异常，建议使用for循环来进行安全的插入与删除操作。
let treeSet : TreeSet<string> = new TreeSet<string>();
for(let i = 0; i < 10; i++) {
  treeSet.add("sparrow" + i);
}
for(let i = 0; i < 10; i++) {
  treeSet.remove("sparrow" + i);
}
```

## forEach

```TypeScript
forEach(callbackFn: (value?: T, key?: T, set?: TreeSet<T>) => void, thisArg?: Object): void
```

通过回调函数来遍历实例对象上的元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-forEach(callbackFn: (value?: T, key?: T, set?: TreeSet<T>) => void, thisArg?: Object): void--><!--Device-TreeSet-forEach(callbackFn: (value?: T, key?: T, set?: TreeSet<T>) => void, thisArg?: Object): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value?: T, key?: T, set?: TreeSet&lt;T&gt;) =&gt; void | 是 | 遍历实例对象中每个元素时调用的回调函数，开发者可在回调中对元素及其下标进行自定义处理。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值。当需要在回调函数中使用特定的this上下文（如访问外部对象属性）时传入此参数。不传入时默认值为当前实例对象， 回调函数中的this指向TreeSet实例本身。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The forEach method cannot be bound. |

**示例**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add('sparrow');
treeSet.add('gull');
// 通过forEach遍历TreeSet中的元素
treeSet.forEach((value: string, key: string): void => {
  console.info('value:' + value);
});
// value:gull
// value:sparrow
```

```TypeScript
// 不建议在forEach中使用add、remove方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。
let treeSet = new TreeSet<string>();
for (let i = 0; i < 10; i++) {
  treeSet.add('sparrow' + i);
}
for (let i = 0; i < 10; i++) {
  treeSet.remove('sparrow' + i);
}
```

## forEach

```TypeScript
forEach(callbackFn: TreeSetForEachCb<T>): void
```

通过回调函数来遍历实例对象上的元素。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-forEach(callbackFn: TreeSetForEachCb<T>): void--><!--Device-TreeSet-forEach(callbackFn: TreeSetForEachCb<T>): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | [TreeSetForEachCb](arkts-arkts-treesetforeachcb-t.md)&lt;T&gt; | 是 | 遍历实例对象中每个元素时调用的回调函数，开发者可在回调中对元素及其下标进行自定义处理。 |

**示例**

```TypeScript
import { TreeSetForEachCb } from '@kit.ArkTS';

let treeSet: TreeSet<string> = new TreeSet<string>();
treeSet.add("sparrow");
treeSet.add("gull");
let treeSetCb: TreeSetForEachCb<string> = (value: string, key: string, set: TreeSet<string>) => {
  console.info("value: " + value, " key: "+ key);
};
treeSet.forEach(treeSetCb);
```

## getFirstValue

```TypeScript
getFirstValue(): T
```

获取容器中排序第一的元素，为空时返回undefined。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-getFirstValue(): T--><!--Device-TreeSet-getFirstValue(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回排序第一的数据，为空时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getFirstValue method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty.<br>**适用版本：** 23+ |

**示例**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
let result = treeSet.getFirstValue();
console.info('result:', result); // result: sparrow
```

## getHigherValue

```TypeScript
getHigherValue(key: T): T
```

获取容器中比传入元素排序靠后一位的元素，为空时返回undefined。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-getHigherValue(key: T): T--><!--Device-TreeSet-getHigherValue(key: T): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | T | 是 | 作为查找基准的元素，用于定位排序中比该元素靠后一位的数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回排序中传入元素后一位的数据。为空时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getHigherValue method cannot be bound. |

**示例**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
treeSet.add('gander');
let result = treeSet.getHigherValue('sparrow');
console.info('result:', result); // result: squirrel
```

## getHigherValue

```TypeScript
getHigherValue(key: T): T | undefined
```

获取容器中比传入元素排序靠后一位的元素，如果key不存在，则返回undefined。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-getHigherValue(key: T): T | undefined--><!--Device-TreeSet-getHigherValue(key: T): T | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | T | 是 | 对比的元素值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 如果存在则返回指定key元素的后一位值，否则返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty. |

**示例**

```TypeScript
let treeSet : TreeSet<string> = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
treeSet.add("gander");
let result = treeSet.getHigherValue("sparrow");
```

## getLastValue

```TypeScript
getLastValue(): T
```

获取容器中排序最后的数据，为空时返回undefined。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-getLastValue(): T--><!--Device-TreeSet-getLastValue(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回排序最后的数据，为空时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getLastValue method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty.<br>**适用版本：** 23+ |

**示例**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
let result = treeSet.getLastValue();
console.info('result:', result); // result: squirrel
```

## getLowerValue

```TypeScript
getLowerValue(key: T): T
```

获取容器中比传入元素排序靠前一位的元素，为空时返回undefined。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-getLowerValue(key: T): T--><!--Device-TreeSet-getLowerValue(key: T): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | T | 是 | 作为查找基准的元素值，用于定位排序中比该元素靠前一位的数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回排序中传入元素前一位的数据，为空时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getLowerValue method cannot be bound. |

**示例**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
treeSet.add('gander');
let result = treeSet.getLowerValue('sparrow');
console.info('result:', result); // result: gander
```

## getLowerValue

```TypeScript
getLowerValue(key: T): T | undefined
```

获取容器中比传入元素排序靠前一位的元素，如果key不存在，则返回undefined。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-getLowerValue(key: T): T | undefined--><!--Device-TreeSet-getLowerValue(key: T): T | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | T | 是 | 对比的元素值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 如果存在则返回指定key元素的前一位值，否则返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty. |

**示例**

```TypeScript
let treeSet : TreeSet<string> = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
treeSet.add("gander");
let result = treeSet.getLowerValue("sparrow");
```

## has

```TypeScript
has(value: T): boolean
```

判断容器中是否包含指定元素。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-has(value: T): boolean--><!--Device-TreeSet-has(value: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 要判断是否存在于容器中的目标元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 包含指定元素返回true，不包含指定元素返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The has method cannot be bound. |

**示例**

ArkTS-Dyn示例：

```TypeScript
let treeSet = new TreeSet<number>();
treeSet.add(123);
// 判断容器中是否包含指定元素
let result = treeSet.has(123);
console.info('result:', result); // result: true
```

ArkTS-Sta示例：

```TypeScript
let treeSet : TreeSet<int> = new TreeSet<int>();
treeSet.add(123);
let result = treeSet.has(123);
console.info("result = " + result); // result = true
```

## isEmpty

```TypeScript
isEmpty(): boolean
```

判断容器是否为空。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-isEmpty(): boolean--><!--Device-TreeSet-isEmpty(): boolean-End-->

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
const treeSet : TreeSet<string | number | boolean | Object>  = new TreeSet<string | number | boolean | Object>();
let result = treeSet.isEmpty();
console.info("result:", result);  // result: true
```

ArkTS-Sta示例：

```TypeScript
let treeSet = new TreeSet<string>();
// 判断容器是否为空
let result = treeSet.isEmpty();
console.info('result:', result);  // result: true
```

## popFirst

```TypeScript
popFirst(): T
```

删除容器中排序最前的数据，为空时返回undefined。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-popFirst(): T--><!--Device-TreeSet-popFirst(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回删除的数据，为空时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The popFirst method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty.<br>**适用版本：** 23+ |

**示例**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
let result = treeSet.popFirst();
console.info('result:', result); // result: sparrow
```

## popLast

```TypeScript
popLast(): T
```

删除容器中排序最后的数据，为空时返回undefined。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-popLast(): T--><!--Device-TreeSet-popLast(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回删除的数据，为空时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The popLast method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty.<br>**适用版本：** 23+ |

**示例**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
let result = treeSet.popLast();
console.info('result:', result); // result: squirrel
```

## remove

```TypeScript
remove(value: T): boolean
```

删除指定的元素。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-remove(value: T): boolean--><!--Device-TreeSet-remove(value: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 要从容器中删除的目标元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 成功删除元素返回true，指定元素不存在返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The remove method cannot be bound. |

**示例**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
let result = treeSet.remove('sparrow');
console.info('result:', result); // result: true
```

## values

```TypeScript
values(): IterableIterator<T>
```

返回包含此容器中元素值的新迭代器对象。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-values(): IterableIterator<T>--><!--Device-TreeSet-values(): IterableIterator<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;T&gt; | 返回包含TreeSet中所有元素的迭代器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The values method cannot be bound. |

**示例**

```TypeScript
// 不建议在values中使用add、remove方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
let values = treeSet.values();
for (let value of values) {
  console.info('value:', value);
}
// value: sparrow
// value: squirrel
```

## length

```TypeScript
length: number
```

TreeSet的元素个数。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-length: number--><!--Device-TreeSet-length: number-End-->

**系统能力：** SystemCapability.Utils.Lang

