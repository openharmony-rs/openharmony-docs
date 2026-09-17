# WindowMode

Enumerates the window modes in which a UIAbility can be displayed at startup. It can be used in [startAbility](arkts-ability-uiabilitycontext-c.md#startability).

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## WINDOW_MODE_FULLSCREEN

```TypeScript
WINDOW_MODE_FULLSCREEN = 1
```

Full-screen mode. It takes effect only on 2-in-1 devices and tablets.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## WINDOW_MODE_SPLIT_PRIMARY

```TypeScript
WINDOW_MODE_SPLIT_PRIMARY = 100
```

Primary screen (left screen in the case of horizontal orientation) in split-screen mode. It is valid only in intra-app redirection scenarios. It takes effect only on foldable devices and tablets.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## WINDOW_MODE_SPLIT_SECONDARY

```TypeScript
WINDOW_MODE_SPLIT_SECONDARY = 101
```

Secondary screen (right screen in the case of horizontal orientation) in split-screen mode. It is valid only in intra-app redirection scenarios. It takes effect only on foldable devices and tablets.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## WINDOW_MODE_SPLIT

```TypeScript
WINDOW_MODE_SPLIT = 105
```

The ability is displayed in split-screen mode. It is valid only in intra-app redirection scenarios. It takes effect only on foldable devices and tablets.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
