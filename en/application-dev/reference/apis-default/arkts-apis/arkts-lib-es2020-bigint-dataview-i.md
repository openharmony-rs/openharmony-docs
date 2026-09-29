# DataView

```TypeScript
interface DataView
```

## Modules to Import

```TypeScript
```

## getBigInt64

```TypeScript
getBigInt64(byteOffset: number, littleEndian?: boolean): bigint
```

Gets the BigInt64 value at the specified byte offset from the start of the view. There is no alignment constraint; multi-byte values may be fetched from any offset.

<!--Device-DataView-getBigInt64(byteOffset: number, littleEndian?: boolean): bigint--><!--Device-DataView-getBigInt64(byteOffset: number, littleEndian?: boolean): bigint-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| byteOffset | number | Yes |  |
| littleEndian | boolean | No |  |

## getBigUint64

```TypeScript
getBigUint64(byteOffset: number, littleEndian?: boolean): bigint
```

Gets the BigUint64 value at the specified byte offset from the start of the view. There is no alignment constraint; multi-byte values may be fetched from any offset.

<!--Device-DataView-getBigUint64(byteOffset: number, littleEndian?: boolean): bigint--><!--Device-DataView-getBigUint64(byteOffset: number, littleEndian?: boolean): bigint-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| byteOffset | number | Yes |  |
| littleEndian | boolean | No |  |

## setBigInt64

```TypeScript
setBigInt64(byteOffset: number, value: bigint, littleEndian?: boolean): void
```

Stores a BigInt64 value at the specified byte offset from the start of the view.

<!--Device-DataView-setBigInt64(byteOffset: number, value: bigint, littleEndian?: boolean): void--><!--Device-DataView-setBigInt64(byteOffset: number, value: bigint, littleEndian?: boolean): void-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| byteOffset | number | Yes |  |
| value | bigint | Yes |  |
| littleEndian | boolean | No |  |

## setBigUint64

```TypeScript
setBigUint64(byteOffset: number, value: bigint, littleEndian?: boolean): void
```

Stores a BigUint64 value at the specified byte offset from the start of the view.

<!--Device-DataView-setBigUint64(byteOffset: number, value: bigint, littleEndian?: boolean): void--><!--Device-DataView-setBigUint64(byteOffset: number, value: bigint, littleEndian?: boolean): void-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| byteOffset | number | Yes |  |
| value | bigint | Yes |  |
| littleEndian | boolean | No |  |
