# IntentResult

```TypeScript
interface IntentResult<T>
```

Defines the return result of intent execution. The [generic type](../../../quick-start/introduction-to-arkts.md#generic-class-and-interface) is supported.

**Since:** 20

<!--Device-insightIntent-interface IntentResult<T>--><!--Device-insightIntent-interface IntentResult<T>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { insightIntent } from '@kit.AbilityKit';
```

## interactionInfo

```TypeScript
interactionInfo?: InteractionInfo
```

Interaction information returned after the intent execution completes.

**Type:** [InteractionInfo](arkts-ability-insightintent-interactioninfo-i-sys.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-IntentResult-interactionInfo?: InteractionInfo--><!--Device-IntentResult-interactionInfo?: InteractionInfo-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
