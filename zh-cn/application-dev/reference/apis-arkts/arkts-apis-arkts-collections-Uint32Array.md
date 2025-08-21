# Class (Uint32Array)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @lijiamin2025-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->
> **说明：**
>
> 本模块首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。

一种线性数据结构，底层基于[ArkTS ArrayBuffer](arkts-apis-arkts-collections-ArrayBuffer.md)实现。

**装饰器类型：**\@Sendable

## 导入模块

```ts
import { collections } from '@kit.ArkTS';
```

## 属性

**系统能力：** SystemCapability.Utils.Lang

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

| 名称   | 类型   | 只读 | 可选 | 说明              |
| ------ | ------ | ---- | ---- | ----------------|
| buffer | ArrayBuffer | 是   | 否  | ArkTS Uint32Array底层使用的buffer。|
| byteLength | number | 是   | 否   | ArkTS Uint32Array的所占的字节数。|
| byteOffset | number | 是   | 否   | ArkTS Uint32Array距离其ArrayBuffer起始位置的偏移。|
| length | number | 是   | 否  | ArkTS Uint32Array元素个数。|
| BYTES_PER_ELEMENT | number | 是   | 否   | ArkTS Uint32Array中每个元素所占用的字节数。|

## constructor
constructor()

构造函数，用于创建一个空ArkTS Uint32Array对象。

**系统能力：** SystemCapability.Utils.Lang

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                                |
| -------- | ------------------------------------------------------- |
| 10200012 | The Uint32Array's constructor cannot be directly invoked. |

**示例：**

```ts
let uint32Array: collections.Uint32Array = new collections.Uint32Array();
```

## constructor
constructor(length: number)

构造函数，用于创建一个指定长度的ArkTS Uint32Array对象。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名  | 类型   | 必填 | 说明                          |
| ------- | ------ | ---- | --------------------------- |
| length | number | 是 | 用于指定ArkTS Uint32Array的长度。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                                  |
| -------- | -------------------------------------------------------  |
| 401      | Parameter error.                                         |
| 10200012 | The Uint32Array's constructor cannot be directly invoked. |


**示例：**

```ts
// 以长度参数构造对象
let uint32Array: collections.Uint32Array = new collections.Uint32Array(12);
```

## constructor
constructor(array: ArrayLike\<number> | ArrayBuffer)

构造函数，以ArrayLike或ArkTS ArrayBuffer创建一个ArkTS Uint32Array对象。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名  | 类型   | 必填 | 说明                                                         |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| array |  ArrayLike\<number> \| ArrayBuffer | 是 | 用于构造ArkTS Uint32Array的对象。当参数类型是ArrayBuffer时buffer所占的字节数须是4的整数倍。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                                |
| -------- | ------------------------------------------------------- |
| 401      | Parameter error.                                         |
| 10200012 | The Uint32Array's constructor cannot be directly invoked. |

**示例：**

```ts
// 例1 从一个ArrayLike构造对象
let arrayLike = [1, 3, 5];
let array: collections.Uint32Array = new collections.Uint32Array(arrayLike);
```

```ts
// 例2 从一个ArrayBuffer构造对象
let arrayBuffer: collections.ArrayBuffer = new collections.ArrayBuffer(12);
let array: collections.Uint32Array = new collections.Uint32Array(arrayBuffer);
```

```ts
// 例3 从另一ArkTS Uint32Array构造对象
let arrayLike = [1, 3, 5];
// uint32Array1 [1, 3, 5]
let uint32Array1: collections.Uint32Array = new collections.Uint32Array(arrayLike);
// uint32Array2 [1, 3, 5]
let uint32Array2: collections.Uint32Array = new collections.Uint32Array(uint32Array1);
```

## constructor
constructor(buffer: ArrayBuffer, byteOffset?: number, length?: number)

构造函数，以ArrayBuffer创建一个ArkTS Uint32Array对象。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名  | 类型   | 必填 | 说明                                         |
| ------- | ------ | ---- | ------------------------------------------ |
| buffer | ArrayBuffer | 是 | 用于构造ArkTS Uint32Array的ArrayBuffer对象。buffer所占的字节数须是4的整数倍。|
| byteOffset | number | 否 | 指定buffer的字节偏移，从0开始，默认为0。 |
| length | number | 否 | 指定ArkTS Uint32Array的长度，默认为0。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                                   |
| -------- | -------------------------------------------------------   |
| 401      | Parameter error.                                         |
| 10200012 | The Uint32Array's constructor cannot be directly invoked. |

**示例：**

```ts
let uint32Array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5, 6]);
console.info("byteLength: " + uint32Array.buffer.byteLength); // byteLength: 24
// 从uint32Array对应buffer第4个字节开始，长度为5
let uint32Array1: collections.Uint32Array = new collections.Uint32Array(uint32Array.buffer, 4, 5);
console.info("[" + uint32Array1 + "]"); // [2, 3, 4, 5, 6]
```

## from
static from(arrayLike: ArrayLike\<number>): Uint32Array

从一个ArrayLike或者可迭代对象中创建一个ArkTS Uint32Array对象。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名  | 类型   | 必填 | 说明                                                  |
| ------- | ------ | ---- | --------------------------------------------------- |
| arrayLike | ArrayLike\<number> | 是 | 用于构造ArkTS Uint32Array的ArrayLike对象。 |

**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
| Uint32Array | 新创建的ArkTS Uint32Array对象。|

**示例：**
```ts
let arrayLike = [1, 3, 5];
let array: collections.Uint32Array = collections.Uint32Array.from(arrayLike); // array [1, 3, 5]
```

## from
static from\<T>(arrayLike: ArrayLike\<T>, mapFn: TypedArrayFromMapFn\<T, number>): Uint32Array

从一个ArrayLike中创建一个ArkTS Uint32Array对象。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**
| 参数名  | 类型   | 必填 | 说明                                        |
| ------- | ------ | ---- | ------------------------------------------|
| arrayLike | ArrayLike\<T> | 是 | 用于构造ArrayLike对象。              |
| mapFn | [TypedArrayFromMapFn](arkts-apis-arkts-collections-Types.md#typedarrayfrommapfn)\<T, number> | 是 | 映射函数。|

**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
| Uint32Array | 新创建的ArkTS Uint32Array对象。|

**示例：**

```ts
// 例1 从一个对象创建
let array: collections.Uint32Array = collections.Uint32Array.from<number>(
  { length: 5 }, (v: Object, k: number) => k);
// Uint32Array [0, 1, 2, 3, 4]
```

```ts
// 例2 从一个字符数组创建
let array: collections.Uint32Array = collections.Uint32Array.from<string>(
  ["1", "3", "5"], (v: string, k: number) => parseInt(v));
// Uint32Array [1, 3, 5]
```

```ts
// 例3 从一个字符串创建
let array: collections.Uint32Array = collections.Uint32Array.from<string>(
  "12345", (v: string, k: number) => parseInt(v));
// Uint32Array [1, 2, 3, 4, 5]
```

## from
static from(arrayLike: Iterable\<number>, mapFn?: TypedArrayFromMapFn\<number, number>): Uint32Array

从一个可迭代对象中创建一个ArkTS Uint32Array对象。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**
| 参数名  | 类型   | 必填 | 说明                                |
| ------- | ------ | ---- | -----------------------------------|
| arrayLike | Iterable\<number> | 是 | 用于构造的可迭代对象。   |
| mapFn | [TypedArrayFromMapFn](arkts-apis-arkts-collections-Types.md#typedarrayfrommapfn)\<number, number> | 否 | 映射函数。如果省略，则不对元素进行加工处理。|

**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
| Uint32Array | 新创建的ArkTS Uint32Array对象。|

**示例：**

```ts
// 例1 不指定映射函数
let set: Set<number> = new Set<number>([1, 2, 3]);
let array: collections.Uint32Array = collections.Uint32Array.from(set);
// Uint32Array [1, 2, 3]
```

```ts
// 例2 指定映射函数
let set: Set<number> = new Set<number>([1, 2, 3]);
let array: collections.Uint32Array = collections.Uint32Array.from(
  set, (v: number, k: number) => v + k);
// Uint32Array [1, 3, 5]
```

## of<sup>18+</sup>

static of(...items: number[]): Uint32Array

通过可变数量的参数创建一个新的ArkTS Uint32Array对象，参数个数可以是0个、1个或者多个。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名    | 类型          | 必填 | 说明                            |
| --------- | ------------- | ---- | ------------------------------- |
| items | number[] | 否   | 用于创建数组的元素，参数个数可以是0个、1个或者多个。 |

**返回值：**

| 类型      | 说明                    |
| --------- | ----------------------- |
| Uint32Array | 新的ArkTS Uint32Array实例。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 401 | Parameter error: Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例：**

```ts
let arr: collections.Uint32Array = collections.Uint32Array.of(1, 2, 3, 4);
console.info(arr.toString()); // 预期输出：1,2,3,4
```

## toString<sup>18+</sup>

toString(): string

ArkTS Uint32Array转换为字符串。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型         | 说明            |
| ---------- | ------------- |
| string | 一个包含数组所有元素的字符串。 |

**错误码：**

以下错误码详细介绍请参考[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID    | 错误信息                                 |
| -------- | ------------------------------------ |
| 10200011 | The toString method cannot be bound. |
| 10200201 | Concurrent modification error.       |

**示例：**

```ts
let array = new collections.Uint32Array([1, 2, 3, 4, 5]);
let stringArray = array.toString();
console.info(stringArray); // 预期输出：1,2,3,4,5
```

## toLocaleString<sup>18+</sup>

toLocaleString(): string

根据当前应用的系统地区获取符合当前文化习惯的数字表示形式，让每个元素调用自己的toLocaleString方法把数字转换为字符串，然后使用逗号将每个元素的结果字符串按照顺序拼接成字符串。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型         | 说明            |
| ---------- | ------------- |
| string | 一个包含数组所有元素的字符串。 |

**错误码：**

以下错误码详细介绍请参考[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID    | 错误信息                                       |
| -------- | ------------------------------------------ |
| 10200011 | The toLocaleString method cannot be bound. |
| 10200201 | Concurrent modification error.             |

**示例：**

```ts
// 当前应用所在系统为法国地区
let array = new collections.Uint32Array([1000, 2000, 3000]);
let stringArray = array.toLocaleString();
console.info(stringArray); // 预期输出：1,000, 2,000, 3,000
```

## copyWithin
copyWithin(target: number, start: number, end?: number): Uint32Array

从ArkTS Uint32Array指定范围内的元素依次拷贝到目标位置。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名  | 类型   | 必填 | 说明                                                         |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| target | number | 是 | 目标起始位置的下标。 |
| start | number | 是 | 源起始位置下标，如果`start < 0`，则会从`start + Uint32Array.length`位置开始。 |
| end | number | 否 | 源终止位置下标（不包含end位置的元素），如果`end < 0`，则会从`end + Uint32Array.length`位置终止。默认为ArkTS Uint32Array的长度。|

**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
| Uint32Array | 修改后的Uint32Array。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                          |
| -------- | ------------------------------------------------ |
| 401      | Parameter error.                                 |
| 10200011 | The copyWithin method cannot be bound.           |
| 10200201 | Concurrent modification error.               |

**示例：**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5, 6, 7, 8]);
let copied: collections.Uint32Array = array.copyWithin(3, 1, 3);
// Uint32Array [1, 2, 3, 2, 3, 6, 7, 8]
```

## some
some(predicate: TypedArrayPredicateFn\<number, Uint32Array>): boolean

测试ArkTS Uint32Array中的是否存在元素满足指定条件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名  | 类型   | 必填 | 说明                                                  |
| ------- | ------ | ---- | ---------------------------------------------------- |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Uint32Array> | 是 | 用于测试的断言函数。|

**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
| boolean | 如果存在元素满足指定条件返回true，否则返回false。|

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                            |
| -------- | ---------------------------------- |
| 401      | Parameter error.                   |
| 10200011 | The some method cannot be bound.   |
| 10200201 | Concurrent modification error. |

**示例：**

```ts
let arrayLike = [-10, 20, -30, 40, -50];
let uint32Array: collections.Uint32Array = new collections.Uint32Array(arrayLike);
uint32Array.some((element: number) => element < 0); // false
```

## every
every(predicate: TypedArrayPredicateFn\<number, Uint32Array>): boolean

测试ArkTS Uint32Array中的所有元素是否满足指定条件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名  | 类型   | 必填 | 说明                                                    |
| ------- | ------ | ---- | ----------------------------------------------------- |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Uint32Array> | 是 | 用于测试的断言函数。|

**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
| boolean | 如果所有元素都满足指定条件则返回true，否则返回false。|

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                          |
| -------- | ------------------------------------------------- |
| 401      | Parameter error.                  |
| 10200011 | The every method cannot be bound. |
| 10200201 | Concurrent modification error. |

**示例：**

```ts
let arrayLike = [-10, 20, -30, 40, -50];
let uint32Array: collections.Uint32Array = new collections.Uint32Array(arrayLike);
uint32Array.every((element: number) => element > 0);  // true
```

## fill
fill(value: number, start?: number, end?: number): Uint32Array

使用特定值填充ArkTS Uint32Array指定范围的全部元素。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名  | 类型   | 必填 | 说明                                                      |
| ------- | ------ | ---- | --------------------------------------------------------|
| value | number | 是 | 待填充的值。|
| start | number | 否 | 开始填充的索引，如果`start < 0`，则会从`start + Uint32Array.length`位置开始。默认值为0。|
| end | number | 否 | 结束填充的索引（不包括该元素），如果`end < 0`，则会到`end + Uint32Array.length`位置结束。默认为ArkTS Uint32Array的长度。|

**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
| Uint32Array | 填充后的Uint32Array。|

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                          |
| -------- | ------------------------------------------------- |
| 401      | Parameter error.                 |
| 10200011 | The fill method cannot be bound. |
| 10200201 | Concurrent modification error. |

**示例：**

```ts
let arrayLike = [1, 2, 3];
new collections.Uint32Array(arrayLike).fill(4); // Uint32Array [4, 4, 4]
new collections.Uint32Array(arrayLike).fill(4, 1); // Uint32Array [1, 4, 4]
new collections.Uint32Array(arrayLike).fill(4, 1, 2); // Uint32Array [1, 4, 3]
```

## filter
filter(predicate: TypedArrayPredicateFn\<number, Uint32Array>): Uint32Array

返回一个新ArkTS Uint32Array，其包含满足指定条件的所有元素。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名  | 类型   | 必填 | 说明                                                    |
| ------- | ------ | ---- | ------------------------------------------------------ |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Uint32Array> | 是 | 用于元素过滤的断言函数。 |

**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
| Uint32Array| 过滤后的ArkTS Uint32Array对象。|

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                          |
| -------- | ------------------------------------------------- |
| 401      | Parameter error.                   |
| 10200011 | The filter method cannot be bound. |
| 10200201 | Concurrent modification error. |

**示例：**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([0, 1, 2, 3, 4]);
let filtered: collections.Uint32Array = array.filter((element: number) => element % 2 == 0);
// Uint32Array [0, 2, 4]
```

## find
find(predicate: TypedArrayPredicateFn\<number, Uint32Array>): number | undefined

返回ArkTS Uint32Array中第一个满足指定条件的元素的值，如果所有元素都不满足，则返回undefined。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名  | 类型   | 必填 | 说明                                                         |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Uint32Array> | 是 | 用于元素查找的断言函数。|

**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
|  number \| undefined | 第一个满足条件的元素的值；如果所有元素都不满足条件，则返回undefined。|

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                          |
| -------- | ------------------------------------------------- |
| 401      | Parameter error.                 |
| 10200011 | The find method cannot be bound. |
| 10200201 | Concurrent modification error. |

**示例：**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([0, 1, 2, 3, 4]);
array.find((element: number) => element > 2); // 3
array.find((element: number) => element > 4); // undefined
```

## findIndex
findIndex(predicate: TypedArrayPredicateFn\<number, Uint32Array>): number

返回ArkTS Uint32Array中第一个满足指定条件的元素索引，如果所有元素都不满足，则返回-1。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名  | 类型   | 必填 | 说明                                                         |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Uint32Array> | 是 | 用于元素查找的断言函数。|

**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
| number | 第一个满足条件的元素索引；如果所有元素都不满足条件，则返回-1。|

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                          |
| -------- | ------------------------------------------------- |
| 401      | Parameter error.                      |
| 10200011 | The findIndex method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**示例：**

```ts
const array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
let foundIndex: number = array.findIndex((element: number) => element % 2 === 0); // 1
```

## forEach
forEach(callbackFn: TypedArrayForEachCallback\<number, Uint32Array>): void

对ArkTS Uint32Array中的每个元素执行提供的回调函数。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名  | 类型   | 必填 | 说明                                                         |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| callbackFn | [TypedArrayForEachCallback](arkts-apis-arkts-collections-Types.md#typedarrayforeachcallback)\<number, Uint32Array> | 是 | 用于对每个元素执行的回调函数。|


**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                          |
| -------- | ------------------------------------------------- |
| 401      | Parameter error.                    |
| 10200011 | The forEach method cannot be bound. |
| 10200201 | Concurrent modification error. |

**示例：**

```ts
let uint32Array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3]);
uint32Array.forEach((value: number, index: number, array: collections.Uint32Array) => {
  console.info(`Element ${value} at index ${index}`);
});
```

## indexOf
indexOf(searchElement: number, fromIndex?: number): number

返回在ArkTS Uint32Array中给定元素的第一个索引，如果不存在，则返回-1。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名        | 类型   | 必填 | 说明                        |
| ------------- | ------ | ---- | ---------------------------|
| searchElement | number | 是   | 待索引的值。                |
| fromIndex     | number | 否   | 搜索的起始下标。默认值为0。如果下标大于等于ArkTS Uint32Array的长度，则返回-1。如果提供的下标值是负数，则被当做距离数组尾部的偏移，从前到后搜索。 |

**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
| number | 数组中元素的第一个索引；没有找到，则返回-1。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                          |
| -------- | ------------------------------------------------- |
| 401      | Parameter error.                    |
| 10200011 | The indexOf method cannot be bound. |
| 10200201 | Concurrent modification error.                |

**示例：**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([3, 5, 9]);
array.indexOf(3); // 0
array.indexOf(7); // -1
array.indexOf(9, 2); // 2
array.indexOf(9, -2); // 2
```

## lastIndexOf<sup>18+</sup>

lastIndexOf(searchElement: number, fromIndex?: number): number

返回ArkTS Uint32Array实例中最后一次出现searchElement的索引，如果对象不包含，则为-1。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名           | 类型     | 必填  | 说明                                                                                |
| ------------- | ------ | --- | --------------------------------------------------------------------------------- |
| searchElement | number | 是   | 待索引的值。                                                                            |
| fromIndex     | number | 否   | 搜索的起始下标。默认值为0。如果下标大于等于ArkTS Uint32Array的长度，则返回-1。如果提供的下标值是负数，则被当做距离数组尾部的偏移，从后到前搜索。 |

**返回值：**

| 类型     | 说明                      |
| ------ | ----------------------- |
| number | 数组中给定元素的最后一个索引；没有找到，则返回-1。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID    | 错误信息                                    |
| -------- | --------------------------------------- |
| 10200011 | The lastIndexOf method cannot be bound. |
| 10200201 | Concurrent modification error. |

**示例：**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([3, 5, 9]);
console.info(array.lastIndexOf(3) + ''); // 预期输出：0
console.info(array.lastIndexOf(7) + ''); // 预期输出：-1
console.info(array.lastIndexOf(9, 2) + ''); // 预期输出：2
console.info(array.lastIndexOf(9, -2) + ''); // 预期输出：-1
```

## join
join(separator?: string): string

将ArkTS Uint32Array的所有元素拼接成一个字符串，元素之间使用指定的分隔符分隔。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名    | 类型   | 必填 | 说明                                                 |
| --------- | ------ | ---- | ---------------------------------------------------- |
| separator | string | 否   | 分隔字符串。如果省略，则使用逗号分隔。 |

**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
| string | 包含所有元素拼接成的字符串。如果ArkTS Uint32Array为空，则返回空字符串。|

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                          |
| -------- | ------------------------------------------------- |
| 401      | Parameter error.                 |
| 10200011 | The join method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**示例：**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
let joined: string = array.join('-'); // "1-2-3-4-5"
```

## map
map(callbackFn: TypedArrayMapCallback\<number, Uint32Array>): Uint32Array

对ArkTS Uint32Array中的每个元素应用指定的回调函数，并使用结果创建一个新的ArkTS Uint32Array对象。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**
| 参数名    | 类型   | 必填 | 说明                                                 |
| --------- | ------ | ---- | ---------------------------------------------------- |
| callbackFn | [TypedArrayMapCallback](arkts-apis-arkts-collections-Types.md#typedarraymapcallback)\<number, Uint32Array> | 是  | 回调函数。 |


**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
| Uint32Array | 新ArkTS Uint32Array对象。|

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                          |
| -------- | ------------------------------------------------- |
| 401      | Parameter error.                |
| 10200011 | The map method cannot be bound. |
| 10200201 | Concurrent modification error. |

**示例：**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([25, 36, 49]);
const mapped: collections.Uint32Array = array.map(Math.sqrt); // Uint32Array [5, 6 ,7]
```

## reduce
reduce(callbackFn: TypedArrayReduceCallback\<number, number, Uint32Array>): number

对ArkTS Uint32Array中的每个元素执行归约函数，并返回最终的归约结果。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**
| 参数名     | 类型   | 必填 |  说明     |
| ---------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<number, number, Uint32Array> | 是 | 归约函数。 |

**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
| number | 由归约函数返回的结果。|

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID |                      错误信息                     |
| -------- | ------------------------------------------------ |
| 401      | Parameter error.                                 |
| 10200011 | The reduce method cannot be bound.               |
| 10200201 | Concurrent modification error.               |

**示例：**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
let reducedValue: number = array.reduce((accumulator: number, value: number) => accumulator + value);
// reducedValue == 15
```

## reduceRight<sup>18+</sup>

reduceRight(callbackFn: TypedArrayReduceCallback\<number, number, Uint32Array>): number

反向遍历ArkTS Uint32Array，对ArkTS Uint32Array中的每个元素执行归约函数，并返回最终的归约结果。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**
| 参数名     | 类型   | 必填 |  说明     |
| ---------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<number, number, Uint32Array> | 是 | 归约函数。 |

**返回值：**

| 类型     | 说明          |
| ------ | ----------- |
| number | 由归约函数返回的结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID    | 错误信息                                    |
| -------- | --------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 10200011 | The reduceRight method cannot be bound. |
| 10200201 | Concurrent modification error.      |

**示例：**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
let reducedValue: number = array.reduceRight((accumulator: number, value: number) => accumulator + value);
console.info(reducedValue + ''); // 预期输出： 15
```

## reduce
reduce(callbackFn: TypedArrayReduceCallback\<number, number, Uint32Array>, initialValue: number): number

对ArkTS Uint32Array中的每个元素执行归约函数，且接收一个初始值作为归约函数首次调用的参数，并返回最终的归约结果。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**
| 参数名    | 类型   | 必填 | 说明                                                 |
| --------- | ------ | ---- | --------------------------------------------------- |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<number, number, Uint32Array> | 是  | 归约函数。 |
| initialValue | number | 是  | 初始值。 |


**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
| number | 由归约函数返回的结果。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                          |
| -------- | ------------------------------------------------- |
| 401      | Parameter error.                   |
| 10200011 | The reduce method cannot be bound. |
| 10200201 | Concurrent modification error. |

**示例：**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
let reducedValue: number = array.reduce((accumulator: number, value: number) => accumulator + value, 1);
// reducedValue == 16
```

## reduceRight<sup>18+</sup>

reduceRight\<U = number>(callbackFn: TypedArrayReduceCallback\<U, number, Uint32Array>, initialValue: U): U

反向遍历ArkTS Uint32Array，对ArkTS Uint32Array中的每个元素执行归约函数，且接收一个初始值作为归约函数首次调用的参数，并返回最终的归约结果。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**
| 参数名    | 类型   | 必填 | 说明                                                 |
| --------- | ------ | ---- | --------------------------------------------------- |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<U, number, Uint32Array> | 是  | 归约函数。 |
| initialValue | U | 是  | 初始值。 |

**返回值：**

| 类型     | 说明          |
| ------ | ----------- |
| U | 由归约函数返回的结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID    | 错误信息                                    |
| -------- | --------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 10200011 | The reduceRight method cannot be bound. |
| 10200201 | Concurrent modification error.      |

**示例：**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
let reducedValue: number = array.reduceRight((accumulator: number, value: number) => accumulator + value, 1);
console.info(reducedValue + ''); // 预期输出： 16
```

## reduce
reduce\<U>(callbackFn: TypedArrayReduceCallback\<U, number, Uint32Array>, initialValue: U): U

对ArkTS Uint32Array中的每个元素执行归约函数，且接收一个初始值作为归约函数首次调用的参数，并返回最终的归约结果。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名    | 类型   | 必填 | 说明                                                 |
| --------- | ------ | ---- | ---------------------------------------------------- |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<U, number, Uint32Array> | 是  | 归约函数。 |
| initialValue | U | 是  | 初始值。 |

**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
|  U | 由归约函数返回的结果。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                          |
| -------- | ------------------------------------------------- |
| 401      | Parameter error.                   |
| 10200011 | The reduce method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**示例：**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
let reducedValue: string = array.reduce<string>((accumulator: string, value: number) => accumulator + value, "initialValue");
// reducedValue == initialValue12345
```

## reverse
reverse(): Uint32Array

反转ArkTS Uint32Array。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
| Uint32Array   | 反转后的ArkTS Uint32Array对象。|

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                          |
| -------- | ------------------------------------------------- |
| 10200011 | The reverse method cannot be bound. |
| 10200201 | Concurrent modification error.   |

**示例：**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
let reversed: collections.Uint32Array = array.reverse(); // Uint32Array [5, 4, 3, 2, 1]
```

## set
set(array: ArrayLike\<number>, offset?: number): void

将传入的ArrayLike元素依次写入到指定的起始位置。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**
| 参数名    | 类型   | 必填 | 说明                                                 |
| --------- | ------ | ---- | ---------------------------------------------------- |
| array | ArrayLike\<number> | 是  | 用于设置的ArrayLike对象。|
| offset | number | 否  | 写入的起始位置。默认为0。|

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                          |
| -------- | ------------------------------------------------- |
| 401      | Parameter error.                |
| 10200011 | The set method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**示例：**

```ts
let buffer: collections.ArrayBuffer = new collections.ArrayBuffer(32);
let array: collections.Uint32Array = new collections.Uint32Array(buffer);
array.set([1, 2, 3], 3); // Uint32Array [0, 0, 0, 1, 2, 3, 0, 0]
```

## slice
slice(start?: number, end?: number): Uint32Array

返回一个新的ArkTS Uint32Array对象，其包含原ArkTS Uint32Array指定范围的内容。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型   | 必填 | 说明                                                   |
| ------ | ------ | ---- | -----------------------------------------------------|
| start  | number | 否   | 开始索引，如果`start < 0`，则会从`start + Uint32Array.length`位置开始。默认为0。 |
| end    | number | 否   | 结束索引（不包括该元素），如果`end < 0`，则会到`end + Uint32Array.length`位置结束。默认为ArkTS Uint32Array的长度。|

**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
| Uint32Array | 新的ArkTS Uint32Array对象。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                          |
| -------- | ------------------------------------------------- |
| 401      | Parameter error.                  |
| 10200011 | The slice method cannot be bound. |
| 10200201 | Concurrent modification error. |

**示例：**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
array.slice(); // Uint32Array [1, 2, 3, 4, 5]
array.slice(1, 3); // Uint32Array [2, 3]
array.slice(-2); // Uint32Array [4, 5]
```

## sort
sort(compareFn?: TypedArrayCompareFn\<number>): Uint32Array

对ArkTS Uint32Array进行排序，并返回排序后的ArkTS Uint32Array对象。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名    | 类型                   | 必填 | 说明                                       |
| --------- | ---------------------- | ---- | ------------------------------------------ |
| compareFn | [TypedArrayCompareFn](arkts-apis-arkts-collections-Types.md#typedarraycomparefn)\<number> | 否   | 用于确定元素顺序的函数。默认使用升序排序。 |

**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
| Uint32Array | 排序后的ArkTS Uint32Array对象。|

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------ |
| 401      | Parameter error.                 |
| 10200011 | The sort method cannot be bound. |
| 10200201 | Concurrent modification error.         |

**示例：**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([1, 3, 5, 4, 2]);
array.sort(); // Uint32Array [1, 2, 3, 4, 5]
array.sort((a: number, b: number) => a - b); // Uint32Array [1, 2, 3, 4, 5]
array.sort((a: number, b: number) => b - a); // Uint32Array [5, 4, 3, 2, 1]
```

## subarray
subarray(begin?: number, end?: number): Uint32Array

从指定的位置截取数组，返回一个新的、基于相同ArkTS ArrayBuffer的ArkTS Uint32Array对象。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型   | 必填 | 说明                                                |
| ------ | ------ | ---- | ------------------------------------------------- |
| begin  | number | 否   | 开始索引，如果`begin < 0`，则会从`begin + Uint32Array.length`位置开始。默认值为0。 |
| end    | number | 否   | 结束索引（不包括该元素），如果`end < 0`，则会到`end + Uint32Array.length`位置结束。默认为ArkTS Uint32Array的长度。 |

**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
| Uint32Array | 新的ArkTS Uint32Array对象。|

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID |            错误信息                               |
| -------- | -------------------------------------------------|
| 401      | Parameter error.                                 |
| 10200011 | The subarray method cannot be bound.             |
| 10200201 | Concurrent modification error.               |

**示例：**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
let subArray: collections.Uint32Array = array.subarray(); // Uint32Array [1, 2, 3, 4, 5]
subArray.set([10, 20, 30]); // Uint32Array [10, 20, 30, 4, 5]
```

## at
at(index: number): number | undefined

返回指定下标的元素，如果不存在，则返回undefined。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**
| 参数名 | 类型   | 必填 | 说明                                                         |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| index  | number | 是   | 要返回的Array元素的索引（从零开始），取值为整数。如果`index < 0`，则会访问`index + Uint32Array.length`位置的元素。|

**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
| number \| undefined| 指定下标的元素；如果不存在，则返回undefined。|

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID |                       错误信息                    |
| -------- | ------------------------------------------------ |
| 401      | Parameter error.                                 |
| 10200011 | The at method cannot be bound.                   |
| 10200201 | Concurrent modification error.               |

**示例：**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
console.info("element: " + array.at(2));  // element: 3
console.info("element: " + array.at(-1)); // element: 5
console.info("element: " + array.at(6));  // element: undefined
```

## includes
includes(searchElement: number, fromIndex?: number): boolean

判断ArkTS Uint32Array是否包含特定元素。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**
| 参数名 | 类型   | 必填 | 说明                                      |
| ------ | ------ | ---- | --------------------------------------- |
| searchElement  | number | 是   | 待搜索的元素。 |
| fromIndex  | number | 否  | 开始搜索的索引，如果`fromIndex < 0`，则会从`fromIndex + Uint32Array.length`位置开始。默认值为0。|

**返回值：**

| 类型    | 说明                                                        |
| ------- | ---------------------------------------------------------- |
| boolean | 如果ArkTS Uint32Array包含指定的元素，则返回true；否则返回false。|


**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                          |
| -------- | ------------------------------------------------- |
| 401      | Parameter error.                     |
| 10200011 | The includes method cannot be bound. |
| 10200201 | Concurrent modification error. |

**示例：**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3]);
console.info("includes: " + array.includes(2));    // includes: true
console.info("includes: " + array.includes(4));    // includes: false
console.info("includes: " + array.includes(3, 3)); // includes: false
```

## entries
entries(): IterableIterator\<[number, number]>

返回一个新的迭代器对象，该对象包含ArkTS Uint32Array中每个元素的键值对。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
| IterableIterator\<[number, number]>| 新的迭代器对象。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                          |
| -------- | ------------------------------------------------- |
| 10200011 | The entries method cannot be bound. |
| 10200201 | Concurrent modification error. |

**示例：**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([11, 22, 33]);
let iterator: IterableIterator<[number, number]> = array.entries();
console.info("value: " + iterator.next().value); // value: 0,11
console.info("value: " + iterator.next().value); // value: 1,22
console.info("value: " + iterator.next().value); // value: 2,33
```

## keys
keys(): IterableIterator\<number>

返回一个新的迭代器对象，该对象包含ArkTS Uint32Array中每个元素的键（下标）。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
| IterableIterator\<number> | 新的迭代器对象。|

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                          |
| -------- | ------------------------------------------------- |
| 10200011 | The keys method cannot be bound. |
| 10200201 | Concurrent modification error. |

**示例：**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
let iterator: IterableIterator<number> = array.keys();
for (const key of iterator) {
  console.info("" + key); // 依次输出 0,1,2,3,4
}
```

## values
values(): IterableIterator\<number>

返回一个新的迭代器对象，该对象包含ArkTS Uint32Array中每个元素的值。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
| IterableIterator\<number> | 新的迭代器对象。|

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                          |
| -------- | ------------------------------------------------- |
| 10200011 | The values method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**示例：**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
let iterator: IterableIterator<number> = array.values();
for (const value of iterator) {
  console.info("" + value); // 依次输出 1,2,3,4,5
}
```

## [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;number&gt;

返回一个迭代器，迭代器的每一项都是一个 JavaScript 对象，并返回该对象。

> **说明：**
>
> 本接口不支持在.ets文件中使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型                      | 说明             |
| ------------------------- | ---------------- |
| IterableIterator&lt;T&gt; | 返回一个迭代器。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 10200011 | The Symbol.iterator method cannot be bound. |

**示例：**

```ts
let uint32Array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5, 6]);

for (let item of uint32Array) {
  console.info(`value : ${item}`);
}
```

## [index: number]

&#91;index: number&#93;: number

返回Uint32Array指定索引位置的元素。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

| 参数名    | 类型   | 必填 | 说明                     |
| ----- | ------ | ---- | -------------------------- |
| index | number | 是   | 所需代码单元的从零开始的索引。|

**返回值：**

| 类型   | 说明                 |
| ----- | ---------------------|
| number | 返回number数据类型。 |

**示例：**

```ts
let uint32Array = collections.Uint32Array.from([1, 2, 4]);
console.info("Element at index 1: ", uint32Array[1]);
```
