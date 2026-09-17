# EmbeddedUIExtensionAbility

EmbeddedUIExtensionAbility is a component that enables cross-process UI embedding. It inherits from [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md). You can implement this class to add cross-process UI embedding capabilities to your applications. A typical use case is embedding a UI, provided by the application's own EmbeddedUIExtensionAbility, into a [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) page using an EmbeddedComponent. For details about the inheritance relationship of each ability, see [Inheritance Relationship](../../../reference/apis-ability-kit/js-apis-app-ability-ability.md#ability-inheritance-relationship). This API can be properly called on PCs/2-in-1 devices and tablets. It is unavailable on other devices.

**Inheritance/Implementation:** EmbeddedUIExtensionAbility extends [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { EmbeddedUIExtensionAbility } from '@kit.AbilityKit';
```
