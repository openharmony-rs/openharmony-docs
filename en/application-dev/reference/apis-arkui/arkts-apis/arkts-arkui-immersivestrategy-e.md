# ImmersiveStrategy

```TypeScript
declare enum ImmersiveStrategy
```

Enumerates the immersive strategies for the safe area.

**Since:** 26.1.0

<!--Device-unnamed-declare enum ImmersiveStrategy--><!--Device-unnamed-declare enum ImmersiveStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## AVOID_CUTOUT

```TypeScript
AVOID_CUTOUT = 0
```

Avoid the cutout area.

> **NOTE:** 
> 
> The priority of this strategy is lower than that of the avoid_cutout configuration item in module.json5.
> If avoid_cutout is configured in the metadata of module.json5, the effect of the avoid_cutout
> configuration item prevails.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ImmersiveStrategy-AVOID_CUTOUT = 0--><!--Device-ImmersiveStrategy-AVOID_CUTOUT = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## AVOID_FLOAT_NAV

```TypeScript
AVOID_FLOAT_NAV = 1
```

Avoid the three-button navigation bar area on the phone.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ImmersiveStrategy-AVOID_FLOAT_NAV = 1--><!--Device-ImmersiveStrategy-AVOID_FLOAT_NAV = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## AVOID_WINDOW_CONTROLS

```TypeScript
AVOID_WINDOW_CONTROLS = 6
```

Avoid the window control buttons, which are the close, minimize and zoom buttons.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ImmersiveStrategy-AVOID_WINDOW_CONTROLS = 6--><!--Device-ImmersiveStrategy-AVOID_WINDOW_CONTROLS = 6-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## BIND_SHEET_EXPAND_SAFE_AREA

```TypeScript
BIND_SHEET_EXPAND_SAFE_AREA = 7
```

Expand the title area of bindSheet as safe area for the content region.

> **NOTE:** 
> 
> When this strategy is applied via [applyDefaultImmersiveStrategy](arkts-arkui-arkui-uicontext-uicontext-c.md#applydefaultimmersivestrategy),
> bindSheet's [titleBarHoverMode](../arkts-components/arkts-arkui-common-comp-sheetoptions-i.md#titlebarhovermode) defaults to
> [SAFE_AREA_PADDING](../arkts-components/arkts-arkui-common-comp-sheettitlebarhovermode-e.md#safe_area_padding).

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ImmersiveStrategy-BIND_SHEET_EXPAND_SAFE_AREA = 7--><!--Device-ImmersiveStrategy-BIND_SHEET_EXPAND_SAFE_AREA = 7-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NAVIGATION_EXPAND_SAFE_AREA

```TypeScript
NAVIGATION_EXPAND_SAFE_AREA = 8
```

Expands the TitleBar and ToolBar of Navigation/NavDestination as safe areas for the content region.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ImmersiveStrategy-NAVIGATION_EXPAND_SAFE_AREA = 8--><!--Device-ImmersiveStrategy-NAVIGATION_EXPAND_SAFE_AREA = 8-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
