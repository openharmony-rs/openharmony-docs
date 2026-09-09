# @ohos.app.ability.ActionExtensionAbility (ExtensionAbility for Custom Actions)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=39c91f6014aebaf032e76cba1dba0db7318cd7f0 translatedAt=2026-09-03T09:52:09.033Z pushedAt=2026-09-05T10:47:30.209Z -->

The ActionExtensionAbility module provides a template for you to implement custom actions. It inherits from [UIExtensionAbility](js-apis-app-ability-uiExtensionAbility.md).

By implementing ActionExtensionAbility, you can provide content viewing and processing functionalities for other applications. For example, you can use ActionExtensionAbility to implement a text translation feature. Other applications can then call this ActionExtensionAbility to process content that requires translation and obtain the translated result.

For details about the inheritance relationship of each ability, see [Inheritance Relationship](./js-apis-app-ability-ability.md#ability-inheritance-relationship).

> **NOTE**
>
> The initial APIs of this module are supported since API version 10 and deprecated since API version 26.0.0. No substitute APIs are provided.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { ActionExtensionAbility } from '@kit.AbilityKit';
```

## ActionExtensionAbility<sup>(deprecated)</sup>

The ActionExtensionAbility module provides a template for you to implement custom actions. It inherits from [UIExtensionAbility](js-apis-app-ability-uiExtensionAbility.md).

ActionExtensionAbility is mainly designed to handle content viewing and interaction within the host application. For example, you can add a bookmark, translate the selected text into another language, or edit an image on the current page.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Since**: 10

**Deprecated since:** 26.0.0

**Substitute API:** No substitute API