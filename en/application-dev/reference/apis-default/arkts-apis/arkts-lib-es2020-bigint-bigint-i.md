# BigInt

```TypeScript
interface BigInt
```

## Modules to Import

```TypeScript
```

## toLocaleString

```TypeScript
toLocaleString(locales?: Intl.LocalesArgument, options?: BigIntToLocaleStringOptions): string
```

Returns a string representation appropriate to the host environment's current locale.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locales | [Intl.LocalesArgument](arkts-intl-localesargument-t.md) | No |  |
| options | [BigIntToLocaleStringOptions](arkts-lib-es2020-bigint-biginttolocalestringoptions-i.md) | No |  |

## toString

```TypeScript
toString(radix?: number): string
```

Returns a string representation of an object.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| radix | number | No |  |

## valueOf

```TypeScript
valueOf(): bigint
```

Returns the primitive value of the specified object.

## [Symbol.toStringTag]

```TypeScript
readonly [Symbol.toStringTag]: "BigInt"
```

**Type:** "BigInt"
