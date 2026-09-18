# NavDestinationMode

Mode of the **NavDestination** component.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## STANDARD

```TypeScript
STANDARD = 0
```

Standard mode.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DIALOG

```TypeScript
DIALOG = 1
```

The navigation destination is transparent by default. Stack operations do not affect the visibility of underlying **NavDestination** components (lifecycle methods like **onShown** and **onHidden** remain unchanged). Only the **onActive** and **onInactive** lifecycle methods are triggered.

Before API version 13, no system transition animation is available by default. System transition animations are supported since API version 13.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
