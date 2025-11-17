# @ohos.app.ability.EmbeddableUIAbility (Embeddable UIAbility)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

EmbeddableUIAbility is an embeddable UIAbility component provided for atomic services. It inherits from [UIAbility](js-apis-app-ability-uiAbility.md).

You can implement EmbeddableUIAbility to enable atomic services to be launched by other applications either as a standalone window or embedded within the host application's UI.

For details about the inheritance relationship of each ability, see [Inheritance Relationship](./js-apis-app-ability-ability.md#ability-inheritance-relationship).

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { EmbeddableUIAbility } from '@kit.AbilityKit';
```

## EmbeddableUIAbility

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 12.

| Name| Type| Read-only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| context | [EmbeddableUIAbilityContext](js-apis-inner-application-EmbeddableUIAbilityContext.md) | No| No| Context of the EmbeddableUIAbility.|
