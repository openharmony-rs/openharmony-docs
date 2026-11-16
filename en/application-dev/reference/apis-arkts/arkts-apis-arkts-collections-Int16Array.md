# Class (Int16Array)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=6bc2cc845cd4ead062499f05e503c42d03815d43 translatedAt=2026-11-16T04:39:44.460Z pushedAt=2026-11-16T06:31:14.133Z nl=2 -->

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
| buffer | ArrayBuffer | Yes  | No | Bottom-layer buffer used by an ArkTS Int16Array.|
| byteLength | number | Yes | No | Number of bytes occupied by the ArkTS Int16Array. |
| byteOffset | number | Yes | No | Byte offset of the ArkTS Int16Array from the start of its ArrayBuffer. |
| length | number | Yes  | No | Number of elements in an ArkTS Int16Array.|
| BYTES_PER_ELEMENT | number | Yes | No | Number of bytes occupied by each element in the ArkTS Int16Array. |

## constructor
constructor()

A constructor used to create an empty ArkTS Int16Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 10200012 | The Int16Array's constructor cannot be directly invoked. |

**Example**

```ts
// Create an empty ArkTS Int16Array object.
let int16Array: collections.Int16Array = new collections.Int16Array();
```

## constructor
constructor(length: number)

A constructor used to create an ArkTS Int16Array of a given length.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                         |
| ------- | ------ | ---- | --------------------------- |
| length | number | Yes | Used to specify the length of the ArkTS Int16Array. The value must be a non-negative integer. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                                 |
| -------- | -------------------------------------------------------  |
| 10200012 | The Int16Array's constructor cannot be directly invoked. |


**Example**

```ts
// Construct an object with the length parameter.
let int16Array: collections.Int16Array = new collections.Int16Array(12);
```

## constructor
constructor(elements: Iterable\<number>)

A constructor that creates an ArkTS Int16Array from an iterable object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| elements |  Iterable\<number> | Yes| An iterable collection of numbers used to construct an ArkTS Int16Array object.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 10200012 | The Int16Array's constructor cannot be directly invoked. |

**Example**

```ts
// Construct objects from an iterable object.
let set: Set<number> = new Set<number>([1, 2, 3]);
// Int16Array [1, 2, 3]
let int16Array: collections.Int16Array = new collections.Int16Array(set);
```

## constructor
constructor(array: ArrayLike\<number> | ArrayBuffer)

A constructor that creates an ArkTS Int16Array from an array-like object or ArkTS ArrayBuffer.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| array |  ArrayLike\<number> \| ArrayBuffer | Yes | Object used to construct an ArkTS Int16Array. When the parameter type is ArrayBuffer, the number of bytes occupied by the buffer must be an integer multiple of 2. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 10200012 | The Int16Array's constructor cannot be directly invoked. |

**Example**

```ts
// Example 1: Construct an object from an array-like object.
let arrayLike = [1, 3, 5];
let int16Array: collections.Int16Array = new collections.Int16Array(arrayLike);
```

```ts
// Example 2: Construct an object from an ArrayBuffer.
let arrayBuffer: collections.ArrayBuffer = new collections.ArrayBuffer(12);
let int16Array: collections.Int16Array = new collections.Int16Array(arrayBuffer);
```

```ts
// Example 3: Construct an object from another ArkTS Int16Array.
let arrayLike = [1, 3, 5];
// int16Array1 [1, 3, 5]
let int16Array1: collections.Int16Array = new collections.Int16Array(arrayLike);
// int16Array2 [1, 3, 5]
let int16Array2: collections.Int16Array = new collections.Int16Array(int16Array1);
```

## constructor
constructor(buffer: ArrayBuffer, byteOffset?: number, length?: number)

A constructor that creates an ArkTS Int16Array object from an ArkTS ArrayBuffer.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                        |
| ------- | ------ | ---- | ------------------------------------------ |
| buffer | ArrayBuffer | Yes | ArrayBuffer object used to construct the ArkTS Int16Array. The number of bytes occupied by buffer must be an integer multiple of 2. |
| byteOffset | number | No | Specifies the byte offset of buffer, starting from 0, with a default value of 0. The value must be a multiple of 2. |
| length | number | No | Specifies the length of the ArkTS Int16Array, with a default value of 0. The value must be a non-negative integer and must satisfy byteOffset + length * 2 <= buffer.byteLength. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                                  |
| -------- | -------------------------------------------------------   |
| 10200012 | The Int16Array's constructor cannot be directly invoked. |

**Example**

```ts
let int16Array: collections.Int16Array = collections.Int16Array.from([1, 2, 3, 4, 5, 6]);
console.info("byteLength: " + int16Array.buffer.byteLength); // byteLength: 12
// Start from the second byte of the buffer corresponding to int16Array. The length is 5.
let int16Array1: collections.Int16Array = new collections.Int16Array(int16Array.buffer, 2, 5);
console.info("[" + int16Array1 + "]"); // [2, 3, 4, 5, 6]
```

## from
static from(arrayLike: ArrayLike\<number>): Int16Array

Creates an ArkTS Int16Array object from an ArrayLike.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                 |
| ------- | ------ | ---- | --------------------------------------------------- |
| arrayLike | ArrayLike\<number> | Yes| Array-like object used to construct the ArkTS Int16Array.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Int16Array | New ArkTS Int16Array generated.|

**Example**
```ts
let arrayLike = [1, 3, 5];
let array: collections.Int16Array = collections.Int16Array.from(arrayLike); // array [1, 3, 5]
```

## from
static from\<T>(arrayLike: ArrayLike\<T>, mapFn: TypedArrayFromMapFn\<T, number>): Int16Array

Creates an ArkTS Int16Array from an array-like object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name | Type  | Mandatory| Description                                       |
| ------- | ------ | ---- | ------------------------------------------|
| arrayLike | ArrayLike\<T> | Yes | Array-like object used to construct the ArkTS Int16Array.              |
| mapFn | [TypedArrayFromMapFn](arkts-apis-arkts-collections-Types.md#typedarrayfrommapfn)\<T, number> | Yes| Mapping function.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Int16Array | New ArkTS Int16Array generated.|

**Example**

```ts
// Example 1: Create from an object, Int16Array [0, 1, 2, 3, 4]
let array: collections.Int16Array = collections.Int16Array.from<number>(
  { length: 5 }, (v: Object, k: number) => k);
```

```ts
// Example 2: Create from a character array, Int16Array [1, 3, 5]
let array: collections.Int16Array = collections.Int16Array.from<string>(
  ["1", "3", "5"], (v: string, k: number) => parseInt(v));
```

```ts
// Example 3: Create from a string, Int16Array [1, 2, 3, 4, 5]
let array: collections.Int16Array = collections.Int16Array.from<string>(
  "12345", (v: string, k: number) => parseInt(v));
```

## from
static from(arrayLike: Iterable\<number>, mapFn?: TypedArrayFromMapFn\<number, number>): Int16Array

Creates an ArkTS Int16Array from an iterator object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name | Type  | Mandatory| Description                               |
| ------- | ------ | ---- | -----------------------------------|
| arrayLike | Iterable\<number> | Yes | An iterable object used to construct an ArkTS Int16Array.   |
| mapFn | [TypedArrayFromMapFn](arkts-apis-arkts-collections-Types.md#typedarrayfrommapfn)\<number, number> | No| Mapping function. If no value is passed in, no special processing is conducted on the elements.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Int16Array | New ArkTS Int16Array generated.|

**Example**

```ts
// Example 1: No mapping function is specified.
let set: Set<number> = new Set<number>([1, 2, 3]);
// Int16Array [1, 2, 3]
let array: collections.Int16Array = collections.Int16Array.from(set);
```

```ts
// Example 2: A mapping function is specified.
let set: Set<number> = new Set<number>([1, 2, 3]);
// Int16Array [1, 3, 5]
let array: collections.Int16Array = collections.Int16Array.from(
  set, (v: number, k: number) => v + k);
```

## of<sup>18+</sup>

static of(...items: number[]): Int16Array

Creates a new ArkTS Int16Array object from a variable number of arguments.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type         | Mandatory| Description                           |
| --------- | ------------- | ---- | ------------------------------- |
| items | number[] | No   | Elements used to create the array. The number of parameters is variable. The default value is an empty array. |

**Return value**

| Type     | Description                   |
| --------- | ----------------------- |
| Int16Array | New ArkTS Int16Array object. |

**Example**

```ts
// Create an Int16Array via the of method.
let int16Array: collections.Int16Array = collections.Int16Array.of(1, 2, 3, 4);
console.info(int16Array.toString()); // Expected output: 1,2,3,4
```

## toString<sup>18+</sup>

toString(): string

Converts the ArkTS Int16Array to a string, with elements joined by commas.

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
let int16Array: collections.Int16Array = new collections.Int16Array([1, 2, 3, 4, 5]);
let stringArray = int16Array.toString();
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
let array = new collections.Int16Array([1000, 2000, 3000]);
let stringArray = array.toLocaleString();
console.info(stringArray); // Expected output: 1 000,2 000,3 000
```

## copyWithin
copyWithin(target: number, start: number, end?: number): Int16Array

Copies elements within a given range from this ArkTS Int16Array to another position in sequence.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| target | number | Yes | Index of the target start position. If `target < 0`, it starts from the position `target + Int16Array.length`. |
| start | number | Yes | Index of the source start position. If `start < 0`, it starts from the position `start + Int16Array.length`. |
| end | number | No | Index of the source end position (excluding the element at the end position). If `end < 0`, it ends at the position `end + Int16Array.length`. The default value is the length of the ArkTS Int16Array. |

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Int16Array | Modified ArkTS Int16Array. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------ |
| 10200011 | The copyWithin method cannot be bound.           |
| 10200201 | Concurrent modification error.               |

**Example**

```ts
let int16Array: collections.Int16Array = collections.Int16Array.from([1, 2, 3, 4, 5, 6, 7, 8]);
// Int16Array [1, 2, 3, 2, 3, 6, 7, 8]
let copied: collections.Int16Array = int16Array.copyWithin(3, 1, 3);
```

## some
some(predicate: TypedArrayPredicateFn\<number, Int16Array>): boolean

Tests whether any element in the ArkTS Int16Array satisfies the specified condition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                 |
| ------- | ------ | ---- | ---------------------------------------------------- |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Int16Array> | Yes| Assertion function used for the test.|

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
let int16Array: collections.Int16Array = new collections.Int16Array(arrayLike);
// Determine whether there exists an element less than 0.
int16Array.some((element: number) => element < 0); // true
```

## every
every(predicate: TypedArrayPredicateFn\<number, Int16Array>): boolean

Checks whether all elements in this ArkTS Int16Array meet a given condition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                   |
| ------- | ------ | ---- | ----------------------------------------------------- |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Int16Array> | Yes| Assertion function used for the test.|

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
let int16Array: collections.Int16Array = new collections.Int16Array(arrayLike);
// determine whether all elements are greater than 0.
int16Array.every((element: number) => element > 0);  // false
```

## fill
fill(value: number, start?: number, end?: number): Int16Array

Fills all elements in a given range in this ArkTS Int16Array with a value.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                     |
| ------- | ------ | ---- | --------------------------------------------------------|
| value | number | Yes| Value to fill in.|
| start | number | No| Start index of the range. If a negative number is passed in, it refers to the index of `start + Int16Array.length`. The default value is **0**.|
| end | number | No| End index of the range (exclusive). If a negative number is passed in, it refers to the index of `end + Int16Array.length`. The default value is the length of the ArkTS Int16Array.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Int16Array | The filled ArkTS Int16Array.|

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
new collections.Int16Array(arrayLike).fill(4); // Int16Array [4, 4, 4]
// Start filling 4 from index 1.
new collections.Int16Array(arrayLike).fill(4, 1); // Int16Array [1, 4, 4]
// Fill 4 from index 1 to 2 (exclusive).
new collections.Int16Array(arrayLike).fill(4, 1, 2); // Int16Array [1, 4, 3]
```

## filter
filter(predicate: TypedArrayPredicateFn\<number, Int16Array>): Int16Array

Returns a new ArkTS Int16Array that contains all elements that meet the given condition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                   |
| ------- | ------ | ---- | ------------------------------------------------------ |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Int16Array> | Yes| Assertion function used for the test.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Int16Array| Filtered ArkTS Int16Array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The filter method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Int16Array = collections.Int16Array.from([0, 1, 2, 3, 4]);
// Int16Array [0, 2, 4]
let filtered: collections.Int16Array = array.filter((element: number) => element % 2 == 0);
```

## find
find(predicate: TypedArrayPredicateFn\<number, Int16Array>): number | undefined

Returns the value of the first element that passes a test provided by a callback function. If none of the elements pass the test, **undefined** is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Int16Array> | Yes| Assertion function used for the test.|

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
let array: collections.Int16Array = collections.Int16Array.from([0, 1, 2, 3, 4]);
array.find((element: number) => element > 2); // 3
array.find((element: number) => element > 4); // undefined
```

## findIndex
findIndex(predicate: TypedArrayPredicateFn\<number, Int16Array>): number

Returns the index of the first element that passes a test provided by a callback function. If none of the elements pass the test, **-1** is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Int16Array> | Yes| Assertion function used for the test.|

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
let int16Array: collections.Int16Array = collections.Int16Array.from([1, 2, 3, 4, 5]);
let foundIndex: number = int16Array.findIndex((element: number) => element % 2 === 0); // 1
```

## forEach
forEach(callbackFn: TypedArrayForEachCallback\<number, Int16Array>): void

Calls a callback function for each element in this ArkTS Int16Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| callbackFn | [TypedArrayForEachCallback](arkts-apis-arkts-collections-Types.md#typedarrayforeachcallback)\<number, Int16Array> | Yes| Callback function to run for each element.|


**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The forEach method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let int16Array: collections.Int16Array = collections.Int16Array.from([1, 2, 3]);
// Traverse each element of Int16Array and print the element value and index.
int16Array.forEach((value: number, index: number, array: collections.Int16Array) => {
  console.info("Element " + value + " at index " + index);
});
```

## indexOf
indexOf(searchElement: number, fromIndex?: number): number

Returns the index of the first occurrence of a value in this ArkTS Int16Array. If the value is not found, **-1** is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name       | Type  | Mandatory| Description                       |
| ------------- | ------ | ---- | ---------------------------|
| searchElement | number | Yes  | Element value to search for.                |
| fromIndex     | number | No   | Starting index of the search. Default value: 0. If the index is greater than or equal to the length of the ArkTS Int16Array, -1 is returned. If the index is negative, it is treated as an offset from the end of the array, searching from front to back. |

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
let array: collections.Int16Array = collections.Int16Array.from([3, 5, 9]);
array.indexOf(3); // 0
array.indexOf(7); // -1
array.indexOf(9, 2); // 2
array.indexOf(9, -2); // 2
```

## lastIndexOf<sup>18+</sup>

lastIndexOf(searchElement: number, fromIndex?: number): number

Returns the index of the last occurrence of searchElement in the ArkTS Int16Array instance, or -1 if it does not exist.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name          | Type    | Mandatory | Description                                                                               |
| ------------- | ------ | --- | --------------------------------------------------------------------------------- |
| searchElement | number | Yes  | Element value to search for.                                                                       |
| fromIndex     | number | No   | Starting index of the search, searching backward from this position. Default value: the length of the ArkTS Int16Array minus 1 (i.e., starting from the end). If the index is greater than or equal to the length of the ArkTS Int16Array, the search starts from the end and proceeds backward. If the provided index is negative, it is treated as an offset from the end of the array, searching from back to front. |

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
let array: collections.Int16Array = collections.Int16Array.from([3, 5, 9]);
console.info(array.lastIndexOf(3) + ''); // Expected output: 0
console.info(array.lastIndexOf(7) + ''); // Expected output: -1
console.info(array.lastIndexOf(9, 2) + ''); // Expected output: 2
console.info(array.lastIndexOf(9, -2) + ''); // Expected output: -1
```

## join
join(separator?: string): string

Concatenates all elements in this ArkTS Int16Array into a string, with a given separator.

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
let array: collections.Int16Array = collections.Int16Array.from([1, 2, 3, 4, 5]);
let joined: string = array.join("-"); // "1-2-3-4-5"
```

## map
map(callbackFn: TypedArrayMapCallback\<number, Int16Array>): Int16Array

Applies a callback function to each element in this ArkTS Int16Array and uses the result to create an ArkTS Int16Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | ---------------------------------------------------- |
| callbackFn | [TypedArrayMapCallback](arkts-apis-arkts-collections-Types.md#typedarraymapcallback)\<number, Int16Array> | Yes | Callback function to run for each element.|


**Return value**

| Type        | Description     |
| ------------ | --------- |
| Int16Array | New ArkTS Int16Array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The map method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Int16Array = collections.Int16Array.from([25, 36, 49]);
const mapped: collections.Int16Array = array.map(Math.sqrt); // Int16Array [5, 6, 7]
```

## reduce
reduce(callbackFn: TypedArrayReduceCallback\<number, number, Int16Array>): number

Applies a reduce function on each element in this ArkTS Int16Array and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name    | Type  | Mandatory|  Description    |
| ---------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<number, number, Int16Array> | Yes| Reduce function.|

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
let array: collections.Int16Array = collections.Int16Array.from([1, 2, 3, 4, 5]);
// reducedValue == 15
let reducedValue: number = array.reduce((accumulator: number, value: number) => accumulator + value);
```

## reduceRight<sup>18+</sup>

reduceRight(callbackFn: TypedArrayReduceCallback\<number, number, Int16Array>): number

Traverses the ArkTS Int16Array in reverse order, executes the reduction function on each element, and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name    | Type  | Mandatory|  Description    |
| ---------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<number, number, Int16Array> | Yes| Reduce function.|

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
let array: collections.Int16Array = collections.Int16Array.from([1, 2, 3, 4, 5]);
let reducedValue: number = array.reduceRight((accumulator: number, value: number) => accumulator + value);
console.info(reducedValue + ''); // Expected output: 15
```

## reduce
reduce(callbackFn: TypedArrayReduceCallback\<number, number, Int16Array>, initialValue: number): number

Executes the reduction function on each element in the ArkTS Int16Array, receives the initial value as the argument for the first call of the reduction function, and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | --------------------------------------------------- |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<number, number, Int16Array> | Yes | Reduce function.|
| initialValue | number | Yes  | Initial accumulated value when the reduction function is called for the first time. |


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
let array: collections.Int16Array = collections.Int16Array.from([1, 2, 3, 4, 5]);
// reducedValue == 16
let reducedValue: number = array.reduce((accumulator: number, value: number) => accumulator + value, 1);
```

## reduceRight<sup>18+</sup>

reduceRight\<U = number>(callbackFn: TypedArrayReduceCallback\<U, number, Int16Array>, initialValue: U): U

Traverses the ArkTS Int16Array in reverse order, executes a reduction function on each element, receives the initial value as the argument for the first call of the reduction function, and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | --------------------------------------------------- |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<U, number, Int16Array> | Yes | Reduce function.|
| initialValue | U | Yes | Initial accumulated value when the reduction function is called for the first time. |

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
let array: collections.Int16Array = collections.Int16Array.from([1, 2, 3, 4, 5]);
let reducedValue: number = array.reduceRight((accumulator: number, value: number) => accumulator + value, 1);
console.info(reducedValue + ''); // Expected output: 16
```

## reduce
reduce\<U>(callbackFn: TypedArrayReduceCallback\<U, number, Int16Array>, initialValue: U): U

Applies a reduce function for each element in this ArkTS Int16Array, receives an initial value as the parameter called by the reduce function for the first time, and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | ---------------------------------------------------- |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<U, number, Int16Array> | Yes | Reduce function.|
| initialValue | U | Yes | Initial accumulated value when the reduction function is called for the first time. |

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
let array: collections.Int16Array = collections.Int16Array.from([1, 2, 3, 4, 5]);
// reducedValue == initialValue12345
let reducedValue: string = array.reduce<string>((accumulator: string, value: number) => accumulator + value, "initialValue");
```

## reverse
reverse(): Int16Array

Reverses the order of the elements in the ArkTS Int16Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Int16Array   | Reversed ArkTS Int16Array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The reverse method cannot be bound. |
| 10200201 | Concurrent modification error.   |

**Example**

```ts
let array: collections.Int16Array = collections.Int16Array.from([1, 2, 3, 4, 5]);
let reversed: collections.Int16Array = array.reverse(); // Int16Array [5, 4, 3, 2, 1]
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
| offset | number | No | Start position for writing. The default value is 0. The value is a non-negative integer, and offset + array.length does not exceed the length of the current Int16Array. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The set method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**Example**

```ts
let buffer: collections.ArrayBuffer = new collections.ArrayBuffer(16);
let array: collections.Int16Array = new collections.Int16Array(buffer);
array.set([1, 2, 3], 3); // Int16Array [0, 0, 0, 1, 2, 3, 0, 0]
```

## slice
slice(start?: number, end?: number): Int16Array

Returns a new ArkTS Int16Array object that contains the content of the specified range of the original ArkTS Int16Array. Unlike subarray, the object returned by slice does not affect the original array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description                                                  |
| ------ | ------ | ---- | -----------------------------------------------------|
| start  | number | No   | Start index. If `start < 0`, it starts from the position `start + Int16Array.length`. Default value: 0. |
| end    | number | No  | End index of the range (exclusive). If a negative number is passed in, it refers to the index of `end + Int16Array.length`. The default value is the length of the ArkTS Int16Array.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Int16Array | A new ArkTS Int16Array object that contains the elements in the specified range of the original ArkTS Int16Array. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The slice method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Int16Array = collections.Int16Array.from([1, 2, 3, 4, 5]);
array.slice(); // Int16Array [1, 2, 3, 4, 5]
array.slice(1, 3); // Int16Array [2, 3]
array.slice(-2); // Int16Array [4, 5]
```

## sort
sort(compareFn?: TypedArrayCompareFn\<number>): Int16Array

Sorts the ArkTS Int16Array in place and returns the sorted ArkTS Int16Array object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type                  | Mandatory| Description                                      |
| --------- | ---------------------- | ---- | ------------------------------------------ |
| compareFn | [TypedArrayCompareFn](arkts-apis-arkts-collections-Types.md#typedarraycomparefn)\<number> | No  | Function that determines the sort order. By default, elements are sorted in ascending order.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Int16Array | Sorted ArkTS Int16Array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------ |
| 10200011 | The sort method cannot be bound. |
| 10200201 | Concurrent modification error.         |

**Example**

```ts
let array: collections.Int16Array = collections.Int16Array.from([1, 3, 5, 4, 2]);
// Default ascending sort
array.sort(); // Int16Array [1, 2, 3, 4, 5]
// Ascending sort using a comparison function
array.sort((first: number, second: number) => first - second); // Int16Array [1, 2, 3, 4, 5]
// Descending sort using a comparison function
array.sort((first: number, second: number) => second - first); // Int16Array [5, 4, 3, 2, 1]
```

## subarray
subarray(begin?: number, end?: number): Int16Array

Extracts the array from the specified position and returns a new ArkTS Int16Array object based on the same ArkTS ArrayBuffer. Since the returned object shares the same ArrayBuffer with the original object, modifying one affects the other.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description                                               |
| ------ | ------ | ---- | ------------------------------------------------- |
| begin  | number | No  | Start index of the range. If a negative number is passed in, it refers to the index of `begin + Int16Array.length`. The default value is **0**.|
| end    | number | No  | End index of the range (exclusive). If a negative number is passed in, it refers to the index of `end + Int16Array.length`. The default value is the length of the ArkTS Int16Array.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Int16Array | A new ArkTS Int16Array object based on the same ArrayBuffer.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID|            Error Message                              |
| -------- | -------------------------------------------------|
| 10200011 | The subarray method cannot be bound.             |
| 10200201 | Concurrent modification error.               |

**Example**

```ts
let array: collections.Int16Array = collections.Int16Array.from([1, 2, 3, 4, 5]);
let subArray: collections.Int16Array = array.subarray(); // Int16Array [1, 2, 3, 4, 5]
subArray.set([10, 20, 30]); // Int16Array [10, 20, 30, 4, 5]
```

## at
at(index: number): number | undefined

Returns the element at the specified index, or returns undefined if it does not exist.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| index  | number | Yes   | Index of the ArkTS Int16Array element to return (zero-based), which is an integer. If `index < 0`, the element at position `index + Int16Array.length` is accessed. |

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
let array: collections.Int16Array = collections.Int16Array.from([1, 2, 3, 4, 5]);
console.info("element: " + array.at(2));  // element: 3
console.info("element: " + array.at(-1)); // element: 5
console.info("element: " + array.at(6));  // element: undefined
```

## includes
includes(searchElement: number, fromIndex?: number): boolean

Determines whether the ArkTS Int16Array contains the specified element.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name| Type  | Mandatory| Description                                     |
| ------ | ------ | ---- | --------------------------------------- |
| searchElement  | number | Yes  | Element to search for.|
| fromIndex  | number | No | Index from which the search starts. If a negative number is passed in, it refers to the index of `fromIndex + Int16Array.length`. The default value is **0**.|

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
let array: collections.Int16Array = collections.Int16Array.from([1, 2, 3]);
console.info("includes: " + array.includes(2));    // includes: true
console.info("includes: " + array.includes(4));    // includes: false
console.info("includes: " + array.includes(3, 3)); // includes: false
```

## entries
entries(): IterableIterator\<[number, number]>

Returns an iterator object that contains the key-value pair of each element in this ArkTS Int16Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description     |
| ------------ | --------- |
| IterableIterator\<[number, number]>| An iterator object containing the key-value pair of each element in the ArkTS Int16Array. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The entries method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Int16Array = collections.Int16Array.from([11, 22, 33]);
let iterator: IterableIterator<[number, number]> = array.entries();
console.info("value: " + iterator.next().value); // value: 0,11
console.info("value: " + iterator.next().value); // value: 1,22
console.info("value: " + iterator.next().value); // value: 2,33
```

## keys
keys(): IterableIterator\<number>

Returns a new iterator object that contains the key (index) of each element in the ArkTS Int16Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description     |
| ------------ | --------- |
| IterableIterator\<number> | An iterator object that contains the key (index) of each element in the ArkTS Int16Array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The keys method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Int16Array = collections.Int16Array.from([1, 2, 3, 4, 5]);
let iterator: IterableIterator<number> = array.keys();
for (const key of iterator) {
  console.info("" + key); // 0, 1, 2, 3, and 4 are returned in sequence.
}
```

## values
values(): IterableIterator\<number>

Returns an iterator object that contains the value of each element in this ArkTS Int16Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description     |
| ------------ | --------- |
| IterableIterator\<number> | An iterator object that contains the value of each element in the ArkTS Int16Array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The values method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**Example**

```ts
let array: collections.Int16Array = collections.Int16Array.from([1, 2, 3, 4, 5]);
let iterator: IterableIterator<number> = array.values();
for (const value of iterator) {
  console.info("" + value); // 1, 2, 3, 4, and 5 are returned in sequence.
}
```

## [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;number&gt;

Returns an iterator that contains each element in the ArkTS Int16Array.

> **NOTE**
>
> This API cannot be used in .ets files.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type                     | Description            |
| ------------------------- | ---------------- |
| IterableIterator&lt;number&gt; | An iterator object that contains the value of each element in the ArkTS Int16Array. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 10200011 | The Symbol.iterator method cannot be bound. |

**Example**

```ts
let int16Array: collections.Int16Array = collections.Int16Array.from([1, 2, 3, 4, 5, 6]);
// Iterate the Int16Array via an iterator.
for (let item of int16Array) {
  console.info("value : " + item);
}
```

## [index: number]

&#91;index: number&#93;: number

Returns the element at the specified index position in the ArkTS Int16Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type  | Mandatory| Description                    |
| ----- | ------ | ---- | -------------------------- |
| index | number | Yes | Zero-based element index. The value range is [0, Int16Array.length - 1]. |

**Return value**

| Type  | Description                |
| ----- | ---------------------|
| number | Returns the element value at the specified index position. |

**Example**

```ts
let int16Array = collections.Int16Array.from([1, 2, 4]);
// Access the elements of Int16Array via index.
console.info("Element at index 1: " + int16Array[1]);
```
