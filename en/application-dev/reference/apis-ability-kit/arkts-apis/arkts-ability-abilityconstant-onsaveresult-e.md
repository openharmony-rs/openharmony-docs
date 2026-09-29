# OnSaveResult

```TypeScript
export enum OnSaveResult
```

Enumerates the result types for the operation of saving application data. You can use it in [onSaveState()](arkts-ability-app-ability-uiability-uiability-c.md#onsavestate) of the UIAbility to complete [UIAbility backup and restore](../../../application-models/ability-recover-guideline.md).

**Since:** 9

<!--Device-AbilityConstant-export enum OnSaveResult--><!--Device-AbilityConstant-export enum OnSaveResult-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## ALL_AGREE

```TypeScript
ALL_AGREE = 0
```

Always agreed to save the status.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-OnSaveResult-ALL_AGREE = 0--><!--Device-OnSaveResult-ALL_AGREE = 0-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## CONTINUATION_REJECT

```TypeScript
CONTINUATION_REJECT = 1
```

Rejected to save the status in continuation.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-OnSaveResult-CONTINUATION_REJECT = 1--><!--Device-OnSaveResult-CONTINUATION_REJECT = 1-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## CONTINUATION_MISMATCH

```TypeScript
CONTINUATION_MISMATCH = 2
```

Continuation mismatch.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-OnSaveResult-CONTINUATION_MISMATCH = 2--><!--Device-OnSaveResult-CONTINUATION_MISMATCH = 2-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## RECOVERY_AGREE

```TypeScript
RECOVERY_AGREE = 3
```

Agreed to restore the saved status.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-OnSaveResult-RECOVERY_AGREE = 3--><!--Device-OnSaveResult-RECOVERY_AGREE = 3-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## RECOVERY_REJECT

```TypeScript
RECOVERY_REJECT = 4
```

Rejected to restore the saved status.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-OnSaveResult-RECOVERY_REJECT = 4--><!--Device-OnSaveResult-RECOVERY_REJECT = 4-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## ALL_REJECT

```TypeScript
ALL_REJECT = 5
```

Always rejected to save the status.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-OnSaveResult-ALL_REJECT = 5--><!--Device-OnSaveResult-ALL_REJECT = 5-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
