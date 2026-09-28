# @ohos.app.ability.ExtensionAbility (ExtensionAbility Base Class)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @xialiangwei-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=a914ec5c20531defc3768aa8242b62bbe2d1d08f translatedAt=2026-09-03T10:17:51.380Z pushedAt=2026-09-05T10:47:30.386Z -->

ExtensionAbility is the base class for scenario-specific extension capabilities. It inherits from [Ability](js-apis-app-ability-ability.md), with no property or method added. You cannot directly inherit from ExtensionAbility. Instead, you should inherit from its concrete subclasses (such as <!--Del-->ServiceExtensionAbility, <!--DelEnd-->FormExtensionAbility, and so on) to implement scenario-specific extension capabilities. For details about the inheritance relationship of various abilities, see [Inheritance Relationship](./js-apis-app-ability-ability.md#ability-inheritance-relationship).

> **NOTE**
> 
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { ExtensionAbility } from '@kit.AbilityKit';
```

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore
