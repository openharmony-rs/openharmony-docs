# TextResponseType

Response type of the menu.

> **NOTE:** 
> 
> The system follows the priority order below when determining the menu type to display during text interactions: &gt;

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## RIGHT_CLICK

```TypeScript
RIGHT_CLICK = 0
```

The menu is displayed when the component is right-clicked.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## LONG_PRESS

```TypeScript
LONG_PRESS = 1
```

The menu is displayed when the component is long-pressed.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SELECT

```TypeScript
SELECT = 2
```

The menu is displayed when the component is selected.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 3
```

When this type is registered but **RIGHT_CLICK**, **LONG_PRESS**, or **SELECT** types are not registered, this type will be triggered and displayed for right-click, long press, mouse selection, and [selection](arkts-arkui-text-comp-attribute.md#selection) API calls.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
