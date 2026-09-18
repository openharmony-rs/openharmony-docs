# ShareExtensionAbility

ShareExtensionAbility provides extended capabilities for integrating a share details page. It inherits from [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md).

By implementing ShareExtensionAbility, you can process content shared from other applications. For example, you could use ShareExtensionAbility to implement the text sharing feature. When a user initiates a share action in another application, your application will appear as an option in the system share panel. Upon selection, the system activates your application to process the content and display the share detail page.

For details about the inheritance relationship of each ability, see [Inheritance Relationship](../../../reference/apis-ability-kit/js-apis-app-ability-ability.md#ability-inheritance-relationship).

**Inheritance/Implementation:** ShareExtensionAbility extends [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { ShareExtensionAbility } from '@kit.AbilityKit';
```
