# StateType

```TypeScript
export enum StateType
```

Enumerates the scenarios for saving application data. You can use it in [onSaveState()](arkts-ability-app-ability-uiability-uiability-c.md#onsavestate) of the UIAbility to complete [UIAbility backup and restore](../../../application-models/ability-recover-guideline.md).

**Since:** 9

<!--Device-AbilityConstant-export enum StateType--><!--Device-AbilityConstant-export enum StateType-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## CONTINUATION

```TypeScript
CONTINUATION = 0
```

Application migration scenario.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-StateType-CONTINUATION = 0--><!--Device-StateType-CONTINUATION = 0-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## APP_RECOVERY

```TypeScript
APP_RECOVERY = 1
```

Application recovery scenario.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-StateType-APP_RECOVERY = 1--><!--Device-StateType-APP_RECOVERY = 1-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
