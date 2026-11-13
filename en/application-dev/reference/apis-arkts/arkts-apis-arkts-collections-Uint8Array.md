# Class (Uint8Array)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=71db7138e2704708b0a19c70a4e677ab1c2014cd translatedAt=2026-11-06T08:54:20.707Z pushedAt=2026-11-13T03:23:50.248Z nl=2 -->

A linear data structure whose underlying implementation is based on [ArrayBuffer](arkts-apis-arkts-collections-ArrayBuffer.md).

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This module can be imported and used only in ArkTS files (with the .ets file name extension).

**Decorator type:** [\@Sendable](../../arkts-utils/arkts-sendable.md#sendable-decorator)

## Modules to Import

```ts
import { collections } from '@kit.ArkTS';
```

## Properties

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

| Name  | Type  | Read Only| Optional| Description             |
| ------ | ------ | ---- | ---- | ----------------|
| buffer | ArrayBuffer | Yes  | No | Bottom-layer buffer used by an ArkTS Uint8Array.|
| byteLength | number | Yes | No | Number of bytes occupied by the ArkTS Uint8Array. |
| byteOffset | number | Yes | No | Byte offset of the ArkTS Uint8Array from the start of its ArrayBuffer. |
| length | number | Yes  | No | Number of elements in an ArkTS Uint8Array.|
| BYTES_PER_ELEMENT | number | Yes | No | Number of bytes occupied by each element in the ArkTS Uint8Array. |

## constructor
constructor()

A constructor used to create an empty ArkTS Uint8Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 10200012 | The Uint8Array's constructor cannot be directly invoked. |

**Example**

```ts
let uint8Array: collections.Uint8Array = new collections.Uint8Array();
```

## constructor
constructor(length: number)

A constructor used to create an ArkTS Uint8Array of a given length.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                         |
| ------- | ------ | ---- | --------------------------- |
| length | number | Yes | Used to specify the length of the ArkTS Uint8Array, with a value that is a non-negative integer. |

**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID| Error Message                                                 |
| -------- | -------------------------------------------------------  |
| 10200012 | The Uint8Array's constructor cannot be directly invoked. |


**Example**

```ts
// Construct an object with the length parameter.
let uint8Array: collections.Uint8Array = new collections.Uint8Array(12);
```

## constructor
constructor(elements: Iterable\<number>)

A constructor that creates an ArkTS Uint8Array from an iterable object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| elements |  Iterable\<number> | Yes | An iterable collection of numbers used to construct an ArkTS Uint8Array object. The value range of the numbers in the collection is [0, 255], and values out of range are truncated to the lower 8 bits (for example, the binary of 256 is 100000000, which becomes 00000000 after truncation). |

**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 10200012 | The Uint8Array's constructor cannot be directly invoked. |

**Example**

```ts
// Construct objects from an iterable object.
let set: Set<number> = new Set<number>([1, 2, 3, 256]);
let uint8Array: collections.Uint8Array = new collections.Uint8Array(set);
// Uint8Array [1, 2, 3, 0]
```

## constructor
constructor(array: ArrayLike\<number> | ArrayBuffer)

A constructor that creates an ArkTS Uint8Array from an array-like object or ArkTS ArrayBuffer.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| array |  ArrayLike\<number> \| ArrayBuffer | Yes | Object used to construct the ArkTS Uint8Array. When ArrayLike\<number> is passed in, the value range is [0, 255], and out-of-range values are truncated to the lower 8 bits (for example, the binary of 256 is 100000000, which becomes 00000000 after truncation). |

**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 10200012 | The Uint8Array's constructor cannot be directly invoked. |

**Example**

```ts
// Example 1: Construct an object from an array-like object.
let arrayLike = [1, 3, 5];
let uint8Array: collections.Uint8Array = new collections.Uint8Array(arrayLike);
```

```ts
// Example 2: Construct an object from an ArrayBuffer.
let arrayBuffer: collections.ArrayBuffer = new collections.ArrayBuffer(10);
let uint8Array: collections.Uint8Array = new collections.Uint8Array(arrayBuffer);
```

```ts
// Example 3: Construct an object from another ArkTS Uint8Array.
let arrayLike = [1, 3, 5];
// uint8Array1 [1, 3, 5]
let uint8Array1: collections.Uint8Array = new collections.Uint8Array(arrayLike);
// uint8Array2 [1, 3, 5]
let uint8Array2: collections.Uint8Array = new collections.Uint8Array(uint8Array1);
```

## constructor
constructor(buffer: ArrayBuffer, byteOffset?: number, length?: number)

A constructor that creates an ArkTS Uint8Array from an ArrayBuffer.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                        |
| ------- | ------ | ---- | ------------------------------------------ |
| buffer | ArrayBuffer | Yes | ArrayBuffer object used to construct the ArkTS Uint8Array. The ArkTS Uint8Array and this ArrayBuffer share memory, and modifying data in one affects the other. |
| byteOffset | number | No | Specifies the byte offset of the buffer. The value is a non-negative integer and must be less than buffer.byteLength. An exception is thrown when the value is out of range. The default value is 0. |
| length | number | No | Specifies the length of the ArkTS Uint8Array. The sum of byteOffset and length cannot exceed buffer.byteLength. An exception is thrown when the value is out of range. The default value is buffer.byteLength - byteOffset. |

**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID| Error Message                                                  |
| -------- | -------------------------------------------------------   |
| 10200012 | The Uint8Array's constructor cannot be directly invoked. |

**Example**

```ts
let uint8Array: collections.Uint8Array = collections.Uint8Array.from([1, 2, 3, 4, 5, 6]);
console.info(`byteLength: ${uint8Array.buffer.byteLength}`); // byteLength: 6
// Obtain 5 elements starting from index 1 in the buffer of uint8Array.
let uint8Array1: collections.Uint8Array = new collections.Uint8Array(uint8Array.buffer, 1, 5);
console.info(`[${uint8Array1}]`); // [2, 3, 4, 5, 6]
```

## from
static from(arrayLike: ArrayLike\<number>): Uint8Array

Creates an ArkTS Uint8Array object from an ArrayLike.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                 |
| ------- | ------ | ---- | --------------------------------------------------- |
| arrayLike | ArrayLike\<number> | Yes | The ArrayLike object used to construct the ArkTS Uint8Array. The value range of numeric elements is [0, 255], and out-of-range values are truncated to the lower 8 bits (for example, the binary of 256 is 100000000, which becomes 00000000 after truncation). |

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint8Array | New ArkTS Uint8Array generated.|

**Example**
```ts
let arrayLike = [1, 3, 5];
let uint8Array: collections.Uint8Array = collections.Uint8Array.from(arrayLike); // Uint8Array [1, 3, 5]
```

## from
static from\<T>(arrayLike: ArrayLike\<T>, mapFn: TypedArrayFromMapFn\<T, number>): Uint8Array

Creates an ArkTS Uint8Array from an array-like object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name | Type  | Mandatory| Description                                       |
| ------- | ------ | ---- | ------------------------------------------|
| arrayLike | ArrayLike\<T> | Yes | ArrayLike object used to construct the ArkTS Uint8Array. The value range of numeric elements is [0, 255], and out-of-range values are truncated to the lower 8 bits (for example, the binary of 256 is 100000000, which becomes 00000000 after truncation). |
| mapFn | [TypedArrayFromMapFn](arkts-apis-arkts-collections-Types.md#typedarrayfrommapfn)\<T, number> | Yes | Mapping function that maps each element in the ArrayLike from type T to type number, used to create the ArkTS Uint8Array. The value range of numeric elements is [0, 255], and out-of-range values are truncated to the lower 8 bits (for example, the binary of 256 is 100000000, which becomes 00000000 after truncation). |

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint8Array | New ArkTS Uint8Array generated.|

**Example**

```ts
// Example 1: Create an ArkTS Uint8Array from an object.
let uint8Array: collections.Uint8Array = collections.Uint8Array.from<number>(
  { length: 5 }, (v: Object, k: number) => k);
// Uint8Array [0, 1, 2, 3, 4]
```

```ts
// Example 2: Create an ArkTS Uint8Array from a string array.
let uint8Array: collections.Uint8Array = collections.Uint8Array.from<string>(
  ["1", "3", "5"], (v: string, k: number) => parseInt(v));
// Uint8Array [1, 3, 5]
```

```ts
// Example 3: Create an ArkTS Uint8Array from a string.
let uint8Array: collections.Uint8Array = collections.Uint8Array.from<string>(
  "12345", (v: string, k: number) => parseInt(v));
// Uint8Array [1, 2, 3, 4, 5]
```

## from
static from(arrayLike: Iterable\<number>, mapFn?: TypedArrayFromMapFn\<number, number>): Uint8Array

Creates an ArkTS Uint8Array from an iterator object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name | Type  | Mandatory| Description                               |
| ------- | ------ | ---- | -----------------------------------|
| arrayLike | Iterable\<number> | Yes | Iterable object used to construct the ArkTS Uint8Array. The value range of numeric elements is [0, 255], and out-of-range values are truncated to the lower 8 bits (for example, the binary of 256 is 100000000, which becomes 00000000 after truncation).   |
| mapFn | [TypedArrayFromMapFn](arkts-apis-arkts-collections-Types.md#typedarrayfrommapfn)\<number, number> | No | Mapping function. If omitted, elements are not processed, and the original data is directly used to create the Uint8Array. The value range of numeric elements is [0, 255], and out-of-range values are truncated to the lower 8 bits (for example, the binary of 256 is 100000000, which becomes 00000000 after truncation).|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint8Array | New ArkTS Uint8Array generated.|

**Example**

```ts
// Example 1: No mapping function is specified.
let set: Set<number> = new Set<number>([1, 2, 3]);
let uint8Array: collections.Uint8Array = collections.Uint8Array.from(set);
// Uint8Array [1, 2, 3]
```

```ts
// Example 2: A mapping function is specified.
let set: Set<number> = new Set<number>([1, 2, 3]);
let uint8Array: collections.Uint8Array = collections.Uint8Array.from(
  set, (v: number, k: number) => v + k);
// Uint8Array [1, 3, 5]
```

## of<sup>18+</sup>

static of(...items: number[]): Uint8Array

Creates a new ArkTS Uint8Array object from a variable number of arguments.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type         | Mandatory| Description                           |
| --------- | ------------- | ---- | ------------------------------- |
| items | number[] | No   | Elements used to create the Uint8Array. The number of parameters can be 0, 1, or more. The value range of each parameter is [0, 255]. Values out of range are truncated to the lower 8 bits (for example, the binary of 256 is 100000000, which becomes 00000000 after truncation). The default value is an empty array. |

**Return value**

| Type     | Description                   |
| --------- | ----------------------- |
| Uint8Array | Newly created ArkTS Uint8Array object. |

**Example**

```ts
let uint8Array: collections.Uint8Array = collections.Uint8Array.of(1, 2, 3, 4);
console.info(uint8Array.toString()); // Expected output: 1,2,3,4
```

## toString<sup>18+</sup>

toString(): string

Converts the ArkTS Uint8Array to a string, returning a string formed by concatenating all elements separated by commas.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description           |
| ---------- | ------------- |
| string | A string that contains all elements of the array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID   | Error Message                                |
| -------- | ------------------------------------ |
| 10200011 | The toString method cannot be bound. |
| 10200201 | Concurrent modification error.       |

**Example**

```ts
let uint8Array = new collections.Uint8Array([1, 2, 3, 4, 5]);
let resultString = uint8Array.toString();
console.info(resultString); // Expected output: 1,2,3,4,5
```

## toLocaleString<sup>18+</sup>

toLocaleString(): string

Converts each element to a localized string based on the system locale of the current application, and concatenates them in order with commas into the resulting string.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description           |
| ---------- | ------------- |
| string | A string containing all elements of the array, formatted according to the system locale. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID   | Error Message                                      |
| -------- | ------------------------------------------ |
| 10200011 | The toLocaleString method cannot be bound. |
| 10200201 | Concurrent modification error.             |

**Example**

```ts
// The system where the application is running is set to the French locale.
let uint8Array = new collections.Uint8Array([100, 110, 120]);
let resultString = uint8Array.toLocaleString();
console.info(resultString); // Expected output: 100,110,120
```

## copyWithin
copyWithin(target: number, start: number, end?: number): Uint8Array

Copies the elements within the specified range of the ArkTS Uint8Array to the target position in its own buffer in sequence, overwriting the original data in the target range, and returns the modified ArkTS Uint8Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| target | number | Yes | Subscript of the target start position. If `target < 0`, it starts from the position `target + Uint8Array.length`. |
| start | number | Yes| Start index of the range. If a negative number is passed in, it refers to the index of `start + Uint8Array.length`.|
| end | number | No| End index of the range (exclusive). If a negative number is passed in, it refers to the index of `end + Uint8Array.length`. The default value is the length of the ArkTS Uint8Array.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint8Array | The modified ArkTS Uint8Array. (In-place modification, returns the original object reference.) |

**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------ |
| 10200011 | The copyWithin method cannot be bound.           |
| 10200201 | Concurrent modification error.               |

**Example**

```ts
let uint8Array: collections.Uint8Array = collections.Uint8Array.from([1, 2, 3, 4, 5, 6, 7, 8]);
let copied: collections.Uint8Array = uint8Array.copyWithin(3, 1, 3);
// Uint8Array [1, 2, 3, 2, 3, 6, 7, 8]
```

## some
some(predicate: TypedArrayPredicateFn\<number, Uint8Array>): boolean

Tests whether any element in the ArkTS Uint8Array satisfies the specified condition. Returns true if such an element exists; otherwise, returns false.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                 |
| ------- | ------ | ---- | ---------------------------------------------------- |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Uint8Array> | Yes| Assertion function used for the test.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| boolean | Check result. The value **true** is returned if an element meeting the given condition exists; otherwise, **false** is returned.|

**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID| Error Message                           |
| -------- | ---------------------------------- |
| 10200011 | The some method cannot be bound.   |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let arrayLike = [10, 20, 30, 40, 50];
let uint8Array: collections.Uint8Array = new collections.Uint8Array(arrayLike);
uint8Array.some((element: number) => element < 1); // false
```

## every
every(predicate: TypedArrayPredicateFn\<number, Uint8Array>): boolean

Tests whether all elements in the ArkTS Uint8Array satisfy the specified condition. Returns true if all of them satisfy the condition; otherwise, returns false.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                   |
| ------- | ------ | ---- | ----------------------------------------------------- |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Uint8Array> | Yes| Assertion function used for the test.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| boolean | Check result. The value **true** is returned if all elements meet the given condition; otherwise, **false** is returned.|

**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The every method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let arrayLike = [10, 20, 30, 40, 50];
let uint8Array: collections.Uint8Array = new collections.Uint8Array(arrayLike);
uint8Array.every((element: number) => element > 1);  // true
```

## fill
fill(value: number, start?: number, end?: number): Uint8Array

Fills and replaces all elements within the specified range of the ArkTS Uint8Array with a specific value, and returns the modified ArkTS Uint8Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                     |
| ------- | ------ | ---- | --------------------------------------------------------|
| value | number | Yes | Value to be filled. The value range is [0, 255]. Values out of range are truncated. |
| start | number | No| Start index of the range. If a negative number is passed in, it refers to the index of `start + Uint8Array.length`. The default value is **0**.|
| end | number | No | Index at which to end filling (the element at this index is not included). If `end < 0`, filling ends at `end + Uint8Array.length`. The default value is the length of the ArkTS Uint8Array. |

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint8Array | The filled ArkTS Uint8Array (in-place modification, returns the original object reference). |

**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The fill method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let arrayLike = [1, 2, 3];
new collections.Uint8Array(arrayLike).fill(4); // Uint8Array [4, 4, 4]
new collections.Uint8Array(arrayLike).fill(4, 1); // Uint8Array [1, 4, 4]
new collections.Uint8Array(arrayLike).fill(4, 1, 2); // Uint8Array [1, 4, 3]
```

## filter
filter(predicate: TypedArrayPredicateFn\<number, Uint8Array>): Uint8Array

Returns a new ArkTS Uint8Array that contains all elements that meet the given condition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                   |
| ------- | ------ | ---- | ------------------------------------------------------ |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Uint8Array> | Yes| Assertion function used for the test.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint8Array| Filtered ArkTS Uint8Array.|

**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The filter method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let uint8Array: collections.Uint8Array = collections.Uint8Array.from([0, 1, 2, 3, 4]);
let filtered: collections.Uint8Array = uint8Array.filter((element: number) => element % 2 == 0);
// Uint8Array [0, 2, 4]
```

## find
find(predicate: TypedArrayPredicateFn\<number, Uint8Array>): number | undefined

Returns the value of the first element that passes a test provided by a callback function. If none of the elements pass the test, **undefined** is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Uint8Array> | Yes| Assertion function used for the test.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
|  number \| undefined | Value of the first element that passes the test. If none of the elements pass the test, **undefined** is returned.|

**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The find method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let uint8Array: collections.Uint8Array = collections.Uint8Array.from([0, 1, 2, 3, 4]);
uint8Array.find((element: number) => element > 2); // 3
uint8Array.find((element: number) => element > 4); // undefined
```

## findIndex
findIndex(predicate: TypedArrayPredicateFn\<number, Uint8Array>): number

Returns the index of the first element that passes a test provided by a callback function. If none of the elements pass the test, **-1** is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Uint8Array> | Yes| Assertion function used for the test.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| number | Index of the first element that passes the test. If none of the elements pass the test, **-1** is returned.|

**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The findIndex method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**Example**

```ts
const uint8Array: collections.Uint8Array = collections.Uint8Array.from([1, 2, 3, 4, 5]);
let foundIndex: number = uint8Array.findIndex((element: number) => element % 2 === 0); // 1
```

## forEach
forEach(callbackFn: TypedArrayForEachCallback\<number, Uint8Array>): void

Executes the provided callback function on each element of the ArkTS Uint8Array in order. This method has no return value.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| callbackFn | [TypedArrayForEachCallback](arkts-apis-arkts-collections-Types.md#typedarrayforeachcallback)\<number, Uint8Array> | Yes| Callback function to run for each element.|


**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The forEach method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let uint8Array: collections.Uint8Array = collections.Uint8Array.from([1, 2, 3]);
uint8Array.forEach((value: number, index: number, array: collections.Uint8Array) => {
  console.info(`Element ${value} at index ${index}`);
});
```

## indexOf
indexOf(searchElement: number, fromIndex?: number): number

Returns the first index of the given element in the ArkTS Uint8Array, or -1 if the element is not found.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name       | Type  | Mandatory| Description                       |
| ------------- | ------ | ---- | ---------------------------|
| searchElement | number | Yes  | Element whose index is to be found.                |
| fromIndex     | number | No   | Starting index for the front-to-back search. The default value is 0. If `fromIndex < 0`, the search starts from the position `fromIndex + Uint8Array.length` in a front-to-back manner. If the value of fromIndex causes the search interval to have no overlap with the array range, -1 is returned. |

**Return value**

| Type        | Description     |
| ------------ | --------- |
| number | The first index of the specified element in the specified range of the array; if not found, -1 is returned. |

**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The indexOf method cannot be bound. |
| 10200201 | Concurrent modification error.                |

**Example**

```ts
let uint8Array: collections.Uint8Array = collections.Uint8Array.from([3, 5, 9]);
uint8Array.indexOf(3); // 0
uint8Array.indexOf(7); // -1
uint8Array.indexOf(9, 2); // 2
uint8Array.indexOf(9, -2); // 2
```

## lastIndexOf<sup>18+</sup>

lastIndexOf(searchElement: number, fromIndex?: number): number

Returns the index of the last occurrence of the given element in the ArkTS Uint8Array instance, or -1 if the element is not found.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name          | Type    | Mandatory | Description                                                                               |
| ------------- | ------ | --- | --------------------------------------------------------------------------------- |
| searchElement | number | Yes  | Element to search for.                                                                            |
| fromIndex     | number | No   | Starting index for searching from back to front. The default value is the length of ArkTS Uint8Array minus 1. If `fromIndex < 0`, the search starts from the position `fromIndex + Uint8Array.length` and proceeds from back to front. If the value of fromIndex causes the search interval to have no overlap with the array range, -1 is returned. |

**Return value**

| Type    | Description                     |
| ------ | ----------------------- |
| number | The last index of the element in the specified range of the array; if not found, -1 is returned. |

**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID   | Error Message                                   |
| -------- | --------------------------------------- |
| 10200011 | The lastIndexOf method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let uint8Array: collections.Uint8Array = collections.Uint8Array.from([3, 5, 9]);
console.info(`${uint8Array.lastIndexOf(3)}`); // Expected output: 0
console.info(`${uint8Array.lastIndexOf(7)}`); // Expected output: -1
console.info(`${uint8Array.lastIndexOf(9, 2)}`); // Expected output: 2
console.info(`${uint8Array.lastIndexOf(9, -2)}`); // Expected output: -1
```

## join
join(separator?: string): string

Concatenates all elements in this ArkTS Uint8Array into a string, with a given separator.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | ---------------------------------------------------- |
| separator | string | No  | Separator to be used. If no value is passed in, a comma (,) is used as the separator.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| string | String obtained. If the array is empty, an empty string is returned.|

**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The join method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**Example**

```ts
let uint8Array: collections.Uint8Array = collections.Uint8Array.from([1, 2, 3, 4, 5]);
let joined: string = uint8Array.join('-'); // "1-2-3-4-5"
```

## map
map(callbackFn: TypedArrayMapCallback\<number, Uint8Array>): Uint8Array

Applies a callback function to each element in this ArkTS Uint8Array and uses the result to create an ArkTS Uint8Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | ---------------------------------------------------- |
| callbackFn | [TypedArrayMapCallback](arkts-apis-arkts-collections-Types.md#typedarraymapcallback)\<number, Uint8Array> | Yes | Callback function that performs a conversion operation on each element in the ArkTS Uint8Array. The return value is used as the new element at the corresponding position. If the return value is out of the value range [0, 255], it is truncated to the lower 8 bits (for example, the binary of 256 is 100000000, which becomes 00000000 after truncation). |


**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint8Array | Newly created ArkTS Uint8Array object containing the conversion result of the callback function. |

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The map method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let uint8Array: collections.Uint8Array = collections.Uint8Array.from([25, 36, 49]);
const mapped: collections.Uint8Array = uint8Array.map(Math.sqrt); // Uint8Array [5, 6, 7]
```

## reduce
reduce(callbackFn: TypedArrayReduceCallback\<number, number, Uint8Array>): number

Applies a reduce function on each element in this ArkTS Uint8Array and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name    | Type  | Mandatory|  Description    |
| ---------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<number, number, Uint8Array> | Yes| Reduce function.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| number | Final result obtained from the last call of the reduce function.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID|                      Error Message                    |
| -------- | ------------------------------------------------ |
| 10200011 | The reduce method cannot be bound.               |
| 10200201 | Concurrent modification error.               |

**Example**

```ts
let uint8Array: collections.Uint8Array = collections.Uint8Array.from([1, 2, 3, 4, 5]);
let reducedValue: number = uint8Array.reduce((accumulator: number, value: number) => accumulator + value);
// reducedValue == 15
```

## reduceRight<sup>18+</sup>

reduceRight(callbackFn: TypedArrayReduceCallback\<number, number, Uint8Array>): number

Reversely traverses this ArkTS Uint8Array, applies a reduce function on each element in the array, and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name    | Type  | Mandatory|  Description    |
| ---------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<number, number, Uint8Array> | Yes| Reduce function.|

**Return value**

| Type    | Description         |
| ------ | ----------- |
| number | Final result obtained from the last call of the reduce function.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID   | Error Message                                   |
| -------- | --------------------------------------- |
| 10200011 | The reduceRight method cannot be bound. |
| 10200201 | Concurrent modification error.      |

**Example**

```ts
let uint8Array: collections.Uint8Array = collections.Uint8Array.from([1, 2, 3, 4, 5]);
let reducedValue: number = uint8Array.reduceRight((accumulator: number, value: number) => accumulator + value);
console.info(`${reducedValue}`); // Expected output: 15
```

## reduce
reduce(callbackFn: TypedArrayReduceCallback\<number, number, Uint8Array>, initialValue: number): number

Executes a reduction function on each element in the ArkTS Uint8Array, receives an initial value as the argument for the first call, and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | --------------------------------------------------- |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<number, number, Uint8Array> | Yes | Reduce function.|
| initialValue | number | Yes | Initial value.|


**Return value**

| Type        | Description     |
| ------------ | --------- |
| number | Final result obtained from the last call of the reduce function.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The reduce method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let uint8Array: collections.Uint8Array = collections.Uint8Array.from([1, 2, 3, 4, 5]);
let reducedValue: number = uint8Array.reduce((accumulator: number, value: number) => accumulator + value, 1);
// reducedValue == 16
```

## reduceRight<sup>18+</sup>

reduceRight\<U = number>(callbackFn: TypedArrayReduceCallback\<U, number, Uint8Array>, initialValue: U): U

Traverses the ArkTS Uint8Array in reverse order, executes a reduction function on each element, receives an initial value as the argument for the first call of the reduction function, and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | --------------------------------------------------- |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<U, number, Uint8Array> | Yes | Reduce function.|
| initialValue | U | Yes | Initial value.|

**Return value**

| Type    | Description         |
| ------ | ----------- |
| U | Final result obtained from the last call of the reduce function.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID   | Error Message                                   |
| -------- | --------------------------------------- |
| 10200011 | The reduceRight method cannot be bound. |
| 10200201 | Concurrent modification error.      |

**Example**

```ts
let uint8Array: collections.Uint8Array = collections.Uint8Array.from([1, 2, 3, 4, 5]);
let reducedValue: number = uint8Array.reduceRight((accumulator: number, value: number) => accumulator + value, 1);
console.info(`${reducedValue}`); // Expected output: 16
```

## reduce
reduce\<U>(callbackFn: TypedArrayReduceCallback\<U, number, Uint8Array>, initialValue: U): U

Applies a reduce function for each element in this ArkTS Uint8Array, receives an initial value as the parameter called by the reduce function for the first time, and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | ---------------------------------------------------- |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<U, number, Uint8Array> | Yes | Reduce function.|
| initialValue | U | Yes | Initial value.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
|  U | Final result obtained from the last call of the reduce function.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The reduce method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**Example**

```ts
let uint8Array: collections.Uint8Array = collections.Uint8Array.from([1, 2, 3, 4, 5]);
let reducedValue: string = uint8Array.reduce<string>((accumulator: string, value: number) => accumulator + value, "initialValue");
// reducedValue == initialValue12345
```

## reverse
reverse(): Uint8Array

Reverses the order of the elements in the ArkTS Uint8Array and returns the reversed ArkTS Uint8Array object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint8Array   | The reversed ArkTS Uint8Array object (in-place modification, returns the original object reference). |

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The reverse method cannot be bound. |
| 10200201 | Concurrent modification error.   |

**Example**

```ts
let uint8Array: collections.Uint8Array = collections.Uint8Array.from([1, 2, 3, 4, 5]);
let reversed: collections.Uint8Array = uint8Array.reverse(); // Uint8Array [5, 4, 3, 2, 1]
```

## set
set(array: ArrayLike\<number>, offset?: number): void

Writes the passed-in ArrayLike elements into the ArkTS Uint8Array in sequence, replacing the original elements starting from the start position.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | ---------------------------------------------------- |
| array | ArrayLike\<number> | Yes | The ArrayLike object used for setting. The value range of numeric elements is [0, 255], and out-of-range values are truncated to the lower 8 bits (for example, the binary of 256 is 100000000, which becomes 00000000 after truncation). |
| offset | number | No | The starting position for writing, which is a non-negative integer. The sum of offset and array.length cannot exceed the length of the ArkTS Uint8Array; otherwise, an exception is thrown. The default value is 0. |

**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The set method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**Example**

```ts
let buffer: collections.ArrayBuffer = new collections.ArrayBuffer(8);
let uint8Array: collections.Uint8Array = new collections.Uint8Array(buffer);
uint8Array.set([1, 2, 3], 3); // Uint8Array [0, 0, 0, 1, 2, 3, 0, 0]
```

## slice
slice(start?: number, end?: number): Uint8Array

Returns a new ArkTS Uint8Array object that copies the content of the specified range of the original ArkTS Uint8Array. Unlike [subarray](#subarray), this method generates an independent copy and does not affect the original ArkTS Uint8Array object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description                                                  |
| ------ | ------ | ---- | -----------------------------------------------------|
| start  | number | No  | Start index of the range. If a negative number is passed in, it refers to the index of `start + Uint8Array.length`. The default value is **0**.|
| end    | number | No  | End index of the range (exclusive). If a negative number is passed in, it refers to the index of `end + Uint8Array.length`. The default value is the length of the ArkTS Uint8Array.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint8Array | A new ArkTS Uint8Array object containing the elements in the specified range of the original ArkTS Uint8Array. |

**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The slice method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let uint8Array: collections.Uint8Array = collections.Uint8Array.from([1, 2, 3, 4, 5]);
uint8Array.slice(); // Uint8Array [1, 2, 3, 4, 5]
uint8Array.slice(1, 3); // Uint8Array [2, 3]
uint8Array.slice(-2); // Uint8Array [4, 5]
```

## sort
sort(compareFn?: TypedArrayCompareFn\<number>): Uint8Array

Sorts elements in this ArkTS Uint8Array and returns the sorted ArkTS Uint8Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type                  | Mandatory| Description                                      |
| --------- | ---------------------- | ---- | ------------------------------------------ |
| compareFn | [TypedArrayCompareFn](arkts-apis-arkts-collections-Types.md#typedarraycomparefn)\<number> | No  | Function that determines the sort order. By default, elements are sorted in ascending order.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint8Array | The sorted ArkTS Uint8Array object (in-place sorting, returns a reference to the original object). |

**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------ |
| 10200011 | The sort method cannot be bound. |
| 10200201 | Concurrent modification error.         |

**Example**

```ts
let uint8Array: collections.Uint8Array = collections.Uint8Array.from([1, 3, 5, 4, 2]);
uint8Array.sort(); // Uint8Array [1, 2, 3, 4, 5]
uint8Array.sort((a: number, b: number) => a - b); // Uint8Array [1, 2, 3, 4, 5]
uint8Array.sort((a: number, b: number) => b - a); // Uint8Array [5, 4, 3, 2, 1]
```

## subarray
subarray(begin?: number, end?: number): Uint8Array

Extracts an array from the specified position and returns a new ArkTS Uint8Array object based on the same ArkTS ArrayBuffer. Unlike [slice](#slice), this method does not generate an independent copy and affects the original ArkTS Uint8Array object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description                                               |
| ------ | ------ | ---- | ------------------------------------------------- |
| begin  | number | No  | Start index of the range. If a negative number is passed in, it refers to the index of `begin + Uint8Array.length`. The default value is **0**.|
| end    | number | No  | End index of the range (exclusive). If a negative number is passed in, it refers to the index of `end + Uint8Array.length`. The default value is the length of the ArkTS Uint8Array.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint8Array | A new ArkTS Uint8Array object based on the original ArkTS Uint8Array, truncated from the specified position. |

**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID|            Error Message                              |
| -------- | -------------------------------------------------|
| 10200011 | The subarray method cannot be bound.             |
| 10200201 | Concurrent modification error.               |

**Example**

```ts
let uint8Array: collections.Uint8Array = collections.Uint8Array.from([1, 2, 3, 4, 5]);
let subArray: collections.Uint8Array = uint8Array.subarray(); // Uint8Array [1, 2, 3, 4, 5]
subArray.set([10, 20, 30]); // Uint8Array [10, 20, 30, 4, 5]
```

## at
at(index: number): number | undefined

Returns the element at the given index. If no element is found, **undefined** is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| index  | number | Yes  | Index of the element. The index in an array always starts from 0 and is an integer. If a negative number is passed in, it refers to the index of `index + Uint8Array.length`.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| number \| undefined| Element obtained. If no element is found, **undefined** is returned.|

**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID|                       Error Message                   |
| -------- | ------------------------------------------------ |
| 10200011 | The at method cannot be bound.                   |
| 10200201 | Concurrent modification error.               |

**Example**

```ts
let uint8Array: collections.Uint8Array = collections.Uint8Array.from([1, 2, 3, 4, 5]);
console.info(`element: ${uint8Array.at(2)}`);  // element: 3
console.info(`element: ${uint8Array.at(-1)}`); // element: 5
console.info(`element: ${uint8Array.at(6)}`);  // element: undefined
```

## includes
includes(searchElement: number, fromIndex?: number): boolean

Determines whether the ArkTS Uint8Array contains a specific element. Returns true if it does, and false otherwise.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name| Type  | Mandatory| Description                                     |
| ------ | ------ | ---- | --------------------------------------- |
| searchElement  | number | Yes  | Element to search for.|
| fromIndex  | number | No  | The index to start searching from, with a default value of 0. If `fromIndex < 0`, the search starts from the position `fromIndex + Uint8Array.length` and proceeds from front to back. If the value of fromIndex causes the search interval to have no overlap with the array range, false is returned. |

**Return value**

| Type   | Description                                                       |
| ------- | ---------------------------------------------------------- |
| boolean | Check result. The value **true** is returned if the element exists; otherwise, **false** is returned.|

**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The includes method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let uint8Array: collections.Uint8Array = collections.Uint8Array.from([1, 2, 3]);
console.info(`includes: ${uint8Array.includes(2)}`);    // includes: true
console.info(`includes: ${uint8Array.includes(4)}`);    // includes: false
console.info(`includes: ${uint8Array.includes(3, 3)}`); // includes: false
```

## entries
entries(): IterableIterator\<[number, number]>

Returns a new iterator object that contains the key-value pairs of each element in the ArkTS Uint8Array. During iteration, methods that change the content of the ArkTS Uint8Array must not be used.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description     |
| ------------ | --------- |
| IterableIterator\<[number, number]>| An iterator object containing the key-value pair of each element in the ArkTS Uint8Array. |

**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The entries method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let uint8Array: collections.Uint8Array = collections.Uint8Array.from([11, 22, 33]);
let iterator: IterableIterator<[number, number]> = uint8Array.entries();
console.info(`value: ${iterator.next().value}`); // value: 0,11
console.info(`value: ${iterator.next().value}`); // value: 1,22
console.info(`value: ${iterator.next().value}`); // value: 2,33
```

## keys
keys(): IterableIterator\<number>

Returns a new iterator object that contains the keys (indices) of each element in the ArkTS Uint8Array. During iteration, methods that change the content of the ArkTS Uint8Array must not be used.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description     |
| ------------ | --------- |
| IterableIterator\<number> | An iterator object containing the key (index) of each element in the ArkTS Uint8Array.|

**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The keys method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let uint8Array: collections.Uint8Array = collections.Uint8Array.from([1, 2, 3, 4, 5]);
let iterator: IterableIterator<number> = uint8Array.keys();
for (const key of iterator) {
  console.info(`${key}`); // Output 0,1,2,3,4 in sequence
}
```

## values
values(): IterableIterator\<number>

Returns a new iterator object that contains the values of each element in the ArkTS Uint8Array. During iteration, methods that change the content of the ArkTS Uint8Array must not be used.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description     |
| ------------ | --------- |
| IterableIterator\<number> | An iterator object containing the value of each element in ArkTS Uint8Array.|

**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The values method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**Example**

```ts
let uint8Array: collections.Uint8Array = collections.Uint8Array.from([1, 2, 3, 4, 5]);
let iterator: IterableIterator<number> = uint8Array.values();
for (const value of iterator) {
  console.info(`${value}`); // Output 1,2,3,4,5 in sequence.
}
```

## [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;number&gt;

Returns an iterator object for iterating over the value of each element in the ArkTS Uint8Array. During iteration, methods that change the content of the ArkTS Uint8Array must not be used.

> **NOTE**
>
> This API is not supported in .ets files (unlike the other iterator methods in this document, which do not have this restriction).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type                     | Description            |
| ------------------------- | ---------------- |
| IterableIterator&lt;number&gt; | Iterator object containing the value of each element. |

**Error codes**

For details about the following error codes, see [Language base library error codes](errorcode-utils.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 10200011 | The Symbol.iterator method cannot be bound. |

**Example**

```ts
let uint8Array: collections.Uint8Array = collections.Uint8Array.from([1, 2, 3, 4, 5, 6]);

for (let item of uint8Array) {
  console.info(`value : ${item}`);
}
```

## [index: number]

&#91;index: number&#93;: number

Returns the element at the specified index in the ArkTS Uint8Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

| Name   | Type  | Mandatory| Description                    |
| ----- | ------ | ---- | -------------------------- |
| index | number | Yes | Zero-based index of the desired element, an integer in the value range from 0 to Uint8Array.length-1. Returns undefined when out of range or not an integer. |

**Return value**

| Type  | Description                |
| ----- | ---------------------|
| number | Element at the specified index. Returns undefined if the index is out of the array range. |

**Example**

```ts
let uint8Array = collections.Uint8Array.from([1, 2, 4]);
console.info(`Element at index 1: ${uint8Array[1]}`);
```
