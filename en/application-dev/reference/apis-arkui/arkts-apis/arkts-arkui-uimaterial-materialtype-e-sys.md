# MaterialType

Enumerates system material types.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 0
```

No system material effect. The corresponding effects are: backgroundColor and borderColor are transparent, borderWidth is 0, and there is no shadow.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## SEMI_TRANSPARENT

```TypeScript
SEMI_TRANSPARENT = 1
```

Semi-transparent system material effect. The corresponding effect is as follows:

backgroundColor: #f2f1f3f5 in light mode and #f2303131 in dark mode.

borderColor: [token](../../../ui/theme_skinning.md#system-default-token-color-values) value of **theme.colors.compForegroundPrimary** with 10% transparency.

borderWidth: 1 vp.

shadow: ShadowStyle.OUTER_DEFAULT_SM.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
