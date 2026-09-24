# Float32Array

```TypeScript
interface Float32Array
```

A typed array of 32-bit float values. The contents are initialized to 0. If the requested number of bytes could not be allocated an exception is raised.

## Modules to Import

```TypeScript
```

## copyWithin

```TypeScript
copyWithin(target: number, start: number, end?: number): this
```

Returns the this object after copying a section of the array identified by start and end to the same array starting at position target

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | number | Yes |  |
| start | number | Yes |  |
| end | number | No |  |

## every

```TypeScript
every(predicate: (value: number, index: number, array: Float32Array) => unknown, thisArg?: any): boolean
```

Determines whether all the members of an array satisfy the specified test.

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | (value: number, index: number, array: Float32Array) =&gt; unknown | Yes |  |
| thisArg | any | No |  |

## fill

```TypeScript
fill(value: number, start?: number, end?: number): this
```

Changes all array elements from `start` to `end` index to a static `value` and returns the modified array

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes |  |
| start | number | No |  |
| end | number | No |  |

## filter

```TypeScript
filter(predicate: (value: number, index: number, array: Float32Array) => any, thisArg?: any): Float32Array
```

Returns the elements of an array that meet the condition specified in a callback function.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | (value: number, index: number, array: Float32Array) =&gt; any | Yes |  |
| thisArg | any | No |  |

## find

```TypeScript
find(predicate: (value: number, index: number, obj: Float32Array) => boolean, thisArg?: any): number | undefined
```

Returns the value of the first element in the array where predicate is true, and undefined otherwise.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | (value: number, index: number, obj: Float32Array) =&gt; boolean | Yes |  |
| thisArg | any | No |  |

## findIndex

```TypeScript
findIndex(predicate: (value: number, index: number, obj: Float32Array) => boolean, thisArg?: any): number
```

Returns the index of the first element in the array where predicate is true, and -1 otherwise.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | (value: number, index: number, obj: Float32Array) =&gt; boolean | Yes |  |
| thisArg | any | No |  |

## forEach

```TypeScript
forEach(callbackfn: (value: number, index: number, array: Float32Array) => void, thisArg?: any): void
```

Performs the specified action for each element in an array.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackfn | (value: number, index: number, array: Float32Array) =&gt; void | Yes |  |
| thisArg | any | No |  |

## indexOf

```TypeScript
indexOf(searchElement: number, fromIndex?: number): number
```

Returns the index of the first occurrence of a value in an array.

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

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| separator | string | No |  |

## lastIndexOf

```TypeScript
lastIndexOf(searchElement: number, fromIndex?: number): number
```

Returns the index of the last occurrence of a value in an array.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchElement | number | Yes |  |
| fromIndex | number | No |  |

## map

```TypeScript
map(callbackfn: (value: number, index: number, array: Float32Array) => number, thisArg?: any): Float32Array
```

Calls a defined callback function on each element of an array, and returns an array that contains the results.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackfn | (value: number, index: number, array: Float32Array) =&gt; number | Yes |  |
| thisArg | any | No |  |

## reduce

```TypeScript
reduce(callbackfn: (previousValue: number, currentValue: number, currentIndex: number, array: Float32Array) => number): number
```

Calls the specified callback function for all the elements in an array. The return value of the callback function is the accumulated result, and is provided as an argument in the next call to the callback function.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackfn | (previousValue: number, currentValue: number, currentIndex: number, array: Float32Array) =&gt; number | Yes |  |

<a id="reduce-1"></a>

## reduce

```TypeScript
reduce(callbackfn: (previousValue: number, currentValue: number, currentIndex: number, array: Float32Array) => number, initialValue: number): number
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackfn | (previousValue: number, currentValue: number, currentIndex: number, array: Float32Array) =&gt; number | Yes |  |
| initialValue | number | Yes |  |

<a id="reduce-2"></a>

## reduce

```TypeScript
reduce<U>(callbackfn: (previousValue: U, currentValue: number, currentIndex: number, array: Float32Array) => U, initialValue: U): U
```

Calls the specified callback function for all the elements in an array. The return value of the callback function is the accumulated result, and is provided as an argument in the next call to the callback function.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackfn | (previousValue: U, currentValue: number, currentIndex: number, array: Float32Array) =&gt; U | Yes |  |
| initialValue | U | Yes |  |

## reduceRight

```TypeScript
reduceRight(callbackfn: (previousValue: number, currentValue: number, currentIndex: number, array: Float32Array) => number): number
```

Calls the specified callback function for all the elements in an array, in descending order. The return value of the callback function is the accumulated result, and is provided as an argument in the next call to the callback function.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackfn | (previousValue: number, currentValue: number, currentIndex: number, array: Float32Array) =&gt; number | Yes |  |

<a id="reduceright-1"></a>

## reduceRight

```TypeScript
reduceRight(callbackfn: (previousValue: number, currentValue: number, currentIndex: number, array: Float32Array) => number, initialValue: number): number
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackfn | (previousValue: number, currentValue: number, currentIndex: number, array: Float32Array) =&gt; number | Yes |  |
| initialValue | number | Yes |  |

<a id="reduceright-2"></a>

## reduceRight

```TypeScript
reduceRight<U>(callbackfn: (previousValue: U, currentValue: number, currentIndex: number, array: Float32Array) => U, initialValue: U): U
```

Calls the specified callback function for all the elements in an array, in descending order. The return value of the callback function is the accumulated result, and is provided as an argument in the next call to the callback function.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackfn | (previousValue: U, currentValue: number, currentIndex: number, array: Float32Array) =&gt; U | Yes |  |
| initialValue | U | Yes |  |

## reverse

```TypeScript
reverse(): Float32Array
```

Reverses the elements in an Array.

## set

```TypeScript
set(array: ArrayLike<number>, offset?: number): void
```

Sets a value or an array of values.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| array | ArrayLike&lt;number&gt; | Yes |  |
| offset | number | No |  |

## slice

```TypeScript
slice(start?: number, end?: number): Float32Array
```

Returns a section of an array.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | No |  |
| end | number | No |  |

## some

```TypeScript
some(predicate: (value: number, index: number, array: Float32Array) => unknown, thisArg?: any): boolean
```

Determines whether the specified callback function returns true for any element of an array.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | (value: number, index: number, array: Float32Array) =&gt; unknown | Yes |  |
| thisArg | any | No |  |

## sort

```TypeScript
sort(compareFn?: (a: number, b: number) => number): this
```

Sorts an array.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| compareFn | (a: number, b: number) =&gt; number | No |  |

## subarray

```TypeScript
subarray(begin?: number, end?: number): Float32Array
```

Gets a new Float32Array view of the ArrayBuffer store for this array, referencing the elements at begin, inclusive, up to end, exclusive.

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

## toString

```TypeScript
toString(): string
```

Returns a string representation of an array.

## valueOf

```TypeScript
valueOf(): Float32Array
```

Returns the primitive value of the specified object.

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

## byteLength

```TypeScript
readonly byteLength: number
```

The length in bytes of the array.

**Type:** number

## byteOffset

```TypeScript
readonly byteOffset: number
```

The offset in bytes of the array.

**Type:** number

## BYTES_PER_ELEMENT

```TypeScript
readonly BYTES_PER_ELEMENT: number
```

The size in bytes of each element in the array.

**Type:** number

## length

```TypeScript
readonly length: number
```

The length of the array.

**Type:** number
