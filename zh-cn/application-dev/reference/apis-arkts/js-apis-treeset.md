# @ohos.util.TreeSet (非线性容器TreeSet)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong; @lijin1039-->
<!--Designer: @Malzahar; @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

TreeSet基于[TreeMap](js-apis-treemap.md)实现，在TreeSet中，只对value对象进行处理。TreeSet可用于存储一系列值的集合，元素中value唯一且有序。

TreeSet和[HashSet](js-apis-hashset.md)中的元素都不允许重复。HashSet中的数据无序存放，而TreeSet是有序存放。HashSet允许插入null值，但TreeSet不建议插入null值，可能会影响排序结果。

**推荐使用场景：** 一般需要存储有序集合的场景，可以使用TreeSet。

文档中使用了泛型，涉及以下泛型标记符：

- T：Type，类

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 容器类使用静态语言实现，限制了存储位置和属性，不支持自定义属性和方法。


## 导入模块

```ts
import { TreeSet } from '@kit.ArkTS';
```

## TreeSet

### 属性

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| length | ArkTS-Dyn: number <br> ArkTS-Sta: int | 是 | 否 | TreeSet的元素个数。 |


### constructor

constructor(comparator?: (firstValue: T, secondValue: T) => boolean)

TreeSet的构造函数，支持通过比较函数对元素进行升序或降序排序。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| comparator | function | 否 | 用户自定义的比较函数，可通过比较关系对元素进行排序。默认值为null，表示不提供比较函数。|

comparator的参数说明：

| 参数名 | 类型 | 必填 | 说明 |
| ------| ---- | ----- | -- |
| firstValue | T | 是 | 前一项元素。 |
| secondValue | T | 是 | 后一项元素。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200012 | The TreeSet's constructor cannot be directly invoked. |

**示例：**

```ts
// 默认构造
let treeSet = new TreeSet<string | number | boolean | Object>();
```

```ts
// 使用comparator firstValue < secondValue，表示期望结果为升序排序。反之firstValue > secondValue，表示为降序排序。
let treeSet: TreeSet<string> = new TreeSet<string>((firstValue: string, secondValue: string): boolean => {
  return firstValue < secondValue;
});
treeSet.add("a");
treeSet.add("c");
treeSet.add("d");
treeSet.add("b");
for (let value of treeSet) {
  console.info("value:", value);
}
// value: a
// value: b
// value: c
// value: d
```

```ts
// 当插入自定义类型时，则必须要提供比较函数。
class TestEntry{
  public id: number = 0;
}
let ts1: TreeSet<TestEntry> = new TreeSet<TestEntry>((t1: TestEntry, t2: TestEntry): boolean => {return t1.id > t2.id;});
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

### constructor<sup>23+</sup>

constructor(comparator?: TreeSetComparator\<T\>)

TreeSet的构造函数，支持通过比较函数对元素进行升序或降序排序。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| comparator | [TreeSetComparator\<T\>](#treesetcomparatort23) | 否 | 用户自定义的比较函数，可通过比较关系对元素进行排序。默认值为hole（一个空白占位符），表示不提供比较函数。|

**示例：**

```ts
// 默认构造
let treeSet : TreeSet<string | int | boolean | Object> = new TreeSet<string | int | boolean | Object>();
```

```ts
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

```ts
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


### isEmpty

isEmpty(): boolean

判断容器是否为空。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 为空返回true，不为空返回false。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The isEmpty method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
const treeSet : TreeSet<string | number | boolean | Object>  = new TreeSet<string | number | boolean | Object>();
let result = treeSet.isEmpty();
console.info("result:", result);  // result: true
```

ArkTS-Sta示例：

```ts
let treeSet = new TreeSet<string>();
let result = treeSet.isEmpty();
console.info("result:", result);  // result: true
```


### has

has(value: T): boolean

判断容器中是否包含指定元素。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | T | 是 | 指定元素。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 包含指定元素返回true，否则返回false。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The has method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
let treeSet  = new TreeSet<number>();
treeSet.add(123);
let result = treeSet.has(123);
console.info("result:", result); // result: true
```

ArkTS-Sta示例：

```ts
let treeSet : TreeSet<int> = new TreeSet<int>();
treeSet.add(123);
let result = treeSet.has(123);
console.info("result = " + result); // result = true
```

### getFirstValue

getFirstValue(): T

获取容器中排序第一的数据，为空时返回undefined。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回排序第一的数据，为空时返回undefined。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The getFirstValue method cannot be bound. |
| 10200010 | Container is empty. <br> **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。|

**示例：**

```ts
let treeSet = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
let result = treeSet.getFirstValue();
console.info("result:", result); // result: sparrow
```

### getLastValue

getLastValue(): T

获取容器中排序最后的数据，为空时返回undefined。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回排序最后的数据，为空时返回undefined。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The getLastValue method cannot be bound. |
| 10200010 | Container is empty. <br> **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。|

**示例：**

```ts
let treeSet = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
let result = treeSet.getLastValue();
console.info("result:", result); // result: squirrel
```

### add

add(value: T): boolean

向容器中添加一组数据。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | T | 是 | 添加的成员数据。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 成功添加新数据至容器返回true，否则返回false。 |

**错误码：**

ArkTS-Dyn错误码：

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The add method cannot be bound. |

**示例：**

```ts
let treeSet = new TreeSet<string>();
let result = treeSet.add("squirrel");
console.info("result:", result); // result: true
```

### remove

remove(value: T): boolean

删除指定的元素。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | T | 是 | 指定的元素。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 成功删除元素返回true，否则返回false。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The remove method cannot be bound. |

**示例：**

```ts
let treeSet = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
let result = treeSet.remove("sparrow");
console.info("result:", result); // result: true
```

### getLowerValue

getLowerValue(key: T): T

获取容器中比传入元素排序靠前一位的元素，为空时返回undefined。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| key | T | 是 | 对比的元素值。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回排序中对比元素前一位的数据，为空时返回undefined。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The getLowerValue method cannot be bound. |

**示例：**

```ts
let treeSet = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
treeSet.add("gander");
let result = treeSet.getLowerValue("sparrow");
console.info("result:", result); // result: gander
```

### getLowerValue<sup>23+</sup>

getLowerValue(key: T): T \| undefined

获取容器中比传入元素排序靠前一位的元素，为空时返回undefined。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| key | T | 是 | 对比的元素值。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T \| undefined | 获取容器中比传入元素排序靠前一位的元素，为空时返回undefined。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200010 | Container is empty. |

**示例：**

```ts
let treeSet : TreeSet<string> = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
treeSet.add("gander");
let result = treeSet.getLowerValue("sparrow");
```

### getHigherValue

getHigherValue(key: T): T

获取容器中比传入元素排序靠后一位的元素，为空时返回undefined。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| key | T | 是 | 对比的元素。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回排序中传入元素后一位的数据。为空时返回undefined。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The getHigherValue method cannot be bound. |

**示例：**

```ts
let treeSet = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
treeSet.add("gander");
let result = treeSet.getHigherValue("sparrow");
console.info("result:", result); // result: squirrel
```

### getHigherValue<sup>23+</sup>

getHigherValue(key: T): T \| undefined

获取容器中比传入元素排序靠后一位的元素，为空时返回undefined。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| key | T | 是 | 对比的元素。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T \| undefined | 返回排序中传入元素后一位的数据。为空时返回undefined。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200010 | Container is empty. |

**示例：**

```ts
let treeSet : TreeSet<string> = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
treeSet.add("gander");
let result = treeSet.getHigherValue("sparrow");
```

### popFirst

popFirst(): T

删除容器中排序最前的数据，为空时返回undefined。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回删除的数据，为空时返回undefined。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The popFirst method cannot be bound. |
| 10200010 | Container is empty. <br> **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。|

**示例：**

```ts
let treeSet = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
let result = treeSet.popFirst();
console.info("result:", result); // result: sparrow
```

### popLast

popLast(): T

删除容器中排序最后的数据，为空时返回undefined。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回删除的数据，为空时返回undefined。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The popLast method cannot be bound. |
| 10200010 | Container is empty. <br> **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。|

**示例：**

```ts
let treeSet = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
let result = treeSet.popLast();
console.info("result:", result); // result: squirrel
```

### clear

clear(): void

清除容器中的所有元素，并将length置为0。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The clear method cannot be bound. |

**示例：**

```ts
let treeSet = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
treeSet.clear();
let result = treeSet.isEmpty();
console.info("result:", result); // result: true
```

### values

values(): IterableIterator&lt;T&gt;

返回包含此映射中键值的新迭代器对象。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| IterableIterator&lt;T&gt; | 返回一个迭代器。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The values method cannot be bound. |

**示例：**

```ts
let treeSet = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
let values = treeSet.values();
for (let value of values) {
  console.info("value:", value)
}
// value: sparrow
// value: squirrel
```

### forEach

forEach(callbackFn: (value?: T, key?: T, set?: TreeSet&lt;T&gt;) => void, thisArg?: Object): void

通过回调函数来遍历实例对象上的元素及其下标。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callbackFn | function | 是 | 回调函数。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值，默认值为当前实例对象。 |

callbackFn的参数说明：
| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | T | 否 | 当前遍历到的value元素。 |
| key | T | 否 | 当前遍历到的key元素。 |
| set | TreeSet&lt;T&gt; | 否 | 当前调用forEach方法的实例对象，默认值为当前实例对象。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The forEach method cannot be bound. |

**示例：**

```ts
let treeSet = new TreeSet<string>();
treeSet.add("sparrow");
treeSet.add("gull");
treeSet.forEach((value: string, key: string): void => {
  console.info("value:" + value);
});
// value:gull
// value:sparrow
```
```ts
// 不建议在forEach中使用set、remove方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。
let treeSet = new TreeSet<string>();
for(let i = 0; i < 10; i++) {
  treeSet.add("sparrow" + i);
}
for(let i = 0; i < 10; i++) {
  treeSet.remove("sparrow" + i);
}
```

### forEach<sup>23+</sup>

forEach(callbackFn: TreeSetForEachCb\<T\>): void

通过回调函数来遍历实例对象上的元素以及元素对应的下标。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callbackFn | [TreeSetForEachCb\<T\>](#treesetforeachcbt23) | 是 | 回调函数。 |

**示例：**

```ts
import { TreeSetForEachCb } from '@kit.ArkTS';

let treeSet: TreeSet<string> = new TreeSet<string>();
treeSet.add("sparrow");
treeSet.add("gull");
let treeSetCb: TreeSetForEachCb<string> = (value: string, key: string, set: TreeSet<string>) => {
  console.info("value: " + value, " key: "+ key);
};
treeSet.forEach(treeSetCb);
```

### entries

entries(): IterableIterator<[T, T]>

返回包含此映射中键值对的新迭代器对象。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| IterableIterator<[T, T]> | 返回一个迭代器。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The entries method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
let treeSet = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
let it = treeSet.entries();
let t: IteratorResult<Object[]> = it.next();
while(!t.done) {
  console.info("TreeSet: " + t.value[1]);
  t = it.next()
}
// TreeSet: sparrow
// TreeSet: squirrel
```

```ts
// 不建议在entries中使用set、remove方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。
let treeSet = new TreeSet<string>();
for(let i = 0; i < 10; i++) {
  treeSet.add("sparrow" + i);
}
for(let i = 0; i < 10; i++) {
  treeSet.remove("sparrow" + i);
}
```

ArkTS-Sta示例：

```ts
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

```ts
// 不建议在entries中使用set、remove方法，因其可能导致迭代过程中的状态异常，建议使用for循环来进行安全的插入与删除操作。
let treeSet : TreeSet<string> = new TreeSet<string>();
for(let i = 0; i < 10; i++) {
  treeSet.add("sparrow" + i);
}
for(let i = 0; i < 10; i++) {
  treeSet.remove("sparrow" + i);
}
```

### [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;T&gt;

返回一个迭代器，迭代器的每一项都是一个JavaScript对象。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| IterableIterator&lt;T&gt; | 返回一个迭代器。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The Symbol.iterator method cannot be bound. |

**示例：**

```ts
let treeSet = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");

// 使用方法一：
for (let item of treeSet) {
  console.info("value:" + item);
}
// value:sparrow
// value:squirrel

// 使用方法二：
let iter = treeSet[Symbol.iterator]();
let temp: IteratorResult<string> = iter.next().value;
while(temp != undefined) {
  console.info("value:" + temp);
  temp = iter.next().value;
}
// value:sparrow
// value:squirrel
```

```ts
// 不建议在Symbol.iterator中使用set、remove方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。
let treeSet = new TreeSet<string>();
for(let i = 0; i < 10; i++) {
  treeSet.add("sparrow" + i);
}
for(let i = 0; i < 10; i++) {
  treeSet.remove("sparrow" + i);
}
```

### $_iterator<sup>23+</sup>

\$_iterator\(): IterableIterator&lt;T&gt;

返回一个迭代器，迭代器的每一项都是一个JavaScript对象，并返回该对象。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| IterableIterator&lt;T&gt; | 返回一个迭代器。 |

**示例：**

```ts
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

### TreeSetForEachCb\<T\><sup>23+</sup>

type TreeSetForEachCb\<T\> = (value: T, key: T, set: TreeSet\<T\>) => void

TreeSet中forEach方法的回调函数。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | T | 是 | 当前遍历到的value元素。 |
| key | T | 是 | 当前遍历到的key元素。 |
| set | [TreeSet&lt;T&gt;](#treeset) | 是 | 当前调用[forEach](#foreach23)方法的实例对象。 |

### TreeSetComparator\<T\><sup>23+</sup>

type TreeSetComparator\<T\> = (firstValue: T, secondValue: T) => double

TreeSet中[constructor](#constructor23)方法的回调函数。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| firstValue | T | 是 | 比较关系中第一个元素。 |
| secondValue | T | 是 | 比较关系中第二个元素。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| double | 通过回调函数返回的double，TreeSet能够根据自定义的比较规则维护元素的顺序。 |