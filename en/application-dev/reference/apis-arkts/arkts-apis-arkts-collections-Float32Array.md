# Class (Float32Array)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=08d9523ef0226b259d674e299ae60897c53575d4 translatedAt=2026-11-16T04:39:19.300Z pushedAt=2026-11-16T06:31:14.122Z nl=2 -->

A linear data structure whose underlying implementation is based on [ArrayBuffer](arkts-apis-arkts-collections-ArrayBuffer.md).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This module can be imported only to ArkTS files (with the file name extension .ets).

**Decorator**: \@Sendable

## Modules to Import

```ts
import { collections } from '@kit.ArkTS';
```

## Properties

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

| Name  | Type  | Read Only| Optional| Description             |
| ------ | ------ | ---- | ---- | ----------------|
| buffer | ArrayBuffer | Yes  | No | Bottom-layer buffer used by an ArkTS Float32Array.|
| byteLength | number | Yes | No | Number of bytes occupied by the ArkTS Float32Array. |
| byteOffset | number | Yes | No | Byte offset of the ArkTS Float32Array from the start position of its ArrayBuffer. |
| length | number | Yes  | No | Number of elements in an ArkTS Float32Array.|
| BYTES_PER_ELEMENT | number | Yes | No | Number of bytes occupied by each element in the ArkTS Float32Array. |

## constructor
constructor()

A constructor used to create an empty ArkTS Float32Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 10200012 | The Float32Array's constructor cannot be directly invoked. |

**Example**

```ts
// Create an empty Float32Array object.
let float32Array: collections.Float32Array = new collections.Float32Array();
```

## constructor
constructor(length: number)

A constructor used to create an ArkTS Float32Array of a given length.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                         |
| ------- | ------ | ---- | --------------------------- |
| length | number | Yes | Used to specify the length of the ArkTS Float32Array. The value must be a non-negative integer. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                                 |
| -------- | -------------------------------------------------------  |
| 10200012 | The Float32Array's constructor cannot be directly invoked. |


**Example**

```ts
// Construct an object with the length parameter.
let float32Array: collections.Float32Array = new collections.Float32Array(12);
```

## constructor
constructor(elements: Iterable\<number>)

A constructor that creates an ArkTS Float32Array from an iterable object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| elements |  Iterable\<number> | Yes| An iterable collection of numbers used to construct an ArkTS Float32Array object.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 10200012 | The Float32Array's constructor cannot be directly invoked. |

**Example**

```ts
// Construct an object from an Iterable, Float32Array [1, 2, 3]
let set: Set<number> = new Set<number>([1, 2, 3]);
let float32Array: collections.Float32Array = new collections.Float32Array(set);
```

## constructor
constructor(array: ArrayLike\<number> | ArrayBuffer)

A constructor that creates an ArkTS Float32Array from an array-like object or ArkTS ArrayBuffer.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| array |  ArrayLike\<number> \| ArrayBuffer | Yes | Object used to construct an ArkTS Float32Array. When the parameter type is ArrayBuffer, the number of bytes occupied by the buffer must be an integer multiple of 4. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 10200012 | The Float32Array's constructor cannot be directly invoked. |

**Example**

```ts
// Example 1: Construct an object from an array-like object.
let arrayLike = [1, 3, 5];
let float32Array: collections.Float32Array = new collections.Float32Array(arrayLike);
```

```ts
// Example 2: Construct an object from an ArrayBuffer.
let arrayBuffer: collections.ArrayBuffer = new collections.ArrayBuffer(12);
let float32Array: collections.Float32Array = new collections.Float32Array(arrayBuffer);
```

```ts
// Example 3: Construct an object from another ArkTS Float32Array.
let arrayLike = [1, 3, 5];
// float32Array1 [1, 3, 5]
let float32Array1: collections.Float32Array = new collections.Float32Array(arrayLike);
// float32Array2 [1, 3, 5]
let float32Array2: collections.Float32Array = new collections.Float32Array(float32Array1);
```

## constructor
constructor(buffer: ArrayBuffer, byteOffset?: number, length?: number)

Constructor that creates an ArkTS Float32Array object from an ArkTS ArrayBuffer.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                        |
| ------- | ------ | ---- | ------------------------------------------ |
| buffer | ArrayBuffer | Yes | ArrayBuffer object used to construct the ArkTS Float32Array. The number of bytes occupied by buffer must be an integer multiple of 4. |
| byteOffset | number | No | Specifies the byte offset of buffer, starting from 0. The default value is 0. byteOffset must be an integer multiple of 4. |
| length | number | No | Specifies the length of the ArkTS Float32Array. The default value is 0. The value must be a non-negative integer and must satisfy byteOffset + length * 4 <= buffer.byteLength. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                                  |
| -------- | -------------------------------------------------------   |
| 10200012 | The Float32Array's constructor cannot be directly invoked. |

**Example**

```ts
let float32Array: collections.Float32Array = collections.Float32Array.from([1, 2, 3, 4, 5, 6]);
console.info("byteLength: " + float32Array.buffer.byteLength); // byteLength: 24
// Start from the fourth byte of the buffer corresponding to Float32Array. The length is 5.
let float32Array1: collections.Float32Array = new collections.Float32Array(float32Array.buffer, 4, 5);
console.info("[" + float32Array1 + "]"); // [2, 3, 4, 5, 6]
```

## from
static from(arrayLike: ArrayLike\<number>): Float32Array

Creates an ArkTS Float32Array object from an ArrayLike.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                 |
| ------- | ------ | ---- | --------------------------------------------------- |
| arrayLike | ArrayLike\<number> | Yes| Array-like object used to construct the ArkTS Float32Array.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Float32Array | New ArkTS Float32Array generated.|

**Example**
```ts
let arrayLike = [1, 3, 5];
let array: collections.Float32Array = collections.Float32Array.from(arrayLike); // array [1, 3, 5]
```

## from
static from\<T>(arrayLike: ArrayLike\<T>, mapFn: TypedArrayFromMapFn\<T, number>): Float32Array

Creates an ArkTS Float32Array from an array-like object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name | Type  | Mandatory| Description                                       |
| ------- | ------ | ---- | ------------------------------------------|
| arrayLike | ArrayLike\<T> | Yes | Array-like object used to construct the ArkTS Float32Array. |
| mapFn | [TypedArrayFromMapFn](arkts-apis-arkts-collections-Types.md#typedarrayfrommapfn)\<T, number> | Yes| Mapping function.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Float32Array | New ArkTS Float32Array generated.|

**Example**

```ts
// Example 1: Create from an object, Float32Array [0, 1, 2, 3, 4]
let array: collections.Float32Array = collections.Float32Array.from<number>(
  { length: 5 }, (v: Object, k: number) => k);
```

```ts
// Example 2: Create from a character array, Float32Array [1, 3, 5]
let array: collections.Float32Array = collections.Float32Array.from<string>(
  ["1", "3", "5"], (v: string, k: number) => parseInt(v));
```

```ts
// Example 3: Create from a string, Float32Array [1, 2, 3, 4, 5]
let array: collections.Float32Array = collections.Float32Array.from<string>(
  "12345", (v: string, k: number) => parseInt(v));
```

## from
static from(arrayLike: Iterable\<number>, mapFn?: TypedArrayFromMapFn\<number, number>): Float32Array

Creates an ArkTS Float32Array from an iterator object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name | Type  | Mandatory| Description                               |
| ------- | ------ | ---- | -----------------------------------|
| arrayLike | Iterable\<number> | Yes | An iterable object used to construct an ArkTS Float32Array. |
| mapFn | [TypedArrayFromMapFn](arkts-apis-arkts-collections-Types.md#typedarrayfrommapfn)\<number, number> | No| Mapping function. If no value is passed in, no special processing is conducted on the elements.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Float32Array | New ArkTS Float32Array generated.|

**Example**

```ts
// Example 1: No mapping function is specified. Float32Array [1, 2, 3]
let set: Set<number> = new Set<number>([1, 2, 3]);
let array: collections.Float32Array = collections.Float32Array.from(set);
```

```ts
// Example 2: specified mapping function, Float32Array [1, 3, 5]
let set: Set<number> = new Set<number>([1, 2, 3]);
let array: collections.Float32Array = collections.Float32Array.from(
  set, (v: number, k: number) => v + k);
```

## of<sup>18+</sup>

static of(...items: number[]): Float32Array

Creates a new ArkTS Float32Array object from a variable number of arguments.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type         | Mandatory| Description                           |
| --------- | ------------- | ---- | ------------------------------- |
| items | number[] | No | Elements used to create the array. The number of parameters is variable. The default value is an empty array. |

**Return value**

| Type     | Description                   |
| --------- | ----------------------- |
| Float32Array | New ArkTS Float32Array object. |

**Example**

```ts
// Create a Float32Array object through mutable parameters.
let float32Array: collections.Float32Array = collections.Float32Array.of(1, 2, 3, 4);
console.info(float32Array.toString()); // Expected output: 1,2,3,4
```

## toString<sup>18+</sup>

toString(): string

Converts the ArkTS Float32Array to a string, with elements joined by commas.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description           |
| ---------- | ------------- |
| string | A string containing all elements of the array, with each element separated by a comma. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID   | Error Message                                |
| -------- | ------------------------------------ |
| 10200011 | The toString method cannot be bound. |
| 10200201 | Concurrent modification error.       |

**Example**

```ts
let float32Array = new collections.Float32Array([1, 2, 3, 4, 5]);
let stringArray = float32Array.toString(); // Convert the Float32Array to a string
console.info(stringArray); // Expected output: 1,2,3,4,5
```

## toLocaleString<sup>18+</sup>

toLocaleString(): string

Obtains a number representation that conforms to the current cultural conventions based on the system locale of the current application. Each element calls its own toLocaleString method to convert the number to a string, and then the results of each element are joined in order into a string using commas.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description           |
| ---------- | ------------- |
| string | A string containing all elements of the array, with each element represented in localized format and separated by commas. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID   | Error Message                                      |
| -------- | ------------------------------------------ |
| 10200011 | The toLocaleString method cannot be bound. |
| 10200201 | Concurrent modification error.             |

**Example**

```ts
// The system where the application is running is set to the French locale.
let array = new collections.Float32Array([1000, 2000, 3000]);
let stringArray = array.toLocaleString();
console.info(stringArray); // Expected output: 1 000,2 000,3 000
```

## copyWithin
copyWithin(target: number, start: number, end?: number): Float32Array

Copies elements within a given range from this ArkTS Float32Array to another position in sequence.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| target | number | Yes | Index of the target start position. If `target < 0`, it starts from the position `target + Float32Array.length`. |
| start | number | Yes | Index of the source start position. If `start < 0`, it starts from the position `start + Float32Array.length`. |
| end | number | No | Index of the source end position (excluding the element at the end position). If `end < 0`, it ends at the position `end + Float32Array.length`. The default value is the length of the ArkTS Float32Array. |

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Float32Array | The modified ArkTS Float32Array. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------ |
| 10200011 | The copyWithin method cannot be bound.           |
| 10200201 | Concurrent modification error.               |

**Example**

```ts
let float32Array: collections.Float32Array = collections.Float32Array.from([1, 2, 3, 4, 5, 6, 7, 8]);
// Float32Array [1, 2, 3, 2, 3, 6, 7, 8]
let copied: collections.Float32Array = float32Array.copyWithin(3, 1, 3);
```

## some
some(predicate: TypedArrayPredicateFn\<number, Float32Array>): boolean

Tests whether any element in the ArkTS Float32Array satisfies the specified condition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                 |
| ------- | ------ | ---- | ---------------------------------------------------- |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Float32Array> | Yes| Assertion function used for the test.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| boolean | Check result. The value **true** is returned if an element meeting the given condition exists; otherwise, **false** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                           |
| -------- | ---------------------------------- |
| 10200011 | The some method cannot be bound.   |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let arrayLike = [-10, 20, -30, 40, -50];
let float32Array: collections.Float32Array = new collections.Float32Array(arrayLike);
// Test whether an element less than 0 exists.
float32Array.some((element: number) => element < 0); // true
```

## every
every(predicate: TypedArrayPredicateFn\<number, Float32Array>): boolean

Checks whether all elements in this ArkTS Float32Array meet a given condition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                   |
| ------- | ------ | ---- | ----------------------------------------------------- |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Float32Array> | Yes| Assertion function used for the test.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| boolean | Check result. The value **true** is returned if all elements meet the given condition; otherwise, **false** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The every method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let arrayLike = [-10, 20, -30, 40, -50];
let float32Array: collections.Float32Array = new collections.Float32Array(arrayLike);
// Determine whether all elements are greater than 0.
float32Array.every((element: number) => element > 0);  // false
```

## fill
fill(value: number, start?: number, end?: number): Float32Array

Fills all elements in a given range in this ArkTS Float32Array with a value.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                     |
| ------- | ------ | ---- | --------------------------------------------------------|
| value | number | Yes| Value to fill in.|
| start | number | No| Start index of the range. If a negative number is passed in, it refers to the index of `start + Float32Array.length`. The default value is **0**.|
| end | number | No| End index of the range (exclusive). If a negative number is passed in, it refers to the index of `end + Float32Array.length`. The default value is the length of the ArkTS Float32Array.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Float32Array | The ArkTS Float32Array after filling.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The fill method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let arrayLike = [1, 2, 3];
// Fill all elements with 4.
new collections.Float32Array(arrayLike).fill(4); // Float32Array [4, 4, 4]
// Start filling 4 from index 1.
new collections.Float32Array(arrayLike).fill(4, 1); // Float32Array [1, 4, 4]
// Fill 4 from index 1 to 2 (exclusive).
new collections.Float32Array(arrayLike).fill(4, 1, 2); // Float32Array [1, 4, 3]
```

## filter
filter(predicate: TypedArrayPredicateFn\<number, Float32Array>): Float32Array

Returns a new ArkTS Float32Array that contains all elements that meet the given condition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                   |
| ------- | ------ | ---- | ------------------------------------------------------ |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Float32Array> | Yes| Assertion function used for the test.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Float32Array| Filtered ArkTS Float32Array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The filter method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Float32Array = collections.Float32Array.from([0, 1, 2, 3, 4]);
// Float32Array [0, 2, 4]
let filtered: collections.Float32Array = array.filter((element: number) => element % 2 === 0);
```

## find
find(predicate: TypedArrayPredicateFn\<number, Float32Array>): number | undefined

Returns the value of the first element that passes a test provided by a callback function. If none of the elements pass the test, **undefined** is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Float32Array> | Yes| Assertion function used for the test.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
|  number \| undefined | Value of the first element that passes the test. If none of the elements pass the test, **undefined** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The find method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Float32Array = collections.Float32Array.from([0, 1, 2, 3, 4]);
array.find((element: number) => element > 2); // 3
array.find((element: number) => element > 4); // undefined
```

## findIndex
findIndex(predicate: TypedArrayPredicateFn\<number, Float32Array>): number

Returns the index of the first element that passes a test provided by a callback function. If none of the elements pass the test, **-1** is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Float32Array> | Yes| Assertion function used for the test.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| number | Index of the first element that passes the test. If none of the elements pass the test, **-1** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The findIndex method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**Example**

```ts
const array: collections.Float32Array = collections.Float32Array.from([1, 2, 3, 4, 5]);
let foundIndex: number = array.findIndex((element: number) => element % 2 === 0); // 1
```

## forEach
forEach(callbackFn: TypedArrayForEachCallback\<number, Float32Array>): void

Calls a callback function for each element in this ArkTS Float32Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| callbackFn | [TypedArrayForEachCallback](arkts-apis-arkts-collections-Types.md#typedarrayforeachcallback)\<number, Float32Array> | Yes| Callback function to run for each element.|


**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The forEach method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let float32Array: collections.Float32Array = collections.Float32Array.from([1, 2, 3]);
// Traverse each element in Float32Array.
float32Array.forEach((value: number, index: number, array: collections.Float32Array) => {
  console.info("Element " + value + " at index " + index);
});
```

## indexOf
indexOf(searchElement: number, fromIndex?: number): number

Returns the index of the first occurrence of a value in this ArkTS Float32Array. If the value is not found, **-1** is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name       | Type  | Mandatory| Description                       |
| ------------- | ------ | ---- | ---------------------------|
| searchElement | number | Yes  | Element value to search for.                |
| fromIndex     | number | No   | Start index for the search. The default value is 0. If the index is greater than or equal to the length of the ArkTS Float32Array, -1 is returned. If the index is negative, it is treated as an offset from the end of the array, and the search proceeds from front to back. |

**Return value**

| Type        | Description     |
| ------------ | --------- |
| number | Index of the first occurrence of the value. If the value is not found, **-1** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The indexOf method cannot be bound. |
| 10200201 | Concurrent modification error.                |

**Example**

```ts
let array: collections.Float32Array = collections.Float32Array.from([3, 5, 9]);
array.indexOf(3); // 0
array.indexOf(7); // -1
array.indexOf(9, 2); // 2
array.indexOf(9, -2); // 2
```

## lastIndexOf<sup>18+</sup>

lastIndexOf(searchElement: number, fromIndex?: number): number

Returns the index of the last occurrence of searchElement in the ArkTS Float32Array instance. If it does not exist, -1 is returned.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name          | Type    | Mandatory | Description                                                                               |
| ------------- | ------ | --- | --------------------------------------------------------------------------------- |
| searchElement | number | Yes  | Element value to search for.                                                                  |
| fromIndex     | number | No   | Start index of the search, searching backward from this position. The default value is the length of the ArkTS Float32Array minus 1 (that is, starting from the end). If the index is greater than or equal to the length of the ArkTS Float32Array, the search starts from the end and goes backward. If the provided index is negative, it is treated as an offset from the end of the array, searching from back to front. |

**Return value**

| Type    | Description                     |
| ------ | ----------------------- |
| number | Index of the last occurrence of the value. If the value is not found, **-1** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID   | Error Message                                   |
| -------- | --------------------------------------- |
| 10200011 | The lastIndexOf method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Float32Array = collections.Float32Array.from([3, 5, 9]);
console.info(array.lastIndexOf(3) + ''); // Expected output: 0
console.info(array.lastIndexOf(7) + ''); // Expected output: -1
console.info(array.lastIndexOf(9, 2) + ''); // Expected output: 2
console.info(array.lastIndexOf(9, -2) + ''); // Expected output: -1
```

## join
join(separator?: string): string

Concatenates all elements in this ArkTS Float32Array into a string, with a given separator.

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

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The join method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**Example**

```ts
let array: collections.Float32Array = collections.Float32Array.from([1, 2, 3, 4, 5]);
let joined: string = array.join('-'); // "1-2-3-4-5"
```

## map
map(callbackFn: TypedArrayMapCallback\<number, Float32Array>): Float32Array

Applies a callback function to each element in this ArkTS Float32Array and uses the result to create an ArkTS Float32Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | ---------------------------------------------------- |
| callbackFn | [TypedArrayMapCallback](arkts-apis-arkts-collections-Types.md#typedarraymapcallback)\<number, Float32Array> | Yes | Callback function to run for each element.|


**Return value**

| Type        | Description     |
| ------------ | --------- |
| Float32Array | A new ArkTS Float32Array object containing the results after the callback function processes the elements.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The map method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Float32Array = collections.Float32Array.from([25, 36, 49]);
const mapped: collections.Float32Array = array.map(Math.sqrt); // Float32Array [5, 6, 7]
```

## reduce
reduce(callbackFn: TypedArrayReduceCallback\<number, number, Float32Array>): number

Applies a reduce function on each element in this ArkTS Float32Array and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name    | Type  | Mandatory|  Description    |
| ---------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<number, number, Float32Array> | Yes| Reduce function.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| number | Final result obtained from the last call of the reduce function.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID|                      Error Message                    |
| -------- | ------------------------------------------------ |
| 10200011 | The reduce method cannot be bound.               |
| 10200201 | Concurrent modification error.               |

**Example**

```ts
let array: collections.Float32Array = collections.Float32Array.from([1, 2, 3, 4, 5]);
let reducedValue: number = array.reduce((accumulator: number, value: number) => accumulator + value);
// reducedValue == 15
```

## reduceRight<sup>18+</sup>

reduceRight(callbackFn: TypedArrayReduceCallback\<number, number, Float32Array>): number

Traverses the ArkTS Float32Array in reverse order, executes the reducer function on each element, and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name    | Type  | Mandatory|  Description    |
| ---------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<number, number, Float32Array> | Yes| Reduce function.|

**Return value**

| Type    | Description         |
| ------ | ----------- |
| number | Final result obtained from the last call of the reduce function.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID   | Error Message                                   |
| -------- | --------------------------------------- |
| 10200011 | The reduceRight method cannot be bound. |
| 10200201 | Concurrent modification error.      |

**Example**

```ts
let array: collections.Float32Array = collections.Float32Array.from([1, 2, 3, 4, 5]);
let reducedValue: number = array.reduceRight((accumulator: number, value: number) => accumulator + value);
console.info(reducedValue + ''); // Expected output: 15
```

## reduce
reduce\<U = number>(callbackFn: TypedArrayReduceCallback\<U, number, Float32Array>, initialValue: U): U

Applies a reduce function for each element in this ArkTS Float32Array, receives an initial value as the parameter called by the reduce function for the first time, and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | --------------------------------------------------- |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<U, number, Float32Array> | Yes | Reduce function.|
| initialValue | U | Yes  | Initial accumulated value when the reduction function is called for the first time. |


**Return value**

| Type        | Description     |
| ------------ | --------- |
| U | Final result obtained from the last call of the reduce function.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The reduce method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Float32Array = collections.Float32Array.from([1, 2, 3, 4, 5]);
// reducedValue == 16
let reducedValue: number = array.reduce((accumulator: number, value: number) => accumulator + value, 1);
```

## reduceRight<sup>18+</sup>

reduceRight\<U = number>(callbackFn: TypedArrayReduceCallback\<U, number, Float32Array>, initialValue: U): U

Traverses the ArkTS Float32Array in reverse order, executes the reducer function on each element, receives an initial value as the argument for the first call of the reducer function, and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | --------------------------------------------------- |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<U, number, Float32Array> | Yes | Reduce function.|
| initialValue | U | Yes  | Initial accumulated value when the reduction function is called for the first time. |

**Return value**

| Type    | Description         |
| ------ | ----------- |
| U | Final result obtained from the last call of the reduce function.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID   | Error Message                                   |
| -------- | --------------------------------------- |
| 10200011 | The reduceRight method cannot be bound. |
| 10200201 | Concurrent modification error.      |

**Example**

```ts
let array: collections.Float32Array = collections.Float32Array.from([1, 2, 3, 4, 5]);
let reducedValue: number = array.reduceRight((accumulator: number, value: number) => accumulator + value, 1);
console.info(reducedValue + ''); // Expected output: 16
```

## reverse
reverse(): Float32Array

Reverses the order of elements in the ArkTS Float32Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Float32Array   | Reversed ArkTS Float32Array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The reverse method cannot be bound. |
| 10200201 | Concurrent modification error.   |

**Example**

```ts
let array: collections.Float32Array = collections.Float32Array.from([1, 2, 3, 4, 5]);
let reversed: collections.Float32Array = array.reverse(); // Float32Array [5, 4, 3, 2, 1]
```

## set
set(array: ArrayLike\<number>, offset?: number): void

Writes the elements in an array-like object to the given start position in sequence.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | ---------------------------------------------------- |
| array | ArrayLike\<number> | Yes | Array-like object whose elements will be written.|
| offset | number | No | Start position for writing. The default value is 0. The value is a non-negative integer, and offset + array.length does not exceed the length of the current Float32Array. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The set method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**Example**

```ts
let buffer: collections.ArrayBuffer = new collections.ArrayBuffer(32);
let array: collections.Float32Array = new collections.Float32Array(buffer);
array.set([1, 2, 3], 3); // Float32Array [0, 0, 0, 1, 2, 3, 0, 0]
```

## slice
slice(start?: number, end?: number): Float32Array

Returns a new ArkTS Float32Array object that contains the content of the specified range of the original ArkTS Float32Array. Unlike subarray, the object returned by slice does not affect the original array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description                                                  |
| ------ | ------ | ---- | -----------------------------------------------------|
| start  | number | No   | Start index. If `start < 0`, the search starts from the position `start + Float32Array.length`. The default value is 0. |
| end    | number | No  | End index of the range (exclusive). If a negative number is passed in, it refers to the index of `end + Float32Array.length`. The default value is the length of the ArkTS Float32Array.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Float32Array | A new ArkTS Float32Array object that contains the elements in the specified range of the original ArkTS Float32Array. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The slice method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Float32Array = collections.Float32Array.from([1, 2, 3, 4, 5]);
array.slice(); // Float32Array [1, 2, 3, 4, 5]
array.slice(1, 3); // Float32Array [2, 3]
array.slice(-2); // Float32Array [4, 5]
```

## sort
sort(compareFn?: TypedArrayCompareFn\<number>): Float32Array

Sorts the ArkTS Float32Array in place and returns the sorted ArkTS Float32Array object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type                  | Mandatory| Description                                      |
| --------- | ---------------------- | ---- | ------------------------------------------ |
| compareFn | [TypedArrayCompareFn](arkts-apis-arkts-collections-Types.md#typedarraycomparefn)\<number> | No  | Function that determines the sort order. By default, elements are sorted in ascending order.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Float32Array | Sorted ArkTS Float32Array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------ |
| 10200011 | The sort method cannot be bound. |
| 10200201 | Concurrent modification error.         |

**Example**

```ts
let array: collections.Float32Array = collections.Float32Array.from([1, 3, 5, 4, 2]);
// Sort in ascending order by default.
array.sort(); // Float32Array [1, 2, 3, 4, 5]
// Use a comparison function to sort in ascending order.
array.sort((first: number, second: number) => first - second); // Float32Array [1, 2, 3, 4, 5]
// Use a comparison function to sort in descending order.
array.sort((first: number, second: number) => second - first); // Float32Array [5, 4, 3, 2, 1]
```

## subarray
subarray(begin?: number, end?: number): Float32Array

Extracts the array from the specified position and returns a new ArkTS Float32Array object based on the same ArkTS ArrayBuffer. Since the returned object shares the same ArrayBuffer with the original object, modifying one affects the other.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description                                               |
| ------ | ------ | ---- | ------------------------------------------------- |
| begin  | number | No  | Start index of the range. If a negative number is passed in, it refers to the index of `begin + Float32Array.length`. The default value is **0**.|
| end    | number | No  | End index of the range (exclusive). If a negative number is passed in, it refers to the index of `end + Float32Array.length`. The default value is the length of the ArkTS Float32Array.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Float32Array | A new ArkTS Float32Array object based on the same ArrayBuffer.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID|            Error Message                              |
| -------- | -------------------------------------------------|
| 10200011 | The subarray method cannot be bound.             |
| 10200201 | Concurrent modification error.               |

**Example**

```ts
let array: collections.Float32Array = collections.Float32Array.from([1, 2, 3, 4, 5]);
let subArray: collections.Float32Array = array.subarray(); // Float32Array [1, 2, 3, 4, 5]
subArray.set([10, 20, 30]); // Float32Array [10, 20, 30, 4, 5]
```

## at
at(index: number): number | undefined

Returns the element at the specified index, or returns undefined if it does not exist.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| index  | number | Yes   | Index of the ArkTS Float32Array element to return (zero-based), which is an integer. If `index < 0`, the element at position `index + Float32Array.length` is accessed. |

**Return value**

| Type        | Description     |
| ------------ | --------- |
| number \| undefined| The element at the specified index; if it does not exist, undefined is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID|                       Error Message                   |
| -------- | ------------------------------------------------ |
| 10200011 | The at method cannot be bound.                   |
| 10200201 | Concurrent modification error.               |

**Example**

```ts
let float32Array: collections.Float32Array = collections.Float32Array.from([1, 2, 3, 4, 5]);
console.info("element: " + float32Array.at(2));  // element: 3
console.info("element: " + float32Array.at(-1)); // element: 5
console.info("element: " + float32Array.at(6));  // element: undefined
```

## includes
includes(searchElement: number, fromIndex?: number): boolean

Determines whether the ArkTS Float32Array contains the specified element.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name| Type  | Mandatory| Description                                     |
| ------ | ------ | ---- | --------------------------------------- |
| searchElement  | number | Yes  | Element to search for.|
| fromIndex  | number | No | Index from which the search starts. If a negative number is passed in, it refers to the index of `fromIndex + Float32Array.length`. The default value is **0**.|

**Return value**

| Type   | Description                                                       |
| ------- | ---------------------------------------------------------- |
| boolean | Check result. The value **true** is returned if the element exists; otherwise, **false** is returned.|


**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The includes method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Float32Array = collections.Float32Array.from([1, 2, 3]);
console.info("includes: " + array.includes(2));    // includes: true
console.info("includes: " + array.includes(4));    // includes: false
console.info("includes: " + array.includes(3, 3)); // includes: false
```

## entries
entries(): IterableIterator\<[number, number]>

Returns an iterator object that contains the key-value pair of each element in this ArkTS Float32Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description     |
| ------------ | --------- |
| IterableIterator\<[number, number]>| Iterator object containing the key-value pair of each element in the ArkTS Float32Array. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The entries method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Float32Array = collections.Float32Array.from([11, 22, 33]);
let iterator: IterableIterator<[number, number]> = array.entries();
console.info("value: " + iterator.next().value); // value: 0,11
console.info("value: " + iterator.next().value); // value: 1,22
console.info("value: " + iterator.next().value); // value: 2,33
```

## keys
keys(): IterableIterator\<number>

Returns a new iterator object that contains the key (index) of each element in the ArkTS Float32Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description     |
| ------------ | --------- |
| IterableIterator\<number> | An iterator object that contains the key (index) of each element in the ArkTS Float32Array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The keys method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Float32Array = collections.Float32Array.from([1, 2, 3, 4, 5]);
let iterator: IterableIterator<number> = array.keys();
for (const key of iterator) {
  console.info("" + key); // 0, 1, 2, 3, and 4 are returned in sequence.
}
```

## values
values(): IterableIterator\<number>

Returns an iterator object that contains the value of each element in this ArkTS Float32Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description     |
| ------------ | --------- |
| IterableIterator\<number> | An iterator object containing the value of each element in the ArkTS Float32Array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The values method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**Example**

```ts
let array: collections.Float32Array = collections.Float32Array.from([1, 2, 3, 4, 5]);
let iterator: IterableIterator<number> = array.values();
for (const value of iterator) {
  console.info("" + value); // 1, 2, 3, 4, and 5 are returned in sequence.
}
```

## [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;number&gt;

Returns an iterator that contains each element in the ArkTS Float32Array.

> **NOTE**
>
> This API cannot be used in .ets files.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type                     | Description            |
| ------------------------- | ---------------- |
| IterableIterator&lt;number&gt; | An iterator object containing the value of each element in the ArkTS Float32Array. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 10200011 | The Symbol.iterator method cannot be bound. |

**Example**

```ts
let float32Array: collections.Float32Array = collections.Float32Array.from([1, 2, 3, 4, 5, 6]);
// Traverse the Float32Array through the iterator.
for (let item of float32Array) {
  console.info("value : " + item);
}
```

## [index: number]

&#91;index: number&#93;: number

Returns the element at the specified index in the ArkTS Float32Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type  | Mandatory| Description                    |
| ----- | ------ | ---- | -------------------------- |
| index | number | Yes | Element index starting from 0. The value range is [0, Float32Array.length - 1]. |

**Return value**

| Type  | Description                |
| ----- | ---------------------|
| number | Returns the element value at the specified index position. |

**Example**

```ts
let float32Array = collections.Float32Array.from([1, 2, 4]);
// Access the element in Float32Array by index.
console.info("Element at index 1: ", float32Array[1]);
```
