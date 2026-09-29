# ContinueState

```TypeScript
export enum ContinueState
```

Enumerates the mission continuation states of the application. It is used in the [setMissionContinueState](arkts-ability-uiabilitycontext-c.md#setmissioncontinuestate) API of [UIAbilityContext](arkts-ability-uiabilitycontext-c.md).

> **NOTE:** This API does not take effect on Wearable devices that do not support distributed services.

**Since:** 10

<!--Device-AbilityConstant-export enum ContinueState--><!--Device-AbilityConstant-export enum ContinueState-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## ACTIVE

```TypeScript
ACTIVE = 0
```

Mission continuation is activated for the current application.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ContinueState-ACTIVE = 0--><!--Device-ContinueState-ACTIVE = 0-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## INACTIVE

```TypeScript
INACTIVE = 1
```

Mission continuation is not activated for the current application.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ContinueState-INACTIVE = 1--><!--Device-ContinueState-INACTIVE = 1-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
