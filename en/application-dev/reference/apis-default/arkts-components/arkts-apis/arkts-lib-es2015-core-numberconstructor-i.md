# NumberConstructor

```TypeScript
interface NumberConstructor
```

## Modules to Import

```TypeScript
```

## isFinite

```TypeScript
isFinite(number: unknown): boolean
```

Returns true if passed value is finite. Unlike the global isFinite, Number.isFinite doesn't forcibly convert the parameter to a number. Only finite values of the type number, result in true.

<!--Device-NumberConstructor-isFinite(number: unknown): boolean--><!--Device-NumberConstructor-isFinite(number: unknown): boolean-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| number | unknown | Yes |  |

## isInteger

```TypeScript
isInteger(number: unknown): boolean
```

Returns true if the value passed is an integer, false otherwise.

<!--Device-NumberConstructor-isInteger(number: unknown): boolean--><!--Device-NumberConstructor-isInteger(number: unknown): boolean-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| number | unknown | Yes |  |

## isNaN

```TypeScript
isNaN(number: unknown): boolean
```

Returns a Boolean value that indicates whether a value is the reserved value NaN (not a number). Unlike the global isNaN(), Number.isNaN() doesn't forcefully convert the parameter to a number. Only values of the type number, that are also NaN, result in true.

<!--Device-NumberConstructor-isNaN(number: unknown): boolean--><!--Device-NumberConstructor-isNaN(number: unknown): boolean-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| number | unknown | Yes |  |

## isSafeInteger

```TypeScript
isSafeInteger(number: unknown): boolean
```

Returns true if the value passed is a safe integer.

<!--Device-NumberConstructor-isSafeInteger(number: unknown): boolean--><!--Device-NumberConstructor-isSafeInteger(number: unknown): boolean-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| number | unknown | Yes |  |

## parseFloat

```TypeScript
parseFloat(string: string): number
```

Converts a string to a floating-point number.

<!--Device-NumberConstructor-parseFloat(string: string): number--><!--Device-NumberConstructor-parseFloat(string: string): number-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| string | string | Yes |  |

## parseInt

```TypeScript
parseInt(string: string, radix?: number): number
```

Converts A string to an integer.

<!--Device-NumberConstructor-parseInt(string: string, radix?: number): number--><!--Device-NumberConstructor-parseInt(string: string, radix?: number): number-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| string | string | Yes |  |
| radix | number | No |  |

## EPSILON

```TypeScript
readonly EPSILON: number
```

The value of Number.EPSILON is the difference between 1 and the smallest value greater than 1 that is representable as a Number value, which is approximately: 2.2204460492503130808472633361816 x 10‍−‍16.

**Type:** number

<!--Device-NumberConstructor-readonly EPSILON: number--><!--Device-NumberConstructor-readonly EPSILON: number-End-->

## MAX_SAFE_INTEGER

```TypeScript
readonly MAX_SAFE_INTEGER: number
```

The value of the largest integer n such that n and n + 1 are both exactly representable as a Number value. The value of Number.MAX_SAFE_INTEGER is 9007199254740991 2^53 − 1.

**Type:** number

<!--Device-NumberConstructor-readonly MAX_SAFE_INTEGER: number--><!--Device-NumberConstructor-readonly MAX_SAFE_INTEGER: number-End-->

## MIN_SAFE_INTEGER

```TypeScript
readonly MIN_SAFE_INTEGER: number
```

The value of the smallest integer n such that n and n − 1 are both exactly representable as a Number value. The value of Number.MIN_SAFE_INTEGER is −9007199254740991 (−(2^53 − 1)).

**Type:** number

<!--Device-NumberConstructor-readonly MIN_SAFE_INTEGER: number--><!--Device-NumberConstructor-readonly MIN_SAFE_INTEGER: number-End-->
