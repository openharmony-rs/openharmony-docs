# BaseContext

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

BaseContext is an abstract class that specifies whether a child class Context is used for the stage model or FA model. It is the parent class for all types of Context.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { common } from '@kit.AbilityKit';
```

## Attributes

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name      | Type  | Read-Only  | Optional  | Description     |
| -------- | ------ | ---- | ---- | ------- |
| stageMode | boolean | No   | No   | Whether the child class Context is used for the stage model.<br>**true**: [Stage model](../../application-models/ability-terminology.md#stage-model).<br>**false**: [FA model](../../application-models/ability-terminology.md#fa-model).|

**Example**

Take the stage model as an example. You can access the **stageMode** field through UIAbilityContext.

```ts
import { UIAbility, AbilityConstant, Want } from '@kit.AbilityKit';

class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    // EntryAbility onCreate, isStageMode: true
    console.info(`EntryAbility onCreate, isStageMode: ${this.context.stageMode}`);
  }
}
```
