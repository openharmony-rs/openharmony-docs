# ExtensionContext
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @xialiangwei-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=54a85e57a9e078c186b756489db16f65a538d313 translatedAt=2026-09-03T11:57:44.867Z pushedAt=2026-09-05T10:47:30.796Z -->

ExtensionContext is the context environment of an [ExtensionAbility](js-apis-app-ability-extensionAbility.md). It inherits from [Context](js-apis-inner-application-context.md#context) and is used to access the resources of a specific ExtensionAbility, and to obtain HAP module information, configuration information, and information about the ExtensionAbility itself.

This module provides APIs for accessing the information of a specific [ExtensionAbility](js-apis-app-ability-extensionAbility.md).

> **NOTE**
>
>  - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>  - The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { common } from '@kit.AbilityKit';
```

## Attributes

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| currentHapModuleInfo | [HapModuleInfo](js-apis-bundleManager-hapModuleInfo.md) | No | No | Information about the HAP module to which the current ExtensionAbility belongs, including the module name, type, and description. |
| config   | [Configuration](js-apis-app-ability-configuration.md) | No | No | Configuration information of the current ExtensionAbility, which can be used to obtain the language, color mode, and other configurations. |
| extensionAbilityInfo | [ExtensionAbilityInfo](js-apis-bundleManager-extensionAbilityInfo.md) | No | No | Information about the current ExtensionAbility, including the name, type, label ID, and so on. |

## When to Use
ExtensionContext is mainly used to query the information about the ExtensionAbility to which it belongs, the configuration information of the module, and the information about the HAP module. This helps developers fully understand the runtime environment and configuration of the extension ability, so that they can perform correct logic processing based on actual service requirements.

**Example**

Obtain the context in the extended [FormExtensionAbility](../apis-form-kit/js-apis-app-form-formExtensionAbility.md), and query the information such as the HAP module to which the FormExtensionAbility of the extension belongs.

```ts
import { FormExtensionAbility, formBindingData } from '@kit.FormKit';
import { Want } from '@kit.AbilityKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onAddForm(want: Want) {
    console.info(`FormExtensionAbility onAddForm, want: ${want.abilityName}`);
    let extensionContext = this.context;
    let hapInfo = extensionContext.currentHapModuleInfo;
    console.info(`HAP name is: ${hapInfo.name}`);
    let dataObj1: Record<string, string> = {
      'temperature': '11c',
      'time': '11:00'
    };
    let obj1: formBindingData.FormBindingData = formBindingData.createFormBindingData(dataObj1);
    return obj1;
  }
};
```
