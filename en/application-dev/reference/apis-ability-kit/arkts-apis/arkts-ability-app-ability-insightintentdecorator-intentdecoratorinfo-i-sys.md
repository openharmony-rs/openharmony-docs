# IntentDecoratorInfo (System API)

```TypeScript
declare interface IntentDecoratorInfo
```

Common properties for intent decorators, used to define basic information about an intent (including the intent name and version number). It applies to all decorators provided by this module.

> **NOTE:** 
> 
> If a matching intent is found in the standard intent list based on the **schema** and **intentVersion** fields, the
> system automatically populates the **intentName**, **domain**, **llmDescription**, **keywords**, **parameters**,
> and **result** fields with the values from the matching standard intent.

**Since:** 20

<!--Device-unnamed-declare interface IntentDecoratorInfo--><!--Device-unnamed-declare interface IntentDecoratorInfo-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { InsightIntentLink, InsightIntentPage, InsightIntentFunctionMethod, InsightIntentFunction, InsightIntentEntry, LinkParamCategory, InsightIntentForm, InsightIntentEntity } from '@kit.AbilityKit';
```

## exported

```TypeScript
exported?: boolean
```

Specifies whether the intent can be called by third-party applications. The value true indicates the intent can be called by third-party applications. The value false indicates the intent cannot be called by third-party applications. Default value: false.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-IntentDecoratorInfo-exported?: boolean--><!--Device-IntentDecoratorInfo-exported?: boolean-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
