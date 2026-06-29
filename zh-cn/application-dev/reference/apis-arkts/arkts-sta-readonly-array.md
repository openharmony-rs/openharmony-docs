# ReadonlyArray
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

本模块提供只读数组接口。`ReadonlyArray<T>`允许读取、遍历、查询和派生新数组，但不提供修改原数组内容或长度的接口。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。

## ReadonlyArray

export interface ReadonlyArray\<out T> extends ConcatArray\<T>

只读数组接口。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### concat

concat(...items: FixedArray\<ConcatArray\<T>>): Array\<T>

合并当前数组与传入的数组类对象，并返回新数组。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| items | FixedArray\<ConcatArray\<T>> | 否 | 要合并到当前数组后的数组类对象。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| Array\<T> | 合并后的新数组。 |

**示例：**

```ts
const values: ReadonlyArray<int> = [1, 2];
const more: ConcatArray<int> = [3, 4];
const result = values.concat(more);
console.info(result.length); // 4
console.info(result.join()); // "1,2,3,4"
```

### entries

entries(): IterableIterator\<[int, T]>

返回由索引和值组成的迭代器。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| IterableIterator\<[int, T]> | 包含数组索引和对应元素值的迭代器。 |

**示例：**

```ts
const values: ReadonlyArray<int> = [1, 2, 3];
for (const entry of values.entries()) {
    console.info(entry[1]); // 1, 2, 3
}
```

### every

every(predicate: (value: T, index: int, array: ReadonlyArray\<T>) => boolean): boolean

判断所有元素是否都满足`predicate`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| predicate | (value: T, index: int, array: ReadonlyArray\<T>) => boolean | 是 | 用于测试每个元素的回调函数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否所有元素都满足回调条件。`true`表示所有元素都满足，`false`表示至少一个元素不满足。 |

**示例：**

```ts
const values: ReadonlyArray<int> = [1, 2, 3];
console.info(values.every((value: int, index: int, array: ReadonlyArray<int>): boolean => value > 0)); // true
console.info(values.every((value: int, index: int, array: ReadonlyArray<int>): boolean => value > 2)); // false
```

### filter

filter(predicate: (value: T, index: int, array: ReadonlyArray\<T>) => boolean): Array\<T>

返回所有满足`predicate`的新数组。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| predicate | (value: T, index: int, array: ReadonlyArray\<T>) => boolean | 是 | 用于筛选元素的回调函数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| Array\<T> | 包含所有满足回调条件元素的新数组。 |

**示例：**

```ts
const values: ReadonlyArray<int> = [1, 2, 3];
const result = values.filter((value: int, index: int, array: ReadonlyArray<int>): boolean => value > 1);
console.info(result.length); // 2
console.info(result.join()); // "2,3"
```

### find

find(predicate: (value: T, index: int, obj: ReadonlyArray\<T>) => boolean): T | undefined

返回第一个满足`predicate`的元素；不存在时返回`undefined`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| predicate | (value: T, index: int, obj: ReadonlyArray\<T>) => boolean | 是 | 用于测试每个元素的回调函数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| T \| undefined | 第一个满足条件的元素；不存在时返回`undefined`。 |

**示例：**

```ts
const values: ReadonlyArray<int> = [1, 2, 3];
console.info(values.find((value: int, index: int, obj: ReadonlyArray<int>): boolean => value > 1)); // 2
console.info(values.find((value: int, index: int, obj: ReadonlyArray<int>): boolean => value > 3)); // undefined
```

### findLast

findLast(predicate: (value: T, index: int, obj: ReadonlyArray\<T>) => boolean): T | undefined

返回最后一个满足`predicate`的元素；不存在时返回`undefined`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| predicate | (value: T, index: int, obj: ReadonlyArray\<T>) => boolean | 是 | 用于测试每个元素的回调函数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| T \| undefined | 最后一个满足条件的元素；不存在时返回`undefined`。 |

**示例：**

```ts
const values: ReadonlyArray<int> = [1, 2, 3];
console.info(values.findLast((value: int, index: int, obj: ReadonlyArray<int>): boolean => value > 1)); // 3
console.info(values.findLast((value: int, index: int, obj: ReadonlyArray<int>): boolean => value > 3)); // undefined
```

### findIndex

findIndex(predicate: (value: T, index: int, obj: ReadonlyArray\<T>) => boolean): int

返回第一个满足`predicate`的元素索引；不存在时返回`-1`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| predicate | (value: T, index: int, obj: ReadonlyArray\<T>) => boolean | 是 | 用于测试每个元素的回调函数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| int | 第一个满足条件元素的索引；不存在时返回`-1`。 |

**示例：**

```ts
const values: ReadonlyArray<int> = [1, 2, 3, 2];
console.info(values.findIndex((value: int, index: int, obj: ReadonlyArray<int>): boolean => value == 2)); // 1
console.info(values.findIndex((value: int, index: int, obj: ReadonlyArray<int>): boolean => value == 5)); // -1
```

### findLastIndex

findLastIndex(predicate: (value: T, index: int, obj: ReadonlyArray\<T>) => boolean): int

返回最后一个满足`predicate`的元素索引；不存在时返回`-1`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| predicate | (value: T, index: int, obj: ReadonlyArray\<T>) => boolean | 是 | 用于测试每个元素的回调函数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| int | 最后一个满足条件元素的索引；不存在时返回`-1`。 |

**示例：**

```ts
const values: ReadonlyArray<int> = [1, 2, 3, 2];
console.info(values.findLastIndex((value: int, index: int, obj: ReadonlyArray<int>): boolean => value == 2)); // 3
console.info(values.findLastIndex((value: int, index: int, obj: ReadonlyArray<int>): boolean => value == 5)); // -1
```

### forEach

forEach(action: (value: T, index: int, array: ReadonlyArray\<T>) => void): void

按顺序对每个元素执行`action`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| action | (value: T, index: int, array: ReadonlyArray\<T>) => void | 是 | 针对每个元素执行的回调函数。 |

**示例：**

```ts
const values: ReadonlyArray<int> = [1, 2, 3];
values.forEach((value: int, index: int, array: ReadonlyArray<int>): void => {
    console.info(value); // 1, 2, 3
});
```

### join

join(separator?: string): string

将数组中所有元素连接为一个字符串并返回。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| separator | string | 否 | 用于分隔每个元素的字符串；省略时使用逗号`,`。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string | 由所有元素连接而成的字符串。 |

**示例：**

```ts
const values: ReadonlyArray<int> = [1, 2, 3];
console.info(values.join());    // "1,2,3"
console.info(values.join("-")); // "1-2-3"
```

### includes

includes(searchElement: T, fromIndex?: int): boolean

判断数组是否包含指定元素。`fromIndex`用于指定开始搜索的位置。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| searchElement | T | 是 | 要搜索的元素。 |
| fromIndex | int | 否 | 开始搜索的位置；省略时从`0`开始。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否包含指定元素。`true`表示包含，`false`表示不包含。 |

**示例：**

```ts
const values: ReadonlyArray<int> = [1, 2, 3];
console.info(values.includes(2)); // true
console.info(values.includes(5)); // false
console.info(values.includes(1, 1)); // false
```

### indexOf

indexOf(searchElement: T, fromIndex?: int): int

返回元素首次出现的位置，未找到时返回`-1`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| searchElement | T | 是 | 要搜索的元素。 |
| fromIndex | int | 否 | 开始搜索的位置；省略时从`0`开始。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| int | 元素首次出现的索引；未找到时返回`-1`。 |

**示例：**

```ts
const values: ReadonlyArray<int> = [1, 2, 3, 2];
console.info(values.indexOf(2));  // 1
console.info(values.indexOf(5));  // -1
console.info(values.indexOf(2, 2)); // 3
```

### keys

keys(): IterableIterator\<int>

返回数组索引迭代器。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| IterableIterator\<int> | 包含数组索引的迭代器。 |

**示例：**

```ts
const values: ReadonlyArray<int> = [1, 2, 3];
for (const key of values.keys()) {
    console.info(key); // 0, 1, 2
}
```

### lastIndexOf

lastIndexOf(searchElement: T, fromIndex?: int): int

返回元素最后一次出现的位置，未找到时返回`-1`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| searchElement | T | 是 | 要搜索的元素。 |
| fromIndex | int | 否 | 开始反向搜索的位置；省略时从数组末尾开始。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| int | 元素最后一次出现的索引；未找到时返回`-1`。 |

**示例：**

```ts
const values: ReadonlyArray<int> = [1, 2, 3, 2];
console.info(values.lastIndexOf(2)); // 3
console.info(values.lastIndexOf(5)); // -1
```

### map

map\<U>(mapper: (value: T, index: int, array: ReadonlyArray\<T>) => U): Array\<U>

按`mapper`映射每个元素并返回新数组。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| mapper | (value: T, index: int, array: ReadonlyArray\<T>) => U | 是 | 用于转换每个元素的回调函数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| Array\<U> | 包含映射结果的新数组。 |

**示例：**

```ts
const values: ReadonlyArray<int> = [1, 2, 3];
const result = values.map<int>((value: int, index: int, array: ReadonlyArray<int>): int => value * 2);
console.info(result.join()); // "2,4,6"
```

### reduce

reduce(reducer: (previousValue: T, currentValue: T, currentIndex: int, array: ReadonlyArray\<T>) => T): T

从左到右累计元素并返回累计结果。首个元素作为初始累计值。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| reducer | (previousValue: T, currentValue: T, currentIndex: int, array: ReadonlyArray\<T>) => T | 是 | 用于累计元素的回调函数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| T | 累计后的结果。 |

**示例：**

```ts
const values: ReadonlyArray<int> = [1, 2, 3];
const result = values.reduce((previous: int, current: int): int => previous + current);
console.info(result); // 6
```

### reduce\<U>

reduce\<U>(reducer: (previousValue: U, currentValue: T, currentIndex: int, array: ReadonlyArray\<T>) => U, initialValue: U): U

从左到右累计元素并返回累计结果。传入初始值，首个元素之前的累计值为初始值。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| reducer | (previousValue: U, currentValue: T, currentIndex: int, array: ReadonlyArray\<T>) => U | 是 | 用于累计元素的回调函数。 |
| initialValue | U | 是 | 初始累计值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| U | 累计后的结果。 |

**示例：**

```ts
const values: ReadonlyArray<int> = [1, 2, 3];
const result = values.reduce((previous: int, current: int): int => previous + current, 10);
console.info(result); // 16
```

### reduceRight

reduceRight(reducer: (previousValue: T, currentValue: T, currentIndex: int, array: ReadonlyArray\<T>) => T): T

从右到左累计元素并返回累计结果。最后一个元素作为初始累计值。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| reducer | (previousValue: T, currentValue: T, currentIndex: int, array: ReadonlyArray\<T>) => T | 是 | 用于累计元素的回调函数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| T | 累计后的结果。 |

**示例：**

```ts
const values: ReadonlyArray<string> = ["a", "b", "c"];
const result = values.reduceRight((previous: string, current: string): string => previous + current);
console.info(result); // "cba"
```

### reduceRight\<U>

reduceRight\<U>(reducer: (previousValue: U, currentValue: T, currentIndex: int, array: ReadonlyArray\<T>) => U, initialValue: U): U

从右到左累计元素并返回累计结果。传入初始值，最后一个元素之后的累计值为初始值。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| reducer | (previousValue: U, currentValue: T, currentIndex: int, array: ReadonlyArray\<T>) => U | 是 | 用于累计元素的回调函数。 |
| initialValue | U | 是 | 初始累计值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| U | 累计后的结果。 |

**示例：**

```ts
const values: ReadonlyArray<string> = ["a", "b", "c"];
const result = values.reduceRight((previous: string, current: string): string => previous + current, "f");
console.info(result); // "fcba"
```

### slice

slice(start?: int, end?: int): Array\<T>

返回从`start`到`end`之前的浅拷贝片段。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| start | int | 否 | 开始提取的位置；省略时从`0`开始。 |
| end | int | 否 | 结束提取的位置；省略时提取到数组末尾。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| Array\<T> | 包含提取元素的新数组。 |

**示例：**

```ts
const values: ReadonlyArray<int> = [1, 2, 3, 4, 5];
console.info(values.slice(1, 3).join()); // "2,3"
console.info(values.slice(2).join());    // "3,4,5"
console.info(values.slice(-2).join());   // "4,5"
```

### some

some(predicate: (value: T, index: int, array: ReadonlyArray\<T>) => boolean): boolean

判断是否至少一个元素满足`predicate`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| predicate | (value: T, index: int, array: ReadonlyArray\<T>) => boolean | 是 | 用于测试每个元素的回调函数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| boolean | 判断是否至少一个元素满足回调条件。`true`表示至少一个元素满足，`false`表示所有元素都不满足。 |

**示例：**

```ts
const values: ReadonlyArray<int> = [1, 2, 3];
console.info(values.some((value: int, index: int, array: ReadonlyArray<int>): boolean => value == 2)); // true
console.info(values.some((value: int, index: int, array: ReadonlyArray<int>): boolean => value > 5)); // false
```

### values

values(): IterableIterator\<T>

返回元素值迭代器。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| IterableIterator\<T> | 包含数组元素值的迭代器。 |

**示例：**

```ts
const values: ReadonlyArray<int> = [1, 2, 3];
for (const v of values.values()) {
    console.info(v); // 1, 2, 3
}
```
