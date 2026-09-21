# BigIntConstructor

```TypeScript
interface BigIntConstructor
```

## Modules to Import

```TypeScript
```

## [[Call]]

```TypeScript
(value: bigint | boolean | number | string): bigint
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | bigint &#124; boolean &#124; number &#124; string | Yes |  |

## asIntN

```TypeScript
asIntN(bits: number, number: bigint): bigint
```

Interprets the low bits of a BigInt as a 2's-complement signed integer. All higher bits are discarded.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bits | number | Yes |  |
| int | bigint | Yes |  |

## asUintN

```TypeScript
asUintN(bits: number, number: bigint): bigint
```

Interprets the low bits of a BigInt as an unsigned integer. All higher bits are discarded.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bits | number | Yes |  |
| int | bigint | Yes |  |

## prototype

```TypeScript
readonly prototype: BigInt
```

**Type:** [BigInt](arkts-lib-es2020-bigint-bigint-i.md)
