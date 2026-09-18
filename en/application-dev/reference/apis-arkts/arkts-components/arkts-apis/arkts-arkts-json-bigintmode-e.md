# BigIntMode

Enumerates the modes for processing BigInt.

**Since:** 12

**System capability:** SystemCapability.Utils.Lang

## DEFAULT

```TypeScript
DEFAULT = 0
```

BigInt is not supported.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## PARSE_AS_BIGINT

```TypeScript
PARSE_AS_BIGINT = 1
```

Parses an integer that is less than -(2^53-1) or greater than (2^53-1) as BigInt.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## ALWAYS_PARSE_AS_BIGINT

```TypeScript
ALWAYS_PARSE_AS_BIGINT = 2
```

Parses all integers as BigInt.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
