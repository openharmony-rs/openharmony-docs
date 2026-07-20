# TreeSet

TreeSet基于[TreeMap](arkts-util-treemap.md)实现。在TreeSet中，仅处理value对象。TreeSet可用于存储一系列值的集合，元素中value唯一且有序。

**起始版本：** 8

<!--Device-unnamed-declare class TreeSet<T>--><!--Device-unnamed-declare class TreeSet<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { TreeSet } from '@kit.ArkTS';
```

<a id="[symbol.iterator]"></a>
## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<T>
```

返回一个迭代器，迭代器的每一项都是一个JavaScript对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-[Symbol.iterator](): IterableIterator<T>--><!--Device-TreeSet-[Symbol.iterator](): IterableIterator<T>-End-->

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

<a id="add"></a>
## add

```TypeScript
add(value: T): boolean
```

向容器中添加一组数据。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-add(value: T): boolean--><!--Device-TreeSet-add(value: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 添加的成员数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 该元素是否已存在。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The add method cannot be bound. |

**示例：**

```TypeScript
let treeSet = new TreeSet<string>();
let result = treeSet.add('squirrel');
console.info('result:', result); // result: true

```

<a id="clear"></a>
## clear

```TypeScript
clear(): void
```

清除容器中的所有元素，并将length置为0。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-clear(): void--><!--Device-TreeSet-clear(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The clear method cannot be bound. |

**示例：**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
treeSet.clear();
let result = treeSet.isEmpty();
console.info('result:', result); // result: true

```

<a id="constructor"></a>
## constructor

```TypeScript
constructor(comparator?: (firstValue: T, secondValue: T) => boolean)
```

TreeSet的构造函数，支持通过比较函数对元素进行升序或降序排序。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-constructor(comparator?: (firstValue: T, secondValue: T) => boolean)--><!--Device-TreeSet-constructor(comparator?: (firstValue: T, secondValue: T) => boolean)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| comparator | (firstValue: T, secondValue: T) =&gt; boolean | 否 | 比较函数。comparator（可选）用户自定义的比较函数。firstValue（必填）前一项元素。secondValue（必填）后一项元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The TreeSet's constructor cannot be directly invoked. |

**示例：**

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

<a id="entries"></a>
## entries

```TypeScript
entries(): IterableIterator<[T, T]>
```

返回包含此映射中键值对的新迭代器对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-entries(): IterableIterator<[T, T]>--><!--Device-TreeSet-entries(): IterableIterator<[T, T]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[T, T]&gt; | @throws { BusinessError } 10200011 - The entries method cannot be bound. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The entries method cannot be bound. |

**示例：**

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

<a id="foreach"></a>
## forEach

```TypeScript
forEach(callbackFn: (value?: T, key?: T, set?: TreeSet<T>) => void, thisArg?: Object): void
```

通过回调函数来遍历实例对象上的元素及其下标。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-forEach(callbackFn: (value?: T, key?: T, set?: TreeSet<T>) => void, thisArg?: Object): void--><!--Device-TreeSet-forEach(callbackFn: (value?: T, key?: T, set?: TreeSet<T>) => void, thisArg?: Object): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value?: T, key?: T, set?: TreeSet&lt;T&gt;) =&gt; void | 是 | 回调函数。callbackFn（必填）接受最多三个参数的函数。对每个元素调用的函数。 |
| thisArg | Object | 否 | this值。thisArg（可选）当callbackFn被调用时作为this值使用的对象。如果省略thisArg，则使用undefined作为this值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The forEach method cannot be bound. |

**示例：**

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

<a id="getfirstvalue"></a>
## getFirstValue

```TypeScript
getFirstValue(): T
```

获取容器中排序第一的数据，为空时返回undefined。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-getFirstValue(): T--><!--Device-TreeSet-getFirstValue(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回值或undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getFirstValue method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty.<br>**适用版本：** 23+  **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。 |

**示例：**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
let result = treeSet.getFirstValue();
console.info('result:', result); // result: sparrow

```

<a id="gethighervalue"></a>
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
| key | T | 是 | 对比的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回排序中传入元素后一位的数据。为空时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getHigherValue method cannot be bound. |

**示例：**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
treeSet.add('gander');
let result = treeSet.getHigherValue('sparrow');
console.info('result:', result); // result: squirrel

```

<a id="getlastvalue"></a>
## getLastValue

```TypeScript
getLastValue(): T
```

获取容器中排序最后的数据，为空时返回undefined。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-getLastValue(): T--><!--Device-TreeSet-getLastValue(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回值或undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getLastValue method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty.<br>**适用版本：** 23+  **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。 |

**示例：**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
let result = treeSet.getLastValue();
console.info('result:', result); // result: squirrel

```

<a id="getlowervalue"></a>
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
| key | T | 是 | 对比的元素值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回排序中对比元素前一位的数据，为空时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getLowerValue method cannot be bound. |

**示例：**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
treeSet.add('gander');
let result = treeSet.getLowerValue('sparrow');
console.info('result:', result); // result: gander

```

<a id="has"></a>
## has

```TypeScript
has(value: T): boolean
```

判断容器中是否包含指定元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-has(value: T): boolean--><!--Device-TreeSet-has(value: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 指定的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | boolean类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The has method cannot be bound. |

**示例：**

```TypeScript
let treeSet = new TreeSet<number>();
treeSet.add(123);
// 判断容器中是否包含指定元素
let result = treeSet.has(123);
console.info('result:', result); // result: true

```

<a id="isempty"></a>
## isEmpty

```TypeScript
isEmpty(): boolean
```

判断容器是否为空。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-isEmpty(): boolean--><!--Device-TreeSet-isEmpty(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | boolean类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The isEmpty method cannot be bound. |

**示例：**

```TypeScript
let treeSet = new TreeSet<string>();
// 判断容器是否为空
let result = treeSet.isEmpty();
console.info('result:', result);  // result: true

```

<a id="popfirst"></a>
## popFirst

```TypeScript
popFirst(): T
```

删除容器中排序最前的数据，为空时返回undefined。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-popFirst(): T--><!--Device-TreeSet-popFirst(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 排序最前的数据，为空时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The popFirst method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty.<br>**适用版本：** 23+  **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。 |

**示例：**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
let result = treeSet.popFirst();
console.info('result:', result); // result: sparrow

```

<a id="poplast"></a>
## popLast

```TypeScript
popLast(): T
```

删除容器中排序最后的数据，为空时返回undefined。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-popLast(): T--><!--Device-TreeSet-popLast(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 排序最后的数据，为空时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The popLast method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty.<br>**适用版本：** 23+  **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。 |

**示例：**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
let result = treeSet.popLast();
console.info('result:', result); // result: squirrel

```

<a id="remove"></a>
## remove

```TypeScript
remove(value: T): boolean
```

删除指定的元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-remove(value: T): boolean--><!--Device-TreeSet-remove(value: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 指定的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | boolean类型（是否包含该元素）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The remove method cannot be bound. |

**示例：**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
let result = treeSet.remove('sparrow');
console.info('result:', result); // result: true

```

<a id="values"></a>
## values

```TypeScript
values(): IterableIterator<T>
```

返回包含此映射中键值的新迭代器对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TreeSet-values(): IterableIterator<T>--><!--Device-TreeSet-values(): IterableIterator<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;T&gt; | @throws { BusinessError } 10200011 - The values method cannot be bound. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The values method cannot be bound. |

**示例：**

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

