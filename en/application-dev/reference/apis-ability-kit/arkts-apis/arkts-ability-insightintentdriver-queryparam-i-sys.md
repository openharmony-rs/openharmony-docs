# QueryParam (System API)

```TypeScript
interface QueryParam
```

Intent entity query parameters, used to filter intent entities on the device that meet matching conditions.

**Since:** 26.0.0

<!--Device-insightIntentDriver-interface QueryParam--><!--Device-insightIntentDriver-interface QueryParam-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { insightIntentDriver } from '@kit.AbilityKit';
```

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the application to which the target intent entity belongs.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-QueryParam-bundleName: string--><!--Device-QueryParam-bundleName: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## className

```TypeScript
className: string
```

Class name of the target intent entity decorated by [@InsightIntentEntity](arkts-ability-app-ability-insightintentdecorator-insightintententity-d.md#insightintententity).

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-QueryParam-className: string--><!--Device-QueryParam-className: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## intentName

```TypeScript
intentName: string
```

Intent name to which the target intent entity belongs.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-QueryParam-intentName: string--><!--Device-QueryParam-intentName: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## moduleName

```TypeScript
moduleName: string
```

Module name to which the target intent entity belongs.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-QueryParam-moduleName: string--><!--Device-QueryParam-moduleName: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## queryEntityParam

```TypeScript
queryEntityParam: insightIntent.QueryEntityParam
```

Intent entity query parameters, including the query mode and query conditions, used to specify how intent entities are queried.

**Type:** [insightIntent.QueryEntityParam](arkts-ability-insightintent-queryentityparam-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-QueryParam-queryEntityParam: insightIntent.QueryEntityParam--><!--Device-QueryParam-queryEntityParam: insightIntent.QueryEntityParam-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## userId

```TypeScript
userId?: number
```

User ID to which the target intent entity belongs.

> **NOTE:** 
> 
> If the user ID of the caller application differs from the user ID to which the target intent
> entity belongs, the ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permission is required.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-QueryParam-userId?: int--><!--Device-QueryParam-userId?: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
