# Scenarios

```TypeScript
export enum Scenarios
```

Enumerates the scenarios where the [onNewWant](arkts-ability-app-ability-uiability-uiability-c.md#onnewwant) lifecycle callback is not triggered. It is used in the [setOnNewWantSkipScenarios](arkts-ability-uiabilitycontext-c.md#setonnewwantskipscenarios) API.

**Since:** 20

<!--Device-contextConstant-export enum Scenarios--><!--Device-contextConstant-export enum Scenarios-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## SCENARIO_MOVE_MISSION_TO_FRONT

```TypeScript
SCENARIO_MOVE_MISSION_TO_FRONT = 0x00000001
```

<!--RP1-->A scenario where the system API missionManager.moveMissionToFront is called to move the UIAbility to the foreground.<!--RP1End-->

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-Scenarios-SCENARIO_MOVE_MISSION_TO_FRONT = 0x00000001--><!--Device-Scenarios-SCENARIO_MOVE_MISSION_TO_FRONT = 0x00000001-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## SCENARIO_SHOW_ABILITY

```TypeScript
SCENARIO_SHOW_ABILITY = 0x00000002
```

A scenario where the [showAbility](arkts-ability-uiabilitycontext-c.md#showability) API is called to move the UIAbility to the foreground.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-Scenarios-SCENARIO_SHOW_ABILITY = 0x00000002--><!--Device-Scenarios-SCENARIO_SHOW_ABILITY = 0x00000002-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## SCENARIO_BACK_TO_CALLER_ABILITY_WITH_RESULT

```TypeScript
SCENARIO_BACK_TO_CALLER_ABILITY_WITH_RESULT = 0x00000004
```

A scenario where the [backToCallerAbilityWithResult](arkts-ability-uiabilitycontext-c.md#backtocallerabilitywithresult) API is called to move the UIAbility to the foreground.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-Scenarios-SCENARIO_BACK_TO_CALLER_ABILITY_WITH_RESULT = 0x00000004--><!--Device-Scenarios-SCENARIO_BACK_TO_CALLER_ABILITY_WITH_RESULT = 0x00000004-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
