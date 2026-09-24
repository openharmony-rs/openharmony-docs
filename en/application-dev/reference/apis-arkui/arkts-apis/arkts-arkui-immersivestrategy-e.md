# ImmersiveStrategy

```TypeScript
declare enum ImmersiveStrategy
```

Enumerates the immersive strategies for the safe area.

**Since:** 26.2.0

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

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## AVOID_FLOAT_NAV

```TypeScript
AVOID_FLOAT_NAV = 1
```

Avoid the three-button navigation bar area on the phone.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
