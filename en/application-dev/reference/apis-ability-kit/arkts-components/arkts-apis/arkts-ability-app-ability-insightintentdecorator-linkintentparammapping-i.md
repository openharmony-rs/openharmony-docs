# LinkIntentParamMapping

LinkIntentParamMapping defines the mapping between intent parameters and URI information for the [@InsightIntentLink](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink) decorator.

**Since:** 20

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { InsightIntentLink, InsightIntentPage, InsightIntentFunctionMethod, InsightIntentFunction, InsightIntentEntry, LinkParamCategory, InsightIntentForm, InsightIntentEntity } from '@kit.AbilityKit';
```

## paramCategory

```TypeScript
paramCategory?: LinkParamCategory
```

Category of the intent parameter.

If an intent parameter is of the [LINK](arkts-ability-app-ability-insightintentdecorator-linkparamcategory-e.md) category, the system retrieves **paramMappingName** corresponding to **paramName** and appends it to the URI as a key-value pair (where **key** is the value of **paramMappingName**, and **value** is the intent parameter value).

If an intent parameter is of the [WANT](arkts-ability-app-ability-insightintentdecorator-linkparamcategory-e.md) category, the system retrieves **paramMappingName** corresponding to **paramName** and passes the mapping name and value using the **parameters** field in [Want](arkts-ability-app-ability-want-want-c.md).

**Type:** [LinkParamCategory](arkts-ability-app-ability-insightintentdecorator-linkparamcategory-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## paramMappingName

```TypeScript
paramMappingName?: string
```

Mapping name of the intent parameter.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## paramName

```TypeScript
paramName: string
```

Name of the intent parameter.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
