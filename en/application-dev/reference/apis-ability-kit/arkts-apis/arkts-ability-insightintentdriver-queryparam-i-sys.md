# QueryParam (System API)

Param when query insight intent entity.

@typedef QueryParam

**Since:** 26.0.0

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

Indicates the bundle name.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## className

```TypeScript
className: string
```

Indicates the entity class name.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## intentName

```TypeScript
intentName: string
```

Indicates the intent name.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## moduleName

```TypeScript
moduleName: string
```

Indicates the module name.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## queryEntityParam

```TypeScript
queryEntityParam: insightIntent.QueryEntityParam
```

Indicates the param for query entity.

**Type:** [insightIntent.QueryEntityParam](arkts-ability-insightintent-queryentityparam-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## userId

```TypeScript
userId?: number
```

Indicates the target user ID.

If the user ID of the caller application is different from the target user ID, you need to apply for permission: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
