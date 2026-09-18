# @ohos.app.ability.insightIntent(Basic Definitions of InsightIntent Framework)

This module provides basic definitions of the [InsightIntent framework](../../../application-models/insight-intent-overview.md).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { insightIntent } from '@kit.AbilityKit';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [AppIntentEntity](arkts-ability-insightintent-appintententity-c.md) | Define AppIntentEntity. |

### Interfaces

| Name | Description |
| --- | --- |
| [ExecuteResult](arkts-ability-insightintent-executeresult-i.md) | Enumerates the return results of intent execution. |
| [IntentEntity](arkts-ability-insightintent-intententity-i.md) | Defines the struct of an intent entity. It represents key information objects involved during intent execution, including intent parameters and execution results. |
| [IntentResult](arkts-ability-insightintent-intentresult-i.md) | Defines the return result of intent execution. The [generic type](../../../quick-start/introduction-to-arkts.md#generic-class-and-interface) is supported. |
| [QueryEntityParam](arkts-ability-insightintent-queryentityparam-i.md) | Parameter for query entity. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [ExecuteResult](arkts-ability-insightintent-executeresult-i-sys.md) | Enumerates the return results of intent execution. |
| [IntentResult](arkts-ability-insightintent-intentresult-i-sys.md) | Defines the return result of intent execution. The [generic type](../../../quick-start/introduction-to-arkts.md#generic-class-and-interface) is supported. |
| [InteractionInfo](arkts-ability-insightintent-interactioninfo-i-sys.md) | Defines the interaction information returned after the current intent execution completes, including the next intent to be triggered and the interaction UI to be displayed. |
| [InteractionModalUIExtension](arkts-ability-insightintent-interactionmodaluiextension-i-sys.md) | Defines the information of the modal UIExtension to be displayed as the interaction UI after the current intent execution completes. Does not support distributed scenarios. |
| [InteractionUI](arkts-ability-insightintent-interactionui-i-sys.md) | Defines the base information of the interaction UI to be displayed after the current intent execution completes. This is a base class. Use its subclasses such as [InteractionModalUIExtension](arkts-ability-insightintent-interactionmodaluiextension-i-sys.md) in practice. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [ExecuteMode](arkts-ability-insightintent-executemode-e.md) | Enumerates the intent execution modes. It specifies the mode of execution passed when the intent is triggered by a system entry point. The supported execution modes for each intent are defined during intent development. |
| [QueryType](arkts-ability-insightintent-querytype-e.md) | Enum for query entity mode. |
| [ReturnMode](arkts-ability-insightintent-returnmode-e.md) | Enumerates the modes that define how the execution result of an intent is returned to the intent initiator. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ExecuteMode](arkts-ability-insightintent-executemode-e-sys.md) | Enumerates the intent execution modes. It specifies the mode of execution passed when the intent is triggered by a system entry point. The supported execution modes for each intent are defined during intent development. |
<!--DelEnd-->
