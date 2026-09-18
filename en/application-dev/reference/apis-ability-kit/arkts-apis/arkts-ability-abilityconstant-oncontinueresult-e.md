# OnContinueResult

Enumerates the ability continuation results. You can use it in [onContinue()](arkts-ability-app-ability-uiability-uiability-c.md#oncontinue) of the UIAbility to complete different operations.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## AGREE

```TypeScript
AGREE = 0
```

The ability continuation is accepted.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## REJECT

```TypeScript
REJECT = 1
```

The ability continuation is rejected. If the application is abnormal in [onContinue](arkts-ability-app-ability-uiability-uiability-c.md#oncontinue), which results in abnormal display during data restoration, this result is returned.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## MISMATCH

```TypeScript
MISMATCH = 2
```

The version does not match. The application on the initiator can obtain the version of the target application from [onContinue](arkts-ability-app-ability-uiability-uiability-c.md#oncontinue). If the ability continuation cannot be performed due to version mismatch, this result is returned.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
