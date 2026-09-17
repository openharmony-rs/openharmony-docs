# RichEditorSpanType

Enumerates span types.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## TEXT

```TypeScript
TEXT = 0
```

Text span.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## IMAGE

```TypeScript
IMAGE = 1
```

Image span.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## MIXED

```TypeScript
MIXED = 2
```

Mixed text and image span.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## BUILDER

```TypeScript
BUILDER = 3
```

Span of the custom layout type.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 4
```

When a menu of this type is registered but no TEXT, IMAGE, MIXED, or BUILDER menu is registered, the text type, image type, mixed text-image type, and custom layout type all trigger and display the menu corresponding to this type.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
