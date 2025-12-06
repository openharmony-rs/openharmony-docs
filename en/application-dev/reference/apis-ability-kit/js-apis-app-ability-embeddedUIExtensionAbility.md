# @ohos.app.ability.EmbeddedUIExtensionAbility (ExtensionAbility for Cross-Process UI Embedding)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

EmbeddedUIExtensionAbility is a component that enables cross-process UI embedding. It inherits from [UIExtensionAbility](js-apis-app-ability-uiExtensionAbility.md).

You can implement this class to add cross-process UI embedding capabilities to your applications. A typical use case is embedding a UI, provided by the application's own EmbeddedUIExtensionAbility, into a [UIAbility](js-apis-app-ability-uiAbility.md) page using an [EmbeddedComponent](../apis-arkui/arkui-ts/ts-container-embedded-component.md).

For details about the inheritance relationship of each ability, see [Inheritance Relationship](./js-apis-app-ability-ability.md#ability-inheritance-relationship).

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { EmbeddedUIExtensionAbility } from '@kit.AbilityKit';
```

## EmbeddedUIExtensionAbility

EmbeddedUIExtensionAbility is a component that enables cross-process UI embedding. It inherits from [UIExtensionAbility](js-apis-app-ability-uiExtensionAbility.md).

Currently, an EmbeddedUIExtensionAbility instance can be started only by a UIAbility that belongs to the same application.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices and tablets. It is unavailable on other devices.
