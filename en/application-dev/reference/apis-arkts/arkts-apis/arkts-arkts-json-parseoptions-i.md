# ParseOptions

```TypeScript
interface ParseOptions
```

Describes the parsing options, which can define the mode for processing BigInt.

**Since:** 12

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { JSON } from '@kit.ArkTS';
```

## bigIntMode

```TypeScript
bigIntMode: BigIntMode
```

Mode for processing BigInt.

**Type:** [BigIntMode](arkts-arkts-json-bigintmode-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## parseReturnType

```TypeScript
parseReturnType?: ParseReturnType
```

The return type for parsing. When omitted, defaults to OBJECT. Only effective for [parseSendable](arkts-arkts-json-parsesendable-f.md); ignored by [parse](arkts-arkts-json-parse-f.md).

**Type:** [ParseReturnType](arkts-arkts-json-parsereturntype-e.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Utils.Lang
