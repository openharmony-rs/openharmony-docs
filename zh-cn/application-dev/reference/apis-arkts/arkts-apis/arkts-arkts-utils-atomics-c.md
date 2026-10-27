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
| index | number | 是 | 目标元素的索引。 |
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
| index | number | 是 | 目标元素的索引。 |
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
| index | number | 是 | 目标元素的索引。 |
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
| index | number | 是 | 目标元素的索引。 |
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
| size | number | 是 | 原子操作的字节大小。 |

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
| index | number | 是 | 目标元素的索引。 |

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

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-Atomics-static notify(typedArray: collections.Int32Array, index: number, count?: number): number--><!--Device-Atomics-static notify(typedArray: collections.Int32Array, index: number, count?: number): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typedArray | [collections.Int32Array](arkts-arkts-collections-int32array-c.md) | 是 | 包含目标元素的Int32Array。 |
| index | number | 是 | 目标元素的索引。 |
| count | number | 否 | 要通知的最大等待线程数，默认通知全部等待线程。 |

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
| index | number | 是 | 目标元素的索引。 |
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

以原子方式存储值，并返回转换后的存储值。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-Atomics-static store(typedArray: AtomicIntegerArray, index: number, value: number): number--><!--Device-Atomics-static store(typedArray: AtomicIntegerArray, index: number, value: number): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typedArray | [AtomicIntegerArray](arkts-arkts-atomicintegerarray-t.md) | 是 | 包含目标元素的整数TypedArray。 |
| index | number | 是 | 目标元素的索引。 |
| value | number | 是 | 要存储的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 存入目标元素的转换后值。 |

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
| index | number | 是 | 目标元素的索引。 |
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

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-Atomics-static wait(typedArray: collections.Int32Array, index: number, value: number,      timeout?: number): 'ok' | 'not-equal' | 'timed-out'--><!--Device-Atomics-static wait(typedArray: collections.Int32Array, index: number, value: number,      timeout?: number): 'ok' | 'not-equal' | 'timed-out'-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typedArray | [collections.Int32Array](arkts-arkts-collections-int32array-c.md) | 是 | 包含目标元素的Int32Array。 |
| index | number | 是 | 目标元素的索引。 |
| value | number | 是 | 预期值。 |
| timeout | number | 否 | 最长等待时间，单位为毫秒，默认值为正无穷。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| 'ok' &#124; 'not-equal' &#124; 'timed-out' | 等待操作的结果。 |

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
| index | number | 是 | 目标元素的索引。 |
| value | number | 是 | 用于按位异或运算的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 操作前的元素值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |
