# Uint16Array

```TypeScript
interface Uint16Array
```

A typed array of 16-bit unsigned integer values. The contents are initialized to 0. If the requested number of bytes could not be allocated an exception is raised.

<!--Device-unnamed-interface Uint16Array--><!--Device-unnamed-interface Uint16Array-End-->

## Modules to Import

```TypeScript
```

## copyWithin

```TypeScript
copyWithin(target: number, start: number, end?: number): this
```

Returns the this object after copying a section of the array identified by start and end to the same array starting at position target

<!--Device-Uint16Array-copyWithin(target: number, start: number, end?: number): this--><!--Device-Uint16Array-copyWithin(target: number, start: number, end?: number): this-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | number | Yes |  |
| start | number | Yes |  |
| end | number | No |  |

## every

```TypeScript
every(predicate: (value: number, index: number, array: Uint16Array) => unknown, thisArg?: any): boolean
```

Determines whether all the members of an array satisfy the specified test.

<!--Device-Uint16Array-every(predicate: (value: number, index: number, array: Uint16Array) => unknown, thisArg?: any): boolean--><!--Device-Uint16Array-every(predicate: (value: number, index: number, array: Uint16Array) => unknown, thisArg?: any): boolean-End-->

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | (value: number, index: number, array: Uint16Array) =&gt; unknown | Yes |  |
| thisArg | any | No |  |

## fill

```TypeScript
fill(value: number, start?: number, end?: number): this
```

Changes all array elements from `start` to `end` index to a static `value` and returns the modified array

<!--Device-Uint16Array-fill(value: number, start?: number, end?: number): this--><!--Device-Uint16Array-fill(value: number, start?: number, end?: number): this-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes |  |
| start | number | No |  |
| end | number | No |  |

## filter

```TypeScript
filter(predicate: (value: number, index: number, array: Uint16Array) => any, thisArg?: any): Uint16Array
```

Returns the elements of an array that meet the condition specified in a callback function.

<!--Device-Uint16Array-filter(predicate: (value: number, index: number, array: Uint16Array) => any, thisArg?: any): Uint16Array--><!--Device-Uint16Array-filter(predicate: (value: number, index: number, array: Uint16Array) => any, thisArg?: any): Uint16Array-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | (value: number, index: number, array: Uint16Array) =&gt; any | Yes |  |
| thisArg | any | No |  |

## find

```TypeScript
find(predicate: (value: number, index: number, obj: Uint16Array) => boolean, thisArg?: any): number | undefined
```

Returns the value of the first element in the array where predicate is true, and undefined otherwise.

<!--Device-Uint16Array-find(predicate: (value: number, index: number, obj: Uint16Array) => boolean, thisArg?: any): number | undefined--><!--Device-Uint16Array-find(predicate: (value: number, index: number, obj: Uint16Array) => boolean, thisArg?: any): number | undefined-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | (value: number, index: number, obj: Uint16Array) =&gt; boolean | Yes |  |
| thisArg | any | No |  |

## findIndex

```TypeScript
findIndex(predicate: (value: number, index: number, obj: Uint16Array) => boolean, thisArg?: any): number
```

Returns the index of the first element in the array where predicate is true, and -1 otherwise.

<!--Device-Uint16Array-findIndex(predicate: (value: number, index: number, obj: Uint16Array) => boolean, thisArg?: any): number--><!--Device-Uint16Array-findIndex(predicate: (value: number, index: number, obj: Uint16Array) => boolean, thisArg?: any): number-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | (value: number, index: number, obj: Uint16Array) =&gt; boolean | Yes |  |
| thisArg | any | No |  |

## forEach

```TypeScript
forEach(callbackfn: (value: number, index: number, array: Uint16Array) => void, thisArg?: any): void
```

Performs the specified action for each element in an array.

<!--Device-Uint16Array-forEach(callbackfn: (value: number, index: number, array: Uint16Array) => void, thisArg?: any): void--><!--Device-Uint16Array-forEach(callbackfn: (value: number, index: number, array: Uint16Array) => void, thisArg?: any): void-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackfn | (value: number, index: number, array: Uint16Array) =&gt; void | Yes |  |
| thisArg | any | No |  |

## indexOf

```TypeScript
indexOf(searchElement: number, fromIndex?: number): number
```

Returns the index of the first occurrence of a value in an array.

<!--Device-Uint16Array-indexOf(searchElement: number, fromIndex?: number): number--><!--Device-Uint16Array-indexOf(searchElement: number, fromIndex?: number): number-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchElement | number | Yes |  |
| fromIndex | number | No |  |

## join

```TypeScript
join(separator?: string): string
```

Adds all the elements of an array separated by the specified separator string.

<!--Device-Uint16Array-join(separator?: string): string--><!--Device-Uint16Array-join(separator?: string): string-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| separator | string | No |  |

## lastIndexOf

```TypeScript
lastIndexOf(searchElement: number, fromIndex?: number): number
```

Returns the index of the last occurrence of a value in an array.

<!--Device-Uint16Array-lastIndexOf(searchElement: number, fromIndex?: number): number--><!--Device-Uint16Array-lastIndexOf(searchElement: number, fromIndex?: number): number-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchElement | number | Yes |  |
| fromIndex | number | No |  |

## map

```TypeScript
map(callbackfn: (value: number, index: number, array: Uint16Array) => number, thisArg?: any): Uint16Array
```

Calls a defined callback function on each element of an array, and returns an array that contains the results.

<!--Device-Uint16Array-map(callbackfn: (value: number, index: number, array: Uint16Array) => number, thisArg?: any): Uint16Array--><!--Device-Uint16Array-map(callbackfn: (value: number, index: number, array: Uint16Array) => number, thisArg?: any): Uint16Array-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackfn | (value: number, index: number, array: Uint16Array) =&gt; number | Yes |  |
| thisArg | any | No |  |

## reduce

```TypeScript
reduce(callbackfn: (previousValue: number, currentValue: number, currentIndex: number, array: Uint16Array) => number): number
```

Calls the specified callback function for all the elements in an array. The return value of the callback function is the accumulated result, and is provided as an argument in the next call to the callback function.

<!--Device-Uint16Array-reduce(callbackfn: (previousValue: number, currentValue: number, currentIndex: number, array: Uint16Array) => number): number--><!--Device-Uint16Array-reduce(callbackfn: (previousValue: number, currentValue: number, currentIndex: number, array: Uint16Array) => number): number-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackfn | (previousValue: number, currentValue: number, currentIndex: number, array: Uint16Array) =&gt; number | Yes |  |

<a id="reduce-1"></a>

## reduce

```TypeScript
reduce(callbackfn: (previousValue: number, currentValue: number, currentIndex: number, array: Uint16Array) => number, initialValue: number): number
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackfn | (previousValue: number, currentValue: number, currentIndex: number, array: Uint16Array) =&gt; number | Yes |  |
| initialValue | number | Yes |  |

<a id="reduce-2"></a>

## reduce

```TypeScript
reduce<U>(callbackfn: (previousValue: U, currentValue: number, currentIndex: number, array: Uint16Array) => U, initialValue: U): U
```

Calls the specified callback function for all the elements in an array. The return value of the callback function is the accumulated result, and is provided as an argument in the next call to the callback function.

<!--Device-Uint16Array-reduce<U>(callbackfn: (previousValue: U, currentValue: number, currentIndex: number, array: Uint16Array) => U, initialValue: U): U--><!--Device-Uint16Array-reduce<U>(callbackfn: (previousValue: U, currentValue: number, currentIndex: number, array: Uint16Array) => U, initialValue: U): U-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackfn | (previousValue: U, currentValue: number, currentIndex: number, array: Uint16Array) =&gt; U | Yes |  |
| initialValue | U | Yes |  |

## reduceRight

```TypeScript
reduceRight(callbackfn: (previousValue: number, currentValue: number, currentIndex: number, array: Uint16Array) => number): number
```

Calls the specified callback function for all the elements in an array, in descending order. The return value of the callback function is the accumulated result, and is provided as an argument in the next call to the callback function.

<!--Device-Uint16Array-reduceRight(callbackfn: (previousValue: number, currentValue: number, currentIndex: number, array: Uint16Array) => number): number--><!--Device-Uint16Array-reduceRight(callbackfn: (previousValue: number, currentValue: number, currentIndex: number, array: Uint16Array) => number): number-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackfn | (previousValue: number, currentValue: number, currentIndex: number, array: Uint16Array) =&gt; number | Yes |  |

<a id="reduceright-1"></a>

## reduceRight

```TypeScript
reduceRight(callbackfn: (previousValue: number, currentValue: number, currentIndex: number, array: Uint16Array) => number, initialValue: number): number
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackfn | (previousValue: number, currentValue: number, currentIndex: number, array: Uint16Array) =&gt; number | Yes |  |
| initialValue | number | Yes |  |

<a id="reduceright-2"></a>

## reduceRight

```TypeScript
reduceRight<U>(callbackfn: (previousValue: U, currentValue: number, currentIndex: number, array: Uint16Array) => U, initialValue: U): U
```

Calls the specified callback function for all the elements in an array, in descending order. The return value of the callback function is the accumulated result, and is provided as an argument in the next call to the callback function.

<!--Device-Uint16Array-reduceRight<U>(callbackfn: (previousValue: U, currentValue: number, currentIndex: number, array: Uint16Array) => U, initialValue: U): U--><!--Device-Uint16Array-reduceRight<U>(callbackfn: (previousValue: U, currentValue: number, currentIndex: number, array: Uint16Array) => U, initialValue: U): U-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackfn | (previousValue: U, currentValue: number, currentIndex: number, array: Uint16Array) =&gt; U | Yes |  |
| initialValue | U | Yes |  |

## reverse

```TypeScript
reverse(): Uint16Array
```

Reverses the elements in an Array.

<!--Device-Uint16Array-reverse(): Uint16Array--><!--Device-Uint16Array-reverse(): Uint16Array-End-->

## set

```TypeScript
set(array: ArrayLike<number>, offset?: number): void
```

Sets a value or an array of values.

<!--Device-Uint16Array-set(array: ArrayLike<number>, offset?: number): void--><!--Device-Uint16Array-set(array: ArrayLike<number>, offset?: number): void-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| array | ArrayLike&lt;number&gt; | Yes |  |
| offset | number | No |  |

## slice

```TypeScript
slice(start?: number, end?: number): Uint16Array
```

Returns a section of an array.

<!--Device-Uint16Array-slice(start?: number, end?: number): Uint16Array--><!--Device-Uint16Array-slice(start?: number, end?: number): Uint16Array-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | No |  |
| end | number | No |  |

## some

```TypeScript
some(predicate: (value: number, index: number, array: Uint16Array) => unknown, thisArg?: any): boolean
```

Determines whether the specified callback function returns true for any element of an array.

<!--Device-Uint16Array-some(predicate: (value: number, index: number, array: Uint16Array) => unknown, thisArg?: any): boolean--><!--Device-Uint16Array-some(predicate: (value: number, index: number, array: Uint16Array) => unknown, thisArg?: any): boolean-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | (value: number, index: number, array: Uint16Array) =&gt; unknown | Yes |  |
| thisArg | any | No |  |

## sort

```TypeScript
sort(compareFn?: (a: number, b: number) => number): this
```

Sorts an array.

<!--Device-Uint16Array-sort(compareFn?: (a: number, b: number) => number): this--><!--Device-Uint16Array-sort(compareFn?: (a: number, b: number) => number): this-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| compareFn | (a: number, b: number) =&gt; number | No |  |

## subarray

```TypeScript
subarray(begin?: number, end?: number): Uint16Array
```

Gets a new Uint16Array view of the ArrayBuffer store for this array, referencing the elements at begin, inclusive, up to end, exclusive.

<!--Device-Uint16Array-subarray(begin?: number, end?: number): Uint16Array--><!--Device-Uint16Array-subarray(begin?: number, end?: number): Uint16Array-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| begin | number | No |  |
| end | number | No |  |

## toLocaleString

```TypeScript
toLocaleString(): string
```

Converts a number to a string by using the current locale.

<!--Device-Uint16Array-toLocaleString(): string--><!--Device-Uint16Array-toLocaleString(): string-End-->

## toString

```TypeScript
toString(): string
```

Returns a string representation of an array.

<!--Device-Uint16Array-toString(): string--><!--Device-Uint16Array-toString(): string-End-->

## valueOf

```TypeScript
valueOf(): Uint16Array
```

Returns the primitive value of the specified object.

<!--Device-Uint16Array-valueOf(): Uint16Array--><!--Device-Uint16Array-valueOf(): Uint16Array-End-->

## [index: number]

```TypeScript
[index: number]: number
```

**Type:** number

## buffer

```TypeScript
readonly buffer: ArrayBufferLike
```

The ArrayBuffer instance referenced by the array.

**Type:** [ArrayBufferLike](arkts-arraybufferlike-t.md)

<!--Device-Uint16Array-readonly buffer: ArrayBufferLike--><!--Device-Uint16Array-readonly buffer: ArrayBufferLike-End-->

## byteLength

```TypeScript
readonly byteLength: number
```

The length in bytes of the array.

**Type:** number

<!--Device-Uint16Array-readonly byteLength: number--><!--Device-Uint16Array-readonly byteLength: number-End-->

## byteOffset

```TypeScript
readonly byteOffset: number
```

The offset in bytes of the array.

**Type:** number

<!--Device-Uint16Array-readonly byteOffset: number--><!--Device-Uint16Array-readonly byteOffset: number-End-->

## BYTES_PER_ELEMENT

```TypeScript
readonly BYTES_PER_ELEMENT: number
```

The size in bytes of each element in the array.

**Type:** number

<!--Device-Uint16Array-readonly BYTES_PER_ELEMENT: number--><!--Device-Uint16Array-readonly BYTES_PER_ELEMENT: number-End-->

## length

```TypeScript
readonly length: number
```

The length of the array.

**Type:** number

<!--Device-Uint16Array-readonly length: number--><!--Device-Uint16Array-readonly length: number-End-->
