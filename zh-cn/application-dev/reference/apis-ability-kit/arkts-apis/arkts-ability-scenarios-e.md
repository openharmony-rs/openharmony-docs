# Scenarios

表示不触发[onNewWant](arkts-ability-uiability-c.md#onnewwant-1)生命周期回调场景的枚举，用于
[setOnNewWantSkipScenarios](arkts-ability-uiabilitycontext-c.md#setonnewwantskipscenarios-1)接口。

**起始版本：** 20

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## SCENARIO_MOVE_MISSION_TO_FRONT

```TypeScript
SCENARIO_MOVE_MISSION_TO_FRONT = 0x00000001
```

<!--RP1-->系统接口[missionManager.moveMissionToFront](./js-apis-app-ability-missionManager-sys.md#missionmanagermovemissiontofront-2)接口触发的UIAbility到前台场景。<!--RP1End-->

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## SCENARIO_SHOW_ABILITY

```TypeScript
SCENARIO_SHOW_ABILITY = 0x00000002
```

[showAbility](arkts-ability-uiabilitycontext-c.md#showability-1)接口触发的UIAbility到前台场景。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## SCENARIO_BACK_TO_CALLER_ABILITY_WITH_RESULT

```TypeScript
SCENARIO_BACK_TO_CALLER_ABILITY_WITH_RESULT = 0x00000004
```

[backToCallerAbilityWithResult](arkts-ability-uiabilitycontext-c.md#backtocallerabilitywithresult-1)
接口触发的UIAbility到前台场景。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

