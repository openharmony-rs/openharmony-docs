# ActionExtensionAbility

The ActionExtensionAbility module provides a template for you to implement custom actions. It inherits from [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md).

By implementing ActionExtensionAbility, you can provide content viewing and processing functionalities for other applications. For example, you can use ActionExtensionAbility to implement a text translation feature. Other applications can then call this ActionExtensionAbility to process content that requires translation and obtain the translated result.

For details about the inheritance relationship of each ability, see [Inheritance Relationship](../../../reference/apis-ability-kit/js-apis-app-ability-ability.md#ability-inheritance-relationship).

**Inheritance/Implementation:** ActionExtensionAbility extends [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)

**Since:** 10

**Deprecated since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { ActionExtensionAbility } from '@kit.AbilityKit';
```
