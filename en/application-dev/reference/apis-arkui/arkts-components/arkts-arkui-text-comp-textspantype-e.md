# TextSpanType

```TypeScript
declare enum TextSpanType
```

Provides the [span](arkts-arkui-span-comp.md#span) type information.

> **NOTE:** 
> 
> The system follows the priority order below when determining the menu type to display during text interactions: &gt;

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## TEXT

```TypeScript
TEXT = 0
```

Text span.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## IMAGE

```TypeScript
IMAGE = 1
```

Image span.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## MIXED

```TypeScript
MIXED = 2
```

Mixed span, which contains both text and imagery.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 3
```

When this type is registered but **TEXT**, **IMAGE**, or **MIXED** types are not registered, this type will be triggered and displayed for those registered types.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
