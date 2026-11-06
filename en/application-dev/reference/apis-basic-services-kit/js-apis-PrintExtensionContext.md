# PrintExtensionContext

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @baozewei-->
<!--Tester: @baozewei-->
<!--Adviser: @fang-jinxu-->

**PrintExtensionContext** represents the context of **PrintExtensionAbility** and is inherited from [ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md).

It can be directly used as the context of **PrintExtensionAbility** to obtain and manage printing resources for printing extension development, so as to complete printing tasks. For details about the design logic and accessible resources of **PrintExtensionContext**, see [PrintExtensionAbility](js-apis-app-ability-PrintExtensionAbility.md) and [ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md).

> **NOTE**
>
> - The APIs of this module can be used only in the stage model.
> - **Since:** 26.0.0

## Modules to Import
```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';
```
## How to Use

Obtain **PrintExtensionContext** through a **PrintExtensionAbility** child class instance.

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

export default class PrintExtension extends PrintExtensionAbility {

  onCreate(want: Want) {
    let context = this.context; // Obtain PrintExtensionContext, which can be used to access printing resources.
  }
}
```
