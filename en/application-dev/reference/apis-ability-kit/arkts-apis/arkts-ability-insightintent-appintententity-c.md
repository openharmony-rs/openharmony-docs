# AppIntentEntity

```TypeScript
abstract class AppIntentEntity<T> implements IntentEntity
```

Define AppIntentEntity.

**Inheritance/Implementation:** AppIntentEntity implements [IntentEntity](arkts-ability-insightintent-intententity-i.md)

**Since:** 26.0.0

<!--Device-insightIntent-abstract class AppIntentEntity<T> implements IntentEntity--><!--Device-insightIntent-abstract class AppIntentEntity<T> implements IntentEntity-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { insightIntent } from '@kit.AbilityKit';
```

## onQueryEntity

```TypeScript
abstract onQueryEntity(params: QueryEntityParam): Promise<Array<T>>
```

Called when query entity execute.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-AppIntentEntity-abstract onQueryEntity(params: QueryEntityParam): Promise<Array<T>>--><!--Device-AppIntentEntity-abstract onQueryEntity(params: QueryEntityParam): Promise<Array<T>>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [QueryEntityParam](arkts-ability-insightintent-queryentityparam-i.md) | Yes | The params of query entity. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;T&gt;&gt; | Returns an array of subclasses of the AppIntentEntity class, support promise. |

**Examples**

## displayName

```TypeScript
displayName: string
```

The display name of entity.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-AppIntentEntity-displayName: string--><!--Device-AppIntentEntity-displayName: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
