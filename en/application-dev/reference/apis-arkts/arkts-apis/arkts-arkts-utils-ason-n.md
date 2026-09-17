# ASON(Defines the utils for ArkTS)

ArkTS JSON utils.

**Since:** 12

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { ArkTSUtils } from '@kit.ArkTS';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [parse](arkts-arkts-ason-parse-f.md) | Converts a JavaScript Object Notation (JSON) string into an ArkTS Value. |
| [stringify](arkts-arkts-ason-stringify-f.md) | Converts an ArkTS value to a JavaScript Object Notation (JSON) string. Extra supports Map and Set. |

### Interfaces

| Name | Description |
| --- | --- |
| [ParseOptions](arkts-arkts-ason-parseoptions-i.md) | Parse's options |

### Types

| Name | Description |
| --- | --- |
| [ISendable](arkts-arkts-ason-isendable-t.md) | Redefines ISendable for convenience. |
| [Transformer](arkts-arkts-ason-transformer-t.md) | The type of conversion result function. |

### Enums

| Name | Description |
| --- | --- |
| [BigIntMode](arkts-arkts-ason-bigintmode-e.md) | Enum defining modes for handling bigint. |
| [ParseReturnType](arkts-arkts-ason-parsereturntype-e.md) | The return types for parsing. |
