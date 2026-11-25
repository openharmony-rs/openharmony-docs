# PrintExtensionContext

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @Zouhaifeng1-->
<!--Designer: @baozewei-->
<!--Tester: @baozewei-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=cfbd32eaf8f6889081f1f689234b5a5bcadff8c8 translatedAt=2026-11-23T01:50:14.530Z pushedAt=2026-11-23T12:17:20.897Z nl=1 -->

**PrintExtensionContext** represents the context of **PrintExtensionAbility** and inherits from [ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md).

**PrintExtensionContext** can be directly used as the context of **PrintExtensionAbility** to obtain and manage print-related resources in print extension development scenarios, so as to complete operations related to print tasks. For details about the design logic and accessible resources of **PrintExtensionContext**, see [PrintExtensionAbility](js-apis-app-ability-PrintExtensionAbility.md) and [ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md).

> **NOTE**
>
> - The APIs of this module can be used only in the stage model.
> - **Since:** 26.0.0

## Modules to Import
```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';
```
## How to Use

Obtain the **PrintExtensionContext** through a **PrintExtensionAbility** subclass instance.

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

export default class PrintExtension extends PrintExtensionAbility {

  onCreate(want: Want) {
    let context = this.context; // Obtain the PrintExtensionContext. You can then access print-related resources through context.
  }
}
```
