# Class (Atomics)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @huanghello-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

为以ArkTS `ArrayBuffer`为底层缓冲区的整数`TypedArray`提供原子操作。此类通过`ArkTSUtils`模块提供，所有方法均为静态方法，通过`ArkTSUtils.Atomics`调用。

> **说明：**
>
> 本模块首批接口从API version 12开始支持。后续版本的新增接口，在对应接口描述中标明起始版本。
>
> `Atomics`首批接口从API版本26.1.0开始支持。
>
> 此模块仅支持在ArkTS文件（文件后缀为`.ets`）中导入使用。

**起始版本：** 26.1.0

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```ts
import { ArkTSUtils, collections } from '@kit.ArkTS';
```

## AtomicIntegerArray

type AtomicIntegerArray = collections.Int8Array | collections.Uint8Array | collections.Int16Array | collections.Uint16Array | collections.Int32Array | collections.Uint32Array

支持原子元素操作的ArkTS整数`TypedArray`类型。

**起始版本：** 26.1.0

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

| 类型 | 说明 |
| ------ | ------ |
| [collections.Int8Array](arkts-apis-arkts-collections-Int8Array.md) | `Int8Array`类型的ArkTS数组。 |
| [collections.Uint8Array](arkts-apis-arkts-collections-Uint8Array.md) | `Uint8Array`类型的ArkTS数组。 |
| [collections.Int16Array](arkts-apis-arkts-collections-Int16Array.md) | `Int16Array`类型的ArkTS数组。 |
| [collections.Uint16Array](arkts-apis-arkts-collections-Uint16Array.md) | `Uint16Array`类型的ArkTS数组。 |
| [collections.Int32Array](arkts-apis-arkts-collections-Int32Array.md) | `Int32Array`类型的ArkTS数组。 |
| [collections.Uint32Array](arkts-apis-arkts-collections-Uint32Array.md) | `Uint32Array`类型的ArkTS数组。 |

## Atomics

为ArkTS整数`TypedArray`提供原子操作的类。

**起始版本：** 26.1.0

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

### add

static add(typedArray: AtomicIntegerArray, index: number, value: number): number

以原子方式将指定值与目标元素相加，并返回操作前的值。

**起始版本：** 26.1.0

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ---- | ------ |
| typedArray | [AtomicIntegerArray](#atomicintegerarray) | 是 | 包含目标元素的整数`TypedArray`。 |
| index | number | 是 | 目标元素的索引。 索引从0开始，应小于`typedArray.length`。 |
| value | number | 是 | 要相加的值。 |

**返回值：**

| 类型 | 说明 |
| ------ | ------ |
| number | 操作前的元素值。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| ------ | ------ |
| 10200001 | The value of index is out of range. |

**示例：**

```ts
import { ArkTSUtils, collections } from '@kit.ArkTS';

let array = new collections.Int32Array(1);
array[0] = 10;
console.info(`操作前：${array[0]}`); // 预期输出：操作前：10

let result = ArkTSUtils.Atomics.add(array, 0, 3);
console.info(`返回值：${result}`); // 预期输出：返回值：10
console.info(`操作后：${array[0]}`); // 预期输出：操作后：13
```

### and

static and(typedArray: AtomicIntegerArray, index: number, value: number): number

以原子方式执行按位与运算，并返回操作前的值。

**起始版本：** 26.1.0

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ---- | ------ |
| typedArray | [AtomicIntegerArray](#atomicintegerarray) | 是 | 包含目标元素的整数`TypedArray`。 |
| index | number | 是 | 目标元素的索引。 索引从0开始，应小于`typedArray.length`。 |
| value | number | 是 | 用于按位与运算的值。 |

**返回值：**

| 类型 | 说明 |
| ------ | ------ |
| number | 操作前的元素值。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| ------ | ------ |
| 10200001 | The value of index is out of range. |

**示例：**

```ts
import { ArkTSUtils, collections } from '@kit.ArkTS';

let array = new collections.Int32Array(1);
array[0] = 10;
console.info(`操作前：${array[0]}`); // 预期输出：操作前：10

// 10的二进制为1010，3的二进制为0011。
let result = ArkTSUtils.Atomics.and(array, 0, 3);
console.info(`返回值：${result}`); // 预期输出：返回值：10
console.info(`操作后：${array[0]}`); // 预期输出：操作后：2
```

### compareExchange

static compareExchange(typedArray: AtomicIntegerArray, index: number, expectedValue: number, replacementValue: number): number

目标元素与预期值相等时，以原子方式替换并返回操作前的值。

**起始版本：** 26.1.0

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ---- | ------ |
| typedArray | [AtomicIntegerArray](#atomicintegerarray) | 是 | 包含目标元素的整数`TypedArray`。 |
| index | number | 是 | 目标元素的索引。 索引从0开始，应小于`typedArray.length`。 |
| expectedValue | number | 是 | 用于与目标元素比较的值。 |
| replacementValue | number | 是 | 比较成功时存储的值。 |

**返回值：**

| 类型 | 说明 |
| ------ | ------ |
| number | 操作前的元素值。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| ------ | ------ |
| 10200001 | The value of index is out of range. |

**示例：**

```ts
import { ArkTSUtils, collections } from '@kit.ArkTS';

let array = new collections.Int32Array(1);
array[0] = 10;
console.info(`操作前：${array[0]}`); // 预期输出：操作前：10

let result = ArkTSUtils.Atomics.compareExchange(array, 0, 10, 3);
console.info(`返回值：${result}`); // 预期输出：返回值：10
console.info(`操作后：${array[0]}`); // 预期输出：操作后：3

// 当前值已变为3，与预期值10不相等，因此不会替换为20。
let unmatched = ArkTSUtils.Atomics.compareExchange(array, 0, 10, 20);
console.info(`比较失败的返回值：${unmatched}`); // 预期输出：比较失败的返回值：3
console.info(`比较失败后的值：${array[0]}`); // 预期输出：比较失败后的值：3
```

### exchange

static exchange(typedArray: AtomicIntegerArray, index: number, value: number): number

以原子方式替换目标元素，并返回操作前的值。

**起始版本：** 26.1.0

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ---- | ------ |
| typedArray | [AtomicIntegerArray](#atomicintegerarray) | 是 | 包含目标元素的整数`TypedArray`。 |
| index | number | 是 | 目标元素的索引。 索引从0开始，应小于`typedArray.length`。 |
| value | number | 是 | 替换值。 |

**返回值：**

| 类型 | 说明 |
| ------ | ------ |
| number | 操作前的元素值。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| ------ | ------ |
| 10200001 | The value of index is out of range. |

**示例：**

```ts
import { ArkTSUtils, collections } from '@kit.ArkTS';

let array = new collections.Int32Array(1);
array[0] = 10;
console.info(`操作前：${array[0]}`); // 预期输出：操作前：10

let result = ArkTSUtils.Atomics.exchange(array, 0, 3);
console.info(`返回值：${result}`); // 预期输出：返回值：10
console.info(`操作后：${array[0]}`); // 预期输出：操作后：3
```

### isLockFree

static isLockFree(size: number): boolean

返回指定字节大小的原子操作是否无锁。

**起始版本：** 26.1.0

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ---- | ------ |
| size | number | 是 | 要查询的元素字节大小，而非数组长度。该值按32位整数转换；转换后为1、2、4或8时返回`true`，其他值返回`false`。 |

**返回值：**

| 类型 | 说明 |
| ------ | ------ |
| boolean | 如果指定大小的原子操作无锁，则返回`true`；否则返回`false`。 |

**示例：**

```ts
import { ArkTSUtils } from '@kit.ArkTS';

let result = ArkTSUtils.Atomics.isLockFree(4);
console.info(`是否无锁：${result}`); // 预期输出：是否无锁：true
```

### load

static load(typedArray: AtomicIntegerArray, index: number): number

以原子方式读取并返回目标元素。

**起始版本：** 26.1.0

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ---- | ------ |
| typedArray | [AtomicIntegerArray](#atomicintegerarray) | 是 | 包含目标元素的整数`TypedArray`。 |
| index | number | 是 | 目标元素的索引。 索引从0开始，应小于`typedArray.length`。 |

**返回值：**

| 类型 | 说明 |
| ------ | ------ |
| number | 目标元素的值。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| ------ | ------ |
| 10200001 | The value of index is out of range. |

**示例：**

```ts
import { ArkTSUtils, collections } from '@kit.ArkTS';

let array = new collections.Int32Array(1);
array[0] = 10;
console.info(`操作前：${array[0]}`); // 预期输出：操作前：10

let result = ArkTSUtils.Atomics.load(array, 0);
console.info(`返回值：${result}`); // 预期输出：返回值：10
console.info(`操作后：${array[0]}`); // 预期输出：操作后：10
```

### or

static or(typedArray: AtomicIntegerArray, index: number, value: number): number

以原子方式执行按位或运算，并返回操作前的值。

**起始版本：** 26.1.0

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ---- | ------ |
| typedArray | [AtomicIntegerArray](#atomicintegerarray) | 是 | 包含目标元素的整数`TypedArray`。 |
| index | number | 是 | 目标元素的索引。 索引从0开始，应小于`typedArray.length`。 |
| value | number | 是 | 用于按位或运算的值。 |

**返回值：**

| 类型 | 说明 |
| ------ | ------ |
| number | 操作前的元素值。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| ------ | ------ |
| 10200001 | The value of index is out of range. |

**示例：**

```ts
import { ArkTSUtils, collections } from '@kit.ArkTS';

let array = new collections.Int32Array(1);
array[0] = 10;
console.info(`操作前：${array[0]}`); // 预期输出：操作前：10

// 10的二进制为1010，3的二进制为0011。
let result = ArkTSUtils.Atomics.or(array, 0, 3);
console.info(`返回值：${result}`); // 预期输出：返回值：10
console.info(`操作后：${array[0]}`); // 预期输出：操作后：11
```

### store

static store(typedArray: AtomicIntegerArray, index: number, value: number): number

以原子方式将`value`整数化后写入目标元素，并返回整数化后的`value`。写入时还会根据目标元素的位宽和符号进行类型转换，因此返回值不一定等于实际存入的元素值。

**起始版本：** 26.1.0

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ---- | ------ |
| typedArray | [AtomicIntegerArray](#atomicintegerarray) | 是 | 包含目标元素的整数`TypedArray`。 |
| index | number | 是 | 目标元素的索引。 索引从0开始，应小于`typedArray.length`。 |
| value | number | 是 | 要存储的值。先转换为整数，再按目标元素类型写入。超出目标元素类型表示范围时，按该类型的位宽和符号转换。 |

**返回值：**

| 类型 | 说明 |
| ------ | ------ |
| number | `value`整数化后的值，不包含写入目标元素时按位宽和符号进行的类型转换。例如，向`collections.Uint8Array`写入257时返回257，但实际存入的元素值为1。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| ------ | ------ |
| 10200001 | The value of index is out of range. |

**示例：**

```ts
import { ArkTSUtils, collections } from '@kit.ArkTS';

let array = new collections.Int32Array(1);
array[0] = 10;
console.info(`操作前：${array[0]}`); // 预期输出：操作前：10

let result = ArkTSUtils.Atomics.store(array, 0, 3);
console.info(`返回值：${result}`); // 预期输出：返回值：3
console.info(`操作后：${array[0]}`); // 预期输出：操作后：3

// Uint8Array的元素范围为0~255，展示返回值与实际存储值的区别。
let uint8Array = new collections.Uint8Array(1);
uint8Array[0] = 10;
console.info(`操作前：${uint8Array[0]}`); // 预期输出：操作前：10

let converted = ArkTSUtils.Atomics.store(uint8Array, 0, 257);
console.info(`返回值：${converted}`); // 预期输出：返回值：257
console.info(`操作后：${uint8Array[0]}`); // 预期输出：操作后：1
```

### sub

static sub(typedArray: AtomicIntegerArray, index: number, value: number): number

以原子方式从目标元素减去指定值，并返回操作前的值。

**起始版本：** 26.1.0

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ---- | ------ |
| typedArray | [AtomicIntegerArray](#atomicintegerarray) | 是 | 包含目标元素的整数`TypedArray`。 |
| index | number | 是 | 目标元素的索引。 索引从0开始，应小于`typedArray.length`。 |
| value | number | 是 | 要减去的值。 |

**返回值：**

| 类型 | 说明 |
| ------ | ------ |
| number | 操作前的元素值。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| ------ | ------ |
| 10200001 | The value of index is out of range. |

**示例：**

```ts
import { ArkTSUtils, collections } from '@kit.ArkTS';

let array = new collections.Int32Array(1);
array[0] = 10;
console.info(`操作前：${array[0]}`); // 预期输出：操作前：10

let result = ArkTSUtils.Atomics.sub(array, 0, 3);
console.info(`返回值：${result}`); // 预期输出：返回值：10
console.info(`操作后：${array[0]}`); // 预期输出：操作后：7
```

### wait

static wait(typedArray: collections.Int32Array, index: number, value: number, timeout?: number): 'ok' | 'not-equal' | 'timed-out'

当指定Int32元素等于预期值时，阻塞当前线程，直到收到[notify](#notify)通知或等待超时。值不相等时返回`'not-equal'`，不进入等待。仅修改目标元素的值不会自动唤醒等待线程。

调用线程必须允许阻塞等待。接口会先检查线程是否允许阻塞，再比较元素值；即使`timeout`为0或元素值与预期值不相等，也必须满足该环境要求。不允许阻塞时抛出参数错误。应在允许阻塞的Worker线程中调用，避免阻塞UI线程。

**起始版本：** 26.1.0

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ---- | ------ |
| typedArray | [collections.Int32Array](arkts-apis-arkts-collections-Int32Array.md) | 是 | 包含目标元素的`Int32Array`。 |
| index | number | 是 | 目标元素的索引。 索引从0开始，应小于`typedArray.length`。 |
| value | number | 是 | 预期值。 |
| timeout | number | 否 | 最长等待时间，单位为毫秒。省略、传入`NaN`或正无穷时，若元素值等于预期值，则持续等待直到收到通知；负数按0处理。为0且元素值等于预期值时，立即返回`'timed-out'`。需要限制等待时间时，传入有限的非负数。 |

**返回值：**

| 类型 | 说明 |
| ------ | ------ |
| 'ok' \| 'not-equal' \| 'timed-out' | 等待结果。`'ok'`表示被通知唤醒；`'not-equal'`表示目标元素不等于预期值，未进入等待；`'timed-out'`表示等待超时。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| ------ | ------ |
| 10200001 | The value of index is out of range. |

**示例：**

```ts
import { ArkTSUtils, collections } from '@kit.ArkTS';

let array = new collections.Int32Array(1);
array[0] = 10;
console.info(`操作前：${array[0]}`); // 预期输出：操作前：10

// 此示例须在允许阻塞等待的Worker线程中运行。
// 当前值为10，与预期值9不相等，立即返回且不修改元素。
let result = ArkTSUtils.Atomics.wait(array, 0, 9, 0);
console.info(`返回值：${result}`); // 预期输出：返回值：not-equal
console.info(`操作后：${array[0]}`); // 预期输出：操作后：10
```

### notify

static notify(typedArray: collections.Int32Array, index: number, count?: number): number

通知通过[wait](#wait)等待指定Int32元素的线程，并返回已通知的线程数。等待与通知必须针对同一底层缓冲区的同一字节位置；不同数组中相同的数值索引不代表同一等待位置。使用同一缓冲区的不同视图时，还需考虑视图的`byteOffset`。

此方法仅发送通知，不修改目标元素。通知只作用于当前已进入等待的线程，不会为后续`wait`调用保留。需要通知等待线程读取新值时，应先写入新值，再调用`notify`。

**起始版本：** 26.1.0

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ---- | ------ |
| typedArray | [collections.Int32Array](arkts-apis-arkts-collections-Int32Array.md) | 是 | 包含目标元素的`Int32Array`。 |
| index | number | 是 | 目标元素的索引。 索引从0开始，应小于`typedArray.length`。 |
| count | number | 否 | 要通知的最大等待线程数。省略或传入正无穷时通知全部等待线程；为0或负数时不通知；非整数截去小数部分。 |

**返回值：**

| 类型 | 说明 |
| ------ | ------ |
| number | 已通知的等待线程数。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| ------ | ------ |
| 10200001 | The value of index is out of range. |

**示例：**

```ts
import { ArkTSUtils, collections } from '@kit.ArkTS';

let array = new collections.Int32Array(1);
array[0] = 10;
console.info(`操作前：${array[0]}`); // 预期输出：操作前：10

// 当前没有等待线程，通知数量为0；notify不修改元素。
let result = ArkTSUtils.Atomics.notify(array, 0, 1);
console.info(`返回值：${result}`); // 预期输出：返回值：0
console.info(`操作后：${array[0]}`); // 预期输出：操作后：10
```

### xor

static xor(typedArray: AtomicIntegerArray, index: number, value: number): number

以原子方式执行按位异或运算，并返回操作前的值。

**起始版本：** 26.1.0

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ---- | ------ |
| typedArray | [AtomicIntegerArray](#atomicintegerarray) | 是 | 包含目标元素的整数`TypedArray`。 |
| index | number | 是 | 目标元素的索引。 索引从0开始，应小于`typedArray.length`。 |
| value | number | 是 | 用于按位异或运算的值。 |

**返回值：**

| 类型 | 说明 |
| ------ | ------ |
| number | 操作前的元素值。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| ------ | ------ |
| 10200001 | The value of index is out of range. |

**示例：**

```ts
import { ArkTSUtils, collections } from '@kit.ArkTS';

let array = new collections.Int32Array(1);
array[0] = 10;
console.info(`操作前：${array[0]}`); // 预期输出：操作前：10

// 10的二进制为1010，3的二进制为0011。
let result = ArkTSUtils.Atomics.xor(array, 0, 3);
console.info(`返回值：${result}`); // 预期输出：返回值：10
console.info(`操作后：${array[0]}`); // 预期输出：操作后：9
```
