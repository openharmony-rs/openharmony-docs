# DecimalConfig

Provides configuration for decimal.

**Since:** 12

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { Decimal } from '@kit.ArkTS';
```

## crypto

```TypeScript
crypto?: boolean
```

The value that determines whether cryptographically-secure pseudo-random number generation is used. Default value: false

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## defaults

```TypeScript
defaults?: boolean
```

If object has a 'defaults' property with value true then the new constructor will use the default configuration. Default value: false

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## maxE

```TypeScript
maxE?: number
```

The positive exponent limit, i.e. the exponent value above which overflow to Infinity occurs. Default value: 9e15

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## minE

```TypeScript
minE?: number
```

The negative exponent limit, i.e. the exponent value below which underflow to zero occurs. Default value: -9e15

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## modulo

```TypeScript
modulo?: Modulo
```

The modulo mode used when calculating the modulus: a mod n. Default value: 1 (ROUND_DOWN)

**Type:** [Modulo](arkts-arkts-modulo-t.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## precision

```TypeScript
precision?: number
```

The maximum number of significant digits of the result of an operation. Default value: 20

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## rounding

```TypeScript
rounding?: Rounding
```

The default rounding mode used when rounding the result of an operation to precision significant digits, and when rounding the return value of the round, toBinary, toDecimalPlaces, toExponential, toFixed, toHexadecimal, toNearest, toOctal, toPrecision and toSignificantDigits methods. Default value: 4 (ROUND_HALF_UP)

**Type:** [Rounding](arkts-arkts-rounding-t.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## toExpNeg

```TypeScript
toExpNeg?: number
```

The negative exponent value at and below which toString returns exponential notation. Default value: -7

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## toExpPos

```TypeScript
toExpPos?: number
```

The positive exponent value at and above which toString returns exponential notation. Default value: 21

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
