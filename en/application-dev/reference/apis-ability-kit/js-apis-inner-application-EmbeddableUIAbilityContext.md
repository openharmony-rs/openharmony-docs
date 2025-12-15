# EmbeddableUIAbilityContext

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

EmbeddableUIAbilityContext provides the context environment for the [EmbeddableUIAbility](js-apis-app-ability-embeddableUIAbility.md). It inherits from [UIAbilityContext](js-apis-inner-application-uiAbilityContext.md).

When an EmbeddableUIAbility component is instantiated, the system automatically creates the corresponding EmbeddableUIAbilityContext.


> **NOTE**
>
>  - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>  - The APIs of this module can be used only in the stage model.
>  - The APIs of this module must be used in the main thread, but not in child threads such as Worker and TaskPool.

## Modules to Import

```ts
import { common } from '@kit.AbilityKit';
```

## EmbeddableUIAbilityContext 
Through the EmbeddableUIAbilityContext, you can obtain the EmbeddableUIAbility-related configuration and APIs for operating EmbeddableUIAbility and ServiceExtensionAbility components. For example, you can use the APIs to start an EmbeddableUIAbility, terminate an EmbeddableUIAbility to which the EmbeddableUIAbilityContext belongs, and start, terminate, connect to, or disconnect from a ServiceExtensionAbility.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 12.
