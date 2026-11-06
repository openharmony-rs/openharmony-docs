# @ohos.app.form.FormEditExtensionAbility (FormEditExtensionAbility)
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @Qian-Win-->
<!--Designer: @cx983299475-->
<!--Tester: @mahailong123456-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=3d88c7ae24e860f42daeed81a30fca056541e740 translatedAt=2026-11-03T06:48:36.444Z pushedAt=2026-11-04T03:11:19.922Z nl=1 -->

The FormEditExtensionAbility module provides widget editing capability, allowing users to edit widget content within the widget provider application. It is suitable for scenarios where widget display information needs to be dynamically updated or personalized configuration is required. This module inherits from [UIExtensionAbility](../apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md).

> **NOTE**
>
> The initial APIs of this module are supported since API version 18. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { FormEditExtensionAbility } from '@kit.FormKit';
```
## FormEditExtensionAbility

Provides widget editing capability. After this class is inherited and lifecycle methods are implemented, a widget editing UI can be implemented, which is used to trigger widget editing in scenarios such as when the user long presses a widget.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.Form
  | Name| Type   | Read-Only| Optional |Description|
  | ------ | ------ | ---- | ---- | ---- |
  | context | [FormEditExtensionContext](./js-apis-inner-application-formEditExtensionContext.md) | No | No | Context of FormEditExtensionAbility. [FormEditExtensionContext](./js-apis-inner-application-formEditExtensionContext.md) inherits from [UIExtensionContext](../apis-ability-kit/js-apis-inner-application-uiExtensionContext.md#uiextensioncontext-1). It provides the capability to launch the editing page.|