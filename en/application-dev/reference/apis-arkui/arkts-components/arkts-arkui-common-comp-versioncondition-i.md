# VersionCondition

```TypeScript
declare interface VersionCondition
```

Defines VersionCondition interface

**Since:** 26.2.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxApiVersion

```TypeScript
maxApiVersion?: number | string
```

Maximum API version for the style or extend to take effect. Represets the runtime device version, as a number or a string. Default value: undefined: The version restriction does not take effect.

**Type:** number &#124; string

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## minApiVersion

```TypeScript
minApiVersion?: number | string
```

Minimum API version for the style or extend to take effect. Represets the runtime device version, as a number or a string. Default value: undefined: The version restriction does not take effect.

**Type:** number &#124; string

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
