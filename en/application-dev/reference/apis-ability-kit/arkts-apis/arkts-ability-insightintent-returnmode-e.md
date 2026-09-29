# ReturnMode

```TypeScript
enum ReturnMode
```

Enumerates the modes that define how the execution result of an intent is returned to the intent initiator.

**Since:** 23

<!--Device-insightIntent-enum ReturnMode--><!--Device-insightIntent-enum ReturnMode-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## CALLBACK

```TypeScript
CALLBACK = 0
```

The intent execution result is returned through the [onExecuteInUIAbilityForegroundMode](arkts-ability-app-ability-insightintentexecutor-insightintentexecutor-c.md#onexecuteinuiabilityforegroundmode) or [onExecuteInUIExtensionAbility](arkts-ability-app-ability-insightintentexecutor-insightintentexecutor-c.md#onexecuteinuiextensionability) API in the [intent execution base class](arkts-ability-app-ability-insightintentexecutor-insightintentexecutor-c.md).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-ReturnMode-CALLBACK = 0--><!--Device-ReturnMode-CALLBACK = 0-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## FUNCTION

```TypeScript
FUNCTION = 1
```

The intent execution result is returned after the [sendExecuteResult](arkts-ability-insightintentprovider-sendexecuteresult-f.md) or [sendIntentResult](arkts-ability-insightintentprovider-sendintentresult-f.md) API in [intent provider management](arkts-ability-app-ability-insightintentprovider.md) is called.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-ReturnMode-FUNCTION = 1--><!--Device-ReturnMode-FUNCTION = 1-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
