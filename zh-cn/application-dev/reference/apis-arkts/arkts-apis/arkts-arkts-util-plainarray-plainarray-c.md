# PlainArray

PlainArray可用于存储具有关联关系的key-value键值对集合，其中key值唯一且类型为number，每个key对应一个value。PlainArray依据泛型定义，采用轻量级结构。

**起始版本：** 8

<!--Device-unnamed-declare class PlainArray<T>--><!--Device-unnamed-declare class PlainArray<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { PlainArray } from '@kit.ArkTS';
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<[number, T]>
```

返回一个包含key-value键值对的迭代器对象，其中key是number类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-[Symbol.iterator](): IterableIterator<[number, T]>--><!--Device-PlainArray-[Symbol.iterator](): IterableIterator<[number, T]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[number, T]&gt; | @throws { BusinessError } 10200011 - The Symbol.iterator method cannot be bound. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The Symbol.iterator method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");

for (let item of plainArray) {
  console.info("value:" + item[1], "index:" + item[0]);
}
// value:squirrel index:1
// value:sparrow index:2

```

```TypeScript
// 不建议在Symbol.iterator中使用add、remove、removeAt方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。
let plainArray = new PlainArray<string>();
for(let i = 0; i < 10; i++) {
  plainArray.add(i,"123");
}

for(let i = 0; i < 10; i++) {
  plainArray.remove(i);
}

```

## add

```TypeScript
add(key: number, value: T): void
```

向容器中添加一组数据。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-add(key: int, value: T): void--><!--Device-PlainArray-add(key: int, value: T): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | number | 是 | 添加成员数据的键名。需要小于等于int32_max即2147483647。 |
| value | T | 是 | 添加成员数据的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The add method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
console.info("result:", plainArray.get(1));  // result: squirrel

```

## clear

```TypeScript
clear(): void
```

清除容器中的所有元素，并将length置为0。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-clear(): void--><!--Device-PlainArray-clear(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The clear method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
plainArray.clear();
let result = plainArray.isEmpty();
console.info("result:", result);  // result: true

```

## clone

```TypeScript
clone(): PlainArray<T>
```

克隆一个实例，并返回克隆后的实例。修改克隆后的实例并不会影响原实例。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-clone(): PlainArray<T>--><!--Device-PlainArray-clone(): PlainArray<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PlainArray](arkts-arkts-util-plainarray-plainarray-c.md)&lt;T&gt; | 返回新的对象实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The clone method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let newPlainArray = plainArray.clone();
console.info("result:", newPlainArray.get(1));  // result: squirrel

```

## constructor

```TypeScript
constructor()
```

PlainArray的构造函数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-constructor()--><!--Device-PlainArray-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The PlainArray's constructor cannot be directly invoked. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();

```

## forEach

```TypeScript
forEach(callbackFn: (value: T, index?: number, PlainArray?: PlainArray<T>) => void, thisArg?: Object): void
```

在遍历PlainArray实例对象中每一个元素的过程中，对每个元素执行回调函数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-forEach(callbackFn: (value: T, index?: number, PlainArray?: PlainArray<T>) => void, thisArg?: Object): void--><!--Device-PlainArray-forEach(callbackFn: (value: T, index?: number, PlainArray?: PlainArray<T>) => void, thisArg?: Object): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value: T, index?: number, PlainArray?: PlainArray&lt;T&gt;) =&gt; void | 是 | 回调函数。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值，默认值为当前实例对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The forEach method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
plainArray.forEach((value: string, index: number) => {
  console.info("value:" + value, "index:" + index);
});
// value:squirrel index:1
// value:sparrow index:2

```

```TypeScript
// 不建议在forEach中使用add、remove、removeAt方法，因其可能导致迭代过程中的状态异常，建议使用for循环来进行安全的插入与删除操作。
let plainArray = new PlainArray<string>();
for (let i = 0; i < 10; i++) {
  plainArray.add(i, "123");
}

for (let i = 0; i < 10; i++) {
  plainArray.remove(i);
}

```

## get

```TypeScript
get(key: number): T
```

获取指定key所对应的value。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-get(key: number): T--><!--Device-PlainArray-get(key: number): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | number | 是 | 查找的指定key。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回key映射的value值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The get method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.get(1);
console.info("result:", result);  // result: squirrel

```

## getIndexOfKey

```TypeScript
getIndexOfKey(key: number): number
```

查找指定key对应的下标值，如果未找到则返回-1。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-getIndexOfKey(key: int): int--><!--Device-PlainArray-getIndexOfKey(key: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | number | 是 | 指定key。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回指定key对应的下标值，查找失败返回-1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getIndexOfKey method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.getIndexOfKey(2);
console.info("result:", result); // result: 1

```

## getIndexOfValue

```TypeScript
getIndexOfValue(value: T): number
```

查找指定value元素第一次出现的下标值，如果未找到则返回-1。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-getIndexOfValue(value: T): int--><!--Device-PlainArray-getIndexOfValue(value: T): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 指定value元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回指定value元素第一次出现时的下标值，查找失败返回-1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getIndexOfValue method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.getIndexOfValue("squirrel");
console.info("result:", result);  // result: 0

```

## getKeyAt

```TypeScript
getKeyAt(index: number): number
```

查找指定下标元素键值对中的key值。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-getKeyAt(index: int): int--><!--Device-PlainArray-getKeyAt(index: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 指定下标。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回该下标元素键值对中的key值，失败返回-1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getKeyAt method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.getKeyAt(1);
console.info("result:", result); // result: 2

```

## getValueAt

```TypeScript
getValueAt(index: number): T
```

查找指定下标元素键值对中的Value值，失败则返回undefined。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-getValueAt(index: int): T--><!--Device-PlainArray-getValueAt(index: int): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 指定下标。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回该下标元素键值对中的value值，失败返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getValueAt method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.getValueAt(1);
console.info("result:", result);  // result: sparrow

```

## has

```TypeScript
has(key: number): boolean
```

判断容器中是否包含指定key。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-has(key: int): boolean--><!--Device-PlainArray-has(key: int): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | number | 是 | 指定key。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 包含指定key返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The has method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
let result = plainArray.has(1);
console.info("result:", result); // result: true

```

## isEmpty

```TypeScript
isEmpty(): boolean
```

判断容器是否为空。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-isEmpty(): boolean--><!--Device-PlainArray-isEmpty(): boolean-End-->

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
let plainArray = new PlainArray<string>();
let result = plainArray.isEmpty();
console.info("result:", result); // result: true

```

## remove

```TypeScript
remove(key: number): T
```

删除指定key对应的键值对。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-remove(key: number): T--><!--Device-PlainArray-remove(key: number): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | number | 是 | 指定key。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回所删除的键值对中的Value值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The remove method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.remove(2);
console.info("result:", result);  // result: sparrow

```

## removeAt

```TypeScript
removeAt(index: number): T
```

删除指定下标对应的元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-removeAt(index: number): T--><!--Device-PlainArray-removeAt(index: number): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 指定元素下标。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回删除的元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The removeAt method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.removeAt(1);
console.info("result:", result);  // result: sparrow

```

## removeRangeFrom

```TypeScript
removeRangeFrom(index: number, size: number): number
```

删除指定范围内的元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-removeRangeFrom(index: int, size: int): int--><!--Device-PlainArray-removeRangeFrom(index: int, size: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 删除元素的起始下标。需要小于等于int32_max即2147483647。 |
| size | number | 是 | 期望删除元素个数。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 实际删除元素个数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The removeRangeFrom method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
// 从下标1开始删除元素
let result = plainArray.removeRangeFrom(1, 3);
console.info("result:", result);  // result: 1

```

## setValueAt

```TypeScript
setValueAt(index: number, value: T): void
```

替换容器中指定下标对应键值对中的键值。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-setValueAt(index: int, value: T): void--><!--Device-PlainArray-setValueAt(index: int, value: T): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 指定替换数据下标。需要小于等于int32_max即2147483647。 |
| value | T | 是 | 替换键值对中的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The setValueAt method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string | number>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
// 替换plainArray中下标为1的键值对中的value值为3546
plainArray.setValueAt(1, 3546);
// 获取并打印plainArray中下标为1的键值对中的value值
let result = plainArray.getValueAt(1);
console.info("result:", result);  // result: 3546

```

## toString

```TypeScript
toString(): String
```

获取包含容器中所有键和值的字符串。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-toString(): String--><!--Device-PlainArray-toString(): String-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| String | 返回对应字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The toString method cannot be bound. |

**示例：**

```TypeScript
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.toString();
console.info("result:", result);  // result: 1:squirrel,2:sparrow

```

## length

```TypeScript
length: number
```

PlainArray的元素个数。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PlainArray-length: number--><!--Device-PlainArray-length: number-End-->

**系统能力：** SystemCapability.Utils.Lang

