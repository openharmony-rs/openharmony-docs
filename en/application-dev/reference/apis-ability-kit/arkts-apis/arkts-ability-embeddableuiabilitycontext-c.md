# EmbeddableUIAbilityContext

```TypeScript
export default class EmbeddableUIAbilityContext extends UIAbilityContext
```

EmbeddableUIAbilityContext provides the context environment for the [EmbeddableUIAbility](arkts-ability-app-ability-embeddableuiability-embeddableuiability-c.md). It inherits from [UIAbilityContext](arkts-ability-uiabilitycontext-c.md).

When an EmbeddableUIAbility component is instantiated, the system automatically creates the corresponding EmbeddableUIAbilityContext.

> **NOTE:** 
> 
> - The APIs of this module must be used in the main thread, but not in child threads such as Worker and TaskPool.

**Inheritance/Implementation:** EmbeddableUIAbilityContext extends [UIAbilityContext](arkts-ability-uiabilitycontext-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
