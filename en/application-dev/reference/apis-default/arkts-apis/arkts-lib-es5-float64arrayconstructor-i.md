# Float64ArrayConstructor

```TypeScript
interface Float64ArrayConstructor
```

## Modules to Import

```TypeScript
```

<a id="construct1"></a>

## [[Construct]]

```TypeScript
new(length: number): Float64Array
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| length | number | Yes |  |

<a id="construct2"></a>

## [[Construct]]

```TypeScript
new(array: ArrayLike<number> | ArrayBufferLike): Float64Array
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| array | ArrayLike&lt;number&gt; &#124; [ArrayBufferLike](arkts-arraybufferlike-t.md) | Yes |  |

<a id="construct3"></a>

## [[Construct]]

```TypeScript
new(buffer: ArrayBufferLike, byteOffset?: number, length?: number): Float64Array
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buffer | [ArrayBufferLike](arkts-arraybufferlike-t.md) | Yes |  |
| byteOffset | number | No |  |
| length | number | No |  |

<a id="from1"></a>

## from

```TypeScript
from(arrayLike: ArrayLike<number>): Float64Array
```

Creates an array from an array-like or iterable object.

<!--Device-Float64ArrayConstructor-from(arrayLike: ArrayLike<number>): Float64Array--><!--Device-Float64ArrayConstructor-from(arrayLike: ArrayLike<number>): Float64Array-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLike | ArrayLike&lt;number&gt; | Yes |  |

<a id="from2"></a>

## from

```TypeScript
from<T>(arrayLike: ArrayLike<T>, mapfn: (v: T, k: number) => number, thisArg?: any): Float64Array
```

Creates an array from an array-like or iterable object.

<!--Device-Float64ArrayConstructor-from<T>(arrayLike: ArrayLike<T>, mapfn: (v: T, k: number) => number, thisArg?: any): Float64Array--><!--Device-Float64ArrayConstructor-from<T>(arrayLike: ArrayLike<T>, mapfn: (v: T, k: number) => number, thisArg?: any): Float64Array-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLike | ArrayLike&lt;T&gt; | Yes |  |
| mapfn | (v: T, k: number) =&gt; number | Yes |  |
| thisArg | any | No |  |

## of

```TypeScript
of(...items: number[]): Float64Array
```

Returns a new array from a set of elements.

<!--Device-Float64ArrayConstructor-of(...items: number[]): Float64Array--><!--Device-Float64ArrayConstructor-of(...items: number[]): Float64Array-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| items | number[] | Yes |  |

## BYTES_PER_ELEMENT

```TypeScript
readonly BYTES_PER_ELEMENT: number
```

The size in bytes of each element in the array.

**Type:** number

<!--Device-Float64ArrayConstructor-readonly BYTES_PER_ELEMENT: number--><!--Device-Float64ArrayConstructor-readonly BYTES_PER_ELEMENT: number-End-->

## prototype

```TypeScript
readonly prototype: Float64Array
```

**Type:** Float64Array
