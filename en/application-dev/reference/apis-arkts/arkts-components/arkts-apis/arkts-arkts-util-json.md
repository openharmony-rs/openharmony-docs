# @ohos.util.json(JSON Parsing and Generation)

The JSON module provides a series of APIs for converting JSON text into JSON objects or values and converting objects into JSON text.

**Since:** 12

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { JSON } from '@kit.ArkTS';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [has](arkts-arkts-json-has-f.md) | Checks whether an ArkTS object contains a key. This API can be used for related operations after [JSON.parse](arkts-arkts-json-parse-f.md) is called to parse a JSON string. This API supports only valid JSON strings whose outermost layer is in dictionary format (in braces instead of square brackets). |
| [parse](arkts-arkts-json-parse-f.md) | Parses a JSON string into an ArkTS object or null. |
| [remove](arkts-arkts-json-remove-f.md) | Removes a key from an ArkTS object. This API can be used for related operations after [JSON.parse](arkts-arkts-json-parse-f.md) is called to parse a JSON string. This API supports only valid JSON strings whose outermost layer is in dictionary format (in braces instead of square brackets). |
| [stringify](arkts-arkts-json-stringify-f.md) | Converts an ArkTS object or array into a JSON string. In the case of a container, linear containers are supported, but non-linear containers are not. |
| [stringify](arkts-arkts-json-stringify-f.md) | Converts an ArkTS object or array into a JSON string. In the case of a container, linear containers are supported, but non-linear containers are not. |

### Interfaces

| Name | Description |
| --- | --- |
| [ParseOptions](arkts-arkts-json-parseoptions-i.md) | Describes the parsing options, which can define the mode for processing BigInt. |

### Enums

| Name | Description |
| --- | --- |
| [BigIntMode](arkts-arkts-json-bigintmode-e.md) | Enumerates the modes for processing BigInt. |

### Types

| Name | Description |
| --- | --- |
| [Transformer](arkts-arkts-json-transformer-t.md) | Defines the type of the conversion result function. |
