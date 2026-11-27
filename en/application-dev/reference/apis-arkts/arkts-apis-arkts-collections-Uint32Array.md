# Class (Uint32Array)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=31ba07988632b6f2ed98a078bdae886436926502 translatedAt=2026-11-16T05:01:07.799Z pushedAt=2026-11-16T06:31:14.159Z nl=2 -->

A linear data structure whose underlying implementation is based on [ArrayBuffer](arkts-apis-arkts-collections-ArrayBuffer.md).

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This module can be imported only to ArkTS files (with the file name extension .ets).

**Decorator**: \@Sendable

## Modules to Import

```ts
import { collections } from '@kit.ArkTS';
```

## Properties

**System capability**: SystemCapability.Utils.Lang

**Atomic service API**: This API can be used in atomic services since API version 12.

| Name  | Type  | Read Only| Optional| Description             |
| ------ | ------ | ---- | ---- | ----------------|
| buffer | [ArrayBuffer](arkts-apis-arkts-collections-ArrayBuffer.md) | Yes   | No  | The [ArrayBuffer](arkts-apis-arkts-collections-ArrayBuffer.md) object used by the ArkTS Uint32Array at the underlying layer.|
| byteLength | number | Yes   | No   | The number of bytes occupied by the ArkTS Uint32Array.|
| byteOffset | number | Yes   | No   | The byte offset of the ArkTS Uint32Array from the start position of its ArrayBuffer.|
| length | number | Yes  | No | Number of elements in an ArkTS Uint32Array.|
| BYTES_PER_ELEMENT | number | Yes   | No   | The number of bytes occupied by each element in the ArkTS Uint32Array.|

## constructor
constructor()

A constructor used to create an empty ArkTS Uint32Array.

**System capability**: SystemCapability.Utils.Lang

**Atomic service API**: This API can be used in atomic services since API version 12.

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 10200012 | The Uint32Array's constructor cannot be directly invoked. |

**Example**

```ts
let uint32Array: collections.Uint32Array = new collections.Uint32Array();
```

## constructor
constructor(length: number)

A constructor used to create an ArkTS Uint32Array of a given length.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                         |
| ------- | ------ | ---- | --------------------------- |
| length | number | Yes | Used to specify the length of the ArkTS Uint32Array, which must be a non-negative integer. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                                 |
| -------- | -------------------------------------------------------  |
| 10200012 | The Uint32Array's constructor cannot be directly invoked. |


**Example**

```ts
// Construct an object with the length parameter.
let uint32Array: collections.Uint32Array = new collections.Uint32Array(12);
```

## constructor
constructor(elements: Iterable\<number>)

A constructor that creates an ArkTS Uint32Array from an iterable object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| elements |  Iterable\<number> | Yes| An iterable collection of numbers used to construct an ArkTS Uint32Array object.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 10200012 | The Uint32Array's constructor cannot be directly invoked. |

**Example**

```ts
// Construct objects from an iterable object.
let set: Set<number> = new Set<number>([1, 2, 3]);
let array: collections.Uint32Array = new collections.Uint32Array(set);
// Uint32Array [1, 2, 3]
```

## constructor
constructor(array: ArrayLike\<number> | ArrayBuffer)

A constructor that creates an ArkTS Uint32Array from an array-like object or ArkTS ArrayBuffer.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| array |  ArrayLike\<number> \| ArrayBuffer | Yes | Object used to construct an ArkTS Uint32Array. When the parameter type is ArrayBuffer, the occupied byte count must be an integer multiple of 4. When the parameter type is ArrayLike, its elements are copied and a new underlying [ArrayBuffer](arkts-apis-arkts-collections-ArrayBuffer.md) is created. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 10200012 | The Uint32Array's constructor cannot be directly invoked. |

**Example**

```ts
// Example 1: Construct an object from an array-like object.
let arrayLike = [1, 3, 5];
let array: collections.Uint32Array = new collections.Uint32Array(arrayLike);
```

```ts
// Example 2: Construct an object from an ArrayBuffer.
let arrayBuffer: collections.ArrayBuffer = new collections.ArrayBuffer(12);
let array: collections.Uint32Array = new collections.Uint32Array(arrayBuffer);
```

```ts
// Example 3: Construct an object from another ArkTS Uint32Array.
let arrayLike = [1, 3, 5];
// uint32Array1 [1, 3, 5]
let uint32Array1: collections.Uint32Array = new collections.Uint32Array(arrayLike);
// uint32Array2 [1, 3, 5]
let uint32Array2: collections.Uint32Array = new collections.Uint32Array(uint32Array1);
```

## constructor
constructor(buffer: ArrayBuffer, byteOffset?: number, length?: number)

Constructor that creates an ArkTS Uint32Array object from an ArrayBuffer. The Uint32Array shares the same underlying data with the passed-in ArrayBuffer.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                        |
| ------- | ------ | ---- | ------------------------------------------ |
| buffer | [ArrayBuffer](arkts-apis-arkts-collections-ArrayBuffer.md) | Yes | The [ArrayBuffer](arkts-apis-arkts-collections-ArrayBuffer.md) object used to construct the ArkTS Uint32Array. The number of bytes occupied by the buffer must be a multiple of 4. |
| byteOffset | number | No | Specifies the byte offset of the buffer, which must be a non-negative integer and a multiple of 4. The default value is 0. |
| length | number | No | Specifies the length of the ArkTS Uint32Array, which must be a non-negative integer. The default value is 0. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                                  |
| -------- | -------------------------------------------------------   |
| 10200012 | The Uint32Array's constructor cannot be directly invoked. |

**Example**

```ts
let uint32Array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5, 6]);
console.info(`byteLength: ${uint32Array.buffer.byteLength}`); // byteLength: 24
// Start from the 5th byte of the buffer corresponding to uint32Array, with a length of 5.
let uint32Array1: collections.Uint32Array = new collections.Uint32Array(uint32Array.buffer, 4, 5);
console.info(`[${uint32Array1}]`); // [2, 3, 4, 5, 6]
```

## from
static from(arrayLike: ArrayLike\<number>): Uint32Array

Creates an ArkTS Uint32Array object from an ArrayLike.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                 |
| ------- | ------ | ---- | --------------------------------------------------- |
| arrayLike | ArrayLike\<number> | Yes| Array-like object used to construct the ArkTS Uint32Array.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint32Array | New ArkTS Uint32Array generated.|

**Example**
```ts
let arrayLike = [1, 3, 5];
let array: collections.Uint32Array = collections.Uint32Array.from(arrayLike); // array [1, 3, 5]
```

## from
static from\<T>(arrayLike: ArrayLike\<T>, mapFn: TypedArrayFromMapFn\<T, number>): Uint32Array

Creates an ArkTS Uint32Array object from an ArrayLike, transforming each element through a mapping function.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name | Type  | Mandatory| Description                                       |
| ------- | ------ | ---- | ------------------------------------------|
| arrayLike | ArrayLike\<T> | Yes | Array-like object used to construct the ArkTS Uint32Array.              |
| mapFn | [TypedArrayFromMapFn](arkts-apis-arkts-collections-Types.md#typedarrayfrommapfn)\<T, number> | Yes| Mapping function.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint32Array | New ArkTS Uint32Array generated.|

**Example**

```ts
// Example 1: Create an ArkTS Uint32Array from an object.
let array: collections.Uint32Array = collections.Uint32Array.from<number>(
  { length: 5 }, (v: number, k: number) => k);
// Uint32Array [0, 1, 2, 3, 4]
```

```ts
// Example 2: Create an ArkTS Uint32Array from a string array.
let array: collections.Uint32Array = collections.Uint32Array.from<string>(
  ["1", "3", "5"], (value: string, k: number) => parseInt(value));
// Uint32Array [1, 3, 5]
```

```ts
// Example 3: Create an ArkTS Uint32Array from a string.
let array: collections.Uint32Array = collections.Uint32Array.from<string>(
  "12345", (value: string, k: number) => parseInt(value));
// Uint32Array [1, 2, 3, 4, 5]
```

## from
static from(arrayLike: Iterable\<number>, mapFn?: TypedArrayFromMapFn\<number, number>): Uint32Array

Creates an ArkTS Uint32Array from an iterator object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name | Type  | Mandatory| Description                               |
| ------- | ------ | ---- | -----------------------------------|
| arrayLike | Iterable\<number> | Yes | An iterable object used to construct an ArkTS Uint32Array. |
| mapFn | [TypedArrayFromMapFn](arkts-apis-arkts-collections-Types.md#typedarrayfrommapfn)\<number, number> | No| Mapping function. If no value is passed in, no special processing is conducted on the elements.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint32Array | New ArkTS Uint32Array generated.|

**Example**

```ts
// Example 1: No mapping function is specified.
let set: Set<number> = new Set<number>([1, 2, 3]);
let array: collections.Uint32Array = collections.Uint32Array.from(set);
// Uint32Array [1, 2, 3]
```

```ts
// Example 2: A mapping function is specified.
let set: Set<number> = new Set<number>([1, 2, 3]);
let array: collections.Uint32Array = collections.Uint32Array.from(
  set, (value: number, k: number) => value + k);
// Uint32Array [1, 3, 5]
```

## of<sup>18+</sup>

static of(...items: number[]): Uint32Array

Creates a new ArkTS Uint32Array object from a variable number of arguments.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type         | Mandatory| Description                           |
| --------- | ------------- | ---- | ------------------------------- |
| items | number[] | No  | Array of elements used to create the array. The number of elements can be zero, one, or more. The default value is an empty array.|

**Return value**

| Type     | Description                   |
| --------- | ----------------------- |
| Uint32Array | New ArkTS Uint32Array instance.|

**Example**

```ts
let uint32Array: collections.Uint32Array = collections.Uint32Array.of(1, 2, 3, 4);
console.info(uint32Array.toString()); // Expected output: 1,2,3,4
```

## toString<sup>18+</sup>

toString(): string

Converts the ArkTS Uint32Array to a string.

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
let array = new collections.Uint32Array([1, 2, 3, 4, 5]);
let stringArray = array.toString();
console.info(stringArray); // Expected output: 1,2,3,4,5
```

## toLocaleString<sup>18+</sup>

toLocaleString(): string

Generates a string of digits that matches the cultural conventions of the current system locale. Each element converts its digits to a string via its **toLocaleString** API, and these strings are then joined in sequence with commas (,).

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
let array = new collections.Uint32Array([1000, 2000, 3000]);
let stringArray = array.toLocaleString();
console.info(stringArray); // Expected output: 1,000,2,000,3,000
```

## copyWithin
copyWithin(target: number, start: number, end?: number): Uint32Array

Copies the elements within the specified range of the ArkTS Uint32Array to the target position in sequence.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| target | number | Yes | Subscript of the target start position. If `target < 0`, it starts from the position `target + Uint32Array.length`. |
| start | number | Yes| Start index of the range. If a negative number is passed in, it refers to the index of `start + Uint32Array.length`.|
| end | number | No| End index of the range (exclusive). If a negative number is passed in, it refers to the index of `end + Uint32Array.length`. The default value is the length of the ArkTS Uint32Array.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint32Array | The modified ArkTS Uint32Array object. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------ |
| 10200011 | The copyWithin method cannot be bound.           |
| 10200201 | Concurrent modification error.               |

**Example**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5, 6, 7, 8]);
let copied: collections.Uint32Array = array.copyWithin(3, 1, 3);
// Uint32Array [1, 2, 3, 2, 3, 6, 7, 8]
```

## some
some(predicate: TypedArrayPredicateFn\<number, Uint32Array>): boolean

Tests whether any element in the ArkTS Uint32Array satisfies the specified condition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                 |
| ------- | ------ | ---- | ---------------------------------------------------- |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Uint32Array> | Yes| Assertion function used for the test.|

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
let arrayLike = [10, 20, 30, 40, 50];
let uint32Array: collections.Uint32Array = new collections.Uint32Array(arrayLike);
uint32Array.some((element: number) => element < 1); // false
```

## every
every(predicate: TypedArrayPredicateFn\<number, Uint32Array>): boolean

Checks whether all elements in this ArkTS Uint32Array meet a given condition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                   |
| ------- | ------ | ---- | ----------------------------------------------------- |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Uint32Array> | Yes| Assertion function used for the test.|

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
let arrayLike = [10, 20, 30, 40, 50];
let uint32Array: collections.Uint32Array = new collections.Uint32Array(arrayLike);
uint32Array.every((element: number) => element > 1);  // true
```

## fill
fill(value: number, start?: number, end?: number): Uint32Array

Fills all elements in a given range in this ArkTS Uint32Array with a value.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                     |
| ------- | ------ | ---- | --------------------------------------------------------|
| value | number | Yes| Value to fill in.|
| start | number | No| Start index of the range. If a negative number is passed in, it refers to the index of `start + Uint32Array.length`. The default value is **0**.|
| end | number | No| End index of the range (exclusive). If a negative number is passed in, it refers to the index of `end + Uint32Array.length`. The default value is the length of the ArkTS Uint32Array.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint32Array | The ArkTS Uint32Array object after filling.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The fill method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let arrayLike = [1, 2, 3];
new collections.Uint32Array(arrayLike).fill(4); // Uint32Array [4, 4, 4]
new collections.Uint32Array(arrayLike).fill(4, 1); // Uint32Array [1, 4, 4]
new collections.Uint32Array(arrayLike).fill(4, 1, 2); // Uint32Array [1, 4, 3]
```

## filter
filter(predicate: TypedArrayPredicateFn\<number, Uint32Array>): Uint32Array

Returns a new ArkTS Uint32Array that contains all elements that meet the given condition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                   |
| ------- | ------ | ---- | ------------------------------------------------------ |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Uint32Array> | Yes| Assertion function used for the test.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint32Array| Filtered ArkTS Uint32Array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The filter method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([0, 1, 2, 3, 4]);
let filtered: collections.Uint32Array = array.filter((element: number) => element % 2 == 0);
// Uint32Array [0, 2, 4]
```

## find
find(predicate: TypedArrayPredicateFn\<number, Uint32Array>): number | undefined

Returns the value of the first element that passes a test provided by a callback function. If none of the elements pass the test, **undefined** is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Uint32Array> | Yes| Assertion function used for the test.|

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
let array: collections.Uint32Array = collections.Uint32Array.from([0, 1, 2, 3, 4]);
array.find((element: number) => element > 2); // 3
array.find((element: number) => element > 4); // undefined
```

## findIndex
findIndex(predicate: TypedArrayPredicateFn\<number, Uint32Array>): number

Returns the index of the first element that passes a test provided by a callback function. If none of the elements pass the test, **-1** is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Uint32Array> | Yes| Assertion function used for the test.|

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
const array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
let foundIndex: number = array.findIndex((element: number) => element % 2 === 0); // 1
```

## forEach
forEach(callbackFn: TypedArrayForEachCallback\<number, Uint32Array>): void

Calls a callback function for each element in this ArkTS Uint32Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| callbackFn | [TypedArrayForEachCallback](arkts-apis-arkts-collections-Types.md#typedarrayforeachcallback)\<number, Uint32Array> | Yes| Callback function to run for each element.|


**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The forEach method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let uint32Array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3]);
uint32Array.forEach((value: number, index: number, array: collections.Uint32Array) => {
  console.info(`Element ${value} at index ${index}`);
});
```

## indexOf
indexOf(searchElement: number, fromIndex?: number): number

Returns the index of the first occurrence of a value in this ArkTS Uint32Array. If the value is not found, **-1** is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name       | Type  | Mandatory| Description                       |
| ------------- | ------ | ---- | ---------------------------|
| searchElement | number | Yes  | Value to search for.               |
| fromIndex     | number | No   | Start index of the search. The default value is 0. If the index is greater than or equal to the length of the ArkTS Uint32Array, -1 is returned. If the index is negative, it is treated as an offset from the end of the array, searching from front to back. |

**Return value**

| Type        | Description     |
| ------------ | --------- |
| number | The first index of the given element in the ArkTS Uint32Array; if not found, -1 is returned. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The indexOf method cannot be bound. |
| 10200201 | Concurrent modification error.                |

**Example**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([3, 5, 9]);
array.indexOf(3); // 0
array.indexOf(7); // -1
array.indexOf(9, 2); // 2
array.indexOf(9, -2); // 2
```

## lastIndexOf<sup>18+</sup>

lastIndexOf(searchElement: number, fromIndex?: number): number

Returns the index of the last occurrence of searchElement in the ArkTS Uint32Array instance, or -1 if the element is not contained.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name          | Type    | Mandatory | Description                                                                               |
| ------------- | ------ | --- | --------------------------------------------------------------------------------- |
| searchElement | number | Yes  | Value to search for.                                                                           |
| fromIndex     | number | No   | Start index of the search, searching backward from this position. The default value is the length of the ArkTS Uint32Array minus 1 (that is, starting from the end). If the provided index value is negative, it is treated as an offset from the end of the array, searching from back to front. |

**Return value**

| Type    | Description                     |
| ------ | ----------------------- |
| number | The index of the last occurrence of the given element in the ArkTS Uint32Array; if not found, returns -1. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID   | Error Message                                   |
| -------- | --------------------------------------- |
| 10200011 | The lastIndexOf method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([3, 5, 9]);
console.info(`${array.lastIndexOf(3)}`); // Expected output: 0
console.info(`${array.lastIndexOf(7)}`); // Expected output: -1
console.info(`${array.lastIndexOf(9, 2)}`); // Expected output: 2
console.info(`${array.lastIndexOf(9, -2)}`); // Expected output: -1
```

## join
join(separator?: string): string

Concatenates all elements in this ArkTS Uint32Array into a string, with a given separator.

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
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
let joined: string = array.join('-'); // "1-2-3-4-5"
```

## map
map(callbackFn: TypedArrayMapCallback\<number, Uint32Array>): Uint32Array

Applies a callback function to each element in this ArkTS Uint32Array and uses the result to create an ArkTS Uint32Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | ---------------------------------------------------- |
| callbackFn | [TypedArrayMapCallback](arkts-apis-arkts-collections-Types.md#typedarraymapcallback)\<number, Uint32Array> | Yes | Callback function to run for each element.|


**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint32Array | New ArkTS Uint32Array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The map method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([25, 36, 49]);
const mapped: collections.Uint32Array = array.map(Math.sqrt); // Uint32Array [5, 6, 7]
```

## reduce
reduce(callbackFn: TypedArrayReduceCallback\<number, number, Uint32Array>): number

Executes a reducer function on each element and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name    | Type  | Mandatory|  Description    |
| ---------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<number, number, Uint32Array> | Yes| Reduce function.|

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
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
let reducedValue: number = array.reduce((accumulator: number, value: number) => accumulator + value);
// reducedValue == 15
```

## reduceRight<sup>18+</sup>

reduceRight(callbackFn: TypedArrayReduceCallback\<number, number, Uint32Array>): number

Traverses the ArkTS Uint32Array in reverse order, executes the reducer function on each element, and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name    | Type  | Mandatory|  Description    |
| ---------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<number, number, Uint32Array> | Yes| Reduce function.|

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
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
let reducedValue: number = array.reduceRight((accumulator: number, value: number) => accumulator + value);
console.info(`${reducedValue}`); // Expected output: 15
```

## reduce
reduce(callbackFn: TypedArrayReduceCallback\<number, number, Uint32Array>, initialValue: number): number

Executes the reducer function on each element, receives the initial value as the first call argument, and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | --------------------------------------------------- |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<number, number, Uint32Array> | Yes | Reduce function.|
| initialValue | number | Yes | Initial value.|


**Return value**

| Type        | Description     |
| ------------ | --------- |
| number | Final result obtained from the last call of the reduce function.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The reduce method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
let reducedValue: number = array.reduce((accumulator: number, value: number) => accumulator + value, 1);
// reducedValue == 16
```

## reduceRight<sup>18+</sup>

reduceRight\<U = number>(callbackFn: TypedArrayReduceCallback\<U, number, Uint32Array>, initialValue: U): U

Traverses the ArkTS Uint32Array in reverse order, executes the reducer function on each element, receives the initial value as the first call argument, and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | --------------------------------------------------- |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<U, number, Uint32Array> | Yes | Reduce function.|
| initialValue | U | Yes | Initial value.|

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
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
let reducedValue: number = array.reduceRight((accumulator: number, value: number) => accumulator + value, 1);
console.info(`${reducedValue}`); // Expected output: 16
```

## reduce
reduce\<U>(callbackFn: TypedArrayReduceCallback\<U, number, Uint32Array>, initialValue: U): U

Executes the reducer function on each element, receives the initial value as the first call argument, and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | ---------------------------------------------------- |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<U, number, Uint32Array> | Yes | Reduce function.|
| initialValue | U | Yes | Initial value.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
|  U | Final result obtained from the last call of the reduce function.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The reduce method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**Example**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
let reducedValue: string = array.reduce<string>((accumulator: string, value: number) => accumulator + value, "initialValue");
// reducedValue == initialValue12345
```

## reverse
reverse(): Uint32Array

Reverses the element order of the ArkTS Uint32Array in place (modifies the original array), and returns a reference to the modified original array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint32Array   | Reversed ArkTS Uint32Array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The reverse method cannot be bound. |
| 10200201 | Concurrent modification error.   |

**Example**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
let reversed: collections.Uint32Array = array.reverse(); // Uint32Array [5, 4, 3, 2, 1]
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
| offset | number | No  | Start position for writing, which must be a non-negative integer. The default value is 0. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The set method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**Example**

```ts
let buffer: collections.ArrayBuffer = new collections.ArrayBuffer(32);
let array: collections.Uint32Array = new collections.Uint32Array(buffer);
array.set([1, 2, 3], 3); // Uint32Array [0, 0, 0, 1, 2, 3, 0, 0]
```

## slice
slice(start?: number, end?: number): Uint32Array

Selects a range of elements in this ArkTS Uint32Array to create an ArkTS Uint32Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description                                                  |
| ------ | ------ | ---- | -----------------------------------------------------|
| start  | number | No   | Start index. If `start < 0`, it starts from the position `start + Uint32Array.length`. The default value is 0. |
| end    | number | No  | End index of the range (exclusive). If a negative number is passed in, it refers to the index of `end + Uint32Array.length`. The default value is the length of the ArkTS Uint32Array.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint32Array | New ArkTS Uint32Array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The slice method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
array.slice(); // Uint32Array [1, 2, 3, 4, 5]
array.slice(1, 3); // Uint32Array [2, 3]
array.slice(-2); // Uint32Array [4, 5]
```

## sort
sort(compareFn?: TypedArrayCompareFn\<number>): Uint32Array

Sorts the ArkTS Uint32Array in place (modifies the original array), and returns a reference to the sorted original array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type                  | Mandatory| Description                                      |
| --------- | ---------------------- | ---- | ------------------------------------------ |
| compareFn | [TypedArrayCompareFn](arkts-apis-arkts-collections-Types.md#typedarraycomparefn)\<number> | No  | Function that determines the sort order. By default, elements are sorted in ascending order.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint32Array | Sorted ArkTS Uint32Array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------ |
| 10200011 | The sort method cannot be bound. |
| 10200201 | Concurrent modification error.         |

**Example**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([1, 3, 5, 4, 2]);
array.sort(); // Uint32Array [1, 2, 3, 4, 5]
array.sort((first: number, second: number) => first - second); // Uint32Array [1, 2, 3, 4, 5]
array.sort((first: number, second: number) => second - first); // Uint32Array [5, 4, 3, 2, 1]
```

## subarray
subarray(begin?: number, end?: number): Uint32Array

Extracts a subarray from the specified positions and returns a new ArkTS Uint32Array object based on the same ArkTS ArrayBuffer. Modifying the returned subarray or the original ArkTS Uint32Array affects each other because they share the same underlying [ArrayBuffer](arkts-apis-arkts-collections-ArrayBuffer.md) data. To create an independent copy, use the [slice](#slice) method.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description                                               |
| ------ | ------ | ---- | ------------------------------------------------- |
| begin  | number | No  | Start index of the range. If a negative number is passed in, it refers to the index of `begin + Uint32Array.length`. The default value is **0**.|
| end    | number | No  | End index of the range (exclusive). If a negative number is passed in, it refers to the index of `end + Uint32Array.length`. The default value is the length of the ArkTS Uint32Array.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint32Array | An ArkTS Uint32Array object that shares the underlying ArrayBuffer with the original Uint32Array. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID|            Error Message                              |
| -------- | -------------------------------------------------|
| 10200011 | The subarray method cannot be bound.             |
| 10200201 | Concurrent modification error.               |

**Example**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
let subArray: collections.Uint32Array = array.subarray(); // Uint32Array [1, 2, 3, 4, 5]
subArray.set([10, 20, 30]); // Uint32Array [10, 20, 30, 4, 5]
```

## at
at(index: number): number | undefined

Returns the element at the given index. If no element is found, **undefined** is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| index  | number | Yes   | Index of the element to return (starting from 0), which is an integer. If `index < 0`, the element at position `index + Uint32Array.length` is accessed. |

**Return value**

| Type        | Description     |
| ------------ | --------- |
| number \| undefined| Element obtained. If no element is found, **undefined** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID|                       Error Message                   |
| -------- | ------------------------------------------------ |
| 10200011 | The at method cannot be bound.                   |
| 10200201 | Concurrent modification error.               |

**Example**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
console.info(`element: ${array.at(2)}`);  // element: 3
console.info(`element: ${array.at(-1)}`); // element: 5
console.info(`element: ${array.at(6)}`);  // element: undefined
```

## includes
includes(searchElement: number, fromIndex?: number): boolean

Checks whether elements are contained in this ArkTS Uint32Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name| Type  | Mandatory| Description                                     |
| ------ | ------ | ---- | --------------------------------------- |
| searchElement  | number | Yes  | Element to search for.|
| fromIndex  | number | No | Index from which the search starts. If a negative number is passed in, it refers to the index of `fromIndex + Uint32Array.length`. The default value is **0**.|

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
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3]);
console.info(`includes: ${array.includes(2)}`);    // includes: true
console.info(`includes: ${array.includes(4)}`);    // includes: false
console.info(`includes: ${array.includes(3, 3)}`); // includes: false
```

## entries
entries(): IterableIterator\<[number, number]>

Returns an iterator object that contains the key-value pair of each element in this ArkTS Uint32Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description     |
| ------------ | --------- |
| IterableIterator\<[number, number]>| Iterator object.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The entries method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([11, 22, 33]);
let iterator: IterableIterator<[number, number]> = array.entries();
console.info(`value: ${iterator.next().value}`); // value: 0,11
console.info(`value: ${iterator.next().value}`); // value: 1,22
console.info(`value: ${iterator.next().value}`); // value: 2,33
```

## keys
keys(): IterableIterator\<number>

Returns an iterator object that contains the key (index) of each element in this ArkTS Uint32Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description     |
| ------------ | --------- |
| IterableIterator\<number> | Iterator object.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The keys method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
let iterator: IterableIterator<number> = array.keys();
for (const key of iterator) {
  console.info(`${key}`); // Output sequentially 0,1,2,3,4.
}
```

## values
values(): IterableIterator\<number>

Returns an iterator object that contains the value of each element in this ArkTS Uint32Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description     |
| ------------ | --------- |
| IterableIterator\<number> | Iterator object.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The values method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**Example**

```ts
let array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5]);
let iterator: IterableIterator<number> = array.values();
for (const value of iterator) {
  console.info(`${value}`); // output sequentially 1,2,3,4,5
}
```

## [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;number&gt;

Returns an iterator, where each item of the iterator is the element value at the corresponding position in the ArkTS Uint32Array.

> **NOTE**
>
> This API cannot be used in .ets files.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type                     | Description            |
| ------------------------- | ---------------- |
| IterableIterator&lt;number&gt; | Iterator obtained.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 10200011 | The Symbol.iterator method cannot be bound. |

**Example**

```ts
let uint32Array: collections.Uint32Array = collections.Uint32Array.from([1, 2, 3, 4, 5, 6]);

for (let item of uint32Array) {
  console.info(`value : ${item}`);
}
```

## [index: number]

&#91;index: number&#93;: number

Returns the element at the specified index position of the ArkTS Uint32Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type  | Mandatory| Description                    |
| ----- | ------ | ---- | -------------------------- |
| index | number | Yes | Zero-based index of the desired element. The value range is [0, Uint32Array.length-1]. |

**Return value**

| Type  | Description                |
| ----- | ---------------------|
| number | Returns the element value at the specified index position. |

**Example**

```ts
let uint32Array = collections.Uint32Array.from([1, 2, 4]);
console.info(`Element at index 1: ${uint32Array[1]}`);
```
