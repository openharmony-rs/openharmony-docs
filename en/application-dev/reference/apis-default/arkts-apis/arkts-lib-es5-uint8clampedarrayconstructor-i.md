# Uint8ClampedArrayConstructor

```TypeScript
interface Uint8ClampedArrayConstructor
```

## Modules to Import

```TypeScript
```

## [[Construct]]

```TypeScript
new(length: number): Uint8ClampedArray
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| length | number | Yes |  |

<a id="construct-1"></a>

## [[Construct]]

```TypeScript
new(array: ArrayLike<number> | ArrayBufferLike): Uint8ClampedArray
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| array | ArrayLike&lt;number&gt; &#124; [ArrayBufferLike](arkts-arraybufferlike-t.md) | Yes |  |

<a id="construct-2"></a>

## [[Construct]]

```TypeScript
new(buffer: ArrayBufferLike, byteOffset?: number, length?: number): Uint8ClampedArray
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buffer | [ArrayBufferLike](arkts-arraybufferlike-t.md) | Yes |  |
| byteOffset | number | No |  |
| length | number | No |  |

## from

```TypeScript
from(arrayLike: ArrayLike<number>): Uint8ClampedArray
```

Creates an array from an array-like or iterable object.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLike | ArrayLike&lt;number&gt; | Yes |  |

<a id="from-1"></a>

## from

```TypeScript
from<T>(arrayLike: ArrayLike<T>, mapfn: (v: T, k: number) => number, thisArg?: any): Uint8ClampedArray
```

Creates an array from an array-like or iterable object.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLike | ArrayLike&lt;T&gt; | Yes |  |
| mapfn | (v: T, k: number) =&gt; number | Yes |  |
| thisArg | any | No |  |

## of

```TypeScript
of(...items: number[]): Uint8ClampedArray
```

Returns a new array from a set of elements.

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

## prototype

```TypeScript
readonly prototype: Uint8ClampedArray
```

**Type:** [Uint8ClampedArray](arkts-lib-es5-uint8clampedarray-i.md)
