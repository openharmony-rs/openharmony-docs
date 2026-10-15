# BigUint64ArrayConstructor

```TypeScript
interface BigUint64ArrayConstructor
```

## Modules to Import

```TypeScript
```

<a id="construct1"></a>

## [[Construct]]

```TypeScript
new(length?: number): BigUint64Array
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| length | number | No |  |

<a id="construct2"></a>

## [[Construct]]

```TypeScript
new(array: Iterable<bigint>): BigUint64Array
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| array | Iterable&lt;bigint&gt; | Yes |  |

<a id="construct3"></a>

## [[Construct]]

```TypeScript
new(buffer: ArrayBufferLike, byteOffset?: number, length?: number): BigUint64Array
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
from(arrayLike: ArrayLike<bigint>): BigUint64Array
```

Creates an array from an array-like or iterable object.

<!--Device-BigUint64ArrayConstructor-from(arrayLike: ArrayLike<bigint>): BigUint64Array--><!--Device-BigUint64ArrayConstructor-from(arrayLike: ArrayLike<bigint>): BigUint64Array-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLike | ArrayLike&lt;bigint&gt; | Yes |  |

<a id="from2"></a>

## from

```TypeScript
from<U>(arrayLike: ArrayLike<U>, mapfn: (v: U, k: number) => bigint, thisArg?: any): BigUint64Array
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLike | ArrayLike&lt;U&gt; | Yes |  |
| mapfn | (v: U, k: number) =&gt; bigint | Yes |  |
| thisArg | any | No |  |

## of

```TypeScript
of(...items: bigint[]): BigUint64Array
```

Returns a new array from a set of elements.

<!--Device-BigUint64ArrayConstructor-of(...items: bigint[]): BigUint64Array--><!--Device-BigUint64ArrayConstructor-of(...items: bigint[]): BigUint64Array-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| items | bigint[] | Yes |  |

## BYTES_PER_ELEMENT

```TypeScript
readonly BYTES_PER_ELEMENT: number
```

The size in bytes of each element in the array.

**Type:** number

<!--Device-BigUint64ArrayConstructor-readonly BYTES_PER_ELEMENT: number--><!--Device-BigUint64ArrayConstructor-readonly BYTES_PER_ELEMENT: number-End-->

## prototype

```TypeScript
readonly prototype: BigUint64Array
```

**Type:** [BigUint64Array](arkts-lib-es2020-bigint-biguint64array-i.md)
