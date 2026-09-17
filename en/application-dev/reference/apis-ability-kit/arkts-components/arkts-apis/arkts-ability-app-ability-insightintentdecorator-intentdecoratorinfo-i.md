# IntentDecoratorInfo

Common properties for intent decorators, used to define basic information about an intent (including the intent name and version number). It applies to all decorators provided by this module.

> **NOTE:** 
> 
> If a matching intent is found in the standard intent list based on the **schema** and **intentVersion** fields, the
> system automatically populates the **intentName**, **domain**, **llmDescription**, **keywords**, **parameters**,
> and **result** fields with the values from the matching standard intent.

**Since:** 20

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { InsightIntentLink, InsightIntentPage, InsightIntentFunctionMethod, InsightIntentFunction, InsightIntentEntry, LinkParamCategory, InsightIntentForm, InsightIntentEntity } from '@kit.AbilityKit';
```

## displayDescription

```TypeScript
displayDescription?: string
```

Description of the intent displayed to users.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## displayName

```TypeScript
displayName: string
```

Name of the intent displayed to users.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## domain

```TypeScript
domain: string
```

Vertical domain of the intent. It is used to categorize intents by vertical fields (for example, video, music, and games). For details about the value range, see the vertical domain fields in [smart distribution features in different vertical domains](https://developer.huawei.com/consumer/en/doc/service/intents-ai-distribution-characteristic-0000001901922213#section2656133582215).

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## icon

```TypeScript
icon?: ResourceStr
```

Icon of the intent. It is displayed in the AI entry point.

- If the value is a string, the icon is read from a network resource.  
- If the value is a [resource](../../reference/apis-localization-kit/js-apis-resource-manager.md), the icon is read  
from a local resource.

**Type:** [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## intentName

```TypeScript
intentName: string
```

Intent name, which is the unique identifier of an intent.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## intentVersion

```TypeScript
intentVersion: string
```

Version number of the intent. It is used to distinguish and manage intents when their capabilities evolve.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## keywords

```TypeScript
keywords?: string[]
```

Search keywords for the intent.

**Type:** string[]

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## llmDescription

```TypeScript
llmDescription?: string
```

Function of an intent, which helps large language models understand the intent.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## parameters

```TypeScript
parameters?: Record<string, Object>
```

Data format of intent parameters, which is used to define the input data format during intent calls.

**Type:** Record&lt;string, Object&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## result

```TypeScript
result?: Record<string, Object>
```

Data format for the results returned by intent calls. It defines how the data should be structured.

**Type:** Record&lt;string, Object&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## schema

```TypeScript
schema?: string
```

Name of a standard intent schema. This field is required when you [access a standard intent](../../../application-models/insight-intent-definition.md#accessing-standard-intents). It is not required when you [create a custom intent](../../../application-models/insight-intent-definition.md#creating-custom-intents). For details about the standard intent list, see [Appendix: Standard Intent Access Specifications](../../../application-models/insight-intent-access-specifications.md).

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
