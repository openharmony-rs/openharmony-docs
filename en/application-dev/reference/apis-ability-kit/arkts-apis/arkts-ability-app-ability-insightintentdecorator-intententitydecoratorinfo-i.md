# IntentEntityDecoratorInfo

```TypeScript
declare interface IntentEntityDecoratorInfo
```

Describes the parameters supported by the [@InsightIntentEntity](arkts-ability-app-ability-insightintentdecorator-insightintententity-d.md#insightintententity) decorator.

**Since:** 20

<!--Device-unnamed-declare interface IntentEntityDecoratorInfo--><!--Device-unnamed-declare interface IntentEntityDecoratorInfo-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { InsightIntentLink, InsightIntentPage, InsightIntentFunctionMethod, InsightIntentFunction, InsightIntentEntry, LinkParamCategory, InsightIntentForm, InsightIntentEntity } from '@kit.AbilityKit';
```

## entityCategory

```TypeScript
entityCategory: string
```

Category of the intent entity. Intents can be classified based on intent entity categories.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-IntentEntityDecoratorInfo-entityCategory: string--><!--Device-IntentEntityDecoratorInfo-entityCategory: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## parameters

```TypeScript
parameters?: Record<string, Object>
```

Data format of the intent entity.

**Type:** Record&lt;string, Object&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-IntentEntityDecoratorInfo-parameters?: Record<string, Object>--><!--Device-IntentEntityDecoratorInfo-parameters?: Record<string, Object>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## supportedQueryProperties

```TypeScript
supportedQueryProperties?: string[]
```

List of attributes supported for querying the intent entity. The attribute names in the list must be defined in parameters.

**Type:** string[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-IntentEntityDecoratorInfo-supportedQueryProperties?: string[]--><!--Device-IntentEntityDecoratorInfo-supportedQueryProperties?: string[]-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
