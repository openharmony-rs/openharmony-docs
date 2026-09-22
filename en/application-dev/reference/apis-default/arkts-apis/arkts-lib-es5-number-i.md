# Number

```TypeScript
interface Number
```

## Modules to Import

```TypeScript
```

## toExponential

```TypeScript
toExponential(fractionDigits?: number): string
```

Returns a string containing a number represented in exponential notation.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fractionDigits | number | No |  |

## toFixed

```TypeScript
toFixed(fractionDigits?: number): string
```

Returns a string representing a number in fixed-point notation.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fractionDigits | number | No |  |

## toLocaleString

```TypeScript
toLocaleString(locales?: string[], options?: Intl.NumberFormatOptions): string
```

Converts a number to a string by using the current or specified locale.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locales | string[] | No |  |
| options | [Intl.NumberFormatOptions](arkts-intl-numberformatoptions-i.md) | No |  |

## toPrecision

```TypeScript
toPrecision(precision?: number): string
```

Returns a string containing a number represented either in exponential or fixed-point notation with a specified number of digits.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| precision | number | No |  |

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
valueOf(): number
```

Returns the primitive value of the specified object.
