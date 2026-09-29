# MaterialType

```TypeScript
enum MaterialType
```

Enumerates the system material types. This section contains only the system APIs of this module. For other public types, see [MaterialType](arkts-arkui-uimaterial-materialtype-e.md).

**Since:** 26.0.0

<!--Device-uiMaterial-enum MaterialType--><!--Device-uiMaterial-enum MaterialType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 0
```

No system material effect. The corresponding effects are: [backgroundColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor) is transparent, [borderColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#bordercolor) is transparent, [borderWidth](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#borderwidth) is 0, and no [shadow](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#shadow).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

<!--Device-MaterialType-NONE = 0--><!--Device-MaterialType-NONE = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## SEMI_TRANSPARENT

```TypeScript
SEMI_TRANSPARENT = 1
```

Semi-transparent system material effect. The corresponding effects are:

[backgroundColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor): "#f2f1f3f5" in light mode and "#f2303131" in dark mode.

[borderColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#bordercolor): [token](../../../ui/theme_skinning.md#system-default-token-color-values) value of theme.colors.compForegroundPrimary blended with 10% transparency (alpha value).

[borderWidth](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#borderwidth): 1 vp.

[shadow](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#shadow): ShadowStyle.OUTER_DEFAULT_SM.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

<!--Device-MaterialType-SEMI_TRANSPARENT = 1--><!--Device-MaterialType-SEMI_TRANSPARENT = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
