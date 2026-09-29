# QueryEntityParam

```TypeScript
interface QueryEntityParam
```

Parameter for query entity.

**Since:** 26.0.0

<!--Device-insightIntent-interface QueryEntityParam--><!--Device-insightIntent-interface QueryEntityParam-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { insightIntent } from '@kit.AbilityKit';
```

## parameters

```TypeScript
parameters?: Record<string, Object>
```

Indicates the parameters when querying entities by property.

**Type:** Record&lt;string, Object&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-QueryEntityParam-parameters?: Record<string, Object>--><!--Device-QueryEntityParam-parameters?: Record<string, Object>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## queryType

```TypeScript
queryType: QueryType
```

The query type.

**Type:** [QueryType](arkts-ability-insightintent-querytype-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-QueryEntityParam-queryType: QueryType--><!--Device-QueryEntityParam-queryType: QueryType-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
