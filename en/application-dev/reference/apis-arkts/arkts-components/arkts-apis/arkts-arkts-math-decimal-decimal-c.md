# Decimal

An arbitrary-precision Decimal type

**Since:** 12

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { Decimal } from '@kit.ArkTS';
```

## abs

```TypeScript
abs(): Decimal
```

Return a new Decimal whose value is the absolute value of this Decimal.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

## abs

```TypeScript
static abs(n: Value): Decimal
```

Return a new Decimal whose value is the absolute value of `n`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## acos

```TypeScript
acos(): Decimal
```

Return a new Decimal whose value is the arccosine (inverse cosine) in radians of the value of this Decimal.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200060](../errorcode-utils.md#10200060-precision-limit-is-exceeded) | Precision limit exceeded. |

## acos

```TypeScript
static acos(n: Value): Decimal
```

Return a new Decimal whose value is the arccosine in radians of `n`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-precision-limit-is-exceeded) | Precision limit exceeded. |

## acosh

```TypeScript
acosh(): Decimal
```

Return a new Decimal whose value is the inverse of the hyperbolic cosine in radians of the value of this Decimal.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200060](../errorcode-utils.md#10200060-precision-limit-is-exceeded) | Precision limit exceeded. |

## acosh

```TypeScript
static acosh(n: Value): Decimal
```

Return a new Decimal whose value is the inverse of the hyperbolic cosine of `n`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-precision-limit-is-exceeded) | Precision limit exceeded. |

## add

```TypeScript
add(n: Value): Decimal
```

Return a new Decimal whose value is the value of this Decimal plus `n`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## add

```TypeScript
static add(x: Value, y: Value): Decimal
```

Return a new Decimal whose value is the sum of `x` and `y`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |
| y | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## asin

```TypeScript
asin(): Decimal
```

Return a new Decimal whose value is the arcsine (inverse sine) in radians of the value of this Decimal.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200060](../errorcode-utils.md#10200060-precision-limit-is-exceeded) | Precision limit exceeded. |

## asin

```TypeScript
static asin(n: Value): Decimal
```

Return a new Decimal whose value is the arcsine in radians of `n`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-precision-limit-is-exceeded) | Precision limit exceeded. |

## asinh

```TypeScript
asinh(): Decimal
```

Return a new Decimal whose value is the inverse of the hyperbolic sine in radians of the value of this Decimal.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200060](../errorcode-utils.md#10200060-precision-limit-is-exceeded) | Precision limit exceeded. |

## asinh

```TypeScript
static asinh(n: Value): Decimal
```

Return a new Decimal whose value is the inverse of the hyperbolic sine of `n`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} A value in radians. |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-precision-limit-is-exceeded) | Precision limit exceeded. |

## atan

```TypeScript
atan(): Decimal
```

Return a new Decimal whose value is the arctangent (inverse tangent) in radians of the value of this Decimal.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200060](../errorcode-utils.md#10200060-precision-limit-is-exceeded) | Precision limit exceeded. |

## atan

```TypeScript
static atan(n: Value): Decimal
```

Return a new Decimal whose value is the arctangent in radians of `n`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-precision-limit-is-exceeded) | Precision limit exceeded. |

## atan2

```TypeScript
static atan2(y: Value, x: Value): Decimal
```

Return a new Decimal whose value is the arctangent in radians of `y/x` in the range -pi to pi (inclusive), rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| y | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} The y-coordinate. |
| x | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} The x-coordinate. |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-precision-limit-is-exceeded) | Precision limit exceeded. |

## atanh

```TypeScript
atanh(): Decimal
```

Return a new Decimal whose value is the inverse of the hyperbolic tangent in radians of the value of this Decimal.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200060](../errorcode-utils.md#10200060-precision-limit-is-exceeded) | Precision limit exceeded. |

## atanh

```TypeScript
static atanh(n: Value): Decimal
```

Return a new Decimal whose value is the inverse of the hyperbolic tangent of `n`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} A value in radians. |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-precision-limit-is-exceeded) | Precision limit exceeded. |

## cbrt

```TypeScript
cbrt(): Decimal
```

Return a new Decimal whose value is the cube root of the value of this Decimal, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

## cbrt

```TypeScript
static cbrt(n: Value): Decimal
```

Return a new Decimal whose value is the cube root of `n`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## ceil

```TypeScript
ceil(): Decimal
```

Return a new Decimal whose value is the value of this Decimal rounded to a whole number in the direction of positive Infinity.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

## ceil

```TypeScript
static ceil(n: Value): Decimal
```

Return a new Decimal whose value is `n` rounded to an integer using `ROUND_CEIL`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## clamp

```TypeScript
clamp(min: Value, max: Value): Decimal
```

Return a new Decimal whose value is the value of this Decimal clamped to the range delineated by `min` and `max`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| min | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |
| max | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of `min` is out of range. |

## clamp

```TypeScript
static clamp(n: Value, min: Value, max: Value): Decimal
```

Return a new Decimal whose value is `n` clamped to the range delineated by `min` and `max`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |
| min | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |
| max | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of `min` is out of range. |

## comparedTo

```TypeScript
comparedTo(n: Value): number
```

Return 1 if the value of this Decimal is greater than the value of `n`, -1 if the value of this Decimal is less than the value of `n`, 0 if they have the same value, NaN if the value of either Decimal is NaN.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| number | the number type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## constructor

```TypeScript
constructor(n: Value)
```

Return a new Decimal whose value is the absolute value of this Decimal.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## cos

```TypeScript
cos(): Decimal
```

Return a new Decimal whose value is the cosine of the value in radians of this Decimal.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

## cos

```TypeScript
static cos(n: Value): Decimal
```

Return a new Decimal whose value is the cosine of `n`, rounded to `precision` significant digits using rounding mode `rounding`

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} A value in radians. |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## cosh

```TypeScript
cosh(): Decimal
```

Return a new Decimal whose value is the hyperbolic cosine of the value in radians of this Decimal.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

## cosh

```TypeScript
static cosh(n: Value): Decimal
```

Return a new Decimal whose value is the hyperbolic cosine of `n`, rounded to precision significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} A value in radians. |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## decimalPlaces

```TypeScript
decimalPlaces(): number
```

Return the number of decimal places of the value of this Decimal.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | the number type |

## div

```TypeScript
div(n: Value): Decimal
```

Return a new Decimal whose value is the value of this Decimal divided by `n`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## div

```TypeScript
static div(x: Value, y: Value): Decimal
```

Return a new Decimal whose value is `x` divided by `y`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |
| y | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## dividedToIntegerBy

```TypeScript
dividedToIntegerBy(n: Value): Decimal
```

Return a new Decimal whose value is the integer part of dividing the value of this Decimal by the value of `n`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## equals

```TypeScript
equals(n: Value): boolean
```

Return true if the value of this Decimal is equal to the value of `n`, otherwise return false.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | the boolean type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## exp

```TypeScript
exp(): Decimal
```

Return a new Decimal whose value is the natural exponential of the value of this Decimal, i.e. the base e raised to the power the value of this Decimal, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200060](../errorcode-utils.md#10200060-precision-limit-is-exceeded) | Precision limit exceeded. |

## exp

```TypeScript
static exp(n: Value): Decimal
```

Return a new Decimal whose value is the natural exponential of `n`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-precision-limit-is-exceeded) | Precision limit exceeded. |

## floor

```TypeScript
floor(): Decimal
```

Return a new Decimal whose value is the value of this Decimal rounded to a whole number in the direction of negative Infinity.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

## floor

```TypeScript
static floor(n: Value): Decimal
```

Return a new Decimal whose value is `n` round to an integer using `ROUND_FLOOR`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## greaterThan

```TypeScript
greaterThan(n: Value): boolean
```

Return true if the value of this Decimal is greater than the value of `n`, otherwise return false.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | the boolean type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## greaterThanOrEqualTo

```TypeScript
greaterThanOrEqualTo(n: Value): boolean
```

Return true if the value of this Decimal is greater than or equal to the value of `n`, otherwise return false.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | the boolean type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## hypot

```TypeScript
static hypot(...n: Value[]): Decimal
```

Return a new Decimal whose value is the square root of the sum of the squares of the arguments, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md)[] | Yes | {double &#124; string &#124; Decimal} Decimal |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## isFinite

```TypeScript
isFinite(): boolean
```

Return true if the value of this Decimal is a finite number, otherwise return false.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | the boolean type |

## isInteger

```TypeScript
isInteger(): boolean
```

Return true if the value of this Decimal is an integer, otherwise return false.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | the boolean type |

## isNaN

```TypeScript
isNaN(): boolean
```

Return true if the value of this Decimal is NaN, otherwise return false.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | the boolean type |

## isNegative

```TypeScript
isNegative(): boolean
```

Return true if the value of this Decimal is negative, otherwise return false.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | the boolean type |

## isPositive

```TypeScript
isPositive(): boolean
```

Return true if the value of this Decimal is positive, otherwise return false.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | the boolean type |

## isZero

```TypeScript
isZero(): boolean
```

Return true if the value of this Decimal is 0 or -0, otherwise return false.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | the boolean type |

## lessThan

```TypeScript
lessThan(n: Value): boolean
```

Return true if the value of this Decimal is less than `n`, otherwise return false.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | the boolean type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## lessThanOrEqualTo

```TypeScript
lessThanOrEqualTo(n: Value): boolean
```

Return true if the value of this Decimal is less than or equal to `n`, otherwise return false.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | the boolean type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## ln

```TypeScript
ln(): Decimal
```

Return a new Decimal whose value is the natural logarithm of the value of this Decimal, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200060](../errorcode-utils.md#10200060-precision-limit-is-exceeded) | Precision limit exceeded. |

## ln

```TypeScript
static ln(n: Value): Decimal
```

Return a new Decimal whose value is the natural logarithm of `n`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-precision-limit-is-exceeded) | Precision limit exceeded. |

## log

```TypeScript
log(n: Value): Decimal
```

Return the logarithm of the value of this Decimal to the specified base, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-precision-limit-is-exceeded) | Precision limit exceeded. |

## log

```TypeScript
static log(n: Value, base: Value): Decimal
```

Return a new Decimal whose value is the log of `n` to the base `base`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |
| base | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-precision-limit-is-exceeded) | Precision limit exceeded. |

## log10

```TypeScript
static log10(n: Value): Decimal
```

Return a new Decimal whose value is the base 10 logarithm of `n`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-precision-limit-is-exceeded) | Precision limit exceeded. |

## log2

```TypeScript
static log2(n: Value): Decimal
```

Return a new Decimal whose value is the base 2 logarithm of `n`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-precision-limit-is-exceeded) | Precision limit exceeded. |

## max

```TypeScript
static max(...n: Value[]): Decimal
```

Return a new Decimal whose value is the maximum of the arguments.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md)[] | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## min

```TypeScript
static min(...n: Value[]): Decimal
```

Return a new Decimal whose value is the minimum of the arguments.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md)[] | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## mod

```TypeScript
mod(n: Value): Decimal
```

Return a new Decimal whose value is the value of this Decimal modulo `n`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## mod

```TypeScript
static mod(x: Value, y: Value): Decimal
```

Return a new Decimal whose value is `x` modulo `y`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |
| y | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## mul

```TypeScript
mul(n: Value): Decimal
```

Return a new Decimal whose value is this Decimal times `n`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## mul

```TypeScript
static mul(x: Value, y: Value): Decimal
```

Return a new Decimal whose value is `x` multiplied by `y`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |
| y | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## negate

```TypeScript
negate(): Decimal
```

Return a new Decimal whose value is the value of this Decimal negated, i.e. as if multiplied by -1.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

## pow

```TypeScript
pow(n: Value): Decimal
```

Return a new Decimal whose value is the value of this Decimal raised to the power `n`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-precision-limit-is-exceeded) | Precision limit exceeded. |

## pow

```TypeScript
static pow(base: Value, exponent: Value): Decimal
```

Return a new Decimal whose value is `base` raised to the power `exponent`, rounded to precision significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| base | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} The base. |
| exponent | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} The exponent. |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-precision-limit-is-exceeded) | Precision limit exceeded. |

## precision

```TypeScript
precision(): number
```

Return the number of significant digits of the value of this Decimal.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | the number type |

## precision

```TypeScript
precision(includeZeros: boolean | number): number
```

Return the number of significant digits of the value of this Decimal, whether to count integer-part trailing zeros.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| includeZeros | boolean &#124; number | Yes | Whether to count integer-part trailing zeros: true, false, 1 or 0. |

**Return value:**

| Type | Description |
| --- | --- |
| number | the number type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of `includeZeros` is out of range. |

## random

```TypeScript
static random(): Decimal
```

Returns a new Decimal with a random value equal to or greater than 0 and less than 1.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200061](../errorcode-utils.md#10200061-encryption-method-is-unavailable) | Crypto unavailable |

## random

```TypeScript
static random(significantDigits: number): Decimal
```

Returns a new Decimal with a random value equal to or greater than 0 and less than 1, and with `significantDigits` significant digits (or less if trailing zeros are produced).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| significantDigits | number | Yes | Significant digits. Integer, 0 to MAX_DIGITS inclusive.<br>**Since:** 18 |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [10200061](../errorcode-utils.md#10200061-encryption-method-is-unavailable) | Crypto unavailable |

## round

```TypeScript
static round(n: Value): Decimal
```

Return a new Decimal whose value is `n` rounded to an integer using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## set

```TypeScript
static set(config: DecimalConfig): void
```

Configures the 'global' settings for this particular Decimal constructor.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [DecimalConfig](arkts-arkts-math-decimal-decimalconfig-i.md) | Yes |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of `DecimalConfig.properties` is out of range. |
| [10200061](../errorcode-utils.md#10200061-encryption-method-is-unavailable) | Crypto unavailable |

## sign

```TypeScript
static sign(n: Value): number
```

Return the sign of the passed value to the method. 1 if x &gt; 0, -1 if x &lt; 0, 0 if x is 0, -0 if x is -0, NaN otherwise

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type<br>**Since:** 12 - 17 |
| number | the Decimal type<br>**Since:** 18 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## sin

```TypeScript
sin(): Decimal
```

Return a new Decimal whose value is the sine of the value in radians of this Decimal.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

## sin

```TypeScript
static sin(n: Value): Decimal
```

Return a new Decimal whose value is the sine of `n`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} A value in radians. |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## sinh

```TypeScript
sinh(): Decimal
```

Return a new Decimal whose value is the hyperbolic sine of the value in radians of this Decimal.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

## sinh

```TypeScript
static sinh(n: Value): Decimal
```

Return a new Decimal whose value is the hyperbolic sine of `n`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## sqrt

```TypeScript
sqrt(): Decimal
```

Return a new Decimal whose value is the square root of this Decimal, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

## sqrt

```TypeScript
static sqrt(n: Value): Decimal
```

Return a new Decimal whose value is the square root of `n`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## sub

```TypeScript
sub(n: Value): Decimal
```

Return a new Decimal whose value is the value of this Decimal minus `n`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## sub

```TypeScript
static sub(x: Value, y: Value): Decimal
```

Return a new Decimal whose value is `x` minus `y`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |
| y | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## sum

```TypeScript
static sum(...n: Value[]): Decimal
```

Return a new Decimal whose value is the sum of the arguments, rounded to `precision` significant digits using rounding mode `rounding`.

Only the result is rounded, not the intermediate calculations.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md)[] | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## tan

```TypeScript
tan(): Decimal
```

Return a new Decimal whose value is the tangent of the value in radians of this Decimal.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

## tan

```TypeScript
static tan(n: Value): Decimal
```

Return a new Decimal whose value is the tangent of `n`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} A value in radians. |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## tanh

```TypeScript
tanh(): Decimal
```

Return a new Decimal whose value is the hyperbolic tangent of the value in radians of this Decimal.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

## tanh

```TypeScript
static tanh(n: Value): Decimal
```

Return a new Decimal whose value is the hyperbolic tangent of `n`, rounded to `precision` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} A value in radians. |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## toBinary

```TypeScript
toBinary(): string
```

Return a string representing the value of this Decimal in base 2.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string | the string type |

## toBinary

```TypeScript
toBinary(significantDigits: number): string
```

Return a string representing the value of this Decimal in base 2, round to `significantDigits` significant digits.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| significantDigits | number | Yes | Significant digits. Integer, 1 to MAX_DIGITS inclusive. |

**Return value:**

| Type | Description |
| --- | --- |
| string | the string type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of `significantDigits` is out of range. |

## toBinary

```TypeScript
toBinary(significantDigits: number, rounding: Rounding): string
```

Return a string representing the value of this Decimal in base 2, round to `significantDigits` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| significantDigits | number | Yes | Significant digits. Integer, 1 to MAX_DIGITS inclusive. |
| rounding | [Rounding](arkts-arkts-rounding-t.md) | Yes | Rounding mode. Integer, 0 to 8 inclusive. |

**Return value:**

| Type | Description |
| --- | --- |
| string | the string type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of `significantDigits &#124; rounding` is out of range. |

## toDecimalPlaces

```TypeScript
toDecimalPlaces(): Decimal
```

Return a new Decimal whose value is the value of this Decimal.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

## toDecimalPlaces

```TypeScript
toDecimalPlaces(decimalPlaces: number): Decimal
```

Return a new Decimal whose value is the value of this Decimal rounded to a maximum of `decimalPlaces` decimal places.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| decimalPlaces | number | Yes | Significant digits. Integer, 1 to MAX_DIGITS inclusive. |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of `decimalPlaces` is out of range. |

## toDecimalPlaces

```TypeScript
toDecimalPlaces(decimalPlaces: number, rounding: Rounding): Decimal
```

Return a new Decimal whose value is the value of this Decimal rounded to a maximum of `decimalPlaces` decimal places using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| decimalPlaces | number | Yes | Significant digits. Integer, 1 to MAX_DIGITS inclusive. |
| rounding | [Rounding](arkts-arkts-rounding-t.md) | Yes | Rounding mode. Integer, 0 to 8 inclusive. |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of `decimalPlaces &#124; rounding` is out of range. |

## toExponential

```TypeScript
toExponential(): string
```

Return a string representing the value of this Decimal in exponential notation.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string | the string type |

## toExponential

```TypeScript
toExponential(decimalPlaces: number): string
```

Return a string representing the value of this Decimal in exponential notation rounded to `decimalPlaces` fixed decimal places.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| decimalPlaces | number | Yes | Decimal places. Integer, 0 to MAX_DIGITS inclusive. |

**Return value:**

| Type | Description |
| --- | --- |
| string | the string type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of `decimalPlaces` is out of range. |

## toExponential

```TypeScript
toExponential(decimalPlaces: number, rounding: Rounding): string
```

Return a string representing the value of this Decimal in exponential notation rounded to `decimalPlaces` fixed decimal places using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| decimalPlaces | number | Yes | Decimal places. Integer, 0 to MAX_DIGITS inclusive. |
| rounding | [Rounding](arkts-arkts-rounding-t.md) | Yes | Rounding mode. Integer, 0 to 8 inclusive. |

**Return value:**

| Type | Description |
| --- | --- |
| string | the string type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of `decimalPlaces &#124; rounding` is out of range. |

## toFixed

```TypeScript
toFixed(): string
```

Return a string representing the value of this Decimal in normal (fixed-point).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string | the string type |

## toFixed

```TypeScript
toFixed(decimalPlaces: number): string
```

Return a string representing the value of this Decimal in normal (fixed-point) notation to `decimalPlaces` fixed decimal places.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 18 and later: SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| decimalPlaces | number | Yes | Decimal places. Integer, 0 to MAX_DIGITS inclusive. |

**Return value:**

| Type | Description |
| --- | --- |
| string | the string type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of `decimalPlaces` is out of range. |

## toFixed

```TypeScript
toFixed(decimalPlaces: number, rounding: Rounding): string
```

Return a string representing the value of this Decimal in normal (fixed-point) notation to `decimalPlaces` fixed decimal places and rounded using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| decimalPlaces | number | Yes | Decimal places. Integer, 0 to MAX_DIGITS inclusive. |
| rounding | [Rounding](arkts-arkts-rounding-t.md) | Yes | Rounding mode. Integer, 0 to 8 inclusive. |

**Return value:**

| Type | Description |
| --- | --- |
| string | the string type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of `decimalPlaces &#124; rounding` is out of range. |

## toFraction

```TypeScript
toFraction(): Decimal[]
```

Return an array representing the value of this Decimal as a simple fraction with an integer numerator and an integer denominator.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md)[] | the Decimal[] type |

## toFraction

```TypeScript
toFraction(maxDenominator: Value): Decimal[]
```

Return an array representing the value of this Decimal as a simple fraction with an integer numerator and an integer denominator. The denominator will be a positive non-zero value less than or equal to `max_denominator`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| maxDenominator | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md)[] | the Decimal[] type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## toHexadecimal

```TypeScript
toHexadecimal(): string
```

Return a string representing the value of this Decimal in base 16

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string | the string type |

## toHexadecimal

```TypeScript
toHexadecimal(significantDigits: number): string
```

Return a string representing the value of this Decimal in base 16, round to `significantDigits` significant.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| significantDigits | number | Yes | Significant digits. Integer, 1 to MAX_DIGITS inclusive. |

**Return value:**

| Type | Description |
| --- | --- |
| string | the string type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of `significantDigits` is out of range. |

## toHexadecimal

```TypeScript
toHexadecimal(significantDigits: number, rounding: Rounding): string
```

Return a string representing the value of this Decimal in base 16, round to `significantDigits` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| significantDigits | number | Yes | Significant digits. Integer, 1 to MAX_DIGITS inclusive. |
| rounding | [Rounding](arkts-arkts-rounding-t.md) | Yes | Rounding mode. Integer, 0 to 8 inclusive. |

**Return value:**

| Type | Description |
| --- | --- |
| string | the string type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of `significantDigits &#124; rounding` is out of range. |

## toNearest

```TypeScript
toNearest(n: Value): Decimal
```

Returns a new Decimal whose value is the nearest multiple of `n`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## toNearest

```TypeScript
toNearest(n: Value, rounding: Rounding): Decimal
```

Returns a new Decimal whose value is the nearest multiple of `n` in the direction of rounding mode `rounding`, to the value of this Decimal.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |
| rounding | [Rounding](arkts-arkts-rounding-t.md) | Yes | Rounding mode. Integer, 0 to 8 inclusive. |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of `rounding` is out of range. |

## toNumber

```TypeScript
toNumber(): number
```

Return the value of this Decimal converted to a number primitive. Zero keeps its sign.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | the number type |

## toOctal

```TypeScript
toOctal(): string
```

Return a string representing the value of this Decimal in base 8.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string | the string type |

## toOctal

```TypeScript
toOctal(significantDigits: number): string
```

Return a string representing the value of this Decimal in base 8, round to `significantDigits` significant.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| significantDigits | number | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| string | the string type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of `significantDigits` is out of range. |

## toOctal

```TypeScript
toOctal(significantDigits: number, rounding: Rounding): string
```

Return a string representing the value of this Decimal in base 8, round to `significantDigits` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| significantDigits | number | Yes | {double &#124; string &#124; Decimal} |
| rounding | [Rounding](arkts-arkts-rounding-t.md) | Yes | Rounding mode. Integer, 0 to 8 inclusive. |

**Return value:**

| Type | Description |
| --- | --- |
| string | the string type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of `significantDigits &#124; rounding` is out of range. |

## toPrecision

```TypeScript
toPrecision(): string
```

Return a string representing the value of this Decimal.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string | the string type |

## toPrecision

```TypeScript
toPrecision(significantDigits: number): string
```

Return a string representing the value of this Decimal rounded to `significantDigits` significant digits.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| significantDigits | number | Yes | Significant digits. Integer, 1 to MAX_DIGITS inclusive. |

**Return value:**

| Type | Description |
| --- | --- |
| string | the string type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of `significantDigits` is out of range. |

## toPrecision

```TypeScript
toPrecision(significantDigits: number, rounding: Rounding): string
```

Return a string representing the value of this Decimal rounded to `significantDigits` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| significantDigits | number | Yes | Significant digits. Integer, 1 to MAX_DIGITS inclusive. |
| rounding | [Rounding](arkts-arkts-rounding-t.md) | Yes | Rounding mode. Integer, 0 to 8 inclusive. |

**Return value:**

| Type | Description |
| --- | --- |
| string | the string type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of `significantDigits &#124; rounding` is out of range. |

## toSignificantDigits

```TypeScript
toSignificantDigits(): Decimal
```

Return a new Decimal whose value is the value of this Decimal.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

## toSignificantDigits

```TypeScript
toSignificantDigits(significantDigits: number): Decimal
```

Return a new Decimal whose value is the value of this Decimal rounded to a maximum of `significantDigits` significant digits.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| significantDigits | number | Yes | Significant digits. Integer, 1 to MAX_DIGITS inclusive. |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of `significantDigits` is out of range. |

## toSignificantDigits

```TypeScript
toSignificantDigits(significantDigits: number, rounding: Rounding): Decimal
```

Return a new Decimal whose value is the value of this Decimal rounded to a maximum of `significantDigits` significant digits using rounding mode `rounding`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| significantDigits | number | Yes | Significant digits. Integer, 1 to MAX_DIGITS inclusive. |
| rounding | [Rounding](arkts-arkts-rounding-t.md) | Yes | Rounding mode. Integer, 0 to 8 inclusive. |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of `significantDigits &#124; rounding` is out of range. |

## toString

```TypeScript
toString(): string
```

Return a string representing the value of this Decimal. Return exponential notation if this Decimal has a positive exponent equal to or greater than `toExpPos`, or a negative exponent equal to or less than `toExpNeg`.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string | the string type |

## trunc

```TypeScript
trunc(): Decimal
```

Return a new Decimal whose value is the value of this Decimal truncated to a whole number.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

## trunc

```TypeScript
static trunc(n: Value): Decimal
```

Return a new Decimal whose value is `n` truncated to an integer.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n | [Value](arkts-arkts-value-t.md) | Yes | {double &#124; string &#124; Decimal} |

**Return value:**

| Type | Description |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

## valueOf

```TypeScript
valueOf(): string
```

Return a string representing the value of this Decimal. Unlike `toString`, negative zero will include the minus sign.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string | the string type |

## d

```TypeScript
readonly d: number[]
```

The numbers of decimal digits.

**Type:** number[]

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## e

```TypeScript
get e(): number
```

The number of decimal exponent.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## EUCLIDEAN

```TypeScript
static readonly EUCLIDEAN : 9
```

Not a rounding mode, see modulo

**Type:** 9

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## ROUND_CEILING

```TypeScript
static readonly ROUND_CEILING : 2
```

Rounds towards Infinity

**Type:** 2

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## ROUND_DOWN

```TypeScript
static readonly ROUND_DOWN : 1
```

Rounds towards zero

**Type:** 1

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## ROUND_FLOOR

```TypeScript
static readonly ROUND_FLOOR : 3
```

Rounds towards -Infinity

**Type:** 3

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## ROUND_HALF_CEILING

```TypeScript
static readonly ROUND_HALF_CEILING : 7
```

Rounds towards nearest neighbour. If equidistant, rounds towards Infinity

**Type:** 7

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## ROUND_HALF_DOWN

```TypeScript
static readonly ROUND_HALF_DOWN : 5
```

Rounds towards nearest neighbour. If equidistant, rounds towards zero

**Type:** 5

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## ROUND_HALF_EVEN

```TypeScript
static readonly ROUND_HALF_EVEN : 6
```

Rounds towards nearest neighbour. If equidistant, rounds towards even neighbour

**Type:** 6

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## ROUND_HALF_FLOOR

```TypeScript
static readonly ROUND_HALF_FLOOR : 8
```

Rounds towards nearest neighbour. If equidistant, rounds towards -Infinity

**Type:** 8

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## ROUND_HALF_UP

```TypeScript
static readonly ROUND_HALF_UP : 4
```

Rounds towards nearest neighbour. If equidistant, rounds away from zero

**Type:** 4

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## ROUND_UP

```TypeScript
static readonly ROUND_UP : 0
```

Rounds away from zero

**Type:** 0

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## s

```TypeScript
get s(): number
```

The number of decimal sign.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
