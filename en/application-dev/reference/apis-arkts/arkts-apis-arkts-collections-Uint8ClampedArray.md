# Class (Uint8ClampedArray)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=ee30fc06a4d48737c123d3032041ea2f72a0d534 translatedAt=2026-11-06T08:52:47.674Z pushedAt=2026-11-13T03:35:37.974Z nl=2 -->

A linear data structure implemented based on [ArrayBuffer](arkts-apis-arkts-collections-ArrayBuffer.md). Unlike the truncation handling of Uint8Array, it clamps element values: values less than 0 are clamped to 0, and values greater than 255 are clamped to 255.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This module can be imported only to ArkTS files (with the file name extension .ets).

**Decorator type:** [\@Sendable](../../arkts-utils/arkts-sendable.md#sendable-decorator)

## Modules to Import

```ts
import { collections } from '@kit.ArkTS';
```

## Properties

**System capability**: SystemCapability.Utils.Lang

**Atomic service API**: This API can be used in atomic services since API version 12.

| Name  | Type  | Read Only| Optional| Description             |
| ------ | ------ | ---- | ---- | ----------------|
| buffer | ArrayBuffer | Yes  | No | Bottom-layer buffer used by an ArkTS Uint8ClampedArray.|
| byteLength | number | Yes  | No  | Number of bytes occupied by an ArkTS Uint8ClampedArray.|
| byteOffset | number | Yes  | No  | Offset between the ArkTS Uint8ClampedArray and the start position of the ArrayBuffer.|
| length | number | Yes  | No | Number of elements in an ArkTS Uint8ClampedArray.|
| BYTES_PER_ELEMENT | number | Yes | No | The number of bytes occupied by each element in ArkTS Uint8ClampedArray. |

## constructor
constructor()

A constructor used to create an empty ArkTS Uint8ClampedArray.

**System capability**: SystemCapability.Utils.Lang

**Atomic service API**: This API can be used in atomic services since API version 12.

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 10200012 | The Uint8ClampedArray's constructor cannot be directly invoked. |

**Example**

```ts
let uint8ClampedArray: collections.Uint8ClampedArray = new collections.Uint8ClampedArray();
```

## constructor
constructor(length: number)

Constructor used to create an ArkTS Uint8ClampedArray object of a specified length, with all elements initialized to 0.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                         |
| ------- | ------ | ---- | --------------------------- |
| length | number | Yes | Used to specify the length of the ArkTS Uint8ClampedArray. The value range is a non-negative integer. |

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                                 |
| -------- | -------------------------------------------------------  |
| 10200012 | The Uint8ClampedArray's constructor cannot be directly invoked. |


**Example**

```ts
// Construct an object with the length parameter.
let uint8ClampedArray: collections.Uint8ClampedArray = new collections.Uint8ClampedArray(12);
```

## constructor
constructor(elements: Iterable\<number>)

Constructor used to create an ArkTS Uint8ClampedArray object from an Iterable, with each element in the ArkTS Uint8ClampedArray undergoing clamping.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| elements |  Iterable\<number> | Yes| An iterable collection of numbers used to construct an ArkTS Uint8ClampedArray object.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 10200012 | The Uint8ClampedArray's constructor cannot be directly invoked. |

**Example**

```ts
// Construct objects from an iterable object.
let set: Set<number> = new Set<number>([1, 2, 3]);
let array: collections.Uint8ClampedArray = new collections.Uint8ClampedArray(set);
// Uint8ClampedArray [1, 2, 3]
```

## constructor
constructor(array: ArrayLike\<number> | ArrayBuffer)

Constructor used to create an ArkTS Uint8ClampedArray object from an ArrayLike or an ArkTS ArrayBuffer, with each element in the ArkTS Uint8ClampedArray undergoing clamping.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| array |  ArrayLike\<number> \| ArrayBuffer | Yes | Object used to construct the ArkTS Uint8ClampedArray. |

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 10200012 | The Uint8ClampedArray's constructor cannot be directly invoked. |

**Example**

```ts
// Example 1: Construct an object from an array-like object.
let arrayLike = [1, 3, 5];
let array: collections.Uint8ClampedArray = new collections.Uint8ClampedArray(arrayLike);
```

```ts
// Example 2: Construct an object from an ArrayBuffer.
let arrayBuffer: collections.ArrayBuffer = new collections.ArrayBuffer(10);
let array: collections.Uint8ClampedArray = new collections.Uint8ClampedArray(arrayBuffer);
```

```ts
// Example 3: Construct an object from another ArkTS Uint8ClampedArray.
let arrayLike = [1, 3, 5];
// uint8ClampedArray1 [1, 3, 5]
let uint8ClampedArray1: collections.Uint8ClampedArray = new collections.Uint8ClampedArray(arrayLike);
// uint8ClampedArray2 [1, 3, 5]
let uint8ClampedArray2: collections.Uint8ClampedArray = new collections.Uint8ClampedArray(uint8ClampedArray1);
```

## constructor
constructor(buffer: ArrayBuffer, byteOffset?: number, length?: number)

Constructor used to create an ArkTS Uint8ClampedArray object from an ArrayBuffer, with the ArkTS Uint8ClampedArray and the ArrayBuffer sharing memory.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                        |
| ------- | ------ | ---- | ------------------------------------------ |
| buffer | ArrayBuffer | Yes | The ArrayBuffer object used to construct the ArkTS Uint8ClampedArray. |
| byteOffset | number | No | Specifies the byte offset of the buffer. The value is a non-negative integer and must be less than buffer.byteLength. It starts from 0 and defaults to 0. |
| length | number | No | Specifies the length of the ArkTS Uint8ClampedArray. The default value is 0. The sum of byteOffset and length cannot exceed buffer.byteLength. |

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                                  |
| -------- | -------------------------------------------------------   |
| 10200012 | The Uint8ClampedArray's constructor cannot be directly invoked. |

**Example**

```ts
let uint8ClampedArray: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from([1, 2, 3, 4, 5, 6]);
console.info(`byteLength: ${uint8ClampedArray.buffer.byteLength}`); // byteLength: 6
// Start from the first byte of the buffer corresponding to uint8ClampedArray, with a length of 5. uint8ClampedArray1 and uint8ClampedArray share memory.
let uint8ClampedArray1: collections.Uint8ClampedArray = new collections.Uint8ClampedArray(uint8ClampedArray.buffer, 1, 5);
console.info(`[${uint8ClampedArray1}]`); // [2, 3, 4, 5, 6]
```

## from
static from(arrayLike: ArrayLike\<number>): Uint8ClampedArray

Creates an ArkTS Uint8ClampedArray object from an ArrayLike.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                 |
| ------- | ------ | ---- | --------------------------------------------------- |
| arrayLike | ArrayLike\<number> | Yes| Array-like object used to construct the ArkTS Uint8ClampedArray.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint8ClampedArray | New ArkTS Uint8ClampedArray generated.|

**Example**
```ts
let arrayLike = [1, 3, 5];
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from(arrayLike); // array [1, 3, 5]
```

## from
static from\<T>(arrayLike: ArrayLike\<T>, mapFn: TypedArrayFromMapFn\<T, number>): Uint8ClampedArray

Creates an ArkTS Uint8ClampedArray from an array-like object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name | Type  | Mandatory| Description                                       |
| ------- | ------ | ---- | ------------------------------------------|
| arrayLike | ArrayLike\<T> | Yes | ArrayLike object used to construct an ArkTS Uint8ClampedArray.              |
| mapFn | [TypedArrayFromMapFn](arkts-apis-arkts-collections-Types.md#typedarrayfrommapfn)\<T, number> | Yes| Mapping function.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint8ClampedArray | New ArkTS Uint8ClampedArray generated.|

**Example**

```ts
// Example 1: Create an ArkTS Uint8ClampedArray from an object.
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from<number>(
  { length: 5 }, (v: Object, k: number) => k);
// Uint8ClampedArray [0, 1, 2, 3, 4]
```

```ts
// Example 2: Create an ArkTS Uint8ClampedArray from a string array.
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from<string>(
  ["1", "3", "5"], (v: string, k: number) => parseInt(v));
// Uint8ClampedArray [1, 3, 5]
```

```ts
// Example 3: Create an ArkTS Uint8ClampedArray from a string.
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from<string>(
  "12345", (v: string, k: number) => parseInt(v));
// Uint8ClampedArray [1, 2, 3, 4, 5]
```

## from
static from(arrayLike: Iterable\<number>, mapFn?: TypedArrayFromMapFn\<number, number>): Uint8ClampedArray

Creates an ArkTS Uint8ClampedArray from an iterator object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name | Type  | Mandatory| Description                               |
| ------- | ------ | ---- | -----------------------------------|
| arrayLike | Iterable\<number> | Yes | An iterable object used to construct an ArkTS Uint8ClampedArray.   |
| mapFn | [TypedArrayFromMapFn](arkts-apis-arkts-collections-Types.md#typedarrayfrommapfn)\<number, number> | No | Mapping function. If omitted, elements are not transformed and the original values are used directly.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint8ClampedArray | New ArkTS Uint8ClampedArray generated.|

**Example**

```ts
// Example 1: No mapping function is specified.
let set: Set<number> = new Set<number>([1, 2, 3]);
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from(set);
// Uint8ClampedArray [1, 2, 3]
```

```ts
// Example 2: A mapping function is specified.
let set: Set<number> = new Set<number>([1, 2, 3]);
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from(
  set, (v: number, k: number) => v + k);
// Uint8ClampedArray [1, 3, 5]
```

## of<sup>18+</sup>

static of(...items: number[]): Uint8ClampedArray

Creates an ArkTS Uint8ClampedArray with a variable number of parameters.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type         | Mandatory| Description                           |
| --------- | ------------- | ---- | ------------------------------- |
| items | number[] | No  | Array of elements used to create the array. The number of elements can be zero, one, or more. The default value is an empty array.|

**Return value**

| Type     | Description                   |
| --------- | ----------------------- |
| Uint8ClampedArray | New ArkTS Uint8ClampedArray instance.|

**Example**

```ts
let arr: collections.Uint8ClampedArray = collections.Uint8ClampedArray.of(1, 2, 3, 4);
console.info(arr.toString()); // Expected output: 1,2,3,4
```

## toString<sup>18+</sup>

toString(): string

Converts the ArkTS Uint8ClampedArray to a string, with each element value joined by commas.

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
let array = new collections.Uint8ClampedArray([1, 2, 3, 4, 5]);
let stringArray = array.toString();
console.info(stringArray); // Expected output: 1,2,3,4,5
```

## toLocaleString<sup>18+</sup>

toLocaleString(): string

Converts each element to a localized string based on the system locale of the current application, and joins them in order with commas into a result string.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description           |
| ---------- | ------------- |
| string | A string that contains all elements of the array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID   | Error Message                                      |
| -------- | ------------------------------------------ |
| 10200011 | The toLocaleString method cannot be bound. |
| 10200201 | Concurrent modification error.             |

**Example**

```ts
// The system where the application is running is set to the French locale.
let array = new collections.Uint8ClampedArray([100, 110, 120]);
let stringArray = array.toLocaleString();
console.info(stringArray); // Expected output: 100,110,120
```

## copyWithin
copyWithin(target: number, start: number, end?: number): Uint8ClampedArray

Copies elements within the specified range of the ArkTS Uint8ClampedArray to the target position in its own buffer in sequence, overwriting the original data within the target range.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| target | number | Yes | Subscript of the target start position. If `target < 0`, it starts from the `target + Uint8ClampedArray.length` position. |
| start | number | Yes| Start index of the range. If a negative number is passed in, it refers to the index of `start + Uint8ClampedArray.length`.|
| end | number | No| End index of the range (exclusive). If a negative number is passed in, it refers to the index of `end + Uint8ClampedArray.length`. The default value is the length of the ArkTS Uint8ClampedArray.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint8ClampedArray | Uint8ClampedArray after being modified.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------ |
| 10200011 | The copyWithin method cannot be bound.           |
| 10200201 | Concurrent modification error.               |

**Example**

```ts
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from([1, 2, 3, 4, 5, 6, 7, 8]);
let copied: collections.Uint8ClampedArray = array.copyWithin(3, 1, 3);
// Uint8ClampedArray [1, 2, 3, 2, 3, 6, 7, 8]
```

## some
some(predicate: TypedArrayPredicateFn\<number, Uint8ClampedArray>): boolean

Tests whether any element in the ArkTS Uint8ClampedArray satisfies the specified condition. Returns true if such an element exists; otherwise, returns false.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                 |
| ------- | ------ | ---- | ---------------------------------------------------- |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Uint8ClampedArray> | Yes| Assertion function used for the test.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| boolean | Check result. The value **true** is returned if an element meeting the given condition exists; otherwise, **false** is returned.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                           |
| -------- | ---------------------------------- |
| 10200011 | The some method cannot be bound.   |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let arrayLike = [10, 20, 30, 40, 50];
let uint8ClampedArray: collections.Uint8ClampedArray = new collections.Uint8ClampedArray(arrayLike);
uint8ClampedArray.some((element: number) => element < 1); // false
```

## every
every(predicate: TypedArrayPredicateFn\<number, Uint8ClampedArray>): boolean

Checks whether all elements in this ArkTS Uint8ClampedArray meet a given condition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                   |
| ------- | ------ | ---- | ----------------------------------------------------- |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Uint8ClampedArray> | Yes| Assertion function used for the test.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| boolean | Check result. The value **true** is returned if all elements meet the given condition; otherwise, **false** is returned.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The every method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let arrayLike = [10, 20, 30, 40, 50];
let uint8ClampedArray: collections.Uint8ClampedArray = new collections.Uint8ClampedArray(arrayLike);
uint8ClampedArray.every((element: number) => element > 10);  // false
```

## fill
fill(value: number, start?: number, end?: number): Uint8ClampedArray

Fills all elements in a given range in this ArkTS Uint8ClampedArray with a value.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                     |
| ------- | ------ | ---- | --------------------------------------------------------|
| value | number | Yes | Value to fill. The value range is 0 to 255. Values outside the range are clamped to the range (values less than 0 are automatically corrected to 0, and values greater than 255 are automatically corrected to 255). |
| start | number | No| Start index of the range. If a negative number is passed in, it refers to the index of `start + Uint8ClampedArray.length`. The default value is **0**.|
| end | number | No| End index of the range (exclusive). If a negative number is passed in, it refers to the index of `end + Uint8ClampedArray.length`. The default value is the length of the ArkTS Uint8ClampedArray.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint8ClampedArray | Filled ArkTS Uint8ClampedArray.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The fill method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let arrayLike = [1, 2, 3];
new collections.Uint8ClampedArray(arrayLike).fill(4); // Uint8ClampedArray [4, 4, 4]
new collections.Uint8ClampedArray(arrayLike).fill(4, 1); // Uint8ClampedArray [1, 4, 4]
new collections.Uint8ClampedArray(arrayLike).fill(4, 1, 2); // Uint8ClampedArray [1, 4, 3]
```

## filter
filter(predicate: TypedArrayPredicateFn\<number, Uint8ClampedArray>): Uint8ClampedArray

Returns a new ArkTS Uint8ClampedArray that contains all elements that meet the given condition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                   |
| ------- | ------ | ---- | ------------------------------------------------------ |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Uint8ClampedArray> | Yes| Assertion function used for the test.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint8ClampedArray| Filtered ArkTS Uint8ClampedArray.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The filter method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from([0, 1, 2, 3, 4]);
let filtered: collections.Uint8ClampedArray = array.filter((element: number) => element % 2 == 0);
// Uint8ClampedArray [0, 2, 4]
```

## find
find(predicate: TypedArrayPredicateFn\<number, Uint8ClampedArray>): number | undefined

Returns the value of the first element that passes a test provided by a callback function. If none of the elements pass the test, **undefined** is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Uint8ClampedArray> | Yes| Assertion function used for the test.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
|  number \| undefined | Value of the first element that passes the test. If none of the elements pass the test, **undefined** is returned.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The find method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from([0, 1, 2, 3, 4]);
array.find((element: number) => element > 2); // 3
array.find((element: number) => element > 4); // undefined
```

## findIndex
findIndex(predicate: TypedArrayPredicateFn\<number, Uint8ClampedArray>): number

Returns the index of the first element that passes a test provided by a callback function. If none of the elements pass the test, **-1** is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Uint8ClampedArray> | Yes| Assertion function used for the test.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| number | Index of the first element that passes the test. If none of the elements pass the test, **-1** is returned.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The findIndex method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**Example**

```ts
const array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from([1, 2, 3, 4, 5]);
let foundIndex: number = array.findIndex((element: number) => element % 2 === 0); // 1
```

## forEach
forEach(callbackFn: TypedArrayForEachCallback\<number, Uint8ClampedArray>): void

Calls a callback function for each element in this ArkTS Uint8ClampedArray.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| callbackFn | [TypedArrayForEachCallback](arkts-apis-arkts-collections-Types.md#typedarrayforeachcallback)\<number, Uint8ClampedArray> | Yes| Callback function to run for each element.|


**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The forEach method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let uint8ClampedArray: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from([1, 2, 3]);
uint8ClampedArray.forEach((value: number, index: number, array: collections.Uint8ClampedArray) => {
  console.info(`Element ${value} at index ${index}`);
});
```

## indexOf
indexOf(searchElement: number, fromIndex?: number): number

Returns the index of the first occurrence of a value in this ArkTS Uint8ClampedArray. If the value is not found, **-1** is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name       | Type  | Mandatory| Description                       |
| ------------- | ------ | ---- | ---------------------------|
| searchElement | number | Yes  | Value to search for.               |
| fromIndex     | number | No   | Start index for searching from front to back. Default value is 0. If the provided index value is negative, it is treated as an offset from the end of the array. If the value of fromIndex causes the search range to have no overlap with the array range, -1 is returned. |

**Return value**

| Type        | Description     |
| ------------ | --------- |
| number | Index of the first occurrence of the value. If the value is not found, **-1** is returned.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The indexOf method cannot be bound. |
| 10200201 | Concurrent modification error.                |

**Example**

```ts
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from([3, 5, 9]);
array.indexOf(3); // 0
array.indexOf(7); // -1
array.indexOf(9, 2); // 2
array.indexOf(9, -2); // 2
```

## lastIndexOf<sup>18+</sup>

lastIndexOf(searchElement: number, fromIndex?: number): number

Obtains the index of the last occurrence of the specified value in this ArkTS Uint8ClampedArray.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name          | Type    | Mandatory | Description                                                                               |
| ------------- | ------ | --- | --------------------------------------------------------------------------------- |
| searchElement | number | Yes  | Value to search for.                                                                           |
| fromIndex     | number | No   | The starting index for searching from back to front. The default value is the length of ArkTS Uint8ClampedArray minus 1. If the provided index value is negative, it is treated as an offset from the end of the array. If the value of fromIndex causes the search range and the array range to have no overlap, -1 is returned. |

**Return value**

| Type    | Description                     |
| ------ | ----------------------- |
| number | Index of the last occurrence of the value. If the value is not found, **-1** is returned.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID   | Error Message                                   |
| -------- | --------------------------------------- |
| 10200011 | The lastIndexOf method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from([3, 5, 9]);
console.info(`${array.lastIndexOf(3)}`); // Expected output: 0
console.info(`${array.lastIndexOf(7)}`); // Expected output: -1
console.info(`${array.lastIndexOf(9, 2)}`); // Expected output: 2
console.info(`${array.lastIndexOf(9, -2)}`); // Expected output: -1
```

## join
join(separator?: string): string

Concatenates all elements in this ArkTS Uint8ClampedArray into a string, with a given separator.

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

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The join method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**Example**

```ts
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from([1, 2, 3, 4, 5]);
let joined: string = array.join('-'); // "1-2-3-4-5"
```

## map
map(callbackFn: TypedArrayMapCallback\<number, Uint8ClampedArray>): Uint8ClampedArray

Applies a callback function to each element in this ArkTS Uint8ClampedArray and uses the result to create an ArkTS Uint8ClampedArray.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | ---------------------------------------------------- |
| callbackFn | [TypedArrayMapCallback](arkts-apis-arkts-collections-Types.md#typedarraymapcallback)\<number, Uint8ClampedArray> | Yes | Callback function to run for each element.|


**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint8ClampedArray | New ArkTS Uint8ClampedArray.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The map method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from([25, 36, 49]);
const mapped: collections.Uint8ClampedArray = array.map(Math.sqrt); // Uint8ClampedArray [5, 6, 7]
```

## reduce
reduce(callbackFn: TypedArrayReduceCallback\<number, number, Uint8ClampedArray>): number

Applies a reduce function on each element in this ArkTS Uint8ClampedArray and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name    | Type  | Mandatory|  Description    |
| ---------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<number, number, Uint8ClampedArray> | Yes| Reduce function.|

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
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from([1, 2, 3, 4, 5]);
let reducedValue: number = array.reduce((accumulator: number, value: number) => accumulator + value);
// reducedValue == 15
```

## reduceRight<sup>18+</sup>

reduceRight(callbackFn: TypedArrayReduceCallback\<number, number, Uint8ClampedArray>): number

Reversely traverses this ArkTS Uint8ClampedArray, applies a reduce function on each element in the array, and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name    | Type  | Mandatory|  Description    |
| ---------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<number, number, Uint8ClampedArray> | Yes| Reduce function.|

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
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from([1, 2, 3, 4, 5]);
let reducedValue: number = array.reduceRight((accumulator: number, value: number) => accumulator + value);
console.info(`${reducedValue}`); // Expected output: 15
```

## reduce
reduce\<U = number>(callbackFn: TypedArrayReduceCallback\<U, number, Uint8ClampedArray>, initialValue: U): U

Applies a reduce function for each element in this ArkTS Uint8ClampedArray, receives an initial value as the parameter called by the reduce function for the first time, and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | --------------------------------------------------- |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<U, number, Uint8ClampedArray> | Yes | Reduce function.|
| initialValue | U | Yes | Initial value.|


**Return value**

| Type        | Description     |
| ------------ | --------- |
| U | Final result obtained from the last call of the reduce function.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The reduce method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from([1, 2, 3, 4, 5]);
let reducedValue: number = array.reduce((accumulator: number, value: number) => accumulator + value, 1);
// reducedValue == 16
```

## reduceRight<sup>18+</sup>

reduceRight\<U = number>(callbackFn: TypedArrayReduceCallback\<U, number, Uint8ClampedArray>, initialValue: U): U

Reversely traverses this ArkTS Uint8ClampedArray, applies a reduce function for each element in the array, receives an initial value as the parameter called by the reduce function for the first time, and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | --------------------------------------------------- |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<U, number, Uint8ClampedArray> | Yes | Reduce function.|
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
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from([1, 2, 3, 4, 5]);
let reducedValue: number = array.reduceRight((accumulator: number, value: number) => accumulator + value, 1);
console.info(`${reducedValue}`); // Expected output: 16
```

## reverse
reverse(): Uint8ClampedArray

Reverses the order of the elements in the ArkTS Uint8ClampedArray and returns the reversed ArkTS Uint8ClampedArray object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint8ClampedArray   | Reversed ArkTS Uint8ClampedArray.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The reverse method cannot be bound. |
| 10200201 | Concurrent modification error.   |

**Example**

```ts
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from([1, 2, 3, 4, 5]);
let reversed: collections.Uint8ClampedArray = array.reverse(); // Uint8ClampedArray [5, 4, 3, 2, 1]
```

## set
set(array: ArrayLike\<number>, offset?: number): void

Writes the passed-in ArrayLike elements into the ArkTS Uint8ClampedArray in sequence, replacing the original elements starting from the beginning position.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | ---------------------------------------------------- |
| array | ArrayLike\<number> | Yes | Array-like object whose elements will be written.|
| offset | number | No  | The starting position to write to, which is a non-negative integer, and the sum of offset and array.length cannot exceed the length of the ArkTS Uint8ClampedArray. The default value is 0.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The set method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**Example**

```ts
let buffer: collections.ArrayBuffer = new collections.ArrayBuffer(8);
let array: collections.Uint8ClampedArray = new collections.Uint8ClampedArray(buffer);
array.set([1, 2, 3], 3); // Uint8ClampedArray [0, 0, 0, 1, 2, 3, 0, 0]
```

## slice
slice(start?: number, end?: number): Uint8ClampedArray

Returns a new ArkTS Uint8ClampedArray object that copies the content of the specified range of the original ArkTS Uint8ClampedArray. Unlike [subarray](#subarray), this method generates an independent copy and does not affect the original ArkTS Uint8ClampedArray object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description                                                  |
| ------ | ------ | ---- | -----------------------------------------------------|
| start  | number | No  | Start index of the range. If a negative number is passed in, it refers to the index of `start + Uint8ClampedArray.length`. The default value is **0**.|
| end    | number | No  | End index of the range (exclusive). If a negative number is passed in, it refers to the index of `end + Uint8ClampedArray.length`. The default value is the length of the ArkTS Uint8ClampedArray.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint8ClampedArray | New ArkTS Uint8ClampedArray.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The slice method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from([1, 2, 3, 4, 5]);
array.slice(); // Uint8ClampedArray [1, 2, 3, 4, 5]
array.slice(1, 3); // Uint8ClampedArray [2, 3]
array.slice(-2); // Uint8ClampedArray [4, 5]
```

## sort
sort(compareFn?: TypedArrayCompareFn\<number>): Uint8ClampedArray

Sorts elements in this ArkTS Uint8ClampedArray and returns the sorted ArkTS Uint8ClampedArray.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type                  | Mandatory| Description                                      |
| --------- | ---------------------- | ---- | ------------------------------------------ |
| compareFn | [TypedArrayCompareFn](arkts-apis-arkts-collections-Types.md#typedarraycomparefn)\<number> | No  | Function that determines the sort order. By default, elements are sorted in ascending order.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint8ClampedArray | Sorted ArkTS Uint8ClampedArray.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------ |
| 10200011 | The sort method cannot be bound. |
| 10200201 | Concurrent modification error.         |

**Example**

```ts
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from([1, 3, 5, 4, 2]);
array.sort(); // Uint8ClampedArray [1, 2, 3, 4, 5]
array.sort((a: number, b: number) => a - b); // Uint8ClampedArray [1, 2, 3, 4, 5]
array.sort((a: number, b: number) => b - a); // Uint8ClampedArray [5, 4, 3, 2, 1]
```

## subarray
subarray(begin?: number, end?: number): Uint8ClampedArray

Truncates the array from the specified position and returns a new ArkTS Uint8ClampedArray object based on the same ArkTS ArrayBuffer. Unlike [slice](#slice), this method does not generate an independent copy and affects the original ArkTS Uint8ClampedArray object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description                                               |
| ------ | ------ | ---- | ------------------------------------------------- |
| begin  | number | No  | Start index of the range. If a negative number is passed in, it refers to the index of `begin + Uint8ClampedArray.length`. The default value is **0**.|
| end    | number | No  | End index of the range (exclusive). If a negative number is passed in, it refers to the index of `end + Uint8ClampedArray.length`. The default value is the length of the ArkTS Uint8ClampedArray.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint8ClampedArray | New ArkTS Uint8ClampedArray.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID|            Error Message                              |
| -------- | -------------------------------------------------|
| 10200011 | The subarray method cannot be bound.             |
| 10200201 | Concurrent modification error.               |

**Example**

```ts
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from([1, 2, 3, 4, 5]);
let subArray: collections.Uint8ClampedArray = array.subarray(); // Uint8ClampedArray [1, 2, 3, 4, 5]
subArray.set([10, 20, 30]); // Uint8ClampedArray [10, 20, 30, 4, 5]
```

## at
at(index: number): number | undefined

Returns the element at the given index. If no element is found, **undefined** is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| index  | number | Yes  | Index of the ArkTS Uint8ClampedArray element to return (zero-based), which is an integer. If `index < 0`, the element at position `index + Uint8ClampedArray.length` is accessed. |

**Return value**

| Type        | Description     |
| ------------ | --------- |
| number \| undefined| Element obtained. If no element is found, **undefined** is returned.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID|                       Error Message                   |
| -------- | ------------------------------------------------ |
| 10200011 | The at method cannot be bound.                   |
| 10200201 | Concurrent modification error.               |

**Example**

```ts
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from([1, 2, 3, 4, 5]);
console.info(`element: ${array.at(2)}`);  // element: 3
console.info(`element: ${array.at(-1)}`); // element: 5
console.info(`element: ${array.at(6)}`);  // element: undefined
```

## includes
includes(searchElement: number, fromIndex?: number): boolean

Checks whether elements are contained in this ArkTS Uint8ClampedArray.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name| Type  | Mandatory| Description                                     |
| ------ | ------ | ---- | --------------------------------------- |
| searchElement  | number | Yes  | Element to search for.|
| fromIndex  | number | No | Index from which the search starts. If a negative number is passed in, it refers to the index of `fromIndex + Uint8ClampedArray.length`. The default value is **0**.|

**Return value**

| Type   | Description                                                       |
| ------- | ---------------------------------------------------------- |
| boolean | Check result. The value **true** is returned if the element exists; otherwise, **false** is returned.|


**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The includes method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from([1, 2, 3]);
console.info(`includes: ${array.includes(2)}`);    // includes: true
console.info(`includes: ${array.includes(4)}`);    // includes: false
console.info(`includes: ${array.includes(3, 3)}`); // includes: false
```

## entries
entries(): IterableIterator\<[number, number]>

Returns a new iterator object that contains the key-value pairs of each element in the ArkTS Uint8ClampedArray. During iteration, methods that change the content of the ArkTS Uint8ClampedArray cannot be used.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description     |
| ------------ | --------- |
| IterableIterator\<[number, number]>| Iterator object.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The entries method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from([11, 22, 33]);
let iterator: IterableIterator<[number, number]> = array.entries();
console.info(`value: ${iterator.next().value}`); // value: 0,11
console.info(`value: ${iterator.next().value}`); // value: 1,22
console.info(`value: ${iterator.next().value}`); // value: 2,33
```

## keys
keys(): IterableIterator\<number>

Returns a new iterator object that contains the keys (subscripts) of each element in the ArkTS Uint8ClampedArray. During iteration, methods that change the content of the ArkTS Uint8ClampedArray cannot be used.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description     |
| ------------ | --------- |
| IterableIterator\<number> | Iterator object.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The keys method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from([1, 2, 3, 4, 5]);
let iterator: IterableIterator<number> = array.keys();
for (const key of iterator) {
  console.info(`${key}`); // Output 0,1,2,3,4 in sequence.
}
```

## values
values(): IterableIterator\<number>

Returns a new iterator object that contains the values of each element in the ArkTS Uint8ClampedArray. During iteration, methods that change the content of the ArkTS Uint8ClampedArray cannot be used.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description     |
| ------------ | --------- |
| IterableIterator\<number> | Iterator object.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The values method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**Example**

```ts
let array: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from([1, 2, 3, 4, 5]);
let iterator: IterableIterator<number> = array.values();
for (const value of iterator) {
  console.info(`${value}`); // Output 1,2,3,4,5 in sequence
}
```

## [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;number&gt;

Returns an iterator object used to traverse the value of each element in the ArkTS Uint8ClampedArray. During iteration, methods that change the content of the ArkTS Uint8ClampedArray cannot be used.

> **NOTE**
>
> This API cannot be used in .ets files.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type                     | Description            |
| ------------------------- | ---------------- |
| IterableIterator&lt;number&gt; | Iterator object containing the value of each element. |

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 10200011 | The Symbol.iterator method cannot be bound. |

**Example**

```ts
let uint8ClampedArray: collections.Uint8ClampedArray = collections.Uint8ClampedArray.from([1, 2, 3, 4, 5, 6]);

for (let item of uint8ClampedArray) {
  console.info(`value : ${item}`);
}
```

## [index: number]

&#91;index: number&#93;: number

Returns the element at a given index in this Uint8ClampedArray.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type  | Mandatory| Description                    |
| ----- | ------ | ---- | -------------------------- |
| index | number | Yes | Zero-based index of the desired element. |

**Return value**

| Type  | Description                |
| ----- | ---------------------|
| number | Element at the specified index. |

**Example**

```ts
let uint8ClampedArray = collections.Uint8ClampedArray.from([1, 2, 4]);
console.info(`Element at index 1: ${uint8ClampedArray[1]}`);
```
