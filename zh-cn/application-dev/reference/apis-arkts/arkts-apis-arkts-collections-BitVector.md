# Class (BitVector)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @lijiamin2025-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->
> **说明：**
>
> 本Class同时支持ArkTS-Dyn、ArkTS-Sta。
>
> 本模块首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。

BitVector是一种线性数据结构，底层基于数组实现。BitVector中存储元素为bit值，能存储和处理bit级别的操作。

**装饰器类型：**\@Sendable

## 导入模块

```ts
import { collections } from '@kit.ArkTS';
```

## 属性

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 20

| 名称   | 类型   | 只读 | 可选 | 说明                  |
| ------ | ------ | ---- | ---- | --------------------- |
| length | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 否   | BitVector的元素个数。 |


## constructor

ArkTS-Dyn: constructor(length: number)

ArkTS-Sta: constructor(length: int)

BitVector的构造函数。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名 | 类型   | 必填 | 说明                    |
| ------ | ------ | ---- | ----------------------- |
| length | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 初始化BitVector的长度。 |

**示例：**

```ts
let bitVector: collections.BitVector = new collections.BitVector(0);
```

## push

ArkTS-Dyn: push(element: number): boolean

ArkTS-Sta: push(element: int): boolean

在BitVector尾部插入元素。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名  | 类型   | 必填 | 说明                                |
| ------- | ------ | ---- | ----------------------------------- |
| element | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 待插入的元素，0表示0，其余值表示1。 |

**返回值：**

| 类型    | 说明                              |
| ------- | --------------------------------- |
| boolean | 插入成功返回true，失败返回false。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| 10200011 | The push method cannot be bound.                             |
| 10200201 | Concurrent modification error.                               |

**示例：**

```ts
let bitVector: collections.BitVector = new collections.BitVector(0);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0); // bitVector: [0, 1, 0, 1, 0]
```

## pop

ArkTS-Dyn: pop(): number

ArkTS-Sta: pop(): int | undefined

弹出BitVector尾部的元素。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型   | 说明                                       |
| ------ | ------------------------------------------ |
| ArkTS-Dyn: number<br>ArkTS-Sta: int \| undefined | 弹出BitVector尾部的元素，其值为对应bit值。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                        |
| -------- | ------------------------------- |
| 10200011 | The pop method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**示例：**

```ts
let bitVector: collections.BitVector = new collections.BitVector(0);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0); // bitVector: [0, 1, 0, 1, 0]
let res = bitVector.pop(); // bitVector: [0, 1, 0, 1]
console.info("bitVector pop:", res); // 0
```

## has

ArkTS-Dyn: has(element: number, fromIndex: number, toIndex: number): boolean

ArkTS-Sta: has(element: int, fromIndex: int, toIndex: int): boolean

判断范围内是否包含特定bit值。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名    | 类型   | 必填 | 说明                                 |
| --------- | ------ | ---- | ------------------------------------ |
| element   | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 待判断的bit值，0表示0，其余值表示1。 |
| fromIndex | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 范围起始索引，包含本索引值。fromIndex<0或者fromIndex>=toIndex时，则会抛出错误。  |
| toIndex   | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 范围终止索引，包含本索引值。toIndex<0或者toIndex>=length时，则会抛出错误。       |

**返回值：**

| 类型    | 说明                                   |
| ------- | -------------------------------------- |
| boolean | 包含特定bit值返回true，否则返回false。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 10200001 | The value of fromIndex or toIndex is out of range.           |
| 10200011 | The has method cannot be bound.                              |
| 10200201 | Concurrent modification error.                               |

**示例：**

```ts
let bitVector: collections.BitVector = new collections.BitVector(0);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0); // bitVector: [0, 1, 0, 1, 0]
let res0: boolean = bitVector.has(0, 1, 4);
console.info("bitVector has 0:", res0); // true
```

## setBitsByRange

ArkTS-Dyn: setBitsByRange(element: number, fromIndex: number, toIndex: number): void

ArkTS-Sta: setBitsByRange(element: int, fromIndex: int, toIndex: int): void

将BitVector中指定范围的元素均设为特定bit值。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名    | 类型   | 必填 | 说明                               |
| --------- | ------ | ---- | ---------------------------------- |
| element   | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 待设置的bit值，0表示0，其余表示1。 |
| fromIndex | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 范围起始索引，包含本索引值。fromIndex<0或者fromIndex>=toIndex时，则会抛出错误。  |
| toIndex   | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 范围终止索引，不包含本索引值。toIndex<0或者toIndex>=length时，则会抛出错误。     |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| 10200001 | The value of fromIndex or toIndex is out of range.           |
| 10200011 | The setBitsByRange method cannot be bound.                   |
| 10200201 | Concurrent modification error.                               |

**示例：**

```ts
let bitVector: collections.BitVector = new collections.BitVector(0);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0); // bitVector: [0, 1, 0, 1, 0]
bitVector.setBitsByRange(1, 1, 3); // bitVector: [0, 1, 1, 1, 0]
```

## setAllBits

ArkTS-Dyn: setAllBits(element: number): void

ArkTS-Sta: setAllBits(element: int): void

将BitVector中所有元素均设为特定bit值。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名  | 类型   | 必填 | 说明                                |
| ------- | ------ | ---- | ----------------------------------- |
| element | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 待设置的元素，0表示0，其余值表示1。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| 10200011 | The setAllBits method cannot be bound.                       |
| 10200201 | Concurrent modification error.                               |

**示例：**

```ts
let bitVector: collections.BitVector = new collections.BitVector(0);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0); // bitVector: [0, 1, 0, 1, 0]
bitVector.setAllBits(1); // bitVector: [1, 1, 1, 1, 1]
```

## getBitsByRange

ArkTS-Dyn: getBitsByRange(fromIndex: number, toIndex: number): BitVector

ArkTS-Sta: getBitsByRange(fromIndex: int, toIndex: int): BitVector

获取指定范围内的bit值。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名    | 类型   | 必填 | 说明                           |
| --------- | ------ | ---- | ------------------------------ |
| fromIndex | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 范围起始索引，包含本索引值。fromIndex<0或者fromIndex>=toIndex时，则会抛出错误。   |
| toIndex   | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 范围终止索引，不包含本索引值。toIndex<0或者toIndex>=length时，则会抛出错误。      |

**返回值：**

| 类型      | 说明                               |
| --------- | ---------------------------------- |
| BitVector | 指定范围内的bit值组成的BitVector。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| 10200001 | The value of fromIndex or toIndex is out of range.           |
| 10200011 | The getBitsByRange method cannot be bound.                   |
| 10200201 | Concurrent modification error.                               |

**示例：**

```ts
let bitVector: collections.BitVector = new collections.BitVector(0);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0); // bitVector: [0, 1, 0, 1, 0]
let bitVector2 = bitVector.getBitsByRange(1, 3); // bitVector2: [1, 0]
console.info("bitVector2 length:", bitVector2.length); // 2
```

## resize

ArkTS-Dyn: resize(size: number): void

ArkTS-Sta: resize(size: int): void

改变BitVector的长度。

若size大于原BitVector的长度，则扩充原BitVector的长度，多出的部分其元素设置为0；

若size小于等于原BitVector的长度，则将原BitVector按size长度大小裁剪。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名 | 类型   | 必填 | 说明             |
| ------ | ------ | ---- | ---------------- |
| size   | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 需要改变的长度。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| 10200011 | The resize method cannot be bound.                           |
| 10200201 | Concurrent modification error.                               |

**示例：**

```ts
let bitVector: collections.BitVector = new collections.BitVector(0);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0); // bitVector: [0, 1, 0, 1, 0]
bitVector.resize(10); // bitVector: [0, 1, 0, 1, 0, 0, 0, 0, 0, 0]
console.info("bitVector get bit vector's length:", bitVector.length); // 10
bitVector.resize(3); // bitVector: [0, 1, 0]
console.info("bitVector get bit vector's length:", bitVector.length); // 3
```

## getBitCountByRange

ArkTS-Dyn: getBitCountByRange(element: number, fromIndex: number, toIndex: number): number

ArkTS-Sta: getBitCountByRange(element: int, fromIndex: int, toIndex: int): int

统计指定范围内获取指定bit值的数量。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名    | 类型   | 必填 | 说明                                 |
| --------- | ------ | ---- | ------------------------------------ |
| element   | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 待统计的bit值，0表示0，其余值表示1。 |
| fromIndex | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 范围起始索引，包含本索引值。fromIndex<0或者fromIndex>=toIndex时，则会抛出错误。    |
| toIndex   | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 范围终止索引，不包含本索引值。toIndex<0或者toIndex>=length时，则会抛出错误。       |

**返回值：**

| 类型   | 说明                                |
| ------ | ----------------------------------- |
| ArkTS-Dyn: number<br>ArkTS-Sta: int | 统计指定范围内获取指定bit值的数量。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| 10200001 | The value of fromIndex or toIndex is out of range.           |
| 10200011 | The getBitCountByRange method cannot be bound.               |
| 10200201 | Concurrent modification error.                               |

**示例：**

ArkTS-Dyn示例：
```ts
let bitVector: collections.BitVector = new collections.BitVector(0);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0); // bitVector: [0, 1, 0, 1, 0]
let res: number = bitVector.getBitCountByRange(1, 1, 4);
console.info("bitVector getBitCountByRange:", res); // 2
```

ArkTS-Sta示例：
```ts
let bitVector: collections.BitVector = new collections.BitVector(0);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0); // bitVector: [0, 1, 0, 1, 0]
let res: int = bitVector.getBitCountByRange(1, 1, 4);
console.info("bitVector getBitCountByRange:", res); // 2
```

## getIndexOf

ArkTS-Dyn: getIndexOf(element: number, fromIndex: number, toIndex: number): number

ArkTS-Sta: getIndexOf(element: int, fromIndex: int, toIndex: int): int

返回指定bit值首次出现时的索引值，查找失败返回-1。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名    | 类型   | 必填 | 说明                                 |
| --------- | ------ | ---- | ------------------------------------ |
| element   | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 待统计的bit值，0表示0，其余值表示1。 |
| fromIndex | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 范围起始索引，包含本索引值。fromIndex<0或者fromIndex>=toIndex时，则会抛出错误。    |
| toIndex   | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 范围终止索引，不包含本索引值。toIndex<0或者toIndex>=length时，则会抛出错误。       |

**返回值：**

| 类型   | 说明                                              |
| ------ | ------------------------------------------------- |
| ArkTS-Dyn: number<br>ArkTS-Sta: int | 返回指定bit值首次出现时的下标值，查找失败返回-1。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| 10200001 | The value of fromIndex or toIndex is out of range.           |
| 10200011 | The getIndexOf method cannot be bound.                       |
| 10200201 | Concurrent modification error.                               |

**示例：**

ArkTS-Dyn示例：
```ts
let bitVector: collections.BitVector = new collections.BitVector(0);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0); // bitVector: [0, 1, 0, 1, 0]
let res: number = bitVector.getIndexOf(0, 1, 4);
console.info("bitVector getIndexOf:", res); // 2
```

ArkTS-Sta示例：
```ts
let bitVector: collections.BitVector = new collections.BitVector(0);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0); // bitVector: [0, 1, 0, 1, 0]
let res: int = bitVector.getIndexOf(0, 1, 4);
console.info("bitVector getIndexOf:", res); // 2
```

## getLastIndexOf

ArkTS-Dyn: getLastIndexOf(element: number, fromIndex: number, toIndex: number): number

ArkTS-Sta: getLastIndexOf(element: int, fromIndex: int, toIndex: int): int

返回指定bit值最后一次出现时的下标值，查找失败返回-1。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名    | 类型   | 必填 | 说明                                 |
| --------- | ------ | ---- | ------------------------------------ |
| element   | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 待统计的bit值，0表示0，其余值表示1。 |
| fromIndex | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 范围起始索引，包含本索引值。fromIndex<0或者fromIndex>=toIndex时，则会抛出错误。    |
| toIndex   | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 范围终止索引，不包含本索引值。toIndex<0或者toIndex>=length时，则会抛出错误。       |

**返回值：**

| 类型   | 说明                                                  |
| ------ | ----------------------------------------------------- |
| ArkTS-Dyn: number<br>ArkTS-Sta: int | 返回指定bit值最后一次出现时的下标值，查找失败返回-1。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| 10200001 | The value of fromIndex or toIndex is out of range.           |
| 10200011 | The getLastIndexOf method cannot be bound.                   |
| 10200201 | Concurrent modification error.                               |

**示例：**

ArkTS-Dyn示例：
```ts
let bitVector: collections.BitVector = new collections.BitVector(0);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0); // bitVector: [0, 1, 0, 1, 0]
let res: number = bitVector.getLastIndexOf(0, 1, 4);
console.info("bitVector getLastIndexOf:", res); // 2
```

ArkTS-Sta示例：
```ts
let bitVector: collections.BitVector = new collections.BitVector(0);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0); // bitVector: [0, 1, 0, 1, 0]
let res: int = bitVector.getLastIndexOf(0, 1, 4);
console.info("bitVector getLastIndexOf:", res); // 2
```

## flipBitByIndex

ArkTS-Dyn: flipBitByIndex(index: number): void

ArkTS-Sta: flipBitByIndex(index: int): void

翻转BitVector指定索引处的bit值，0翻转为1，1翻转为0。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名 | 类型   | 必填 | 说明       |
| ------ | ------ | ---- | ---------- |
| index  | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 指定索引。index<0或者index>=length时，则会抛出错误。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| 10200001 | The value of index is out of range.                          |
| 10200011 | The flipBitByIndex method cannot be bound.                   |
| 10200201 | Concurrent modification error.                               |

**示例：**

```ts
let bitVector: collections.BitVector = new collections.BitVector(0);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0); // bitVector: [0, 1, 0, 1, 0]
bitVector.flipBitByIndex(3); // bitVector: [0, 1, 0, 0, 0]
```

## flipBitsByRange

ArkTS-Dyn: flipBitsByRange(fromIndex: number, toIndex: number): void

ArkTS-Sta: flipBitsByRange(fromIndex: int, toIndex: int): void

翻转BitVector指定范围内的bit值，0翻转为1，1翻转为0。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名    | 类型   | 必填 | 说明                           |
| --------- | ------ | ---- | ------------------------------ |
| fromIndex | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 范围起始索引，包含本索引值。fromIndex<0或者fromIndex>=toIndex时，则会抛出错误。  |
| toIndex   | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 范围终止索引，不包含本索引值。toIndex<0或者toIndex>=length时，则会抛出错误。     |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| 10200001 | The value of fromIndex or toIndex is out of range.           |
| 10200011 | The flipBitsByRange method cannot be bound.                  |
| 10200201 | Concurrent modification error.                               |

**示例：**

```ts
let bitVector: collections.BitVector = new collections.BitVector(0);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0); // bitVector: [0, 1, 0, 1, 0]
bitVector.flipBitsByRange(1, 4); // bitVector: [0, 0, 1, 0, 0]
```

## values

ArkTS-Dyn: values(): IterableIterator\<number>

ArkTS-Sta: values(): IterableIterator\<int>

返回一个新的迭代器对象，该对象包含BitVector中每个元素的值。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型                           | 说明                          |
| ------------------------------ | ----------------------------- |
|  ArkTS-Dyn: IterableIterator&lt;number&gt;<br>ArkTS-Sta: IterableIterator&lt;int&gt; | 返回一个BitVector迭代器对象。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                           |
| -------- | ---------------------------------- |
| 10200011 | The values method cannot be bound. |
| 10200201 | Concurrent modification error.     |

**示例：**

ArkTS-Dyn示例：
```ts
let bitVector: collections.BitVector = new collections.BitVector(0);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0); // bitVector: [0, 1, 0, 1, 0]
let iter: IterableIterator<number> = bitVector.values();
let temp: IteratorResult<number> = iter.next();
while (!temp.done) {
  console.info(JSON.stringify(temp.value));
  temp = iter.next();
} // 依次输出 0,1,0,1,0
```

ArkTS-Sta示例：
```ts
let bitVector: collections.BitVector = new collections.BitVector(0);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0); // bitVector: [0, 1, 0, 1, 0]
let iter: IterableIterator<int> = bitVector.values();
let temp: IteratorResult<int> = iter.next();
while (!temp.done) {
  console.info(JSON.stringify(temp.value));
  temp = iter.next();
} // 依次输出 0,1,0,1,0
```

## [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;number&gt;

返回一个迭代器，迭代器的每一项都是一个 JavaScript 对象，并返回该对象。

> **说明：**
>
> 本接口不支持在.ets文件中使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 12

**返回值：**

| 类型                      | 说明             |
| ------------------------- | ---------------- |
| IterableIterator&lt;number&gt; | 返回一个迭代器。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 10200011 | The Symbol.iterator method cannot be bound. |

**示例：**

```ts
let bitVector: collections.BitVector = new collections.BitVector(0);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0);

for (let item of bitVector) {
  console.info("value: " + item);
}
```

## $_iterator<sup>20+</sup>

\$_iterator\(): IterableIterator&lt;int&gt;

返回一个迭代器，迭代器的每一项都是一个 JavaScript 对象，并返回该对象。

> **说明：**
>
> 本接口不支持在.ets文件中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型                      | 说明             |
| ------------------------- | ---------------- |
| IterableIterator&lt;int&gt; | 返回一个迭代器。 |

**示例：**

```ts
let bitVector: collections.BitVector = new collections.BitVector(0);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0);

for (let item of bitVector) {
  console.info("value: " + item);
}
```

## [index: number]

&#91;index: number&#93;: number

返回BitVector指定索引位置的元素。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名    | 类型   | 必填 | 说明                     |
| ----- | ------ | ---- | -------------------------- |
| index | number | 是   | 所需代码单元的从零开始的索引。|

**返回值：**

| 类型   | 说明                 |
| ----- | ---------------------|
| number | 返回number数据类型。 |

**示例：**

```ts
let bitVector: collections.BitVector = new collections.BitVector(0);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0); // bitVector: [0, 1, 0, 1, 0]
console.info("BitVector Element Index at 1: " + bitVector[1]);
```

## [index: int]<sup>20+</sup>

&#91;index: int&#93;: int

返回BitVector指定索引位置的元素。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 20

| 参数名    | 类型   | 必填 | 说明                     |
| ----- | ------ | ---- | -------------------------- |
| index | int | 是   | 所需代码单元的从零开始的索引。|

**返回值：**

| 类型   | 说明                 |
| ----- | ---------------------|
| int | 返回int数据类型。 |

**示例：**

```ts
let bitVector: collections.BitVector = new collections.BitVector(0);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0);
bitVector.push(1);
bitVector.push(0); // bitVector: [0, 1, 0, 1, 0]
console.info("BitVector Element Index at 1: " + bitVector[1]);
```