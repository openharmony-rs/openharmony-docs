# DriverExtensionContext (Driver Extension Context)
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=30ff403ace182f0de0060bb4c7a6927c49cd76ac translatedAt=2026-10-14T05:06:00.864Z pushedAt=2026-10-22T07:51:23.163Z nl=2 -->

The **DriverExtensionContext** module provides the context of **DriverExtensionAbility**. It inherits from **ExtensionContext**.

The **DriverExtensionContext** module provides the operations that need to be actively initiated in the **DriverExtensionAbility** implementation.

> **NOTE**
> 
>  - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>  - The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { DriverExtensionAbility, DriverExtensionContext } from '@kit.DriverDevelopmentKit';
```

## How to Use

Before using **DriverExtensionContext**, you need to obtain it through a **DriverExtensionAbility** child class instance.

```ts
  let context: DriverExtensionContext | undefined;
  class EntryAbility extends DriverExtensionAbility {
    onInit() {
      context = this.context; // Obtain DriverExtensionContext.
    }
  }
```

## DriverExtensionContext.updateDriverState

updateDriverState(): void

Updates the driver state. This interface is reserved and does not provide specific functionality currently.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Driver.ExternalDevice

**Example**

  ```ts
  // The current code implementation depends on the code implementation in the previous section.
  if (context !== undefined) {
    context.updateDriverState();
  }
  ```
