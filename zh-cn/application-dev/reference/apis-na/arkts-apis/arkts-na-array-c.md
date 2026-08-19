# Array

表示与JS API兼容的数组。

**继承/实现关系：** Array implements ReadonlyArray<T>, Iterable<T>

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

<!--Device-unnamed-export class Array--><!--Device-unnamed-export class Array-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## $_get

```TypeScript
$_get(idx: int): T
```

获取指定索引处的元素。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-$_get(idx: int): T--><!--Device-Array-$_get(idx: int): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| idx | int | 是 | 待获取元素的索引。 <br>取值约束：必须为大于或等于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 指定索引处的元素。 |

## $_invoke

```TypeScript
static $_invoke<T>(...items: T[]): Array<T>
```

使用给定的元素创建一个Array实例。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-static $_invoke<T>(...items: T[]): Array<T>--><!--Device-Array-static $_invoke<T>(...items: T[]): Array<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| items | T[] | 是 | 用于初始化数组的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 包含给定元素的新Array实例。 |

## $_iterator

```TypeScript
$_iterator(): IterableIterator<T>
```

返回遍历所有值的迭代器。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-$_iterator(): IterableIterator<T>--><!--Device-Array-$_iterator(): IterableIterator<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;T&gt; | 遍历所有值的迭代器。 |

## $_set

```TypeScript
$_set(idx: int, val: T): void
```

设置指定索引处的元素。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-$_set(idx: int, val: T): void--><!--Device-Array-$_set(idx: int, val: T): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| idx | int | 是 | 待设置元素的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| val | T | 是 | 要在指定索引处设置的值。 |

## at

```TypeScript
public at(index: int): T
```

接受一个整数值并返回该索引处的元素，支持正整数和负整数。 负整数表示从数组的最后一个元素开始向前计数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public at(index: int): T--><!--Device-Array-public at(index: int): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待返回数组元素的索引，从0开始计数。 <br>取值约束：必须为大于或等于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 给定索引处的元素。 |

## concat

```TypeScript
public concat(...items: FixedArray<ConcatArray<T>>): Array<T>
```

将当前`Array`实例与给定的数组和/或值合并，创建一个新的`Array`。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public concat(...items: FixedArray<ConcatArray<T>>): Array<T>--><!--Device-Array-public concat(...items: FixedArray<ConcatArray<T>>): Array<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| items | FixedArray&lt;[ConcatArray](../../apis-arkts/arkts-apis/arkts-arkts-collections-concatarray-i.md)&lt;T&gt;&gt; | 是 | 待拼接成新数组的数组和/或值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 新的Array实例。 |

## constructor

```TypeScript
public constructor()
```

创建一个空的Array实例。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public constructor()--><!--Device-Array-public constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

## constructor

```TypeScript
constructor(first: T, ...d: T[])
```

使用给定的元素创建一个Array实例。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-constructor(first: T, ...d: T[])--><!--Device-Array-constructor(first: T, ...d: T[])-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| first | T | 是 | 数组的第一个元素。 |
| d | T[] | 是 | 用于初始化数组的其余元素。 |

## constructor

```TypeScript
constructor(arrayLen: int, initializer: (index: int) => T)
```

创建一个指定长度的Array实例，并使用函数初始化每个元素。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-constructor(arrayLen: int, initializer: (index: int) => T)--><!--Device-Array-constructor(arrayLen: int, initializer: (index: int) => T)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arrayLen | int | 是 | 数组的元素个数。 <br>取值约束：必须为大于或等于0的整数。 |
| initializer | (index: int) =&gt; T | 是 | 为给定索引生成元素的函数。 |

## copyWithin

```TypeScript
public copyWithin(target: int): this
```

将数组的一部分浅拷贝到同一数组的另一位置并返回该数组， 不改变其长度。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public copyWithin(target: int): this--><!--Device-Array-public copyWithin(target: int): this-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | int | 是 | 序列拷贝到的目标索引，从0开始计数。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 修改后的数组。 |

## copyWithin

```TypeScript
public copyWithin(target: int, start: int): this
```

将数组的一部分浅拷贝到同一数组的另一位置并返回该数组， 不改变其长度。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public copyWithin(target: int, start: int): this--><!--Device-Array-public copyWithin(target: int, start: int): this-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | int | 是 | 序列拷贝到的目标索引，从0开始计数。 <br>取值约束：应为整数。 |
| start | int | 是 | 开始拷贝元素的索引，从0开始计数。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 修改后的数组。 |

## copyWithin

```TypeScript
public copyWithin(target: int, start: int, end?: int): this
```

将数组的一部分浅拷贝到同一数组的另一位置并返回该数组， 不改变其长度。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public copyWithin(target: int, start: int, end?: int): this--><!--Device-Array-public copyWithin(target: int, start: int, end?: int): this-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | int | 是 | 序列拷贝到的目标索引，从0开始计数。 <br>取值约束：应为整数。 |
| start | int | 是 | 开始拷贝元素的索引，从0开始计数。 <br>取值约束：应为整数。 |
| end | int | 否 | 结束拷贝元素的索引，从0开始计数。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 修改后的数组。 |

## create

```TypeScript
public static create<T>(arrayLength: int, initialValue: T): Array<T>
```

创建一个指定长度的数组，并使用指定的初始值填充。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public static create<T>(arrayLength: int, initialValue: T): Array<T>--><!--Device-Array-public static create<T>(arrayLength: int, initialValue: T): Array<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arrayLength | int | 是 | 新数组的元素个数。 <br>取值约束：必须为大于或等于0的整数。 |
| initialValue | T | 是 | 用于填充数组的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 使用初始值填充的新Array实例。 |

## entries

```TypeScript
public entries(): IterableIterator<[int, T]>
```

返回一个新的数组迭代器对象，其中包含数组每个索引的键值对。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public entries(): IterableIterator<[int, T]>--><!--Device-Array-public entries(): IterableIterator<[int, T]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[int, T]&gt; | 新的数组迭代器对象。 |

## every

```TypeScript
public every(predicate: (value: T, index: int, array: Array<T>) => boolean): boolean
```

判断数组中的所有元素是否都满足指定的测试条件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public every(predicate: (value: T, index: int, array: Array<T>) => boolean): boolean--><!--Device-Array-public every(predicate: (value: T, index: int, array: Array<T>) => boolean): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicate | (value: T, index: int, array: Array&lt;T&gt;) =&gt; boolean | 是 | 一个最多接受三个参数的函数。every方法会对数组中的每个元素 调用predicate函数，直到predicate返回可转换为布尔值 false的值，或直到数组末尾。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果数组中所有元素的predicate都返回true则返回true，否则返回false。 |

## extendTo

```TypeScript
public extendTo(arrayLength: int, initialValue: T): void
```

使用新元素将数组扩展到指定长度。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public extendTo(arrayLength: int, initialValue: T): void--><!--Device-Array-public extendTo(arrayLength: int, initialValue: T): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arrayLength | int | 是 | 数组的新长度。 <br>取值约束：必须为大于或等于0的整数。 |
| initialValue | T | 是 | 新增元素的初始值。 |

## fill

```TypeScript
public fill(value: T, start?: int, end?: int): this
```

将数组中从start索引到end索引的所有元素修改为固定值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public fill(value: T, start?: int, end?: int): this--><!--Device-Array-public fill(value: T, start?: int, end?: int): this-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 用于填充数组的值。 |
| start | int | 否 | 可选参数，开始填充的索引。如果start大于或等于 数组长度，则不填充任何元素；如果start为负数，则视为0。 <br>取值约束：应为整数。 |
| end | int | 否 | 可选参数，结束填充的索引（不包含）。如果end大于 数组长度，则以数组长度作为结束索引；如果end为负数，则视为0。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 修改后的数组。 |

## filter

```TypeScript
public filter(predicate: (value: T, index: int, array: Array<T>) => boolean): Array<T>
```

返回数组中满足回调函数指定条件的元素。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public filter(predicate: (value: T, index: int, array: Array<T>) => boolean): Array<T>--><!--Device-Array-public filter(predicate: (value: T, index: int, array: Array<T>) => boolean): Array<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicate | (value: T, index: int, array: Array&lt;T&gt;) =&gt; boolean | 是 | 一个最多接受三个参数的函数。filter方法会对数组中的每个元素 调用一次predicate函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 包含通过测试的元素的新数组。 |

## find

```TypeScript
public find(predicate: (value: T, index: int, array: Array<T>) => boolean): T | undefined
```

遍历数组，返回满足给定测试函数的第一个元素的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public find(predicate: (value: T, index: int, array: Array<T>) => boolean): T | undefined--><!--Device-Array-public find(predicate: (value: T, index: int, array: Array<T>) => boolean): T | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicate | (value: T, index: int, array: Array&lt;T&gt;) =&gt; boolean | 是 | 对数组中每个值执行的函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 满足给定测试函数的第一个元素的值， 否则返回undefined。 |

## findIndex

```TypeScript
public findIndex(predicate: (value: T, index: int, array: Array<T>) => boolean): int
```

返回数组中第一个使predicate为true的元素的索引，如果不存在则返回-1。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public findIndex(predicate: (value: T, index: int, array: Array<T>) => boolean): int--><!--Device-Array-public findIndex(predicate: (value: T, index: int, array: Array<T>) => boolean): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicate | (value: T, index: int, array: Array&lt;T&gt;) =&gt; boolean | 是 | 对数组中每个值执行的函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 满足给定测试函数的第一个元素的索引，否则返回-1。 |

## findLast

```TypeScript
public findLast(predicate: (elem: T, index: int, array: Array<T>) => boolean): T | undefined
```

按逆序遍历数组，返回满足给定测试函数的 第一个元素的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public findLast(predicate: (elem: T, index: int, array: Array<T>) => boolean): T | undefined--><!--Device-Array-public findLast(predicate: (elem: T, index: int, array: Array<T>) => boolean): T | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicate | (elem: T, index: int, array: Array&lt;T&gt;) =&gt; boolean | 是 | 对数组中每个值执行的函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 如果找到则返回该元素的值，否则返回undefined。 |

## findLastIndex

```TypeScript
public findLastIndex(predicate: (element: T, index: int, array: Array<T>) => boolean): int
```

按逆序遍历数组，返回满足给定测试函数的第一个元素的索引。 如果没有元素满足测试函数，则返回-1。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public findLastIndex(predicate: (element: T, index: int, array: Array<T>) => boolean): int--><!--Device-Array-public findLastIndex(predicate: (element: T, index: int, array: Array<T>) => boolean): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicate | (element: T, index: int, array: Array&lt;T&gt;) =&gt; boolean | 是 | 对数组中每个值执行的函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 满足给定测试函数的第一个元素的索引，否则返回-1。 |

## flat

```TypeScript
public flat<U = T>(depth: int): Array<U>
```

创建一个新数组，将所有子数组元素按指定深度递归拼接到其中。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public flat<U = T>(depth: int): Array<U>--><!--Device-Array-public flat<U = T>(depth: int): Array<U>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| depth | int | 是 | 指定嵌套数组结构展平深度的层级。 <br>取值约束：必须为大于或等于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;U&gt; | 拼接了子数组元素的新数组。 |

## flat

```TypeScript
public flat<U = T>(): Array<U>
```

创建一个新数组，将所有子数组元素按默认深度1递归拼接到其中。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public flat<U = T>(): Array<U>--><!--Device-Array-public flat<U = T>(): Array<U>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;U&gt; | 拼接了子数组元素的新数组。 |

## flatMap

```TypeScript
public flatMap<U=T>(fn: (v: T, k: int, arr: Array<T>) => U | ReadonlyArray<U>): Array<U>
```

对数组的每个元素调用指定的回调函数，然后将结果展平到一个新数组中。 等价于先调用map()，再调用深度为1的flat()。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public flatMap<U=T>(fn: (v: T, k: int, arr: Array<T>) => U | ReadonlyArray<U>): Array<U>--><!--Device-Array-public flatMap<U=T>(fn: (v: T, k: int, arr: Array<T>) => U | ReadonlyArray<U>): Array<U>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fn | (v: T, k: int, arr: Array&lt;T&gt;) =&gt; U \| ReadonlyArray&lt;U&gt; | 是 | 生成新数组元素的函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;U&gt; | 新数组，其每个元素均为回调函数的返回结果并已展平。 |

## forEach

```TypeScript
forEach(callbackfn: (value: T, index: int, array: Array<T>) => void): void
```

对数组中的每个元素执行指定的操作。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-forEach(callbackfn: (value: T, index: int, array: Array<T>) => void): void--><!--Device-Array-forEach(callbackfn: (value: T, index: int, array: Array<T>) => void): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackfn | (value: T, index: int, array: Array&lt;T&gt;) =&gt; void | 是 | 一个最多接受三个参数的函数。forEach会对数组中的每个元素 调用一次callbackfn函数。 |

## from

```TypeScript
static from<T>(arr: FixedArray<T>): Array<T>
```

根据`FixedArray`创建一个新的`Array`实例。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-static from<T>(arr: FixedArray<T>): Array<T>--><!--Device-Array-static from<T>(arr: FixedArray<T>): Array<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arr | FixedArray&lt;T&gt; | 是 | 源基础数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 包含源数组元素的新Array实例。 |

## from

```TypeScript
static from<T>(arr: ArrayLike<T>): Array<T>
```

根据`ArrayLike`对象创建一个新的`Array`实例。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-static from<T>(arr: ArrayLike<T>): Array<T>--><!--Device-Array-static from<T>(arr: ArrayLike<T>): Array<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arr | [ArrayLike](arkts-na-arraylike-i.md)&lt;T&gt; | 是 | 待转换为数组的类数组对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 包含类数组对象元素的新Array实例。 |

## from

```TypeScript
static from<T>(iterable: ArrayLike<T> | Iterable<T>): Array<T>
```

根据可迭代对象或类数组对象创建一个新的`Array`实例。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-static from<T>(iterable: ArrayLike<T> | Iterable<T>): Array<T>--><!--Device-Array-static from<T>(iterable: ArrayLike<T> | Iterable<T>): Array<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| iterable | [ArrayLike](arkts-na-arraylike-i.md)&lt;T&gt; \| Iterable&lt;T&gt; | 是 | 待转换为数组的可迭代对象或类数组对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 包含可迭代对象元素的新Array实例。 |

## from

```TypeScript
static from<T, U>(values: FixedArray<T>, mapfn: (v: T, k: int) => U): Array<U>
```

根据`FixedArray`创建一个新的`Array`实例，并对每个元素应用映射函数。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-static from<T, U>(values: FixedArray<T>, mapfn: (v: T, k: int) => U): Array<U>--><!--Device-Array-static from<T, U>(values: FixedArray<T>, mapfn: (v: T, k: int) => U): Array<U>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| values | FixedArray&lt;T&gt; | 是 | 源基础数组。 |
| mapfn | (v: T, k: int) =&gt; U | 是 | 对数组每个元素调用的映射函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;U&gt; | 包含映射后值的新Array实例。 |

## from

```TypeScript
static from<T, U>(iterable: ArrayLike<T> | Iterable<T>, mapfn: (v: T, k: int) => U): Array<U>
```

根据可迭代对象创建一个新的`Array`实例，并对每个元素应用映射函数。 每个待添加到数组的值都会先经过该函数处理，最终添加到数组中的是`mapfn`的返回值， 而不是原始值。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-static from<T, U>(iterable: ArrayLike<T> | Iterable<T>, mapfn: (v: T, k: int) => U): Array<U>--><!--Device-Array-static from<T, U>(iterable: ArrayLike<T> | Iterable<T>, mapfn: (v: T, k: int) => U): Array<U>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| iterable | [ArrayLike](arkts-na-arraylike-i.md)&lt;T&gt; \| Iterable&lt;T&gt; | 是 | 待转换为数组的可迭代对象或类数组对象。 |
| mapfn | (v: T, k: int) =&gt; U | 是 | 对数组每个元素调用的映射函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;U&gt; | 包含映射后值的新Array实例。 |

## includes

```TypeScript
public includes(val: T, fromIndex?: int): boolean
```

判断数组的元素中是否包含某个值，并相应地返回true或false。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public includes(val: T, fromIndex?: int): boolean--><!--Device-Array-public includes(val: T, fromIndex?: int): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | T | 是 | 待查找的值。 |
| fromIndex | int | 否 | 在该数组中开始查找值的位置。 <br>取值约束：必须为大于或等于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果找到该值则返回true，否则返回false。 |

## indexOf

```TypeScript
public indexOf(val: T): int
```

返回给定元素在数组中首次出现的索引，如果不存在则返回-1。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public indexOf(val: T): int--><!--Device-Array-public indexOf(val: T): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | T | 是 | 待在数组中查找的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 该元素在数组中的第一个索引，未找到时返回-1。 |

## indexOf

```TypeScript
public indexOf(val: T, fromIndex?: int): int
```

返回给定元素在数组中首次出现的索引，如果不存在则返回-1。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public indexOf(val: T, fromIndex?: int): int--><!--Device-Array-public indexOf(val: T, fromIndex?: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | T | 是 | 待在数组中查找的元素。 |
| fromIndex | int | 否 | 开始搜索的索引。 <br>取值约束：必须为大于或等于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 该元素在数组中的第一个索引，未找到时返回-1。 |

## isArray

```TypeScript
static isArray(o: Any): boolean
```

检查传入的值是否为数组。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-static isArray(o: Any): boolean--><!--Device-Array-static isArray(o: Any): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| o | Any | 是 | 待检查的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果该值为数组则返回true，否则返回false。 |

## join

```TypeScript
public join(sep?: string): string
```

使用指定的分隔符字符串连接`Array`中的所有元素， 创建并返回一个新字符串。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public join(sep?: string): string--><!--Device-Array-public join(sep?: string): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sep | string | 否 | 用于分隔数组中每对相邻元素的字符串。省略时，数组 元素之间以逗号分隔。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 连接所有数组元素后的字符串。 |

## keys

```TypeScript
public keys(): IterableIterator<int>
```

返回一个新的数组迭代器对象，其中包含数组每个索引的键。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public keys(): IterableIterator<int>--><!--Device-Array-public keys(): IterableIterator<int>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;int&gt; | 新的数组迭代器对象。 |

## lastIndexOf

```TypeScript
public lastIndexOf(searchElement: T): int
```

返回给定元素在数组中最后一次出现的索引，如果不存在则返回-1。 数组按逆序进行搜索。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public lastIndexOf(searchElement: T): int--><!--Device-Array-public lastIndexOf(searchElement: T): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| searchElement | T | 是 | 待在数组中查找的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 该元素在数组中的最后一个索引，未找到时返回-1。 |

## lastIndexOf

```TypeScript
public lastIndexOf(searchElement: T, fromIndex?: int): int
```

返回给定元素在数组中最后一次出现的索引，如果不存在则返回-1。 数组从fromIndex开始按逆序进行搜索。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public lastIndexOf(searchElement: T, fromIndex?: int): int--><!--Device-Array-public lastIndexOf(searchElement: T, fromIndex?: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| searchElement | T | 是 | 待在数组中查找的元素。 |
| fromIndex | int | 否 | 开始逆序搜索的索引。 <br>取值约束：必须为大于或等于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 该元素在数组中的最后一个索引，未找到时返回-1。 |

## map

```TypeScript
public map<U>(callbackfn: (value: T, index: int, array: Array<T>) => U): Array<U>
```

创建一个新数组，其元素为对原数组每个元素调用给定函数后的 返回结果。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public map<U>(callbackfn: (value: T, index: int, array: Array<T>) => U): Array<U>--><!--Device-Array-public map<U>(callbackfn: (value: T, index: int, array: Array<T>) => U): Array<U>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackfn | (value: T, index: int, array: Array&lt;T&gt;) =&gt; U | 是 | 对数组每个元素调用的函数。每次callbackfn执行时， 其返回值都会被添加到新数组中。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;U&gt; | 新数组，其每个元素均为回调函数的返回结果。 |

## pop

```TypeScript
public pop(): T | undefined
```

从数组中删除最后一个元素并返回该元素。该方法会改变数组的长度。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public pop(): T | undefined--><!--Device-Array-public pop(): T | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 从数组中被删除的元素，如果数组为空则返回undefined。 |

## push

```TypeScript
public push(...val: T[]): int
```

将指定元素添加到数组末尾，并返回数组的新长度。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public push(...val: T[]): int--><!--Device-Array-public push(...val: T[]): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | T[] | 是 | 要添加到数组末尾的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 调用该方法的数组的新长度。 |

## reduce

```TypeScript
public reduce(callbackfn: (previousValue: T, currentValue: T, index: int, array: Array<T>) => T): T
```

对数组中所有元素调用指定的回调函数。回调函数的返回值为 累加结果，并作为参数传入下一次回调函数的调用。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public reduce(callbackfn: (previousValue: T, currentValue: T, index: int, array: Array<T>) => T): T--><!--Device-Array-public reduce(callbackfn: (previousValue: T, currentValue: T, index: int, array: Array<T>) => T): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackfn | (previousValue: T, currentValue: T, index: int, array: Array&lt;T&gt;) =&gt; T | 是 | 一个最多接受四个参数的函数。reduce方法会对数组中的每个元素 调用一次callbackfn函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 累加结果。 |

## reduce

```TypeScript
public reduce<U = T>(callbackfn: (previousValue: U, currentValue: T, index: int, array: Array<T>) => U,
                         initialValue: U): U
```

对数组中所有元素调用指定的回调函数。回调函数的返回值为 累加结果，并作为参数传入下一次回调函数的调用。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public reduce<U = T>(callbackfn: (previousValue: U, currentValue: T, index: int, array: Array<T>) => U,                         initialValue: U): U--><!--Device-Array-public reduce<U = T>(callbackfn: (previousValue: U, currentValue: T, index: int, array: Array<T>) => U,                         initialValue: U): U-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackfn | (previousValue: U, currentValue: T, index: int, array: Array&lt;T&gt;) =&gt; U | 是 | 一个最多接受四个参数的函数。reduce方法会对数组中的每个元素 调用一次callbackfn函数。 |
| initialValue | U | 是 | 累加器的初始值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| U | 累加结果。 |

## reduceRight

```TypeScript
public reduceRight<U>(callbackfn: (previousValue: U, currentValue: T, index: int, array: Array<T>) => U,
                          initialValue: U): U
```

按逆序对数组中所有元素调用指定的回调函数。 回调函数的返回值为累加结果，并作为参数传入下一次回调 函数的调用。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public reduceRight<U>(callbackfn: (previousValue: U, currentValue: T, index: int, array: Array<T>) => U,                          initialValue: U): U--><!--Device-Array-public reduceRight<U>(callbackfn: (previousValue: U, currentValue: T, index: int, array: Array<T>) => U,                          initialValue: U): U-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackfn | (previousValue: U, currentValue: T, index: int, array: Array&lt;T&gt;) =&gt; U | 是 | 一个最多接受四个参数的函数。reduceRight方法会对数组中的每个元素 调用一次callbackfn函数。 |
| initialValue | U | 是 | 累加器的初始值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| U | 累加结果。 |

## reduceRight

```TypeScript
public reduceRight(callbackfn: (previousValue: T, currentValue: T, index: int, array: Array<T>) => T): T
```

按逆序对数组中所有元素调用指定的回调函数。 回调函数的返回值为累加结果，并作为参数传入下一次回调 函数的调用。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public reduceRight(callbackfn: (previousValue: T, currentValue: T, index: int, array: Array<T>) => T): T--><!--Device-Array-public reduceRight(callbackfn: (previousValue: T, currentValue: T, index: int, array: Array<T>) => T): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackfn | (previousValue: T, currentValue: T, index: int, array: Array&lt;T&gt;) =&gt; T | 是 | 一个最多接受四个参数的函数。reduceRight方法会对数组中的每个元素 调用一次callbackfn函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 累加结果。 |

## reverse

```TypeScript
public reverse(): this
```

原地反转数组。数组的第一个元素变为最后一个元素，最后一个元素变为 第一个元素。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public reverse(): this--><!--Device-Array-public reverse(): this-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 反转后的数组。 |

## shift

```TypeScript
public shift(): T | undefined
```

从数组中删除第一个元素，并返回被删除的元素。 该方法会改变数组的长度。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public shift(): T | undefined--><!--Device-Array-public shift(): T | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 从数组中被删除的元素，如果数组为空则返回undefined。 |

## shrinkTo

```TypeScript
public shrinkTo(arrayLength: int): void
```

将数组收缩到指定长度，超出新长度的元素将被删除。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public shrinkTo(arrayLength: int): void--><!--Device-Array-public shrinkTo(arrayLength: int): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arrayLength | int | 是 | 数组收缩到的长度。 <br>取值约束：必须为大于或等于0的整数。 |

## slice

```TypeScript
public slice(start: int): Array<T>
```

返回数组中某一部分的副本。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public slice(start: int): Array<T>--><!--Device-Array-public slice(start: int): Array<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | int | 是 | 数组中指定部分的起始索引。如果start大于 或等于数组长度，则返回空数组；如果start为负数， 则视为length + start。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 包含所提取元素的新Array对象。 |

## slice

```TypeScript
public slice(start?: int, end?: int): Array<T>
```

返回数组中某一部分的副本。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public slice(start?: int, end?: int): Array<T>--><!--Device-Array-public slice(start?: int, end?: int): Array<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | int | 否 | 数组中指定部分的起始索引。如果start大于 或等于数组长度，则返回空数组；如果start为负数， 则视为length + start。 <br>取值约束：应为整数。 |
| end | int | 否 | 数组中指定部分的结束索引。如果end大于 数组长度，则以数组长度作为结束索引；如果end为负数，则视为0。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 包含所提取元素的新Array对象。 |

## some

```TypeScript
public some(predicate: (value: T, index: int, array: Array<T>) => boolean): boolean
```

判断数组中是否存在任一元素使指定的回调函数返回true。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public some(predicate: (value: T, index: int, array: Array<T>) => boolean): boolean--><!--Device-Array-public some(predicate: (value: T, index: int, array: Array<T>) => boolean): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicate | (value: T, index: int, array: Array&lt;T&gt;) =&gt; boolean | 是 | 一个最多接受三个参数的函数。some方法会对数组中的每个元素 调用predicate函数，直到predicate返回可转换为布尔值 true的值，或直到数组末尾。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果数组中至少有一个元素的predicate返回true则返回true，否则返回false。 |

## sort

```TypeScript
public sort(comparator?: (a: T, b: T) => int): this
```

对数组元素进行原地排序，并返回排序后同一数组的引用。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public sort(comparator?: (a: T, b: T) => int): this--><!--Device-Array-public sort(comparator?: (a: T, b: T) => int): this-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| comparator | (a: T, b: T) =&gt; int | 否 | 可选参数，用于定义排序顺序的函数。省略时， 数组将按照每个元素转换为字符串后的结果， 依据各字符的Unicode码点值进行排序。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 排序后的数组。 |

## splice

```TypeScript
public splice(start: int, del: int | undefined, ...items: T[]): Array<T>
```

通过原地删除、替换已有元素或添加新元素来修改数组内容。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public splice(start: int, del: int | undefined, ...items: T[]): Array<T>--><!--Device-Array-public splice(start: int, del: int | undefined, ...items: T[]): Array<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | int | 是 | 开始修改数组的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| del | int \| undefined | 是 | 从start索引开始要删除的元素个数。如果传入 undefined，则表示0，不删除任何元素。 |
| items | T[] | 是 | 从start位置开始添加到数组中的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 从数组中删除元素，并在必要时在其位置插入新元素， 返回被删除的元素。 |

## splice

```TypeScript
public splice(start: int): Array<T>
```

通过原地删除从start索引到末尾的已有元素来修改数组内容。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public splice(start: int): Array<T>--><!--Device-Array-public splice(start: int): Array<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | int | 是 | 开始修改数组的索引。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 包含被删除元素的数组。 |

## toLocaleString

```TypeScript
public toLocaleString(locales?: Intl.LocalesArgument, options?: object): string
```

返回表示数组元素的字符串。元素通过各自的 toLocaleString方法转换为字符串。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public toLocaleString(locales?: Intl.LocalesArgument, options?: object): string--><!--Device-Array-public toLocaleString(locales?: Intl.LocalesArgument, options?: object): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locales | Intl.LocalesArgument | 否 | 带有BCP 47语言标签的字符串，或 由此类字符串组成的数组。 |
| options | object | 否 | 包含配置属性的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示数组元素的字符串。 |

## toReversed

```TypeScript
public toReversed(): Array<T>
```

返回一个元素顺序反转后的新数组。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public toReversed(): Array<T>--><!--Device-Array-public toReversed(): Array<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 反转后的新数组。 |

## toSorted

```TypeScript
public toSorted(): Array<T>
```

按升序排序，返回包含这些元素的新数组。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public toSorted(): Array<T>--><!--Device-Array-public toSorted(): Array<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 排序后的新数组。 |

## toSorted

```TypeScript
public toSorted(comparator: (a: T, b: T) => int): Array<T>
```

返回一个使用给定比较函数排序后的新数组。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public toSorted(comparator: (a: T, b: T) => int): Array<T>--><!--Device-Array-public toSorted(comparator: (a: T, b: T) => int): Array<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| comparator | (a: T, b: T) =&gt; int | 是 | 用于定义排序顺序的函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 排序后的新数组。 |

## toSpliced

```TypeScript
public toSpliced(start: int): Array<T>
```

返回一个在指定索引处删除和/或替换部分元素后的新数组。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public toSpliced(start: int): Array<T>--><!--Device-Array-public toSpliced(start: int): Array<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | int | 是 | 开始修改数组的索引，从0开始计数。 <br>取值约束：必须为大于或等于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 应用修改后的新数组。 |

## toSpliced

```TypeScript
public toSpliced(start: int, del: int, ...items: FixedArray<T>): Array<T>
```

返回一个在指定索引处删除和/或替换部分元素后的新数组。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public toSpliced(start: int, del: int, ...items: FixedArray<T>): Array<T>--><!--Device-Array-public toSpliced(start: int, del: int, ...items: FixedArray<T>): Array<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | int | 是 | 开始修改数组的索引，从0开始计数。 <br>取值约束：必须为大于或等于0的整数。 |
| del | int | 是 | 要删除的元素个数。 <br>取值约束：必须为大于或等于0的整数。 |
| items | FixedArray&lt;T&gt; | 是 | 要添加到数组中的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 应用修改后的新数组。 |

## toSpliced

```TypeScript
public toSpliced(start?: int, del?: int): Array<T>
```

返回一个在指定索引处删除和/或替换部分元素后的新数组。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public toSpliced(start?: int, del?: int): Array<T>--><!--Device-Array-public toSpliced(start?: int, del?: int): Array<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | int | 否 | 开始修改数组的索引，从0开始计数。 <br>取值约束：必须为大于或等于0的整数。 |
| del | int | 否 | 要删除的元素个数。 <br>取值约束：必须为大于或等于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 应用修改后的新数组。 |

## toString

```TypeScript
public toString(): string
```

返回表示指定数组及其元素的字符串。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public toString(): string--><!--Device-Array-public toString(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示该数组的字符串。 |

## unshift

```TypeScript
public unshift(...values: T[]): int
```

将指定元素添加到数组开头，并返回数组的新长度。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public unshift(...values: T[]): int--><!--Device-Array-public unshift(...values: T[]): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| values | T[] | 是 | 要添加到数组开头的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 数组的新长度。 |

## values

```TypeScript
public values(): IterableIterator<T>
```

返回一个新的数组迭代器对象，其中包含数组每个索引的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public values(): IterableIterator<T>--><!--Device-Array-public values(): IterableIterator<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;T&gt; | 新的数组迭代器对象。 |

## with

```TypeScript
public with(index: int, value: T): Array<T>
```

返回一个将给定索引处的元素替换为给定值后的新数组。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Array-public with(index: int, value: T): Array<T>--><!--Device-Array-public with(index: int, value: T): Array<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 替换值的索引，从0开始计数。 <br>取值约束：应为整数。 |
| value | T | 是 | 要插入到给定索引处的新值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 替换该元素后的新数组。 |

