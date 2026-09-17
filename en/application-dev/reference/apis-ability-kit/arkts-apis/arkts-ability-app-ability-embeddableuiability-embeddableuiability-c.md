# EmbeddableUIAbility

EmbeddableUIAbility is an embeddable UIAbility component provided for atomic services. It inherits from [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md). You can implement EmbeddableUIAbility to enable atomic services to be launched by other applications either as a standalone window or embedded within the host application's UI. For details about the inheritance relationship of each ability, see [Inheritance Relationship](../../../reference/apis-ability-kit/js-apis-app-ability-ability.md#ability-inheritance-relationship).

**Inheritance/Implementation:** EmbeddableUIAbility extends [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md)

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { EmbeddableUIAbility } from '@kit.AbilityKit';
```

## context

```TypeScript
context: EmbeddableUIAbilityContext
```

Context of the EmbeddableUIAbility.

**Type:** [EmbeddableUIAbilityContext](arkts-ability-embeddableuiabilitycontext-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
