# @ohos.app.ability.ShareExtensionAbility (ExtensionAbility for Share Detail Page Integration)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

ShareExtensionAbility provides extended capabilities for integrating a share details page. It inherits from [UIExtensionAbility](js-apis-app-ability-uiExtensionAbility.md).

By implementing ShareExtensionAbility, you can process content shared from other applications. For example, you could use ShareExtensionAbility to implement the text sharing feature. When a user initiates a share action in another application, your application will appear as an option in the system share panel. Upon selection, the system activates your application to process the content and display the share detail page.

For details about the inheritance relationship of each ability, see [Inheritance Relationship](./js-apis-app-ability-ability.md#ability-inheritance-relationship).

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { ShareExtensionAbility } from '@kit.AbilityKit';
```

## ShareExtensionAbility

ShareExtensionAbility provides extended capabilities for integrating share details pages. It inherits from [UIExtensionAbility](js-apis-app-ability-uiExtensionAbility.md).

This module allows you to create share detail pages that can receive shared content, and it places the application entry in the recommended applications area on the system share panel.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core
