# Int32ArrayConstructor

```TypeScript
interface Int32ArrayConstructor
```

## Modules to Import

```TypeScript
```

<a id="construct1"></a>

## [[Construct]]

```TypeScript
new(length: number): Int32Array
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| length | number | Yes |  |

<a id="construct2"></a>

## [[Construct]]

```TypeScript
new(array: ArrayLike<number> | ArrayBufferLike): Int32Array
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| array | ArrayLike&lt;number&gt; &#124; [ArrayBufferLike](arkts-arraybufferlike-t.md) | Yes |  |

<a id="construct3"></a>

## [[Construct]]

```TypeScript
new(buffer: ArrayBufferLike, byteOffset?: number, length?: number): Int32Array
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
from(arrayLike: ArrayLike<number>): Int32Array
```

Creates an array from an array-like or iterable object.

<!--Device-Int32ArrayConstructor-from(arrayLike: ArrayLike<number>): Int32Array--><!--Device-Int32ArrayConstructor-from(arrayLike: ArrayLike<number>): Int32Array-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLike | ArrayLike&lt;number&gt; | Yes |  |

<a id="from2"></a>

## from

```TypeScript
from<T>(arrayLike: ArrayLike<T>, mapfn: (v: T, k: number) => number, thisArg?: any): Int32Array
```

Creates an array from an array-like or iterable object.

<!--Device-Int32ArrayConstructor-from<T>(arrayLike: ArrayLike<T>, mapfn: (v: T, k: number) => number, thisArg?: any): Int32Array--><!--Device-Int32ArrayConstructor-from<T>(arrayLike: ArrayLike<T>, mapfn: (v: T, k: number) => number, thisArg?: any): Int32Array-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLike | ArrayLike&lt;T&gt; | Yes |  |
| mapfn | (v: T, k: number) =&gt; number | Yes |  |
| thisArg | any | No |  |

## of

```TypeScript
of(...items: number[]): Int32Array
```

Returns a new array from a set of elements.

<!--Device-Int32ArrayConstructor-of(...items: number[]): Int32Array--><!--Device-Int32ArrayConstructor-of(...items: number[]): Int32Array-End-->

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

<!--Device-Int32ArrayConstructor-readonly BYTES_PER_ELEMENT: number--><!--Device-Int32ArrayConstructor-readonly BYTES_PER_ELEMENT: number-End-->

## prototype

```TypeScript
readonly prototype: Int32Array
```

**Type:** Int32Array
