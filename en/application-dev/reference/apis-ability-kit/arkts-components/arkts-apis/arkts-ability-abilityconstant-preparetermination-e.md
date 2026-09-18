# PrepareTermination

Enumerates the actions triggered when an application is closed by the user. You can use it in [onPrepareTermination](arkts-ability-app-ability-abilitystage-abilitystage-c.md#onpreparetermination) or [onPrepareTerminationAsync](arkts-ability-app-ability-abilitystage-abilitystage-c.md#onprepareterminationasync) of [AbilityStage](arkts-ability-app-ability-abilitystage-abilitystage-c.md).

**Since:** 15

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## TERMINATE_IMMEDIATELY

```TypeScript
TERMINATE_IMMEDIATELY = 0
```

Executes the termination action immediately. This is the default behavior.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## CANCEL

```TypeScript
CANCEL = 1
```

Cancels the termination action.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
