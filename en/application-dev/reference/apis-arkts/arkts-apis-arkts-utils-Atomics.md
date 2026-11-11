# Class (Atomics)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @huanghello-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=5e21320b086cc38c3f22d99f159dd89d7a573108 translatedAt=2026-11-03T13:36:55.587Z pushedAt=2026-11-04T06:57:10.286Z nl=1 -->

Provides atomic operations for integer `TypedArray` with ArkTS `ArrayBuffer` as the underlying buffer. This class is provided by the `ArkTSUtils` module. All methods are static methods and are called through `ArkTSUtils.Atomics`.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with the starting version in their respective API descriptions.
>
> The initial APIs of `Atomics` are supported since API version 26.1.0.
>
> This module can be imported and used only in ArkTS files (with the `.ets` file extension).

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

## Modules to Import

```ts
import { ArkTSUtils, collections } from '@kit.ArkTS';
```

## AtomicIntegerArray

type AtomicIntegerArray = collections.Int8Array | collections.Uint8Array | collections.Int16Array | collections.Uint16Array | collections.Int32Array | collections.Uint32Array

ArkTS integer `TypedArray` type that supports atomic element operations.

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

| Type | Description |
| ------ | ------ |
| [collections.Int8Array](arkts-apis-arkts-collections-Int8Array.md) | ArkTS array of the `Int8Array` type. |
| [collections.Uint8Array](arkts-apis-arkts-collections-Uint8Array.md) | ArkTS array of the `Uint8Array` type. |
| [collections.Int16Array](arkts-apis-arkts-collections-Int16Array.md) | ArkTS array of the `Int16Array` type. |
| [collections.Uint16Array](arkts-apis-arkts-collections-Uint16Array.md) | ArkTS array of the `Uint16Array` type. |
| [collections.Int32Array](arkts-apis-arkts-collections-Int32Array.md) | ArkTS array of the `Int32Array` type. |
| [collections.Uint32Array](arkts-apis-arkts-collections-Uint32Array.md) | ArkTS array of the `Uint32Array` type. |

## Atomics

A class that provides atomic operations for ArkTS integer `TypedArray`.

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

### add

static add(typedArray: AtomicIntegerArray, index: number, value: number): number

Atomically adds a specified value to the target element and returns the value before the operation.

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | ------ |
| typedArray | [AtomicIntegerArray](#atomicintegerarray) | Yes | Integer `TypedArray` that contains the target element. |
| index | number | Yes | Index of the target element. The index starts from 0 and should be less than `typedArray.length`. |
| value | number | Yes | Value to be added. |

**Returns**

| Type | Description |
| ------ | ------ |
| number | Element value before the operation. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID | Error Message |
| ------ | ------ |
| 10200001 | The value of index is out of range. |

**Example**

```ts
import { ArkTSUtils, collections } from '@kit.ArkTS';

let array = new collections.Int32Array(1);
array[0] = 10;
console.info(`Before operation: ${array[0]}`); // Expected output: Before operation: 10

let result = ArkTSUtils.Atomics.add(array, 0, 3);
console.info(`Return value: ${result}`); // Expected output: Return value: 10
console.info(`After operation: ${array[0]}`); // Expected output: After operation: 13
```

### and

static and(typedArray: AtomicIntegerArray, index: number, value: number): number

Performs a bitwise AND operation atomically and returns the value before the operation.

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | ------ |
| typedArray | [AtomicIntegerArray](#atomicintegerarray) | Yes | Integer `TypedArray` containing the target element. |
| index | number | Yes | Index of the target element. The index starts from 0 and should be less than `typedArray.length`. |
| value | number | Yes | Value used for the bitwise AND operation. |

**Returns**

| Type | Description |
| ------ | ------ |
| number | Element value before the operation. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID | Error Message |
| ------ | ------ |
| 10200001 | The value of index is out of range. |

**Example**

```ts
import { ArkTSUtils, collections } from '@kit.ArkTS';

let array = new collections.Int32Array(1);
array[0] = 10;
console.info(`Before operation: ${array[0]}`); // Expected output: Before operation: 10

// The binary of 10 is 1010, and the binary of 3 is 0011.
let result = ArkTSUtils.Atomics.and(array, 0, 3);
console.info(`Return value: ${result}`); // Expected output: Return value: 10
console.info(`After operation: ${array[0]}`); // Expected output: After operation: 2
```

### compareExchange

static compareExchange(typedArray: AtomicIntegerArray, index: number, expectedValue: number, replacementValue: number): number

When the target element equals the expected value, replaces it atomically and returns the value before the operation.

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | ------ |
| typedArray | [AtomicIntegerArray](#atomicintegerarray) | Yes | The integer `TypedArray` that contains the target element. |
| index | number | Yes | Index of the target element. The index starts from 0 and should be less than `typedArray.length`. |
| expectedValue | number | Yes | Value used to compare with the target element. |
| replacementValue | number | Yes | Value stored when the comparison succeeds. |

**Returns**

| Type | Description |
| ------ | ------ |
| number | Element value before the operation. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID | Error Message |
| ------ | ------ |
| 10200001 | The value of index is out of range. |

**Example**

```ts
import { ArkTSUtils, collections } from '@kit.ArkTS';

let array = new collections.Int32Array(1);
array[0] = 10;
console.info(`Before operation: ${array[0]}`); // Expected output: Before operation: 10

let result = ArkTSUtils.Atomics.compareExchange(array, 0, 10, 3);
console.info(`Return value: ${result}`); // Expected output: Return value: 10
console.info(`After operation: ${array[0]}`); // Expected output: After operation: 3

// The current value has become 3, which is not equal to the expected value 10, so it will not be replaced with 20.
let unmatched = ArkTSUtils.Atomics.compareExchange(array, 0, 10, 20);
console.info(`Return value when comparison fails: ${unmatched}`); // Expected output: Return value when comparison fails: 3
console.info(`Value after comparison fails: ${array[0]}`); // Expected output: Value after comparison fails: 3
```

### exchange

static exchange(typedArray: AtomicIntegerArray, index: number, value: number): number

Atomically replaces the target element and returns the value before the operation.

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | ------ |
| typedArray | [AtomicIntegerArray](#atomicintegerarray) | Yes | Integer `TypedArray` containing the target element. |
| index | number | Yes | Index of the target element. The index starts from 0 and should be less than `typedArray.length`. |
| value | number | Yes | Replacement value. |

**Returns**

| Type | Description |
| ------ | ------ |
| number | Element value before the operation. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID | Error Message |
| ------ | ------ |
| 10200001 | The value of index is out of range. |

**Example**

```ts
import { ArkTSUtils, collections } from '@kit.ArkTS';

let array = new collections.Int32Array(1);
array[0] = 10;
console.info(`Before operation: ${array[0]}`); // Expected output: Before operation: 10

let result = ArkTSUtils.Atomics.exchange(array, 0, 3);
console.info(`Return value: ${result}`); // Expected output: Return value: 10
console.info(`After operation: ${array[0]}`); // Expected output: After operation: 3
```

### isLockFree

static isLockFree(size: number): boolean

Returns whether the atomic operation of the specified byte size is lock-free.

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | ------ |
| size | number | Yes | Byte size of the element to query, not the array length. This value is converted to a 32-bit integer; if the converted value is 1, 2, 4, or 8, `true` is returned; otherwise, `false` is returned. |

**Returns**

| Type | Description |
| ------ | ------ |
| boolean | Returns `true` if the atomic operation of the specified size is lock-free; otherwise, returns `false`. |

**Example**

```ts
import { ArkTSUtils } from '@kit.ArkTS';

let result = ArkTSUtils.Atomics.isLockFree(4);
console.info(`Lock-free: ${result}`); // Expected output: Lock-free: true
```

### load

static load(typedArray: AtomicIntegerArray, index: number): number

Reads and returns the target element in an atomic manner.

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | ------ |
| typedArray | [AtomicIntegerArray](#atomicintegerarray) | Yes | Integer `TypedArray` that contains the target element. |
| index | number | Yes | Index of the target element. The index starts from 0 and should be less than `typedArray.length`. |

**Returns**

| Type | Description |
| ------ | ------ |
| number | Value of the target element. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID | Error Message |
| ------ | ------ |
| 10200001 | The value of index is out of range. |

**Example**

```ts
import { ArkTSUtils, collections } from '@kit.ArkTS';

let array = new collections.Int32Array(1);
array[0] = 10;
console.info(`Before operation: ${array[0]}`); // Expected output: Before operation: 10

let result = ArkTSUtils.Atomics.load(array, 0);
console.info(`Return value: ${result}`); // Expected output: Return value: 10
console.info(`After operation: ${array[0]}`); // Expected output: After operation: 10
```

### or

static or(typedArray: AtomicIntegerArray, index: number, value: number): number

Performs a bitwise OR operation in an atomic manner and returns the value before the operation.

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | ------ |
| typedArray | [AtomicIntegerArray](#atomicintegerarray) | Yes | Integer `TypedArray` that contains the target element. |
| index | number | Yes | Index of the target element. The index starts from 0 and should be less than `typedArray.length`. |
| value | number | Yes | Value used for the bitwise OR operation. |

**Returns**

| Type | Description |
| ------ | ------ |
| number | Element value before the operation. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID | Error Message |
| ------ | ------ |
| 10200001 | The value of index is out of range. |

**Example**

```ts
import { ArkTSUtils, collections } from '@kit.ArkTS';

let array = new collections.Int32Array(1);
array[0] = 10;
console.info(`Before operation: ${array[0]}`); // Expected output: Before operation: 10

// The binary of 10 is 1010, and the binary of 3 is 0011.
let result = ArkTSUtils.Atomics.or(array, 0, 3);
console.info(`Return value: ${result}`); // Expected output: Return value: 10
console.info(`After operation: ${array[0]}`); // Expected output: After operation: 11
```

### store

static store(typedArray: AtomicIntegerArray, index: number, value: number): number

Writes `value` to the target element in an atomic manner after integerizing it, and returns the integerized `value`. During the write, type conversion is also performed based on the bit width and sign of the target element, so the return value may not equal the element value actually stored.

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | ------ |
| typedArray | [AtomicIntegerArray](#atomicintegerarray) | Yes | Integer `TypedArray` that contains the target element. |
| index | number | Yes | Index of the target element. The index starts from 0 and must be less than `typedArray.length`. |
| value | number | Yes | Value to store. It is first converted to an integer and then written according to the target element type. If it exceeds the representable range of the target element type, it is converted according to the bit width and sign of that type. |

**Returns**

| Type | Description |
| ------ | ------ |
| number | Value after `value` is integerized, excluding the type conversion based on bit width and sign performed when writing to the target element. For example, writing 257 to `collections.Uint8Array` returns 257, but the element value actually stored is 1. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID | Error Message |
| ------ | ------ |
| 10200001 | The value of index is out of range. |

**Example**

```ts
import { ArkTSUtils, collections } from '@kit.ArkTS';

let array = new collections.Int32Array(1);
array[0] = 10;
console.info(`Before operation: ${array[0]}`); // Expected output: Before operation: 10

let result = ArkTSUtils.Atomics.store(array, 0, 3);
console.info(`Return value: ${result}`); // Expected output: Return value: 3
console.info(`After operation: ${array[0]}`); // Expected output: After operation: 3

// The element range of Uint8Array is 0 to 255, showing the difference between the return value and the actually stored value.
let uint8Array = new collections.Uint8Array(1);
uint8Array[0] = 10;
console.info(`Before operation: ${uint8Array[0]}`); // Expected output: Before operation: 10

let converted = ArkTSUtils.Atomics.store(uint8Array, 0, 257);
console.info(`Return value: ${converted}`); // Expected output: Return value: 257
console.info(`After operation: ${uint8Array[0]}`); // Expected output: After operation: 1
```

### sub

static sub(typedArray: AtomicIntegerArray, index: number, value: number): number

Subtracts a specified value from the target element in an atomic manner and returns the value before the operation.

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | ------ |
| typedArray | [AtomicIntegerArray](#atomicintegerarray) | Yes | Integer `TypedArray` containing the target element. |
| index | number | Yes | Index of the target element. The index starts from 0 and should be less than `typedArray.length`. |
| value | number | Yes | Value to be subtracted. |

**Returns**

| Type | Description |
| ------ | ------ |
| number | Element value before the operation. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID | Error Message |
| ------ | ------ |
| 10200001 | The value of index is out of range. |

**Example**

```ts
import { ArkTSUtils, collections } from '@kit.ArkTS';

let array = new collections.Int32Array(1);
array[0] = 10;
console.info(`Before operation: ${array[0]}`); // Expected output: Before operation: 10

let result = ArkTSUtils.Atomics.sub(array, 0, 3);
console.info(`Return value: ${result}`); // Expected output: Return value: 10
console.info(`After operation: ${array[0]}`); // Expected output: After operation: 7
```

### wait

static wait(typedArray: collections.Int32Array, index: number, value: number, timeout?: number): 'ok' | 'not-equal' | 'timed-out'

When the specified Int32 element equals the expected value, blocks the current thread until it receives a [notify](#notify) notification or the wait times out. If the values are not equal, returns `'not-equal'` without entering the wait. Merely modifying the value of the target element does not automatically wake up the waiting thread.

The calling thread must be allowed to block and wait. The API first checks whether the thread is allowed to block, and then compares the element value; even if `timeout` is 0 or the element value is not equal to the expected value, this environment requirement must still be met. If blocking is not allowed, a parameter error is thrown. It should be called in a Worker thread that allows blocking to avoid blocking the UI thread.

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | ------ |
| typedArray | [collections.Int32Array](arkts-apis-arkts-collections-Int32Array.md) | Yes | The `Int32Array` that contains the target element. |
| index | number | Yes | The index of the target element. The index starts from 0 and should be less than `typedArray.length`. |
| value | number | Yes | The expected value. |
| timeout | number | No | The maximum wait time, in milliseconds. If omitted, or if `NaN` or positive infinity is passed, and the element value equals the expected value, the wait continues until a notification is received; a negative number is treated as 0. If it is 0 and the element value equals the expected value, `'timed-out'` is returned immediately. To limit the wait time, pass a finite non-negative number. |

**Returns**

| Type | Description |
| ------ | ------ |
| 'ok' \| 'not-equal' \| 'timed-out' | The wait result. `'ok'` indicates that the thread was woken up by a notification; `'not-equal'` indicates that the target element is not equal to the expected value and the wait was not entered; `'timed-out'` indicates that the wait timed out. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID | Error Message |
| ------ | ------ |
| 10200001 | The value of index is out of range. |

**Example**

```ts
import { ArkTSUtils, collections } from '@kit.ArkTS';

let array = new collections.Int32Array(1);
array[0] = 10;
console.info(`Before operation: ${array[0]}`); // Expected output: Before operation: 10

// This example must be run in a Worker thread that allows blocking and waiting.
// The current value is 10, which is not equal to the expected value 9, so it returns immediately without modifying the element.
let result = ArkTSUtils.Atomics.wait(array, 0, 9, 0);
console.info(`Return value: ${result}`); // Expected output: Return value: not-equal
console.info(`After operation: ${array[0]}`); // Expected output: After operation: 10
```

### notify

static notify(typedArray: collections.Int32Array, index: number, count?: number): number

Notifies threads waiting on the specified Int32 element via [wait](#wait) and returns the number of threads notified. The wait and notify must target the same byte position in the same underlying buffer; the same numeric index in different arrays does not represent the same wait position. When using different views of the same buffer, the `byteOffset` of the view must also be considered.

This method only sends notifications and does not modify the target element. Notifications only affect threads that have already entered the wait state and are not retained for subsequent `wait` calls. When a waiting thread needs to be notified to read a new value, write the new value first, and then call `notify`.

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | ------ |
| typedArray | [collections.Int32Array](arkts-apis-arkts-collections-Int32Array.md) | Yes | The `Int32Array` containing the target element. |
| index | number | Yes | The index of the target element. The index starts from 0 and should be less than `typedArray.length`. |
| count | number | No | The maximum number of waiting threads to notify. When omitted or set to positive infinity, all waiting threads are notified; when 0 or negative, no threads are notified; non-integers are truncated to their integer part. |

**Returns**

| Type | Description |
| ------ | ------ |
| number | The number of waiting threads notified. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID | Error Message |
| ------ | ------ |
| 10200001 | The value of index is out of range. |

**Example**

```ts
import { ArkTSUtils, collections } from '@kit.ArkTS';

let array = new collections.Int32Array(1);
array[0] = 10;
console.info(`Before operation: ${array[0]}`); // Expected output: Before operation: 10

// No thread is currently waiting and the notification count is 0; notify does not modify the element.
let result = ArkTSUtils.Atomics.notify(array, 0, 1);
console.info(`Return value: ${result}`); // Expected output: Return value: 0
console.info(`After operation: ${array[0]}`); // Expected output: After operation: 10
```

### xor

static xor(typedArray: AtomicIntegerArray, index: number, value: number): number

Performs a bitwise XOR operation in an atomic manner and returns the value before the operation.

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | ------ |
| typedArray | [AtomicIntegerArray](#atomicintegerarray) | Yes | Integer `TypedArray` that contains the target element. |
| index | number | Yes | Index of the target element. The index starts from 0 and should be less than `typedArray.length`. |
| value | number | Yes | Value used for the bitwise XOR operation. |

**Returns**

| Type | Description |
| ------ | ------ |
| number | Element value before the operation. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID | Error Message |
| ------ | ------ |
| 10200001 | The value of index is out of range. |

**Example**

```ts
import { ArkTSUtils, collections } from '@kit.ArkTS';

let array = new collections.Int32Array(1);
array[0] = 10;
console.info(`Before operation: ${array[0]}`); // Expected output: Before operation: 10

// The binary of 10 is 1010, and the binary of 3 is 0011.
let result = ArkTSUtils.Atomics.xor(array, 0, 3);
console.info(`Return value: ${result}`); // Expected output: Return value: 10
console.info(`After operation: ${array[0]}`); // Expected output: After operation: 9
```
