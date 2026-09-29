# TextSpanType

```TypeScript
declare enum TextSpanType
```

Provides the [span](arkts-arkui-span-comp.md) type information.

> **NOTE:** 
> 
> The system follows the priority order below when determining the menu type to display during text interactions:
> 
> 1. Check whether a menu is registered for **TextSpanType.TEXT** and **TextResponseType.LONG_PRESS**.
> 
> 2. Check whether a menu is registered for **TextSpanType.TEXT** and **TextResponseType.DEFAULT**.
> 
> 3. Check whether a menu is registered for **TextSpanType.DEFAULT** and **TextResponseType.LONG_PRESS**.
> 
> 4. Check whether a menu is registered for **TextSpanType.DEFAULT** and **TextResponseType.DEFAULT**.

**Since:** 11

<!--Device-unnamed-declare enum TextSpanType--><!--Device-unnamed-declare enum TextSpanType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## TEXT

```TypeScript
TEXT = 0
```

Text span.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextSpanType-TEXT = 0--><!--Device-TextSpanType-TEXT = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## IMAGE

```TypeScript
IMAGE = 1
```

Image span.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextSpanType-IMAGE = 1--><!--Device-TextSpanType-IMAGE = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## MIXED

```TypeScript
MIXED = 2
```

Mixed span, which contains both text and imagery.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextSpanType-MIXED = 2--><!--Device-TextSpanType-MIXED = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 3
```

When this type is registered but **TEXT**, **IMAGE**, or **MIXED** types are not registered, this type will be triggered and displayed for those registered types.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TextSpanType-DEFAULT = 3--><!--Device-TextSpanType-DEFAULT = 3-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
