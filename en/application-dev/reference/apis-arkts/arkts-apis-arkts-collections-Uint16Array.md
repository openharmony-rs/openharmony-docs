# Class (Uint16Array)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=08d9523ef0226b259d674e299ae60897c53575d4 translatedAt=2026-11-16T04:59:38.995Z pushedAt=2026-11-16T06:31:14.155Z nl=2 -->

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
| buffer | [ArrayBuffer](arkts-apis-arkts-collections-ArrayBuffer.md) | Yes | No | The [ArrayBuffer](arkts-apis-arkts-collections-ArrayBuffer.md) object used by the ArkTS Uint16Array as its underlying buffer. |
| byteLength | number | Yes | No | The number of bytes occupied by the ArkTS Uint16Array. |
| byteOffset | number | Yes | No | The byte offset of the ArkTS Uint16Array from the start of its ArrayBuffer. |
| length | number | Yes  | No | Number of elements in an ArkTS Uint16Array.|
| BYTES_PER_ELEMENT | number | Yes | No | The number of bytes occupied by each element in the ArkTS Uint16Array. |

## constructor
constructor()

A constructor used to create an empty ArkTS Uint16Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 10200012 | The Uint16Array's constructor cannot be directly invoked. |

**Example**

```ts
let uint16Array: collections.Uint16Array = new collections.Uint16Array();
```

## constructor
constructor(length: number)

A constructor used to create an ArkTS Uint16Array of a given length.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                         |
| ------- | ------ | ---- | --------------------------- |
| length | number | Yes | Used to specify the length of the ArkTS Uint16Array, which must be a non-negative integer. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                                 |
| -------- | -------------------------------------------------------  |
| 10200012 | The Uint16Array's constructor cannot be directly invoked. |


**Example**

```ts
// Construct an object with the length parameter.
let uint16Array: collections.Uint16Array = new collections.Uint16Array(12);
```

## constructor
constructor(elements: Iterable\<number>)

A constructor that creates an ArkTS Uint16Array from an iterable object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| elements |  Iterable\<number> | Yes | Iterable numeric collection used to create an ArkTS Uint16Array object. The value range of each element is 0 to 2^16-1, that is, 0 to 65535. If an element is out of this range, it is converted to a value in the range 0 to 65535 through a modulo operation (that is, the value & 0xFFFF operation is performed). |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 10200012 | The Uint16Array's constructor cannot be directly invoked. |

**Example**

```ts
// Construct objects from an iterable object.
let set: Set<number> = new Set<number>([1, 2, 3]);
let array: collections.Uint16Array = new collections.Uint16Array(set);
// Uint16Array [1, 2, 3]
```

## constructor
constructor(array: ArrayLike\<number> | ArrayBuffer)

A constructor that creates an ArkTS Uint16Array from an array-like object or ArkTS ArrayBuffer.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| array |  ArrayLike\<number> \| ArrayBuffer | Yes | Used to construct an ArkTS Uint16Array object. When the parameter type is ArrayBuffer, the number of bytes occupied by the buffer must be an integer multiple of 2. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 10200012 | The Uint16Array's constructor cannot be directly invoked. |

**Example**

```ts
// Example 1: Construct an object from an array-like object.
let arrayLike = [1, 3, 5];
let array: collections.Uint16Array = new collections.Uint16Array(arrayLike);
```

```ts
// Example 2: Construct an object from an ArrayBuffer.
let arrayBuffer: collections.ArrayBuffer = new collections.ArrayBuffer(12);
let array: collections.Uint16Array = new collections.Uint16Array(arrayBuffer);
```

```ts
// Example 3: Construct an object from another ArkTS Uint16Array.
let arrayLike = [1, 3, 5];
// uint16Array1 [1, 3, 5]
let uint16Array1: collections.Uint16Array = new collections.Uint16Array(arrayLike);
// uint16Array2 [1, 3, 5]
let uint16Array2: collections.Uint16Array = new collections.Uint16Array(uint16Array1);
```

## constructor
constructor(buffer: ArrayBuffer, byteOffset?: number, length?: number)

A constructor that creates an ArkTS Uint16Array from an ArrayBuffer.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                        |
| ------- | ------ | ---- | ------------------------------------------ |
| buffer | [ArrayBuffer](arkts-apis-arkts-collections-ArrayBuffer.md) | Yes | The [ArrayBuffer](arkts-apis-arkts-collections-ArrayBuffer.md) object used to create the ArkTS Uint16Array. The bytes occupied by the buffer must be a multiple of 2. |
| byteOffset | number | No | Specifies the byte offset of the buffer, which must be a non-negative integer. The default value is 0. |
| length | number | No | Specifies the length of the ArkTS Uint16Array, which must be a non-negative integer. The default value is 0, in which case it indicates all elements from byteOffset to the end of the buffer. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                                  |
| -------- | -------------------------------------------------------   |
| 10200012 | The Uint16Array's constructor cannot be directly invoked. |

**Example**

```ts
let uint16Array: collections.Uint16Array = collections.Uint16Array.from([1, 2, 3, 4, 5, 6]);
console.info(`byteLength: ${uint16Array.buffer.byteLength}`); // byteLength: 12
// Start from the 3rd byte of the buffer corresponding to uint16Array, with a length of 5.
let uint16Array1: collections.Uint16Array = new collections.Uint16Array(uint16Array.buffer, 2, 5);
console.info(`[${uint16Array1}]`); // [2, 3, 4, 5, 6]
```

## from
static from(arrayLike: ArrayLike\<number>): Uint16Array

Creates an ArkTS Uint16Array object from an ArrayLike.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                 |
| ------- | ------ | ---- | --------------------------------------------------- |
| arrayLike | ArrayLike\<number> | Yes| Array-like object used to construct the ArkTS Uint16Array.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint16Array | New ArkTS Uint16Array generated.|

**Example**
```ts
let arrayLike = [1, 3, 5];
let array: collections.Uint16Array = collections.Uint16Array.from(arrayLike); // array [1, 3, 5]
```

## from
static from\<T>(arrayLike: ArrayLike\<T>, mapFn: TypedArrayFromMapFn\<T, number>): Uint16Array

Creates an ArkTS Uint16Array from an array-like object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name | Type  | Mandatory| Description                                       |
| ------- | ------ | ---- | ------------------------------------------|
| arrayLike | ArrayLike\<T> | Yes | Array-like object used to construct the ArkTS Uint16Array.              |
| mapFn | [TypedArrayFromMapFn](arkts-apis-arkts-collections-Types.md#typedarrayfrommapfn)\<T, number> | Yes | Mapping function that maps each element of type T in the ArrayLike to the number type. The mapping result is used to create the corresponding element of the ArkTS Uint16Array. |

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint16Array | New ArkTS Uint16Array generated.|

**Example**

```ts
// Example 1: Create an ArkTS Uint16Array from an object.
let array: collections.Uint16Array = collections.Uint16Array.from<number>(
  { length: 5 }, (v: Object, k: number) => k);
// Uint16Array [0, 1, 2, 3, 4]
```

```ts
// Example 2: Create an ArkTS Uint16Array from a string array.
let array: collections.Uint16Array = collections.Uint16Array.from<string>(
  ["1", "3", "5"], (v: string, k: number) => parseInt(v));
// Uint16Array [1, 3, 5]
```

```ts
// Example 3: Create an ArkTS Uint16Array from a string.
let array: collections.Uint16Array = collections.Uint16Array.from<string>(
  "12345", (v: string, k: number) => parseInt(v));
// Uint16Array [1, 2, 3, 4, 5]
```

## from
static from(arrayLike: Iterable\<number>, mapFn?: TypedArrayFromMapFn\<number, number>): Uint16Array

Creates an ArkTS Uint16Array from an iterator object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name | Type  | Mandatory| Description                               |
| ------- | ------ | ---- | -----------------------------------|
| arrayLike | Iterable\<number> | Yes | Iterable object used to create an ArkTS Uint16Array.   |
| mapFn | [TypedArrayFromMapFn](arkts-apis-arkts-collections-Types.md#typedarrayfrommapfn)\<number, number> | No | Mapping function. If omitted, the elements are not mapped and the original element values are used directly. |

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint16Array | New ArkTS Uint16Array generated.|

**Example**

```ts
// Example 1: No mapping function is specified.
let set: Set<number> = new Set<number>([1, 2, 3]);
let array: collections.Uint16Array = collections.Uint16Array.from(set);
// Uint16Array [1, 2, 3]
```

```ts
// Example 2: A mapping function is specified.
let set: Set<number> = new Set<number>([1, 2, 3]);
let array: collections.Uint16Array = collections.Uint16Array.from(
  set, (v: number, k: number) => v + k);
// Uint16Array [1, 3, 5]
```

## of<sup>18+</sup>

static of(...items: number[]): Uint16Array

Creates a new ArkTS Uint16Array object from a variable number of arguments.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type         | Mandatory| Description                           |
| --------- | ------------- | ---- | ------------------------------- |
| items | number[] | No  | Array of elements used to create the array. The number of elements can be zero, one, or more. The default value is an empty array.|

**Return value**

| Type     | Description                   |
| --------- | ----------------------- |
| Uint16Array | New ArkTS Uint16Array object. |

**Example**

```ts
let arr: collections.Uint16Array = collections.Uint16Array.of(1, 2, 3, 4);
console.info(arr.toString()); // Expected output: 1,2,3,4
```

## toString<sup>18+</sup>

toString(): string

Converts an ArkTS Uint16Array into a string.

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
let array = new collections.Uint16Array([1, 2, 3, 4, 5]);
let stringArray = array.toString();
console.info(stringArray); // Expected output: 1,2,3,4,5
```

## toLocaleString<sup>18+</sup>

toLocaleString(): string

Obtains the numeric representation that conforms to the current cultural conventions based on the system locale of the current application, calls the toLocaleString method on each element to convert the number to a string, and then concatenates the resulting strings of each element in order using commas.

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
let array = new collections.Uint16Array([1000, 2000, 3000]);
let stringArray = array.toLocaleString();
console.info(stringArray); // Expected output: 1,000,2,000,3,000
```

## copyWithin
copyWithin(target: number, start: number, end?: number): Uint16Array

Copies elements within a given range from this ArkTS Uint16Array to another position in sequence.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| target | number | Yes | Subscript of the target start position. If `target < 0`, it starts from `target + Uint16Array.length`. |
| start | number | Yes| Start index of the range. If a negative number is passed in, it refers to the index of `start + Uint16Array.length`.|
| end | number | No | Subscript of the source end position (excluding the element at the end position). If `end < 0`, it ends at `end + Uint16Array.length`. The default value is the length of the ArkTS Uint16Array. |

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint16Array | The modified ArkTS Uint16Array. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------ |
| 10200011 | The copyWithin method cannot be bound.           |
| 10200201 | Concurrent modification error.               |

**Example**

```ts
let array: collections.Uint16Array = collections.Uint16Array.from([1, 2, 3, 4, 5, 6, 7, 8]);
let copied: collections.Uint16Array = array.copyWithin(3, 1, 3);
// Uint16Array [1, 2, 3, 2, 3, 6, 7, 8]
```

## some
some(predicate: TypedArrayPredicateFn\<number, Uint16Array>): boolean

Tests whether an element that meets the specified condition exists in the ArkTS Uint16Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                 |
| ------- | ------ | ---- | ---------------------------------------------------- |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Uint16Array> | Yes| Assertion function used for the test.|

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
let uint16Array: collections.Uint16Array = new collections.Uint16Array(arrayLike);
uint16Array.some((element: number) => element < 1); // false
```

## every
every(predicate: TypedArrayPredicateFn\<number, Uint16Array>): boolean

Checks whether all elements in this ArkTS Uint16Array meet a given condition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                   |
| ------- | ------ | ---- | ----------------------------------------------------- |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Uint16Array> | Yes| Assertion function used for the test.|

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
let uint16Array: collections.Uint16Array = new collections.Uint16Array(arrayLike);
uint16Array.every((element: number) => element > 1);  // true
```

## fill
fill(value: number, start?: number, end?: number): Uint16Array

Fills all elements in a given range in this ArkTS Uint16Array with a value.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                     |
| ------- | ------ | ---- | --------------------------------------------------------|
| value | number | Yes | Value to be filled. The value range is 0 to 2^16-1, that is, 0 to 65535. If an element is out of this range, the element is converted to a value in the range of 0 to 65535 through a modulo operation (that is, the value & 0xFFFF operation is performed). |
| start | number | No| Start index of the range. If a negative number is passed in, it refers to the index of `start + Uint16Array.length`. The default value is **0**.|
| end | number | No| End index of the range (exclusive). If a negative number is passed in, it refers to the index of `end + Uint16Array.length`. The default value is the length of the ArkTS Uint16Array.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint16Array | The filled ArkTS Uint16Array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The fill method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let arrayLike = [1, 2, 3];
new collections.Uint16Array(arrayLike).fill(4); // Uint16Array [4, 4, 4]
new collections.Uint16Array(arrayLike).fill(4, 1); // Uint16Array [1, 4, 4]
new collections.Uint16Array(arrayLike).fill(4, 1, 2); // Uint16Array [1, 4, 3]
```

## filter
filter(predicate: TypedArrayPredicateFn\<number, Uint16Array>): Uint16Array

Returns a new ArkTS Uint16Array that contains all elements that meet the given condition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                   |
| ------- | ------ | ---- | ------------------------------------------------------ |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Uint16Array> | Yes| Assertion function used for the test.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint16Array| Filtered ArkTS Uint16Array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The filter method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Uint16Array = collections.Uint16Array.from([0, 1, 2, 3, 4]);
let filtered: collections.Uint16Array = array.filter((element: number) => element % 2 == 0);
// Uint16Array [0, 2, 4]
```

## find
find(predicate: TypedArrayPredicateFn\<number, Uint16Array>): number | undefined

Returns the value of the first element that passes a test provided by a callback function. If none of the elements pass the test, **undefined** is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Uint16Array> | Yes| Assertion function used for the test.|

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
let array: collections.Uint16Array = collections.Uint16Array.from([0, 1, 2, 3, 4]);
array.find((element: number) => element > 2); // 3
array.find((element: number) => element > 4); // undefined
```

## findIndex
findIndex(predicate: TypedArrayPredicateFn\<number, Uint16Array>): number

Returns the index of the first element that passes a test provided by a callback function. If none of the elements pass the test, **-1** is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| predicate | [TypedArrayPredicateFn](arkts-apis-arkts-collections-Types.md#typedarraypredicatefn)\<number, Uint16Array> | Yes| Assertion function used for the test.|

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
const array: collections.Uint16Array = collections.Uint16Array.from([1, 2, 3, 4, 5]);
let foundIndex: number = array.findIndex((element: number) => element % 2 === 0); // 1
```

## forEach
forEach(callbackFn: TypedArrayForEachCallback\<number, Uint16Array>): void

Calls a callback function for each element in this ArkTS Uint16Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| callbackFn | [TypedArrayForEachCallback](arkts-apis-arkts-collections-Types.md#typedarrayforeachcallback)\<number, Uint16Array> | Yes| Callback function to run for each element.|


**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The forEach method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let uint16Array: collections.Uint16Array = collections.Uint16Array.from([1, 2, 3]);
uint16Array.forEach((value: number, index: number, array: collections.Uint16Array) => {
  console.info(`Element ${value} at index ${index}`);
});
```

## indexOf
indexOf(searchElement: number, fromIndex?: number): number

Returns the index of the first occurrence of a value in this ArkTS Uint16Array. If the value is not found, **-1** is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name       | Type  | Mandatory| Description                       |
| ------------- | ------ | ---- | ---------------------------|
| searchElement | number | Yes  | Value to search for.               |
| fromIndex     | number | No   | Start index for the search. The default value is 0. If the index is greater than or equal to the length of the ArkTS Uint16Array, -1 is returned. If the index is negative, it is treated as an offset from the end of the array, searching from front to back. |

**Return value**

| Type        | Description     |
| ------------ | --------- |
| number | The first index of the given element in the ArkTS Uint16Array; returns -1 if not found. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The indexOf method cannot be bound. |
| 10200201 | Concurrent modification error.                |

**Example**

```ts
let array: collections.Uint16Array = collections.Uint16Array.from([3, 5, 9]);
array.indexOf(3); // 0
array.indexOf(7); // -1
array.indexOf(9, 2); // 2
array.indexOf(9, -2); // 2
```

## lastIndexOf<sup>18+</sup>

lastIndexOf(searchElement: number, fromIndex?: number): number

Returns the index of the last occurrence of searchElement in the ArkTS Uint16Array instance, or -1 if the element is not contained.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name          | Type    | Mandatory | Description                                                                               |
| ------------- | ------ | --- | --------------------------------------------------------------------------------- |
| searchElement | number | Yes  | Value to search for.                                                                           |
| fromIndex     | number | No   | Start index for the search, searching backward from this position. The default value is the length of the ArkTS Uint16Array minus 1 (that is, starting from the end). If the provided index value is negative, it is treated as an offset from the end of the array, searching from back to front. |

**Return value**

| Type    | Description                     |
| ------ | ----------------------- |
| number | The last index of the given element in the ArkTS Uint16Array; returns -1 if not found. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID   | Error Message                                   |
| -------- | --------------------------------------- |
| 10200011 | The lastIndexOf method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Uint16Array = collections.Uint16Array.from([3, 5, 9]);
console.info(array.lastIndexOf(3) + ''); // Expected output: 0
console.info(array.lastIndexOf(7) + ''); // Expected output: -1
console.info(array.lastIndexOf(9, 2) + ''); // Expected output: 2
console.info(array.lastIndexOf(9, -2) + ''); // Expected output: -1
```

## join
join(separator?: string): string

Concatenates all elements in this ArkTS Uint16Array into a string, with a given separator.

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
let array: collections.Uint16Array = collections.Uint16Array.from([1, 2, 3, 4, 5]);
let joined: string = array.join('-'); // "1-2-3-4-5"
```

## map
map(callbackFn: TypedArrayMapCallback\<number, Uint16Array>): Uint16Array

Applies a callback function to each element in this ArkTS Uint16Array and uses the result to create an ArkTS Uint16Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | ---------------------------------------------------- |
| callbackFn | [TypedArrayMapCallback](arkts-apis-arkts-collections-Types.md#typedarraymapcallback)\<number, Uint16Array> | Yes  | Callback function used to transform each element, whose return values sequentially form the corresponding elements of the new ArkTS Uint16Array. |


**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint16Array | New ArkTS Uint16Array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The map method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Uint16Array = collections.Uint16Array.from([25, 36, 49]);
const mapped: collections.Uint16Array = array.map(Math.sqrt); // Uint16Array [5, 6, 7]
```

## reduce
reduce(callbackFn: TypedArrayReduceCallback\<number, number, Uint16Array>): number

Applies a reduce function on each element in this ArkTS Uint16Array and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name    | Type  | Mandatory|  Description    |
| ---------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<number, number, Uint16Array> | Yes| Reduce function.|

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
let array: collections.Uint16Array = collections.Uint16Array.from([1, 2, 3, 4, 5]);
let reducedValue: number = array.reduce((accumulator: number, value: number) => accumulator + value);
// reducedValue == 15
```

## reduceRight<sup>18+</sup>

reduceRight(callbackFn: TypedArrayReduceCallback\<number, number, Uint16Array>): number

Traverses the ArkTS Uint16Array in reverse order, executes the reduction function on each element, and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name    | Type  | Mandatory|  Description    |
| ---------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<number, number, Uint16Array> | Yes| Reduce function.|

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
let array: collections.Uint16Array = collections.Uint16Array.from([1, 2, 3, 4, 5]);
let reducedValue: number = array.reduceRight((accumulator: number, value: number) => accumulator + value);
console.info(reducedValue + ''); // Expected output: 15
```

## reduce
reduce(callbackFn: TypedArrayReduceCallback\<number, number, Uint16Array>, initialValue: number): number

Executes the reduction function on each element in the ArkTS Uint16Array, receives the initial value as the first call argument, and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | --------------------------------------------------- |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<number, number, Uint16Array> | Yes | Reduce function.|
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
let array: collections.Uint16Array = collections.Uint16Array.from([1, 2, 3, 4, 5]);
let reducedValue: number = array.reduce((accumulator: number, value: number) => accumulator + value, 1);
// reducedValue == 16
```

## reduceRight<sup>18+</sup>

reduceRight\<U = number>(callbackFn: TypedArrayReduceCallback\<U, number, Uint16Array>, initialValue: U): U

Traverses the ArkTS Uint16Array in reverse order, executes the reduction function on each element, receives the initial value as the first call argument, and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | --------------------------------------------------- |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<U, number, Uint16Array> | Yes | Reduce function.|
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
let array: collections.Uint16Array = collections.Uint16Array.from([1, 2, 3, 4, 5]);
let reducedValue: number = array.reduceRight((accumulator: number, value: number) => accumulator + value, 1);
console.info(reducedValue + ''); // Expected output: 16
```

## reduce
reduce\<U>(callbackFn: TypedArrayReduceCallback\<U, number, Uint16Array>, initialValue: U): U

Applies a reduce function for each element in this ArkTS Uint16Array, receives an initial value as the parameter called by the reduce function for the first time, and returns the final reduction result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type  | Mandatory| Description                                                |
| --------- | ------ | ---- | ---------------------------------------------------- |
| callbackFn | [TypedArrayReduceCallback](arkts-apis-arkts-collections-Types.md#typedarrayreducecallback)\<U, number, Uint16Array> | Yes | Reduce function.|
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
let array: collections.Uint16Array = collections.Uint16Array.from([1, 2, 3, 4, 5]);
let reducedValue: string = array.reduce<string>((accumulator: string, value: number) => accumulator + value, "initialValue");
// reducedValue == initialValue12345
```

## reverse
reverse(): Uint16Array

Reverses the order of the elements of the ArkTS Uint16Array in place (modifies the original array), and returns the reference to the modified original array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint16Array   | Reversed ArkTS Uint16Array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The reverse method cannot be bound. |
| 10200201 | Concurrent modification error.   |

**Example**

```ts
let array: collections.Uint16Array = collections.Uint16Array.from([1, 2, 3, 4, 5]);
let reversed: collections.Uint16Array = array.reverse(); // Uint16Array [5, 4, 3, 2, 1]
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
| offset | number | No | Start position for writing, which must be a non-negative integer. The default value is 0. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The set method cannot be bound. |
| 10200201 | Concurrent modification error.  |

**Example**

```ts
let buffer: collections.ArrayBuffer = new collections.ArrayBuffer(16);
let array: collections.Uint16Array = new collections.Uint16Array(buffer);
array.set([1, 2, 3], 3); // Uint16Array [0, 0, 0, 1, 2, 3, 0, 0]
```

## slice
slice(start?: number, end?: number): Uint16Array

Selects a range of elements in this ArkTS Uint16Array to create an ArkTS Uint16Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description                                                  |
| ------ | ------ | ---- | -----------------------------------------------------|
| start  | number | No   | Start index, with a value range of [0, Uint16Array.length - 1]. If `start < 0`, it starts from the position `start + Uint16Array.length`. When out of range, it is automatically corrected to the boundary value. The default value is 0. |
| end    | number | No   | End index (excluding the element at this index), with a value range of [0, Uint16Array.length]. If `end < 0`, it ends at the position `end + Uint16Array.length`. When out of range, it is automatically corrected to the boundary value. The default value is the length of the ArkTS Uint16Array.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint16Array | A new ArkTS Uint16Array object containing the content of the specified range of the original ArkTS Uint16Array. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The slice method cannot be bound. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
let array: collections.Uint16Array = collections.Uint16Array.from([1, 2, 3, 4, 5]);
array.slice(); // Uint16Array [1, 2, 3, 4, 5]
array.slice(1, 3); // Uint16Array [2, 3]
array.slice(-2); // Uint16Array [4, 5]
```

## sort
sort(compareFn?: TypedArrayCompareFn\<number>): Uint16Array

Sorts the ArkTS Uint16Array in place (modifies the original array) and returns a reference to the sorted original array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type                  | Mandatory| Description                                      |
| --------- | ---------------------- | ---- | ------------------------------------------ |
| compareFn | [TypedArrayCompareFn](arkts-apis-arkts-collections-Types.md#typedarraycomparefn)\<number> | No  | Function that determines the sort order. By default, elements are sorted in ascending order.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint16Array | Sorted ArkTS Uint16Array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------ |
| 10200011 | The sort method cannot be bound. |
| 10200201 | Concurrent modification error.         |

**Example**

```ts
let array: collections.Uint16Array = collections.Uint16Array.from([1, 3, 5, 4, 2]);
array.sort(); // Uint16Array [1, 2, 3, 4, 5]
array.sort((first: number, second: number) => first - second); // Uint16Array [1, 2, 3, 4, 5]
array.sort((first: number, second: number) => second - first); // Uint16Array [5, 4, 3, 2, 1]
```

## subarray
subarray(begin?: number, end?: number): Uint16Array

Extracts a portion of the array from the specified position and returns a new ArkTS Uint16Array object based on the same ArkTS ArrayBuffer. Modifying the returned subarray or the original Uint16Array affects each other because they share the same underlying [ArrayBuffer](arkts-apis-arkts-collections-ArrayBuffer.md) data. To create an independent copy, use the [slice](#slice) method.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description                                               |
| ------ | ------ | ---- | ------------------------------------------------- |
| begin  | number | No   | Start index, with a value range of [0, Uint16Array.length - 1]. If `begin < 0`, it starts from the position `begin + Uint16Array.length`. When out of range, it is automatically corrected to the boundary value. The default value is 0. |
| end    | number | No  | End index of the range (exclusive). If a negative number is passed in, it refers to the index of `end + Uint16Array.length`. The default value is the length of the ArkTS Uint16Array.|

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Uint16Array | New ArkTS Uint16Array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID|            Error Message                              |
| -------- | -------------------------------------------------|
| 10200011 | The subarray method cannot be bound.             |
| 10200201 | Concurrent modification error.               |

**Example**

```ts
let array: collections.Uint16Array = collections.Uint16Array.from([1, 2, 3, 4, 5]);
let subArray: collections.Uint16Array = array.subarray(); // Uint16Array [1, 2, 3, 4, 5]
subArray.set([10, 20, 30]); // Uint16Array [10, 20, 30, 4, 5]
```

## at
at(index: number): number | undefined

Returns the element at the given index. If no element is found, **undefined** is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| index  | number | Yes   | Index of the element to return (starting from 0), which is an integer. If `index < 0`, the element at the position `index + Uint16Array.length` is accessed. |

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
let array: collections.Uint16Array = collections.Uint16Array.from([1, 2, 3, 4, 5]);
console.info(`element: ${array.at(2)}`);  // element: 3
console.info(`element: ${array.at(-1)}`); // element: 5
console.info(`element: ${array.at(6)}`);  // element: undefined
```

## includes
includes(searchElement: number, fromIndex?: number): boolean

Checks whether elements are contained in this ArkTS Uint16Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**
| Name| Type  | Mandatory| Description                                     |
| ------ | ------ | ---- | --------------------------------------- |
| searchElement  | number | Yes  | Element to search for.|
| fromIndex  | number | No | Index from which the search starts. If a negative number is passed in, it refers to the index of `fromIndex + Uint16Array.length`. The default value is **0**.|

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
let array: collections.Uint16Array = collections.Uint16Array.from([1, 2, 3]);
console.info(`includes: ${array.includes(2)}`);    // includes: true
console.info(`includes: ${array.includes(4)}`);    // includes: false
console.info(`includes: ${array.includes(3, 3)}`); // includes: false
```

## entries
entries(): IterableIterator\<[number, number]>

Returns an iterator object that contains the key-value pair of each element in this ArkTS Uint16Array.

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
let array: collections.Uint16Array = collections.Uint16Array.from([11, 22, 33]);
let iterator: IterableIterator<[number, number]> = array.entries();
console.info(`value: ${iterator.next().value}`); // value: 0,11
console.info(`value: ${iterator.next().value}`); // value: 1,22
console.info(`value: ${iterator.next().value}`); // value: 2,33
```

## keys
keys(): IterableIterator\<number>

Returns an iterator object that contains the key (index) of each element in this ArkTS Uint16Array.

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
let array: collections.Uint16Array = collections.Uint16Array.from([1, 2, 3, 4, 5]);
let iterator: IterableIterator<number> = array.keys();
for (const key of iterator) {
  console.info(`${key}`); // output in sequence 0,1,2,3,4
}
```

## values
values(): IterableIterator\<number>

Returns an iterator object that contains the value of each element in this ArkTS Uint16Array.

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
let array: collections.Uint16Array = collections.Uint16Array.from([1, 2, 3, 4, 5]);
let iterator: IterableIterator<number> = array.values();
for (const value of iterator) {
  console.info(`${value}`); // output in sequence 1,2,3,4,5
}
```

## [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;number&gt;

Returns an iterator, where each item of the iterator is the element value at the corresponding position in the Uint16Array.

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
let uint16Array: collections.Uint16Array = collections.Uint16Array.from([1, 2, 3, 4, 5, 6]);

for (let item of uint16Array) {
  console.info(`value : ${item}`);
}
```

## [index: number]

&#91;index: number&#93;: number

Returns the element at a given index in this Uint16Array.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type  | Mandatory| Description                    |
| ----- | ------ | ---- | -------------------------- |
| index | number | Yes | Zero-based index of the desired element. |

**Return value**

| Type  | Description                |
| ----- | ---------------------|
| number | Returns the element value at the specified index position. |

**Example**

```ts
let uint16Array = collections.Uint16Array.from([1, 2, 4]);
console.info(`Element at index 1: ${uint16Array[1]}`);
```
