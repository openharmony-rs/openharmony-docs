# BarStyle

Enumerates the layout styles of the title bar and toolbar. Note that this API is not supported for the toolbar in **NavDestination**.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## STANDARD

```TypeScript
STANDARD = 0
```

In this mode, the title bar or toolbar is laid out above the content area.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## STACK

```TypeScript
STACK = 1
```

In this mode, the title bar or toolbar is overlaid on top of the content area.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SAFE_AREA_PADDING

```TypeScript
SAFE_AREA_PADDING = 2
```

In this mode, the title bar or toolbar is configured to respect the [component-level safe area](arkts-arkui-commonmethod-c.md#safeareapadding).

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
