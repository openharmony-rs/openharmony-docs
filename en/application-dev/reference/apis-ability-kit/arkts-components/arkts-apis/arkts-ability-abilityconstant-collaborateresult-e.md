# CollaborateResult

```TypeScript
export enum CollaborateResult
```

Enumerates the collaboration request results. You can use it in multi-device collaboration scenarios to specify whether the target application accepts the collaboration request from the caller application. You can use it in [onCollaborate()](arkts-ability-app-ability-uiability-uiability-c.md#oncollaborate) of the UIAbility.

**Since:** 18

<!--Device-AbilityConstant-export enum CollaborateResult--><!--Device-AbilityConstant-export enum CollaborateResult-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## ACCEPT

```TypeScript
ACCEPT = 0
```

Accepts the collaboration request.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-CollaborateResult-ACCEPT = 0--><!--Device-CollaborateResult-ACCEPT = 0-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## REJECT

```TypeScript
REJECT = 1
```

Rejects the collaboration request.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-CollaborateResult-REJECT = 1--><!--Device-CollaborateResult-REJECT = 1-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
