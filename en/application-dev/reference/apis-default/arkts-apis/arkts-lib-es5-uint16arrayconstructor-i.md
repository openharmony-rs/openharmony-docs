# Uint16ArrayConstructor

```TypeScript
interface Uint16ArrayConstructor
```

## Modules to Import

```TypeScript
```

<a id="construct1"></a>

## [[Construct]]

```TypeScript
new(length: number): Uint16Array
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| length | number | Yes |  |

<a id="construct2"></a>

## [[Construct]]

```TypeScript
new(array: ArrayLike<number> | ArrayBufferLike): Uint16Array
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| array | ArrayLike&lt;number&gt; &#124; [ArrayBufferLike](arkts-arraybufferlike-t.md) | Yes |  |

<a id="construct3"></a>

## [[Construct]]

```TypeScript
new(buffer: ArrayBufferLike, byteOffset?: number, length?: number): Uint16Array
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
from(arrayLike: ArrayLike<number>): Uint16Array
```

Creates an array from an array-like or iterable object.

<!--Device-Uint16ArrayConstructor-from(arrayLike: ArrayLike<number>): Uint16Array--><!--Device-Uint16ArrayConstructor-from(arrayLike: ArrayLike<number>): Uint16Array-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLike | ArrayLike&lt;number&gt; | Yes |  |

<a id="from2"></a>

## from

```TypeScript
from<T>(arrayLike: ArrayLike<T>, mapfn: (v: T, k: number) => number, thisArg?: any): Uint16Array
```

Creates an array from an array-like or iterable object.

<!--Device-Uint16ArrayConstructor-from<T>(arrayLike: ArrayLike<T>, mapfn: (v: T, k: number) => number, thisArg?: any): Uint16Array--><!--Device-Uint16ArrayConstructor-from<T>(arrayLike: ArrayLike<T>, mapfn: (v: T, k: number) => number, thisArg?: any): Uint16Array-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLike | ArrayLike&lt;T&gt; | Yes |  |
| mapfn | (v: T, k: number) =&gt; number | Yes |  |
| thisArg | any | No |  |

## of

```TypeScript
of(...items: number[]): Uint16Array
```

Returns a new array from a set of elements.

<!--Device-Uint16ArrayConstructor-of(...items: number[]): Uint16Array--><!--Device-Uint16ArrayConstructor-of(...items: number[]): Uint16Array-End-->

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

<!--Device-Uint16ArrayConstructor-readonly BYTES_PER_ELEMENT: number--><!--Device-Uint16ArrayConstructor-readonly BYTES_PER_ELEMENT: number-End-->

## prototype

```TypeScript
readonly prototype: Uint16Array
```

**Type:** Uint16Array
