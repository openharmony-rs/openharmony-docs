# IntentEntity

```TypeScript
interface IntentEntity
```

Defines the struct of an intent entity. It represents key information objects involved during intent execution, including intent parameters and execution results.

You can define intent entities by inheriting this class. The child class must be decorated with [@InsightIntentEntity](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintententity).

**Since:** 20

<!--Device-insightIntent-interface IntentEntity--><!--Device-insightIntent-interface IntentEntity-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { insightIntent } from '@kit.AbilityKit';
```

## entityId

```TypeScript
entityId: string
```

ID of the intent entity.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-IntentEntity-entityId: string--><!--Device-IntentEntity-entityId: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
