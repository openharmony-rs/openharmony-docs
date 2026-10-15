# BaseContext

```TypeScript
export default abstract class BaseContext
```

BaseContext is an abstract class that specifies whether a child class Context is used for the stage model or FA model. It is the parent class for all types of Context.

**Since:** 8

<!--Device-unnamed-export default abstract class BaseContext--><!--Device-unnamed-export default abstract class BaseContext-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## stageMode

```TypeScript
stageMode: boolean
```

Whether the child class Context is used for the stage model. true: [Stage model](../../../application-models/ability-terminology.md#stage-model). false：[FA model](../../../application-models/ability-terminology.md#fa-model).

**Type:** boolean

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-BaseContext-stageMode: boolean--><!--Device-BaseContext-stageMode: boolean-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
