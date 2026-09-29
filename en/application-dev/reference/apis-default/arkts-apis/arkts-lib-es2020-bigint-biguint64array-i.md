# BigUint64Array

```TypeScript
interface BigUint64Array
```

A typed array of 64-bit unsigned integer values. The contents are initialized to 0. If the requested number of bytes could not be allocated, an exception is raised.

<!--Device-unnamed-interface BigUint64Array--><!--Device-unnamed-interface BigUint64Array-End-->

## Modules to Import

```TypeScript
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<bigint>
```

## copyWithin

```TypeScript
copyWithin(target: number, start: number, end?: number): this
```

Returns the this object after copying a section of the array identified by start and end to the same array starting at position target

<!--Device-BigUint64Array-copyWithin(target: number, start: number, end?: number): this--><!--Device-BigUint64Array-copyWithin(target: number, start: number, end?: number): this-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | number | Yes |  |
| start | number | Yes |  |
| end | number | No |  |

## entries

```TypeScript
entries(): IterableIterator<[number, bigint]>
```

Yields index, value pairs for every entry in the array.

<!--Device-BigUint64Array-entries(): IterableIterator<[number, bigint]>--><!--Device-BigUint64Array-entries(): IterableIterator<[number, bigint]>-End-->

## every

```TypeScript
every(predicate: (value: bigint, index: number, array: BigUint64Array) => boolean, thisArg?: any): boolean
```

Determines whether all the members of an array satisfy the specified test.

<!--Device-BigUint64Array-every(predicate: (value: bigint, index: number, array: BigUint64Array) => boolean, thisArg?: any): boolean--><!--Device-BigUint64Array-every(predicate: (value: bigint, index: number, array: BigUint64Array) => boolean, thisArg?: any): boolean-End-->

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | (value: bigint, index: number, array: BigUint64Array) =&gt; boolean | Yes |  |
| thisArg | any | No |  |

## fill

```TypeScript
fill(value: bigint, start?: number, end?: number): this
```

Changes all array elements from `start` to `end` index to a static `value` and returns the modified array

<!--Device-BigUint64Array-fill(value: bigint, start?: number, end?: number): this--><!--Device-BigUint64Array-fill(value: bigint, start?: number, end?: number): this-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | bigint | Yes |  |
| start | number | No |  |
| end | number | No |  |

## filter

```TypeScript
filter(predicate: (value: bigint, index: number, array: BigUint64Array) => any, thisArg?: any): BigUint64Array
```

Returns the elements of an array that meet the condition specified in a callback function.

<!--Device-BigUint64Array-filter(predicate: (value: bigint, index: number, array: BigUint64Array) => any, thisArg?: any): BigUint64Array--><!--Device-BigUint64Array-filter(predicate: (value: bigint, index: number, array: BigUint64Array) => any, thisArg?: any): BigUint64Array-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | (value: bigint, index: number, array: BigUint64Array) =&gt; any | Yes |  |
| thisArg | any | No |  |

## find

```TypeScript
find(predicate: (value: bigint, index: number, array: BigUint64Array) => boolean, thisArg?: any): bigint | undefined
```

Returns the value of the first element in the array where predicate is true, and undefined otherwise.

<!--Device-BigUint64Array-find(predicate: (value: bigint, index: number, array: BigUint64Array) => boolean, thisArg?: any): bigint | undefined--><!--Device-BigUint64Array-find(predicate: (value: bigint, index: number, array: BigUint64Array) => boolean, thisArg?: any): bigint | undefined-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | (value: bigint, index: number, array: BigUint64Array) =&gt; boolean | Yes |  |
| thisArg | any | No |  |

## findIndex

```TypeScript
findIndex(predicate: (value: bigint, index: number, array: BigUint64Array) => boolean, thisArg?: any): number
```

Returns the index of the first element in the array where predicate is true, and -1 otherwise.

<!--Device-BigUint64Array-findIndex(predicate: (value: bigint, index: number, array: BigUint64Array) => boolean, thisArg?: any): number--><!--Device-BigUint64Array-findIndex(predicate: (value: bigint, index: number, array: BigUint64Array) => boolean, thisArg?: any): number-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | (value: bigint, index: number, array: BigUint64Array) =&gt; boolean | Yes |  |
| thisArg | any | No |  |

## forEach

```TypeScript
forEach(callbackfn: (value: bigint, index: number, array: BigUint64Array) => void, thisArg?: any): void
```

Performs the specified action for each element in an array.

<!--Device-BigUint64Array-forEach(callbackfn: (value: bigint, index: number, array: BigUint64Array) => void, thisArg?: any): void--><!--Device-BigUint64Array-forEach(callbackfn: (value: bigint, index: number, array: BigUint64Array) => void, thisArg?: any): void-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackfn | (value: bigint, index: number, array: BigUint64Array) =&gt; void | Yes |  |
| thisArg | any | No |  |

## includes

```TypeScript
includes(searchElement: bigint, fromIndex?: number): boolean
```

Determines whether an array includes a certain element, returning true or false as appropriate.

<!--Device-BigUint64Array-includes(searchElement: bigint, fromIndex?: number): boolean--><!--Device-BigUint64Array-includes(searchElement: bigint, fromIndex?: number): boolean-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchElement | bigint | Yes |  |
| fromIndex | number | No |  |

## indexOf

```TypeScript
indexOf(searchElement: bigint, fromIndex?: number): number
```

Returns the index of the first occurrence of a value in an array.

<!--Device-BigUint64Array-indexOf(searchElement: bigint, fromIndex?: number): number--><!--Device-BigUint64Array-indexOf(searchElement: bigint, fromIndex?: number): number-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchElement | bigint | Yes |  |
| fromIndex | number | No |  |

## join

```TypeScript
join(separator?: string): string
```

Adds all the elements of an array separated by the specified separator string.

<!--Device-BigUint64Array-join(separator?: string): string--><!--Device-BigUint64Array-join(separator?: string): string-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| separator | string | No |  |

## keys

```TypeScript
keys(): IterableIterator<number>
```

Yields each index in the array.

<!--Device-BigUint64Array-keys(): IterableIterator<number>--><!--Device-BigUint64Array-keys(): IterableIterator<number>-End-->

## lastIndexOf

```TypeScript
lastIndexOf(searchElement: bigint, fromIndex?: number): number
```

Returns the index of the last occurrence of a value in an array.

<!--Device-BigUint64Array-lastIndexOf(searchElement: bigint, fromIndex?: number): number--><!--Device-BigUint64Array-lastIndexOf(searchElement: bigint, fromIndex?: number): number-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchElement | bigint | Yes |  |
| fromIndex | number | No |  |

## map

```TypeScript
map(callbackfn: (value: bigint, index: number, array: BigUint64Array) => bigint, thisArg?: any): BigUint64Array
```

Calls a defined callback function on each element of an array, and returns an array that contains the results.

<!--Device-BigUint64Array-map(callbackfn: (value: bigint, index: number, array: BigUint64Array) => bigint, thisArg?: any): BigUint64Array--><!--Device-BigUint64Array-map(callbackfn: (value: bigint, index: number, array: BigUint64Array) => bigint, thisArg?: any): BigUint64Array-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackfn | (value: bigint, index: number, array: BigUint64Array) =&gt; bigint | Yes |  |
| thisArg | any | No |  |

## reduce

```TypeScript
reduce(callbackfn: (previousValue: bigint, currentValue: bigint, currentIndex: number, array: BigUint64Array) => bigint): bigint
```

Calls the specified callback function for all the elements in an array. The return value of the callback function is the accumulated result, and is provided as an argument in the next call to the callback function.

<!--Device-BigUint64Array-reduce(callbackfn: (previousValue: bigint, currentValue: bigint, currentIndex: number, array: BigUint64Array) => bigint): bigint--><!--Device-BigUint64Array-reduce(callbackfn: (previousValue: bigint, currentValue: bigint, currentIndex: number, array: BigUint64Array) => bigint): bigint-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackfn | (previousValue: bigint, currentValue: bigint, currentIndex: number, array: BigUint64Array) =&gt; bigint | Yes |  |

<a id="reduce-1"></a>

## reduce

```TypeScript
reduce<U>(callbackfn: (previousValue: U, currentValue: bigint, currentIndex: number, array: BigUint64Array) => U, initialValue: U): U
```

Calls the specified callback function for all the elements in an array. The return value of the callback function is the accumulated result, and is provided as an argument in the next call to the callback function.

<!--Device-BigUint64Array-reduce<U>(callbackfn: (previousValue: U, currentValue: bigint, currentIndex: number, array: BigUint64Array) => U, initialValue: U): U--><!--Device-BigUint64Array-reduce<U>(callbackfn: (previousValue: U, currentValue: bigint, currentIndex: number, array: BigUint64Array) => U, initialValue: U): U-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackfn | (previousValue: U, currentValue: bigint, currentIndex: number, array: BigUint64Array) =&gt; U | Yes |  |
| initialValue | U | Yes |  |

## reduceRight

```TypeScript
reduceRight(callbackfn: (previousValue: bigint, currentValue: bigint, currentIndex: number, array: BigUint64Array) => bigint): bigint
```

Calls the specified callback function for all the elements in an array, in descending order. The return value of the callback function is the accumulated result, and is provided as an argument in the next call to the callback function.

<!--Device-BigUint64Array-reduceRight(callbackfn: (previousValue: bigint, currentValue: bigint, currentIndex: number, array: BigUint64Array) => bigint): bigint--><!--Device-BigUint64Array-reduceRight(callbackfn: (previousValue: bigint, currentValue: bigint, currentIndex: number, array: BigUint64Array) => bigint): bigint-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackfn | (previousValue: bigint, currentValue: bigint, currentIndex: number, array: BigUint64Array) =&gt; bigint | Yes |  |

<a id="reduceright-1"></a>

## reduceRight

```TypeScript
reduceRight<U>(callbackfn: (previousValue: U, currentValue: bigint, currentIndex: number, array: BigUint64Array) => U, initialValue: U): U
```

Calls the specified callback function for all the elements in an array, in descending order. The return value of the callback function is the accumulated result, and is provided as an argument in the next call to the callback function.

<!--Device-BigUint64Array-reduceRight<U>(callbackfn: (previousValue: U, currentValue: bigint, currentIndex: number, array: BigUint64Array) => U, initialValue: U): U--><!--Device-BigUint64Array-reduceRight<U>(callbackfn: (previousValue: U, currentValue: bigint, currentIndex: number, array: BigUint64Array) => U, initialValue: U): U-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackfn | (previousValue: U, currentValue: bigint, currentIndex: number, array: BigUint64Array) =&gt; U | Yes |  |
| initialValue | U | Yes |  |

## reverse

```TypeScript
reverse(): this
```

Reverses the elements in the array.

<!--Device-BigUint64Array-reverse(): this--><!--Device-BigUint64Array-reverse(): this-End-->

## set

```TypeScript
set(array: ArrayLike<bigint>, offset?: number): void
```

Sets a value or an array of values.

<!--Device-BigUint64Array-set(array: ArrayLike<bigint>, offset?: number): void--><!--Device-BigUint64Array-set(array: ArrayLike<bigint>, offset?: number): void-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| array | ArrayLike&lt;bigint&gt; | Yes |  |
| offset | number | No |  |

## slice

```TypeScript
slice(start?: number, end?: number): BigUint64Array
```

Returns a section of an array.

<!--Device-BigUint64Array-slice(start?: number, end?: number): BigUint64Array--><!--Device-BigUint64Array-slice(start?: number, end?: number): BigUint64Array-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | No |  |
| end | number | No |  |

## some

```TypeScript
some(predicate: (value: bigint, index: number, array: BigUint64Array) => boolean, thisArg?: any): boolean
```

Determines whether the specified callback function returns true for any element of an array.

<!--Device-BigUint64Array-some(predicate: (value: bigint, index: number, array: BigUint64Array) => boolean, thisArg?: any): boolean--><!--Device-BigUint64Array-some(predicate: (value: bigint, index: number, array: BigUint64Array) => boolean, thisArg?: any): boolean-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | (value: bigint, index: number, array: BigUint64Array) =&gt; boolean | Yes |  |
| thisArg | any | No |  |

## sort

```TypeScript
sort(compareFn?: (a: bigint, b: bigint) => number | bigint): this
```

Sorts the array.

<!--Device-BigUint64Array-sort(compareFn?: (a: bigint, b: bigint) => number | bigint): this--><!--Device-BigUint64Array-sort(compareFn?: (a: bigint, b: bigint) => number | bigint): this-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| compareFn | (a: bigint, b: bigint) =&gt; number &#124; bigint | No |  |

## subarray

```TypeScript
subarray(begin?: number, end?: number): BigUint64Array
```

Gets a new BigUint64Array view of the ArrayBuffer store for this array, referencing the elements at begin, inclusive, up to end, exclusive.

<!--Device-BigUint64Array-subarray(begin?: number, end?: number): BigUint64Array--><!--Device-BigUint64Array-subarray(begin?: number, end?: number): BigUint64Array-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| begin | number | No |  |
| end | number | No |  |

## toLocaleString

```TypeScript
toLocaleString(): string
```

Converts the array to a string by using the current locale.

<!--Device-BigUint64Array-toLocaleString(): string--><!--Device-BigUint64Array-toLocaleString(): string-End-->

## toString

```TypeScript
toString(): string
```

Returns a string representation of the array.

<!--Device-BigUint64Array-toString(): string--><!--Device-BigUint64Array-toString(): string-End-->

## valueOf

```TypeScript
valueOf(): BigUint64Array
```

Returns the primitive value of the specified object.

<!--Device-BigUint64Array-valueOf(): BigUint64Array--><!--Device-BigUint64Array-valueOf(): BigUint64Array-End-->

## values

```TypeScript
values(): IterableIterator<bigint>
```

Yields each value in the array.

<!--Device-BigUint64Array-values(): IterableIterator<bigint>--><!--Device-BigUint64Array-values(): IterableIterator<bigint>-End-->

## [index: number]

```TypeScript
[index: number]: bigint
```

**Type:** bigint

## [Symbol.toStringTag]

```TypeScript
readonly [Symbol.toStringTag]: "BigUint64Array"
```

**Type:** "BigUint64Array"

## buffer

```TypeScript
readonly buffer: ArrayBufferLike
```

The ArrayBuffer instance referenced by the array.

**Type:** [ArrayBufferLike](arkts-arraybufferlike-t.md)

<!--Device-BigUint64Array-readonly buffer: ArrayBufferLike--><!--Device-BigUint64Array-readonly buffer: ArrayBufferLike-End-->

## byteLength

```TypeScript
readonly byteLength: number
```

The length in bytes of the array.

**Type:** number

<!--Device-BigUint64Array-readonly byteLength: number--><!--Device-BigUint64Array-readonly byteLength: number-End-->

## byteOffset

```TypeScript
readonly byteOffset: number
```

The offset in bytes of the array.

**Type:** number

<!--Device-BigUint64Array-readonly byteOffset: number--><!--Device-BigUint64Array-readonly byteOffset: number-End-->

## BYTES_PER_ELEMENT

```TypeScript
readonly BYTES_PER_ELEMENT: number
```

The size in bytes of each element in the array.

**Type:** number

<!--Device-BigUint64Array-readonly BYTES_PER_ELEMENT: number--><!--Device-BigUint64Array-readonly BYTES_PER_ELEMENT: number-End-->

## length

```TypeScript
readonly length: number
```

The length of the array.

**Type:** number

<!--Device-BigUint64Array-readonly length: number--><!--Device-BigUint64Array-readonly length: number-End-->
