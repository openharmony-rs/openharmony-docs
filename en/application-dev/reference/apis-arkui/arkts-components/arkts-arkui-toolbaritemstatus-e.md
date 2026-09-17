# ToolbarItemStatus

Enumerates the toolbar item states.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NORMAL

```TypeScript
NORMAL = 0
```

Normal state. In this state, the toolbar item takes on the default style and can switch to another state-specific style by responding to the hover, press, and focus events.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DISABLED

```TypeScript
DISABLED = 1
```

Disabled state. In this state, the toolbar item is disabled and does not allow for user interactions.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ACTIVE

```TypeScript
ACTIVE = 2
```

Active state. In this state, the toolbar item can update its icon to the one specified by **activeIcon** by responding to a click event.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
