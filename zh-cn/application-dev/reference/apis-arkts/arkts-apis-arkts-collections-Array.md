# Class (Array)
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

一种线性数据结构，底层基于数组实现，可以在ArkTS上并发实例间传递。

当需要在ArkTS上并发实例间传递Array时，可以通过传递Array引用提升传递性能。

文档中存在泛型的使用，涉及以下泛型标记符：

- T：Type，支持[Sendable支持的数据类型](../../arkts-utils/arkts-sendable.md#sendable支持的数据类型)。

**装饰器类型：**\@Sendable

## 导入模块

```ts
import { collections } from '@kit.ArkTS';
```

## 属性

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

| 名称   | 类型   | 只读 | 可选 | 说明              |
| ------ | ------ | ---- | ---- | ----------------- |
| length | number | 是   | 否   | Array的元素个数。 |


## constructor

**构造函数**

constructor()

创建一个ArkTS Array的构造函数。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                            |
| -------- | --------------------------------------------------- |
| 10200012 | The Array's constructor cannot be directly invoked. |

**示例：**

```ts
let array = new collections.Array<number>();
```

## constructor

constructor(first: T, ...left: T[])

ArkTS Array的构造函数，通过开发者提供的元素进行初始化。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明                            |
| ------ | ---- | ---- | ------------------------------- |
| first  | T    | 是   | 初始化ArkTS Array的第一个元素。 |
| left   | T[]  | 否   | 初始化ArkTS Array的剩余元素。   |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                            |
| -------- | --------------------------------------------------- |
| 401      | Parameter error.                                    |
| 10200012 | The Array's constructor cannot be directly invoked. |

**示例：**

```ts
let array = new collections.Array<number>(1, 2, 3, 4);
```
## constructor

constructor(...items: T[])

ArkTS Array的构造函数，通过开发者提供的元素进行初始化。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明                            |
| ------ | ---- | ---- | ------------------------------- |
| items  | T[]  | 否   | 初始化ArkTS Array的元素。       |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                            |
| -------- | --------------------------------------------------- |
| 401      | Parameter error.                                    |
| 10200012 | The Array's constructor cannot be directly invoked. |

**示例：**

```ts
let arrayPara  = [1,2,3];
let array = new collections.Array<number>(...arrayPara);
```

## create

static create\<T>(arrayLength: number, initialValue: T): Array\<T>

生成一个固定长度的Array，其中，每个元素的初始值为initialValue。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名    | 类型          | 必填 | 说明                            |
| --------- | ------------- | ---- | ------------------------------- |
| arrayLength | number | 是   | 用于构造ArkTS Array的长度。 |
| initialValue | T | 是   | 用于填充ArkTS Array的值。 |

**返回值：**

| 类型      | 说明                    |
| --------- | ----------------------- |
| Array\<T> | 新创建的ArkTS Array实例。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 401      | Parameter error.                   |

**示例：**

```ts
let array = collections.Array.create<number>(3, 10); // [10, 10, 10]
```

## from

static from\<T>(arrayLike: ArrayLike\<T>): Array\<T>

从一个实现了ArrayLike接口的对象创建一个新的ArkTS Array。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名    | 类型          | 必填 | 说明                            |
| --------- | ------------- | ---- | ------------------------------- |
| arrayLike | ArrayLike\<T> | 是   | 用于构造ArkTS Array的对象。 |

**返回值：**

| 类型      | 说明                    |
| --------- | ----------------------- |
| Array\<T> | 新创建的ArkTS Array实例。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 401      | Parameter error.                 |

**示例：**

```ts
// 正例
let array : Array<string> = ['str1', 'str2', 'str3']; // 原生Array<T>，T是Sendable数据类型。
let sendableArray = collections.Array.from<string>(array); // 返回Sendable Array<T>
```

<!--code_no_check-->
```ts
// 反例
let array : Array<Array<string>> = [['str1', 'str2', 'str3'], ['str4', 'str5', 'str6'], ['str7', 'str8', 'str9']]; // 原生Array<T>，T是非Sendable数据类型。
let sendableArray = collections.Array.from<Array<string>>(array); // 打印异常信息：Parameter error.Only accept sendable value
```

## from

static from\<T>(iterable: Iterable\<T>): Array\<T>

从一个实现了Iterable接口的对象创建一个新的ArkTS Array。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名    | 类型          | 必填 | 说明                            |
| --------- | ------------- | ---- | ------------------------------- |
| iterable | Iterable\<T> | 是   | 用于构造ArkTS Array的对象。 |

**返回值：**

| 类型      | 说明                    |
| --------- | ----------------------- |
| Array\<T> | 新创建的ArkTS Array实例。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 401 | Parameter error: Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
// 正例
const mapper = new Map([
  ['1', 'a'],
  ['2', 'b'],
]);
let newArray: collections.Array<string> = collections.Array.from(mapper.values());
console.info(newArray.toString()); // 预期输出： a,b
```

## from<sup>18+</sup>

static from\<T>(arrayLike: ArrayLike\<T> | Iterable\<T>, mapFn: ArrayFromMapFn\<T, T>): Array\<T>

从一个实现了ArrayLike接口的对象创建一个新的ArkTS Array，并且使用自定义函数处理每个数组元素。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名    | 类型          | 必填 | 说明                            |
| --------- | ------------- | ---- | ------------------------------- |
| arrayLike | ArrayLike\<T> \| Iterable\<T> | 是   | 用于构造ArkTS Array的对象。 |
| mapFn | [ArrayFromMapFn](arkts-apis-arkts-collections-Types.md#arrayfrommapfn18)\<T,T> | 是   | 调用数组每个元素的函数。 |

**返回值：**

| 类型      | 说明                    |
| --------- | ----------------------- |
| Array\<T> | 新创建的ArkTS Array实例。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 401 | Parameter error: Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
let array : Array<number> = [1, 2, 3]; // 原生Array<T>，T是Sendable数据类型。
let newArray = collections.Array.from<number>(array, (value, index) => value + index); // 返回新的 Array<T>
console.info(newArray.toString()); // 预期输出： 1, 3, 5
```

## from<sup>18+</sup>

static from\<U, T>(arrayLike: ArrayLike\<U> | Iterable\<U>, mapFn: ArrayFromMapFn\<U, T>): Array\<T>

从一个实现了ArrayLike接口的对象创建一个新的ArkTS Array，并且使用自定义函数处理每个数组元素，ArrayLike接口对象的元素类型可以和数组元素的类型不一样。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名    | 类型          | 必填 | 说明                            |
| --------- | ------------- | ---- | ------------------------------- |
| arrayLike | ArrayLike\<U> \| Iterable\<U> | 是   | 用于构造ArkTS Array的对象。 |
| mapFn | [ArrayFromMapFn](arkts-apis-arkts-collections-Types.md#arrayfrommapfn18)\<U, T> | 是   | 调用数组每个元素的函数。 |

**返回值：**

| 类型      | 说明                    |
| --------- | ----------------------- |
| Array\<T> | 新创建的ArkTS Array实例。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 401 | Parameter error: Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
let array : Array<number> = [1, 2, 3]; // 原生Array<T>
let newArray = collections.Array.from<number, string>(array, (value, index) => value + "." + index); // 返回新的 Array<T>
console.info(newArray.toString()); // 预期输出： 1.0, 2.1, 3.2
```

## isArray<sup>18+</sup>

static isArray(value: Object | undefined | null): boolean

检查传入的参数是否是一个ArkTS Array。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名    | 类型          | 必填 | 说明                            |
| --------- | ------------- | ---- | ------------------------------- |
| value | Object \| undefined \| null | 是   | 需要被检查的值。 |

**返回值：**

| 类型      | 说明                    |
| --------- | ----------------------- |
| boolean | 假如给定对象是ArkTS Array数组，返回true，否则返回false。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 401 | Parameter error: Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
let arr: collections.Array<string> = new collections.Array('a', 'b', 'c', 'd');
let result: boolean = collections.Array.isArray(arr);
console.info(result + ''); // 预期输出： true
```

## of<sup>18+</sup>

static of\<T>(...items: T\[]): Array\<T>

通过可变数量的参数创建一个新的ArkTS Array。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名    | 类型          | 必填 | 说明                            |
| --------- | ------------- | ---- | ------------------------------- |
| items | T[] | 否   | 用于创建数组的元素集合，参数个数可以是0个、1个或者多个。 |

**返回值：**

| 类型      | 说明                    |
| --------- | ----------------------- |
| Array\<T> | 新的ArkTS Array实例。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 401 | Parameter error: Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
let arr: collections.Array<string> = collections.Array.of('a', 'b', 'c', 'd');
console.info(arr.toString()); // 预期输出： a, b, c, d
```

## copyWithin<sup>18+</sup>
copyWithin(target: number, start: number, end?: number): Array\<T>

从ArkTS Array指定范围内的元素依次拷贝到目标位置。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名  | 类型   | 必填 | 说明                                                         |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| target | number | 是 | 目标起始位置的下标。 |
| start | number | 是 | 源起始位置下标，如果`start < 0`，则会从`start + array.length`位置开始。 |
| end | number | 否 | 源终止位置下标，如果`end < 0`，则会从`end + array.length`位置终止。默认为ArkTS Array的长度。|

**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
| Array\<T> | 修改后的Array。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                          |
| -------- | ------------------------------------------------ |
| 401 | Parameter error: Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| 10200011 | The copyWithin method cannot be bound.           |
| 10200201 | Concurrent modification error.               |

**示例：**

```ts
let array: collections.Array<number> = collections.Array.from([1, 2, 3, 4, 5, 6, 7, 8]);
let copied: collections.Array<number> = array.copyWithin(3, 1, 3);
console.info(copied.toString()); // 预期输出： 1, 2, 3, 2, 3, 6, 7, 8
```

## lastIndexOf<sup>18+</sup>

lastIndexOf(searchElement: T, fromIndex?: number): number

返回ArkTS Array实例中最后一次出现searchElement的索引，如果对象不包含，则为-1。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名           | 类型     | 必填  | 说明                                                                                |
| ------------- | ------ | --- | --------------------------------------------------------------------------------- |
| searchElement | T | 是   | 待索引的值。                                                                            |
| fromIndex     | number | 否   | 搜索的起始下标。默认值为0。如果下标大于等于ArkTS Array的长度，则返回-1。如果提供的下标值是负数，则从数组末尾开始倒数计数：使用 fromIndex + array.length 的值。 |

**返回值：**

| 类型     | 说明                      |
| ------ | ----------------------- |
| number | 数组中元素的最后一个索引；没有找到，则返回-1。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID    | 错误信息                                    |
| -------- | --------------------------------------- |
| 10200011 | The lastIndexOf method cannot be bound. |
| 10200201 | Concurrent modification error.      |

**示例：**

```ts
let array: collections.Array<number> = collections.Array.from([3, 5, 9]);
console.info(array.lastIndexOf(3) + ''); // 预期输出： 0
console.info(array.lastIndexOf(7) + ''); // 预期输出： -1
console.info(array.lastIndexOf(9, 2) + ''); // 预期输出： 2
console.info(array.lastIndexOf(9, -2) + ''); // 预期输出： -1
```

## some<sup>18+</sup>
some(predicate: ArrayPredicateFn\<T, Array\<T>>): boolean

测试ArkTS Array是否存在满足指定条件的元素。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名  | 类型   | 必填 | 说明                                                  |
| ------- | ------ | ---- | ---------------------------------------------------- |
| predicate | [ArrayPredicateFn](arkts-apis-arkts-collections-Types.md#arraypredicatefn18)\<T, Array\<T>> | 是 | 用于测试的断言函数。|

**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
| boolean | 如果存在元素满足指定条件返回true，否则返回false。|

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                            |
| -------- | ---------------------------------- |
| 10200011 | The some method cannot be bound.   |
| 10200201 | Concurrent modification error. |

**示例：**

```ts
let newArray: collections.Array<number> = collections.Array.from([-10, 20, -30, 40, -50]);
console.info(newArray.some((element: number) => element < 0) + ''); // 预期输出： true
```

## reduceRight<sup>18+</sup>

reduceRight(callbackFn: ArrayReduceCallback\<T, T, Array\<T>>): T

对Array中的每个元素按照从右到左顺序执行回调函数，将其结果作为累加值，并返回最终的结果。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名        | 类型                                                                               | 必填  | 说明                                         |
| ---------- | -------------------------------------------------------------------------------- | --- | ------------------------------------------ |
| callbackFn | [ArrayReduceCallback](arkts-apis-arkts-collections-Types.md#arrayreducecallback18)\<T, T, Array\<T>> | 是   | 一个接受四个参数的函数，用于对每个元素执行操作，并将结果作为累加值传递给下一个元素。 |

**返回值：**

| 类型  | 说明            |
| --- | ------------- |
| T   | 回调函数执行后的最终结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID    | 错误信息                                    |
| -------- | --------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 10200011 | The reduceRight method cannot be bound. |
| 10200201 | Concurrent modification error.          |

**示例：**

```ts
let array = new collections.Array<number>(1, 2, 3, 4, 5);
let reducedValue = array.reduceRight((accumulator, value) => accumulator + value); // 累加所有元素
console.info(reducedValue + ''); // 预期输出： 15
```

## reduceRight<sup>18+</sup>

reduceRight\<U = T>(callbackFn: ArrayReduceCallback\<U, T, Array\<T>>, initialValue: U): U

与 [reduceRight](#reduceright18)方法类似，但它接受一个初始值作为第二个参数，用于在Array从右到左顺序遍历开始前初始化累加器。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名          | 类型                                                                                           | 必填  | 说明                                         |
| ------------ | -------------------------------------------------------------------------------------------- | --- | ------------------------------------------ |
| callbackFn   | [ArrayReduceCallback](arkts-apis-arkts-collections-Types.md#arrayreducecallback18)\<U, T, Array\<T>> | 是   | 一个接受四个参数的函数，用于对每个元素执行操作，并将结果作为累加值传递给下一个元素。 |
| initialValue | U                                                                                            | 是   | 用于初始化累加器的值。                                |

**返回值：**

| 类型  | 说明            |
| --- | ------------- |
| U   | 回调函数执行后的最终结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID    | 错误信息                                    |
| -------- | --------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 10200011 | The reduceRight method cannot be bound. |
| 10200201 | Concurrent modification error.          |

**示例：**

```ts
// 此处使用一个初始值为0的累加器，并将其与Array中的每个元素相加，最终返回累加后的总和
let array = new collections.Array<number>(1, 2, 3, 4, 5);
let reducedValue = array.reduceRight<number>((accumulator: number, value: number) => accumulator + value, 0); // 累加所有元素，初始值为0
console.info(reducedValue + ''); // 预期输出： 15
```

## pop

pop(): T | undefined

从ArkTS Array中移除并返回最后一个元素。如果Array为空，则返回undefined，且Array不发生变化。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型           | 说明                                                |
| -------------- | --------------------------------------------------- |
| T \| undefined | 从Array中移除的元素；如果Array为空，则返回undefined。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                        |
| -------- | ------------------------------- |
| 10200011 | The pop method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**示例：**

```ts
let array = new collections.Array<number>(1, 2, 3);
let lastElement = array.pop(); // 返回3，Array变为[1, 2]
```

## push

push(...items: T[]): number

在ArkTS Array的末尾添加元素，并返回新的Array长度。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明                               |
| ------ | ---- | ---- | ---------------------------------- |
| items  | T[]  | 否   | 要添加到Array末尾的元素。 |

**返回值：**

| 类型   | 说明               |
| ------ | ------------------ |
| number | 返回新Array的长度。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 401      | Parameter error.                 |
| 10200011 | The push method cannot be bound. |
| 10200201 | Concurrent modification error.   |

**示例：**

```ts
let array = new collections.Array<number>(1, 2, 3);
let length = array.push(4, 5); // 返回5，Array变为[1, 2, 3, 4, 5]
```

## join

join(separator?: string): string

将ArkTS Array的所有元素连接成一个字符串，元素之间可以用指定的分隔符分隔。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名    | 类型   | 必填 | 说明                                                 |
| --------- | ------ | ---- | ---------------------------------------------------- |
| separator | string | 否   | 用于分隔Array元素的字符串。如果省略，则使用逗号分隔。 |

**返回值：**

| 类型   | 说明                                                         |
| ------ | ------------------------------------------------------------ |
| string | 包含所有Array元素连接成的字符串。如果Array为空，则返回空字符串。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 401      | Parameter error.                 |
| 10200011 | The join method cannot be bound. |
| 10200201 | Concurrent modification error.   |

**示例：**

```ts
let array = new collections.Array<string>('a', 'b', 'c');
let joinedString = array.join('-'); // 返回 "a-b-c"
```

## shift

shift(): T | undefined

从ArkTS Array中移除并返回第一个元素。如果Array为空，则返回undefined，且Array不发生变化。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型           | 说明                                                |
| -------------- | --------------------------------------------------- |
| T \| undefined | 从Array中移除的元素；如果Array为空，则返回undefined。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                          |
| -------- | --------------------------------- |
| 10200011 | The shift method cannot be bound. |
| 10200201 | Concurrent modification error.    |

**示例：**

```ts
let array = new collections.Array<number>(1, 2, 3);
let firstElement = array.shift(); // 返回1，Array变为[2, 3]
```

## reverse<sup>18+</sup>

reverse(): Array\<T>

反转ArkTS Array数组中的元素，并返回同一数组的引用。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型    | 说明                 |
| ----- | ------------------ |
| Array\<T> | 反转后的ArkTS Array对象。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID    | 错误信息                                |
| -------- | ----------------------------------- |
| 10200011 | The reverse method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**示例：**

```ts
let array = new collections.Array<number>(1, 2, 3, 4, 5);
let reversed = array.reverse();
console.info(array.toString()); // 预期输出： 5, 4, 3, 2, 1
```

## unshift

unshift(...items: T[]): number

在ArkTS Array的首端插入元素，并返回新的Array长度。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明                     |
| ------ | ---- | ---- | ------------------------ |
| items  | T[]  | 否   | 要插入到Array首端的元素。 |

**返回值：**

| 类型   | 说明           |
| ------ | -------------- |
| number | 新Array的长度。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401      | Parameter error.                    |
| 10200011 | The unshift method cannot be bound. |
| 10200201 | Concurrent modification error.      |

**示例：**

```ts
let array = new collections.Array<number>(1, 2, 3);
let newLength = array.unshift(0); // 返回4，Array变为[0, 1, 2, 3]
```

## toString<sup>18+</sup>

toString(): string

ArkTS数组转换为字符串。

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
let array = new collections.Array<number>(1, 2, 3, 4, 5);
let stringArray = array.toString();
console.info(stringArray); // 预期输出：1,2,3,4,5
```

## slice

slice(start?: number, end?: number): Array\<T>

返回一个新的Array，该Array是原始ArkTS Array的切片。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**
| 参数名 | 类型   | 必填 | 说明                                                         |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| start  | number | 否   | 开始索引。如果`start < 0`，则会从`start + array.length`位置开始。默认值为0。   |
| end    | number | 否   | 结束索引（不包括该元素）。如果`end < 0`，则会到`end + array.length`位置结束。默认为原始ArkTS Array的长度。 |

**返回值：**

| 类型      | 说明                       |
| --------- | -------------------------- |
| Array\<T> | 包含原始Array切片的新Array。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                          |
| -------- | --------------------------------- |
| 401      | Parameter error.                  |
| 10200011 | The slice method cannot be bound. |
| 10200201 | Concurrent modification error.    |

**示例：**

```ts
let array = new collections.Array<number>(1, 2, 3, 4, 5);
let slicedArray = array.slice(1, 3); // 返回[2, 3]，Array保持不变
```

## sort

sort(compareFn?: (a: T, b: T) => number): Array\<T>

对ArkTS Array进行排序，并返回排序后的Array。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名    | 类型                   | 必填 | 说明                                       |
| --------- | ---------------------- | ---- | ------------------------------------------ |
| compareFn | (a: T, b: T) => number | 否   | 用于确定元素顺序的函数。默认使用升序排序。 |

**返回值：**

| 类型      | 说明           |
| --------- | -------------- |
| Array\<T> | 排序后的Array。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 401      | Parameter error.                 |
| 10200011 | The sort method cannot be bound. |
| 10200201 | Concurrent modification error.   |

**示例：**

```ts
let array = new collections.Array<number>(1, 3, 5, 4, 2);
array.sort((a: number, b: number) => a - b); // [1, 2, 3, 4, 5]
array.sort((a: number, b: number) => b - a); // [5, 4, 3, 2, 1]
```

## indexOf

indexOf(searchElement: T, fromIndex?: number): number

返回在ArkTS Array中搜索元素首次出现的索引，如果不存在则返回-1。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名        | 类型   | 必填 | 说明                        |
| ------------- | ------ | ---- | --------------------------- |
| searchElement | T      | 是   | 要搜索的值。                |
| fromIndex     | number | 否   | 开始搜索的索引，从0开始，默认值为0。 |

**返回值：**

| 类型   | 说明                                           |
| ------ | ---------------------------------------------- |
| number | 搜索元素首次出现的索引；如果不存在，则返回-1。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401      | Parameter error.                    |
| 10200011 | The indexOf method cannot be bound. |
| 10200201 | Concurrent modification error.      |

**示例：**

```ts
let array = new collections.Array<string>('a', 'b', 'c');
let index = array.indexOf('b'); // 返回1，因为'b'在索引1的位置
```

## forEach

forEach(callbackFn: (value: T, index: number, array: Array\<T>) => void): void

对Array中的每个元素执行提供的回调函数。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名     | 类型                                                | 必填 | 说明                           |
| ---------- | --------------------------------------------------- | ---- | ------------------------------ |
| callbackFn | (value: T, index: number, array: Array\<T>) => void | 是   | 用于对每个元素执行的回调函数。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401      | Parameter error.                    |
| 10200011 | The forEach method cannot be bound. |
| 10200201 | Concurrent modification error.      |

**示例：**

```ts
let array = new collections.Array<string>('a', 'b', 'c');
array.forEach((value, index, array) => {
  console.info(`Element ${value} at index ${index}`);
});
```

## map

map\<U>(callbackFn: (value: T, index: number, array: Array\<T>) => U): Array\<U>

对Array中的每个元素执行提供的回调函数，并返回一个新的Array，该Array包含回调函数的结果。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名     | 类型                                             | 必填 | 说明                           |
| ---------- | ------------------------------------------------ | ---- | ------------------------------ |
| callbackFn | (value: T, index: number, array: Array\<T>) => U | 是   | 用于对每个元素执行的回调函数。 |

**返回值：**

| 类型      | 说明                       |
| --------- | -------------------------- |
| Array\<U> | 包含回调函数结果的新Array。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                        |
| -------- | ------------------------------- |
| 401      | Parameter error.                |
| 10200011 | The map method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**示例：**

```ts
// 此处将原始Array中的每个字符串元素转换为大写形式，并返回一个新Array，其中包含转换后的字符串
let array = new collections.Array<string>('a', 'b', 'c');
let mappedArray = array.map((value, index, array) => {
  return value.toUpperCase(); // 将每个字符串元素转换为大写
});
console.info("" + mappedArray); // 输出: A, B, C
```

## filter

filter(predicate: (value: T, index: number, array: Array\<T>) => boolean): Array\<T>

返回一个新Array，其中包含通过指定回调函数测试的所有元素。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名    | 类型                                                   | 必填 | 说明                                                         |
| --------- | ------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| predicate | (value: T, index: number, array: Array\<T>) => boolean | 是   | 一个接受三个参数的函数，用于测试每个元素是否应该包含在新Array中。当返回值为true时表示当前元素通过测试，需被保留在新数组中。为false时表示当前元素未通过测试，需被排除在新数组外。 |

**返回值：**

| 类型      | 说明                         |
| --------- | ---------------------------- |
| Array\<T> | 包含通过测试的元素的新Array。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                           |
| -------- | ---------------------------------- |
| 401      | Parameter error.                   |
| 10200011 | The filter method cannot be bound. |
| 10200201 | Concurrent modification error.     |

**示例：**

```ts
let array = new collections.Array<number>(1, 2, 3, 4, 5);
let filteredArray = array.filter((value : number) => value % 2 === 0); // 返回[2, 4]，只包含偶数
```

## reduce

reduce(callbackFn: (previousValue: T, currentValue: T, currentIndex: number, array: Array\<T>) => T): T

对Array中的每个元素执行回调函数，将其结果作为累加值，并返回最终的结果。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名     | 类型                                                         | 必填 | 说明                                                         |
| ---------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callbackFn | (previousValue: T, currentValue: T, currentIndex: number, array: Array\<T>) => T | 是   | 一个接受四个参数的函数，用于对每个元素执行操作，并将结果作为累加值传递给下一个元素。 |

**返回值：**

| 类型 | 说明                       |
| ---- | -------------------------- |
| T    | 回调函数执行后的最终结果。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                           |
| -------- | ---------------------------------- |
| 401      | Parameter error.                   |
| 10200011 | The reduce method cannot be bound. |
| 10200201 | Concurrent modification error.     |

**示例：**

```ts
let array = new collections.Array<number>(1, 2, 3, 4, 5);
let reducedValue = array.reduce((accumulator, value) => accumulator + value); // 返回15，累加所有元素
```

## reduce

reduce\<U>(callbackFn: (previousValue: U, currentValue: T, currentIndex: number, array: Array\<T>) => U, initialValue: U): U

与 reduce方法类似，但它接受一个初始值作为第二个参数，用于在Array遍历开始前初始化累加器。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名       | 类型                                                         | 必填 | 说明                                                         |
| ------------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callbackFn   | (previousValue: U, currentValue: T, currentIndex: number, array: Array\<T>) => U | 是   | 一个接受四个参数的函数，用于对每个元素执行操作，并将结果作为累加值传递给下一个元素。 |
| initialValue | U                                                            | 是   | 用于初始化累加器的值。                                       |

**返回值：**

| 类型 | 说明                       |
| ---- | -------------------------- |
| U    | 回调函数执行后的最终结果。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                           |
| -------- | ---------------------------------- |
| 401      | Parameter error.                   |
| 10200011 | The reduce method cannot be bound. |
| 10200201 | Concurrent modification error.     |

**示例：**

```ts
// 此处使用一个初始值为0的累加器，并将其与Array中的每个元素相加，最终返回累加后的总和
let array = new collections.Array(1, 2, 3, 4, 5);
let reducedValue = array.reduce<number>((accumulator: number, value: number) => accumulator + value, 0); // 返回15，累加所有元素，初始值为0
```

## at

at(index: number): T | undefined

返回Array中指定索引位置的元素。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型   | 必填 | 说明                                                         |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| index  | number | 是   | 要返回的Array元素的索引（从零开始），取值为整数。负数索引从Array末尾开始计数，如果`index < 0`，则会访问`index + array.length`位置的元素。 |


**返回值：**

| 类型           | 说明                                                         |
| -------------- | ------------------------------------------------------------ |
| T \| undefined | 返回指定索引处的元素；如果索引超出范围或无效，则返回undefined。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                       |
| -------- | ------------------------------ |
| 401      | Parameter error.               |
| 10200011 | The at method cannot be bound. |
| 10200201 | Concurrent modification error. |

**示例：**

```ts
let array = new collections.Array<number>(1, 2, 3, 4, 5);
let elementAtIndex = array.at(2); // 返回3，因为索引是从0开始的
```

## entries

entries(): IterableIterator<[number, T]>

返回一个新的可迭代对象，该对象包含Array中每个元素的键值对。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型                          | 说明                                       |
| ----------------------------- | ------------------------------------------ |
| IterableIterator<[number, T]> | 包含Array中每个元素的键值对的迭代器。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 10200011 | The entries method cannot be bound. |
| 10200201 | Concurrent modification error.      |

**示例：**

```ts
let array = new collections.Array<number>(1, 2, 3, 4, 5);
let iterator = array.entries();
console.info(iterator.next().value); // 输出：[0, 1]，第一个元素的键值对
```

## keys

keys(): IterableIterator\<number>

返回一个新的可迭代对象，该对象包含Array中每个元素的索引。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型                      | 说明                                   |
| ------------------------- | -------------------------------------- |
| IterableIterator\<number> | 包含Array中每个元素的索引的可迭代迭代器。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 10200011 | The keys method cannot be bound. |
| 10200201 | Concurrent modification error.   |

**示例：**

```ts
let array = new collections.Array<number>(1, 2, 3, 4, 5);
let iterator = array.keys();
for (const key of iterator) {
  console.info("" + key); // 依次输出 0,1,2,3,4
}
```

## values

values(): IterableIterator\<T>

返回一个新的可迭代对象，该对象包含Array中每个元素的值。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型                 | 说明                                   |
| -------------------- | -------------------------------------- |
| IterableIterator\<T> | 包含Array中每个元素的值的可迭代迭代器。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                           |
| -------- | ---------------------------------- |
| 10200011 | The values method cannot be bound. |
| 10200201 | Concurrent modification error.     |

**示例：**

```ts
let array = new collections.Array<number>(1, 2, 3, 4, 5);
let iterator = array.values();
for(const value of iterator) {
  console.info("" + value); // 依次输出 1,2,3,4,5
}
```

## find

find(predicate: (value: T, index: number, obj: Array\<T>) => boolean): T | undefined

返回Array中第一个满足指定测试函数的元素的值，如果所有元素都不满足，则返回undefined。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名    | 类型                                                 | 必填 | 说明                                                   |
| --------- | ---------------------------------------------------- | ---- | ------------------------------------------------------ |
| predicate | (value: T, index: number, obj: Array\<T>) => boolean | 是   | 一个接受三个参数的函数，用于测试每个元素是否满足条件。当返回值为true时表示元素满足条件，会立即停止遍历，并将该元素作为结果返回。为false时表示元素不满足条件，会继续检查下一个元素，直到找到符合条件的元素或遍历完整个数组。 |

**返回值：**

| 类型           | 说明                                                         |
| -------------- | ------------------------------------------------------------ |
| T \| undefined | 第一个满足条件的元素的值；如果所有元素都不满足条件，则返回undefined。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 401      | Parameter error.                 |
| 10200011 | The find method cannot be bound. |
| 10200201 | Concurrent modification error.   |

**示例：**

```ts
let array = new collections.Array<number>(1, 2, 3, 4, 5);
let foundValue = array.find((value: number) => value % 2 === 0); // 返回2，第一个偶数元素
```

## includes

includes(searchElement: T, fromIndex?: number): boolean

判断Array是否包含指定的元素，并返回一个布尔值。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名        | 类型   | 必填 | 说明                        |
| ------------- | ------ | ---- | --------------------------- |
| searchElement | T      | 是   | 要搜索的元素。              |
| fromIndex     | number | 否   | 开始搜索的索引。默认值为0。 |

**返回值：**

| 类型    | 说明                                                |
| ------- | --------------------------------------------------- |
| boolean | 如果Array包含指定的元素，则返回true；否则返回false。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                             |
| -------- | ------------------------------------ |
| 401      | Parameter error.                     |
| 10200011 | The includes method cannot be bound. |
| 10200201 | Concurrent modification error.       |

**示例：**

```ts
let array = new collections.Array<number>(1, 2, 3, 4, 5);
let includesResult = array.includes(3); // 返回true，因为Array中包含3
```

## findIndex

findIndex(predicate: (value: T, index: number, obj: Array\<T>) => boolean): number

返回Array中第一个满足指定测试函数的元素的索引，如果所有元素都不满足，则返回-1。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名    | 类型                                                 | 必填 | 说明                                                   |
| --------- | ---------------------------------------------------- | ---- | ------------------------------------------------------ |
| predicate | (value: T, index: number, obj: Array\<T>) => boolean | 是   | 一个接受三个参数的函数，用于测试每个元素是否满足条件。当返回值为true时表示当前元素满足条件，会立即停止遍历，并返回该元素的索引。为false时表示当前元素不满足条件，会继续检查下一个元素，直到找到符合条件的元素或遍历完整个数组。 |

**返回值：**

| 类型   | 说明                                                         |
| ------ | ------------------------------------------------------------ |
| number | 第一个满足条件的元素的索引；如果所有元素都不满足条件，则返回-1。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                              |
| -------- | ------------------------------------- |
| 401      | Parameter error.                      |
| 10200011 | The findIndex method cannot be bound. |
| 10200201 | Concurrent modification error.        |

**示例：**

```ts
let array = new collections.Array<number>(1, 2, 3, 4, 5);
let foundIndex = array.findIndex((value: number) => value % 2 === 0); // 返回1，因为2是第一个偶数元素
```

## fill

fill(value: T, start?: number, end?: number): Array\<T>

使用指定的值填充Array中指定范围的所有元素。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型   | 必填 | 说明                                                   |
| ------ | ------ | ---- | ------------------------------------------------------ |
| value  | T      | 是   | 要填充的值。                                           |
| start  | number | 否   | 开始填充的索引。默认值为0。                            |
| end    | number | 否   | 结束填充的索引（不包括该元素）。如果省略，则填充到Array的最后一个元素。 |

**返回值：**

| 类型      | 说明           |
| --------- | -------------- |
| Array\<T> | 填充后的Array。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 401      | Parameter error.                 |
| 10200011 | The fill method cannot be bound. |
| 10200201 | Concurrent modification error.   |

**示例：**

```ts
let array = new collections.Array(1, 2, 3, 4, 5);
array.fill(0, 1, 3); // 返回[1, 0, 0, 4, 5]，因为1到3的索引范围内的元素被替换为0
```

## shrinkTo

shrinkTo(arrayLength: number): void

使Array收缩到指定长度。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型   | 必填 | 说明                                                   |
| ------ | ------ | ---- | ------------------------------------------------------ |
| arrayLength  | number  | 是   | Array的新长度。如果arrayLength >= array.length，则Array不变。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 401      | Parameter error.                 |
| 10200011 | The shrinkTo method cannot be bound. |
| 10200201 | Concurrent modification error.   |

**示例：**

```ts
let array1 = new collections.Array(1, 2, 3, 4, 5);
array1.shrinkTo(1); // array内容变为：[1]

let array2 = new collections.Array(1, 2, 3, 4, 5);
array2.shrinkTo(10); // array内容不变
```

## extendTo

extendTo(arrayLength: number, initialValue: T): void

使Array扩展到指定长度，扩展的部分使用给定值填充。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型   | 必填 | 说明                                                   |
| ------ | ------ | ---- | ------------------------------------------------------ |
| arrayLength  | number  | 是   | Array的新长度。如果arrayLength <= array.length，则Array不变。 |
| initialValue  | T  | 是   | 扩展的部分的填充值。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 401      | Parameter error.                 |
| 10200011 | The extendTo method cannot be bound. |
| 10200201 | Concurrent modification error.   |

**示例：**

```ts
let array1 = new collections.Array(1, 2, 3);
array1.extendTo(5, 10); // array内容变为：[1, 2, 3, 10, 10]

let array2 = new collections.Array(1, 2, 3);
array2.extendTo(1, 10); // array内容不变
```

## concat

concat(...items: ConcatArray\<T>[]): Array\<T>

拼接两个或多个数组。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明                               |
| ------ | ---- | ---- | ---------------------------------- |
| items  | ConcatArray\<T>[]  | 否   | 拼接两个或多个数组。 |

**返回值：**

| 类型 | 说明                               |
| ---- | ---------------------------------- |
| Array\<T>  | 拼接后的数组。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                         |
| ------- | -------- |
| 401 |  Parameter error. Not a valid array. |
| 10200011 | The concat method cannot be bound. |
| 10200201 | Concurrent modification error.   |

**示例：**

```ts
let array = new collections.Array(1, 2, 3);
let array1 = new collections.Array(4, 5, 6);
let array2 = new collections.Array(7, 8, 9);

let concatArray = array.concat(array1, array2); // concatArray的内容为：[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

## splice

splice(start: number): Array\<T>

删除Array中指定位置的元素。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型  | 必填 | 说明                                                                |
| ----- | ------ | -- | ------------------------------------------------------------------- |
| start | number | 是 | 开始索引。如果`-array.length =< start < 0`，从`start + array.length`开始，如果`start < -array.length`，则从0开始。 |

**返回值：**

| 类型      | 说明                   |
| --------- | --------------------- |
| Array\<T> | 返回一个新的包含被删除元素的Array对象。如果没有元素被删除，返回一个空的Array对象。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                            |
| -------- | ---------------------------------- |
| 401      | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| 10200011 | The splice method cannot be bound. |
| 10200201 | Concurrent modification error.     |

**示例：**

```ts
let array = new collections.Array<number>(1, 2, 3, 4, 5);
let removeArray = array.splice(2); // array内容变为[1, 2]，返回[3, 4, 5]
```

## every<sup>18+</sup>

every(predicate: ArrayPredicateFn\<T, Array\<T>>): boolean

测试ArkTS Array中的所有元素是否满足指定条件。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**
| 参数名  | 类型   | 必填 | 说明                                                    |
| ------- | ------ | ---- | ----------------------------------------------------- |
| predicate | [ArrayPredicateFn](arkts-apis-arkts-collections-Types.md#arraypredicatefn18)\<T, Array\<T>> | 是 | 用于测试的断言函数。|

**返回值：**

| 类型         | 说明      |
| ------------ | --------- |
| boolean | 如果所有元素都满足指定条件则返回true，否则返回false。|

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                          |
| -------- | ------------------------------------------------- |
| 10200011 | The every method cannot be bound. |
| 10200201 | Concurrent modification error. |

**示例：**

```ts
let newArray: collections.Array<number> = collections.Array.from([-10, 20, -30, 40, -50]);
console.info(newArray.every((element: number) => element > 0) + ''); // 预期输出：false
```

## toLocaleString<sup>18+</sup>

toLocaleString(): string

根据当前应用的系统地区获取符合当前文化习惯的字符串表示形式，让每个元素调用自己的toLocaleString方法转换为字符串，然后使用逗号将每个元素的结果字符串按照顺序拼接成字符串。

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
let array = new collections.Array<number | string>(1000, 'Test', 53621);
let stringArray = array.toLocaleString();
console.info(stringArray); // 预期输出：1,000,Test,53,621
```

## splice

splice(start: number, deleteCount: number, ...items: T[]): Array\<T>

删除Array中指定位置的元素，需要时在Array的指定位置插入新元素。

**原子化服务API**：从API version 12 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名       | 类型   | 必填 | 说明                                                                |
| ----------- | ------ | --  | ------------------------------------------------------------------- |
| start       | number | 是  | 开始索引。如果`-array.length =< start < 0`，从`start + array.length`开始，如果`start < -array.length`，则从0开始。 |
| deleteCount | number | 是  | 删除元素的个数。                                                      |
| items       | T[]    | 否  | 从`start`位置开始插入的新元素。如果省略，仅删除Array内的指定元素。        |

**返回值：**

| 类型      | 说明                                  |
| --------- | ------------------------------------ |
| Array\<T> | 返回一个新的包含被删除元素的Array对象。如果没有元素被删除，返回一个空的Array对象。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                            |
| -------- | ---------------------------------- |
| 401      | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| 10200011 | The splice method cannot be bound. |
| 10200201 | Concurrent modification error.     |

**示例：**

```ts
// 例1：
let array = new collections.Array<number>(1, 2, 3, 4, 5);
let removeArray = array.splice(2, 2); // array内容变为[1, 2, 5]，返回[3, 4]
```

```ts
// 例2：
let array = new collections.Array<number>(1, 2, 3, 4, 5);
let removeArray = array.splice(2, 2, 6, 7, 8); // array内容变为[1, 2, 6, 7, 8, 5]，返回[3, 4]
```

## [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;T&gt;

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
let array= new collections.Array<number>(1, 2, 3, 4);

for (let item of array) {
  console.info(`value : ${item}`);
}
```

## [index: number]

&#91;index: number&#93;: T

返回Array指定索引位置的元素。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

| 参数名    | 类型   | 必填 | 说明                                                            |
| ----- | ------ | ---- | ------------------------------------------------------------------ |
| index | number | 是   | 所需代码单元的从零开始的索引。当index<0 或者index>=length，则会抛出错误。 |

**返回值：**

| 类型   | 说明                     |
| ----- | ------------------------ |
|   T   | Array给定的元素数据类型。  |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                             |
| ------- | ------------------------------------ |
| 401 |        Parameter error.                  |
| 10200001 | The value of index is out of range. |

**示例：**

```ts
let array = new collections.Array<number>(1, 2, 4);
console.info("Element at index 1: ", array[1]);
```
