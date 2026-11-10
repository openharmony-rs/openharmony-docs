# Atomics

```TypeScript
class Atomics
```

为以ArkTS ArrayBuffer为底层缓冲区的整数TypedArray提供原子操作。与ECMAScript内置Atomics对象不同，此类通过utils模块提供，仅包含面向ArkTS TypedArray的静态方法。

**起始版本：** 26.1.0

<!--Device-utils-class Atomics--><!--Device-utils-class Atomics-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { ArkTSUtils } from '@kit.ArkTS';
```

## add

```TypeScript
static add(typedArray: AtomicIntegerArray, index: number, value: number): number
```

以原子方式将指定值与目标元素相加，并返回操作前的值。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-Atomics-static add(typedArray: AtomicIntegerArray, index: number, value: number): number--><!--Device-Atomics-static add(typedArray: AtomicIntegerArray, index: number, value: number): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typedArray | [AtomicIntegerArray](arkts-arkts-atomicintegerarray-t.md) | 是 | 包含目标元素的整数TypedArray。 |
| index | number | 是 | 目标元素的索引。索引从0开始，应小于typedArray.length。 |
| value | number | 是 | 要相加的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 操作前的元素值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

## and

```TypeScript
static and(typedArray: AtomicIntegerArray, index: number, value: number): number
```

以原子方式执行按位与运算，并返回操作前的值。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-Atomics-static and(typedArray: AtomicIntegerArray, index: number, value: number): number--><!--Device-Atomics-static and(typedArray: AtomicIntegerArray, index: number, value: number): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typedArray | [AtomicIntegerArray](arkts-arkts-atomicintegerarray-t.md) | 是 | 包含目标元素的整数TypedArray。 |
| index | number | 是 | 目标元素的索引。索引从0开始，应小于typedArray.length。 |
| value | number | 是 | 用于按位与运算的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 操作前的元素值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

## compareExchange

```TypeScript
static compareExchange(typedArray: AtomicIntegerArray, index: number, expectedValue: number,
      replacementValue: number): number
```

目标元素与预期值相等时，以原子方式替换并返回操作前的值。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-Atomics-static compareExchange(typedArray: AtomicIntegerArray, index: number, expectedValue: number,      replacementValue: number): number--><!--Device-Atomics-static compareExchange(typedArray: AtomicIntegerArray, index: number, expectedValue: number,      replacementValue: number): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typedArray | [AtomicIntegerArray](arkts-arkts-atomicintegerarray-t.md) | 是 | 包含目标元素的整数TypedArray。 |
| index | number | 是 | 目标元素的索引。索引从0开始，应小于typedArray.length。 |
| expectedValue | number | 是 | 用于与目标元素比较的值。 |
| replacementValue | number | 是 | 比较成功时存储的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 操作前的元素值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

## exchange

```TypeScript
static exchange(typedArray: AtomicIntegerArray, index: number, value: number): number
```

以原子方式替换目标元素，并返回操作前的值。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-Atomics-static exchange(typedArray: AtomicIntegerArray, index: number, value: number): number--><!--Device-Atomics-static exchange(typedArray: AtomicIntegerArray, index: number, value: number): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typedArray | [AtomicIntegerArray](arkts-arkts-atomicintegerarray-t.md) | 是 | 包含目标元素的整数TypedArray。 |
| index | number | 是 | 目标元素的索引。索引从0开始，应小于typedArray.length。 |
| value | number | 是 | 替换值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 操作前的元素值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

## isLockFree

```TypeScript
static isLockFree(size: number): boolean
```

返回指定字节大小的原子操作是否无锁。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-Atomics-static isLockFree(size: number): boolean--><!--Device-Atomics-static isLockFree(size: number): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 要查询的元素字节大小，而非数组长度。该值按32位整数转换；转换后为1、2、4或8时返回true，其他值返回false。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果指定大小的原子操作无锁，则返回true；否则返回false。 |

## load

```TypeScript
static load(typedArray: AtomicIntegerArray, index: number): number
```

以原子方式读取并返回目标元素。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-Atomics-static load(typedArray: AtomicIntegerArray, index: number): number--><!--Device-Atomics-static load(typedArray: AtomicIntegerArray, index: number): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typedArray | [AtomicIntegerArray](arkts-arkts-atomicintegerarray-t.md) | 是 | 包含目标元素的整数TypedArray。 |
| index | number | 是 | 目标元素的索引。索引从0开始，应小于typedArray.length。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 目标元素的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

## notify

```TypeScript
static notify(typedArray: collections.Int32Array, index: number, count?: number): number
```

通知等待指定Int32元素的线程，并返回已通知的线程数。

等待与通知必须针对同一底层缓冲区的同一字节位置；不同数组中相同的数值索引不代表同一等待位置。使用同一缓冲区的不同视图时，还需考虑byteOffset。此方法仅发送通知，不修改目标元素。通知只作用于当前已进入等待的线程，不会为后续wait调用保留。需要通知等待线程读取新值时，应先写入新值，再调用notify。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-Atomics-static notify(typedArray: collections.Int32Array, index: number, count?: number): number--><!--Device-Atomics-static notify(typedArray: collections.Int32Array, index: number, count?: number): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typedArray | [collections.Int32Array](arkts-arkts-collections-int32array-c.md) | 是 | 包含目标元素的Int32Array。 |
| index | number | 是 | 目标元素的索引。索引从0开始，应小于typedArray.length。 |
| count | number | 否 | 要通知的最大等待线程数。省略或传入正无穷时通知全部等待线程；为0或负数时不通知；非整数截去小数部分。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 已通知的等待线程数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

## or

```TypeScript
static or(typedArray: AtomicIntegerArray, index: number, value: number): number
```

以原子方式执行按位或运算，并返回操作前的值。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-Atomics-static or(typedArray: AtomicIntegerArray, index: number, value: number): number--><!--Device-Atomics-static or(typedArray: AtomicIntegerArray, index: number, value: number): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typedArray | [AtomicIntegerArray](arkts-arkts-atomicintegerarray-t.md) | 是 | 包含目标元素的整数TypedArray。 |
| index | number | 是 | 目标元素的索引。索引从0开始，应小于typedArray.length。 |
| value | number | 是 | 用于按位或运算的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 操作前的元素值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

## store

```TypeScript
static store(typedArray: AtomicIntegerArray, index: number, value: number): number
```

以原子方式将value整数化后写入目标元素，并返回整数化后的value。

返回值是value整数化后的值，不包含写入目标元素时按位宽和符号进行的类型转换，因此不一定等于实际存入的元素值。例如向collections.Uint8Array写入257时返回257，但实际存入的元素值为1。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-Atomics-static store(typedArray: AtomicIntegerArray, index: number, value: number): number--><!--Device-Atomics-static store(typedArray: AtomicIntegerArray, index: number, value: number): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typedArray | [AtomicIntegerArray](arkts-arkts-atomicintegerarray-t.md) | 是 | 包含目标元素的整数TypedArray。 |
| index | number | 是 | 目标元素的索引。索引从0开始，应小于typedArray.length。 |
| value | number | 是 | 要存储的值。先转换为整数，再按目标元素类型写入。超出目标元素类型表示范围时，按该类型的位宽和符号转换。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | value整数化后的值，不包含按目标元素位宽和符号进行的类型转换。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

## sub

```TypeScript
static sub(typedArray: AtomicIntegerArray, index: number, value: number): number
```

以原子方式从目标元素减去指定值，并返回操作前的值。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-Atomics-static sub(typedArray: AtomicIntegerArray, index: number, value: number): number--><!--Device-Atomics-static sub(typedArray: AtomicIntegerArray, index: number, value: number): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typedArray | [AtomicIntegerArray](arkts-arkts-atomicintegerarray-t.md) | 是 | 包含目标元素的整数TypedArray。 |
| index | number | 是 | 目标元素的索引。索引从0开始，应小于typedArray.length。 |
| value | number | 是 | 要减去的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 操作前的元素值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

## wait

```TypeScript
static wait(typedArray: collections.Int32Array, index: number, value: number,
      timeout?: number): 'ok' | 'not-equal' | 'timed-out'
```

当指定Int32元素等于预期值时等待。

当元素等于预期值时阻塞当前线程，直到收到notify通知或等待超时。值不相等时返回not-equal，不进入等待。仅修改目标元素的值不会自动唤醒等待线程。调用线程必须允许阻塞等待；接口先检查线程是否允许阻塞，再比较元素值，即使timeout为0或元素值不等也必须满足此要求。不允许阻塞时抛出参数错误。应在允许阻塞的Worker线程中调用，避免阻塞UI线程。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-Atomics-static wait(typedArray: collections.Int32Array, index: number, value: number,      timeout?: number): 'ok' | 'not-equal' | 'timed-out'--><!--Device-Atomics-static wait(typedArray: collections.Int32Array, index: number, value: number,      timeout?: number): 'ok' | 'not-equal' | 'timed-out'-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typedArray | [collections.Int32Array](arkts-arkts-collections-int32array-c.md) | 是 | 包含目标元素的Int32Array。 |
| index | number | 是 | 目标元素的索引。索引从0开始，应小于typedArray.length。 |
| value | number | 是 | 预期值。 |
| timeout | number | 否 | 最长等待时间，单位为毫秒。省略、传入NaN或正无穷时，若元素值等于预期值，则持续等待直到收到通知；负数按0处理。为0且元素值等于预期值时，立即返回timed-out。需要限制等待时间时，传入有限的非负数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| 'ok' &#124; 'not-equal' &#124; 'timed-out' | 等待结果。ok表示被通知唤醒；not-equal表示目标元素不等于预期值，未进入等待；timed-out表示等待超时。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

## xor

```TypeScript
static xor(typedArray: AtomicIntegerArray, index: number, value: number): number
```

以原子方式执行按位异或运算，并返回操作前的值。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-Atomics-static xor(typedArray: AtomicIntegerArray, index: number, value: number): number--><!--Device-Atomics-static xor(typedArray: AtomicIntegerArray, index: number, value: number): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typedArray | [AtomicIntegerArray](arkts-arkts-atomicintegerarray-t.md) | 是 | 包含目标元素的整数TypedArray。 |
| index | number | 是 | 目标元素的索引。索引从0开始，应小于typedArray.length。 |
| value | number | 是 | 用于按位异或运算的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 操作前的元素值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |
