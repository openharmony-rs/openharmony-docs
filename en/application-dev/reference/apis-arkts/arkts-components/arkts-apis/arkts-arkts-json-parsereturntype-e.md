# ParseReturnType

```TypeScript
const enum ParseReturnType
```

Enumerates the return types for parsing.

When parseReturnType is MAP, the parsed result is a Sendable Map (JSSharedMap) instead of a Sendable Object (JSSharedObject). Only effective for [parseSendable](arkts-arkts-json-parsesendable-f.md); ignored by [parse](arkts-arkts-json-parse-f.md).

**Since:** 26.0.1

**System capability:** SystemCapability.Utils.Lang

## OBJECT

```TypeScript
OBJECT = 0
```

The parsing result is a non-extensible Sendable object, whose existing properties can be updated but cannot be added or deleted.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Utils.Lang

## MAP

```TypeScript
MAP = 1
```

The parsing result is a sendable Map, which supports adding and deleting entries.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Utils.Lang
