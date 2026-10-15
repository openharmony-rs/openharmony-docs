# DateConstructor

```TypeScript
interface DateConstructor
```

## Modules to Import

```TypeScript
```

## [[Call]]

```TypeScript
(): string
```

<a id="construct1"></a>

## [[Construct]]

```TypeScript
new(): Date
```

<a id="construct2"></a>

## [[Construct]]

```TypeScript
new(value: number | string): Date
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string | Yes |  |

<a id="construct3"></a>

## [[Construct]]

```TypeScript
new(year: number, monthIndex: number, date?: number, hours?: number, minutes?: number, seconds?: number, ms?: number): Date
```

Creates a new Date.

<!--Device-DateConstructor-new(year: number, monthIndex: number, date?: number, hours?: number, minutes?: number, seconds?: number, ms?: number): Date--><!--Device-DateConstructor-new(year: number, monthIndex: number, date?: number, hours?: number, minutes?: number, seconds?: number, ms?: number): Date-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| year | number | Yes |  |
| monthIndex | number | Yes |  |
| date | number | No |  |
| hours | number | No |  |
| minutes | number | No |  |
| seconds | number | No |  |
| ms | number | No |  |

## now

```TypeScript
now(): number
```

Returns the number of milliseconds elapsed since midnight, January 1, 1970 Universal Coordinated Time (UTC).

<!--Device-DateConstructor-now(): number--><!--Device-DateConstructor-now(): number-End-->

## parse

```TypeScript
parse(s: string): number
```

Parses a string containing a date, and returns the number of milliseconds between that date and midnight, January 1, 1970.

<!--Device-DateConstructor-parse(s: string): number--><!--Device-DateConstructor-parse(s: string): number-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| s | string | Yes |  |

## UTC

```TypeScript
UTC(year: number, monthIndex: number, date?: number, hours?: number, minutes?: number, seconds?: number, ms?: number): number
```

Returns the number of milliseconds between midnight, January 1, 1970 Universal Coordinated Time (UTC) (or GMT) and the specified date.

<!--Device-DateConstructor-UTC(year: number, monthIndex: number, date?: number, hours?: number, minutes?: number, seconds?: number, ms?: number): number--><!--Device-DateConstructor-UTC(year: number, monthIndex: number, date?: number, hours?: number, minutes?: number, seconds?: number, ms?: number): number-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| year | number | Yes |  |
| monthIndex | number | Yes |  |
| date | number | No |  |
| hours | number | No |  |
| minutes | number | No |  |
| seconds | number | No |  |
| ms | number | No |  |

## prototype

```TypeScript
readonly prototype: Date
```

**Type:** Date
