# BigIntMode

```TypeScript
const enum BigIntMode
```

Enum defining modes for handling bigint.

**Since:** 12

<!--Device-ASON-const enum BigIntMode--><!--Device-ASON-const enum BigIntMode-End-->

**System capability:** SystemCapability.Utils.Lang

## DEFAULT

```TypeScript
DEFAULT = 0
```

BigInt is not supported.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-BigIntMode-DEFAULT = 0--><!--Device-BigIntMode-DEFAULT = 0-End-->

**System capability:** SystemCapability.Utils.Lang

## PARSE_AS_BIGINT

```TypeScript
PARSE_AS_BIGINT = 1
```

Parse as BigInt when number less than -(2^53 �? 1) or greater than (2^53 �? 1).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-BigIntMode-PARSE_AS_BIGINT = 1--><!--Device-BigIntMode-PARSE_AS_BIGINT = 1-End-->

**System capability:** SystemCapability.Utils.Lang

## ALWAYS_PARSE_AS_BIGINT

```TypeScript
ALWAYS_PARSE_AS_BIGINT = 2
```

All numbers parse as BigInt.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-BigIntMode-ALWAYS_PARSE_AS_BIGINT = 2--><!--Device-BigIntMode-ALWAYS_PARSE_AS_BIGINT = 2-End-->

**System capability:** SystemCapability.Utils.Lang
