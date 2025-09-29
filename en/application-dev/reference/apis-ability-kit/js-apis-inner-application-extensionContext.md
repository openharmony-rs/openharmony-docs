# ExtensionContext
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yewei0794-->
<!--Designer: @jsjzju-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

ExtensionContext provides the context environment for an [ExtensionAbility](js-apis-app-ability-extensionAbility.md). It inherits from [Context](js-apis-inner-application-context.md#context).

This module provides APIs for accessing resources of a specific [ExtensionAbility](js-apis-app-ability-extensionAbility.md). An ExtensionAbility can use the context directly provided by ExtensionContext or that extended from ExtensionContext.

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
| currentHapModuleInfo | [HapModuleInfo](js-apis-bundleManager-hapModuleInfo.md) | No| No| Information about the HAP file.|
| config   | [Configuration](js-apis-app-ability-configuration.md) | No| No| Module configuration information.|
| extensionAbilityInfo | [ExtensionAbilityInfo](js-apis-bundleManager-extensionAbilityInfo.md) | No| No| [ExtensionAbility](js-apis-app-ability-extensionAbility.md) information.|

## When to Use
ExtensionContext provides information about an ExtensionAbility, module, and HAP file. You can use the information based on service requirements.

**Example**

Obtain the context of a [FormExtensionAbility](../apis-form-kit/js-apis-app-form-formExtensionAbility.md) and query information such as its HAP file.

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
