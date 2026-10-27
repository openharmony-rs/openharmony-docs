# Atomics

```TypeScript
class Atomics
```

Provides atomic operations for ArkTS integer typed arrays backed by an ArkTS ArrayBuffer. Unlike the ECMAScript built-in Atomics object, this class is exposed through the utils module and provides only static methods for ArkTS typed arrays.

**Since:** 26.1.0

<!--Device-utils-class Atomics--><!--Device-utils-class Atomics-End-->

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { ArkTSUtils } from '@kit.ArkTS';
```

## add

```TypeScript
static add(typedArray: AtomicIntegerArray, index: number, value: number): number
```

Atomically adds a value and returns the previous value.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-Atomics-static add(typedArray: AtomicIntegerArray, index: number, value: number): number--><!--Device-Atomics-static add(typedArray: AtomicIntegerArray, index: number, value: number): number-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | [AtomicIntegerArray](arkts-arkts-atomicintegerarray-t.md) | Yes | Integer typed array containing the target element. |
| index | number | Yes | Index of the target element. |
| value | number | Yes | Value to add. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Value of the element before the operation. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of index is out of range. |

## and

```TypeScript
static and(typedArray: AtomicIntegerArray, index: number, value: number): number
```

Atomically applies bitwise AND and returns the previous value.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-Atomics-static and(typedArray: AtomicIntegerArray, index: number, value: number): number--><!--Device-Atomics-static and(typedArray: AtomicIntegerArray, index: number, value: number): number-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | [AtomicIntegerArray](arkts-arkts-atomicintegerarray-t.md) | Yes | Integer typed array containing the target element. |
| index | number | Yes | Index of the target element. |
| value | number | Yes | Value used in the bitwise AND operation. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Value of the element before the operation. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of index is out of range. |

## compareExchange

```TypeScript
static compareExchange(typedArray: AtomicIntegerArray, index: number, expectedValue: number,
      replacementValue: number): number
```

Atomically replaces a matching value and returns the previous value.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-Atomics-static compareExchange(typedArray: AtomicIntegerArray, index: number, expectedValue: number,      replacementValue: number): number--><!--Device-Atomics-static compareExchange(typedArray: AtomicIntegerArray, index: number, expectedValue: number,      replacementValue: number): number-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | [AtomicIntegerArray](arkts-arkts-atomicintegerarray-t.md) | Yes | Integer typed array containing the target element. |
| index | number | Yes | Index of the target element. |
| expectedValue | number | Yes | Value to compare with the target element. |
| replacementValue | number | Yes | Value stored when the comparison succeeds. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Value of the element before the operation. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of index is out of range. |

## exchange

```TypeScript
static exchange(typedArray: AtomicIntegerArray, index: number, value: number): number
```

Atomically replaces a value and returns the previous value.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-Atomics-static exchange(typedArray: AtomicIntegerArray, index: number, value: number): number--><!--Device-Atomics-static exchange(typedArray: AtomicIntegerArray, index: number, value: number): number-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | [AtomicIntegerArray](arkts-arkts-atomicintegerarray-t.md) | Yes | Integer typed array containing the target element. |
| index | number | Yes | Index of the target element. |
| value | number | Yes | Replacement value. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Value of the element before the operation. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of index is out of range. |

## isLockFree

```TypeScript
static isLockFree(size: number): boolean
```

Returns whether atomic operations of the specified byte size are lock-free.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-Atomics-static isLockFree(size: number): boolean--><!--Device-Atomics-static isLockFree(size: number): boolean-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | number | Yes | Size of the atomic operation, in bytes. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if atomic operations of the specified size are lock-free; otherwise false. |

## load

```TypeScript
static load(typedArray: AtomicIntegerArray, index: number): number
```

Atomically loads and returns a value.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-Atomics-static load(typedArray: AtomicIntegerArray, index: number): number--><!--Device-Atomics-static load(typedArray: AtomicIntegerArray, index: number): number-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | [AtomicIntegerArray](arkts-arkts-atomicintegerarray-t.md) | Yes | Integer typed array containing the target element. |
| index | number | Yes | Index of the target element. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Value of the target element. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of index is out of range. |

## notify

```TypeScript
static notify(typedArray: collections.Int32Array, index: number, count?: number): number
```

Notifies waiters on the selected Int32 element and returns the number notified.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-Atomics-static notify(typedArray: collections.Int32Array, index: number, count?: number): number--><!--Device-Atomics-static notify(typedArray: collections.Int32Array, index: number, count?: number): number-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | [collections.Int32Array](arkts-arkts-collections-int32array-c.md) | Yes | Int32Array containing the target element. |
| index | number | Yes | Index of the target element. |
| count | number | No | Maximum number of waiters to notify. By default, all waiters are notified. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of waiters notified. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of index is out of range. |

## or

```TypeScript
static or(typedArray: AtomicIntegerArray, index: number, value: number): number
```

Atomically applies bitwise OR and returns the previous value.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-Atomics-static or(typedArray: AtomicIntegerArray, index: number, value: number): number--><!--Device-Atomics-static or(typedArray: AtomicIntegerArray, index: number, value: number): number-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | [AtomicIntegerArray](arkts-arkts-atomicintegerarray-t.md) | Yes | Integer typed array containing the target element. |
| index | number | Yes | Index of the target element. |
| value | number | Yes | Value used in the bitwise OR operation. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Value of the element before the operation. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of index is out of range. |

## store

```TypeScript
static store(typedArray: AtomicIntegerArray, index: number, value: number): number
```

Atomically stores a value and returns the converted stored value.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-Atomics-static store(typedArray: AtomicIntegerArray, index: number, value: number): number--><!--Device-Atomics-static store(typedArray: AtomicIntegerArray, index: number, value: number): number-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | [AtomicIntegerArray](arkts-arkts-atomicintegerarray-t.md) | Yes | Integer typed array containing the target element. |
| index | number | Yes | Index of the target element. |
| value | number | Yes | Value to store. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Converted value stored in the target element. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of index is out of range. |

## sub

```TypeScript
static sub(typedArray: AtomicIntegerArray, index: number, value: number): number
```

Atomically subtracts a value and returns the previous value.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-Atomics-static sub(typedArray: AtomicIntegerArray, index: number, value: number): number--><!--Device-Atomics-static sub(typedArray: AtomicIntegerArray, index: number, value: number): number-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | [AtomicIntegerArray](arkts-arkts-atomicintegerarray-t.md) | Yes | Integer typed array containing the target element. |
| index | number | Yes | Index of the target element. |
| value | number | Yes | Value to subtract. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Value of the element before the operation. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of index is out of range. |

## wait

```TypeScript
static wait(typedArray: collections.Int32Array, index: number, value: number,
      timeout?: number): 'ok' | 'not-equal' | 'timed-out'
```

Waits while the selected Int32 element equals the expected value.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-Atomics-static wait(typedArray: collections.Int32Array, index: number, value: number,      timeout?: number): 'ok' | 'not-equal' | 'timed-out'--><!--Device-Atomics-static wait(typedArray: collections.Int32Array, index: number, value: number,      timeout?: number): 'ok' | 'not-equal' | 'timed-out'-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | [collections.Int32Array](arkts-arkts-collections-int32array-c.md) | Yes | Int32Array containing the target element. |
| index | number | Yes | Index of the target element. |
| value | number | Yes | Expected value. |
| timeout | number | No | Maximum wait time, in milliseconds. The default value is positive infinity. |

**Return value:**

| Type | Description |
| --- | --- |
| 'ok' &#124; 'not-equal' &#124; 'timed-out' | Result of the wait operation. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of index is out of range. |

## xor

```TypeScript
static xor(typedArray: AtomicIntegerArray, index: number, value: number): number
```

Atomically applies bitwise XOR and returns the previous value.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-Atomics-static xor(typedArray: AtomicIntegerArray, index: number, value: number): number--><!--Device-Atomics-static xor(typedArray: AtomicIntegerArray, index: number, value: number): number-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedArray | [AtomicIntegerArray](arkts-arkts-atomicintegerarray-t.md) | Yes | Integer typed array containing the target element. |
| index | number | Yes | Index of the target element. |
| value | number | Yes | Value used in the bitwise XOR operation. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Value of the element before the operation. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of index is out of range. |
