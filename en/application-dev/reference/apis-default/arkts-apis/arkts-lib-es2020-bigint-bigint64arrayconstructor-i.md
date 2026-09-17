# BigInt64ArrayConstructor

## Modules to Import

```TypeScript
```

## [[Construct]]

```TypeScript
new(length?: number): BigInt64Array
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| length | number | No |  |

## [[Construct]]

```TypeScript
new(array: Iterable<bigint>): BigInt64Array
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| array | Iterable&lt;bigint&gt; | Yes |  |

## [[Construct]]

```TypeScript
new(buffer: ArrayBufferLike, byteOffset?: number, length?: number): BigInt64Array
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buffer | [ArrayBufferLike](arkts-arraybufferlike-t.md) | Yes |  |
| byteOffset | number | No |  |
| length | number | No |  |

## from

```TypeScript
from(arrayLike: ArrayLike<bigint>): BigInt64Array
```

Creates an array from an array-like or iterable object.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLike | ArrayLike&lt;bigint&gt; | Yes |  |

## from

```TypeScript
from<U>(arrayLike: ArrayLike<U>, mapfn: (v: U, k: number) => bigint, thisArg?: any): BigInt64Array
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLike | ArrayLike&lt;U&gt; | Yes |  |
| mapfn | (v: U, k: number) =&gt; bigint | Yes |  |
| thisArg | any | No |  |

## of

```TypeScript
of(...items: bigint[]): BigInt64Array
```

Returns a new array from a set of elements.

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

## prototype

```TypeScript
readonly prototype: BigInt64Array
```

**Type:** [BigInt64Array](arkts-lib-es2020-bigint-bigint64array-i.md)
