# EntityInfo (System API)

```TypeScript
interface EntityInfo
```

EntityInfo inherits from [IntentEntityDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intententitydecoratorinfo-i.md) and is used to describe the information about the intent entity defined by the [@InsightIntentEntity](arkts-ability-app-ability-insightintentdecorator-insightintententity-d.md#insightintententity) decorator.

**Since:** 20

<!--Device-insightIntentDriver-interface EntityInfo--><!--Device-insightIntentDriver-interface EntityInfo-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { insightIntentDriver } from '@kit.AbilityKit';
```

## className

```TypeScript
readonly className: string
```

Class name decorated by [@InsightIntentEntity](arkts-ability-app-ability-insightintentdecorator-insightintententity-d.md#insightintententity).

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-EntityInfo-readonly className: string--><!--Device-EntityInfo-readonly className: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## entityCategory

```TypeScript
readonly entityCategory: string
```

Category of the intent entity.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-EntityInfo-readonly entityCategory: string--><!--Device-EntityInfo-readonly entityCategory: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## entityId

```TypeScript
readonly entityId: string
```

ID of the intent entity.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-EntityInfo-readonly entityId: string--><!--Device-EntityInfo-readonly entityId: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## isQueryable

```TypeScript
readonly isQueryable?: boolean
```

Whether the intent entity class decorated by [@InsightIntentEntity](arkts-ability-app-ability-insightintentdecorator-insightintententity-d.md#insightintententity) supports query. Only intent entities inherited from the [insightIntent.AppIntentEntity](arkts-ability-insightintent-appintententity-c.md) class support query.  
- true: query is supported.  
- false: query is not supported.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-EntityInfo-readonly isQueryable?: boolean--><!--Device-EntityInfo-readonly isQueryable?: boolean-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## parameters

```TypeScript
readonly parameters: Record<string, Object>
```

Data format declaration of the intent entity parameters, used to define the data format of entity parameters during intent invocation.

**Type:** Record&lt;string, Object&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-EntityInfo-readonly parameters: Record<string, Object>--><!--Device-EntityInfo-readonly parameters: Record<string, Object>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## parentClassName

```TypeScript
readonly parentClassName: string
```

Parent class name decorated by [@InsightIntentEntity](arkts-ability-app-ability-insightintentdecorator-insightintententity-d.md#insightintententity).

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-EntityInfo-readonly parentClassName: string--><!--Device-EntityInfo-readonly parentClassName: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## supportedQueryProperties

```TypeScript
readonly supportedQueryProperties?: string[]
```

Properties through which the intent entity decorated by [@InsightIntentEntity](arkts-ability-app-ability-insightintentdecorator-insightintententity-d.md#insightintententity) supports query. The key value of the intent entity query parameter [parameters](arkts-ability-insightintent-queryentityparam-i.md) must be in this property list.

**Type:** string[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-EntityInfo-readonly supportedQueryProperties?: string[]--><!--Device-EntityInfo-readonly supportedQueryProperties?: string[]-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
