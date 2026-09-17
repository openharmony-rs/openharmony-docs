# WorkSchedulerExtensionContext

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=76d1d65f298d7d63cfb8a09c303008923aa8d35e translatedAt=2026-09-15T14:00:43.358Z pushedAt=2026-09-17T09:19:10.170Z -->

**WorkSchedulerExtensionContext** is the context of [WorkSchedulerExtensionAbility](./js-apis-WorkSchedulerExtensionAbility.md#workschedulerextensionability) and inherits from [ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md).

WorkSchedulerExtensionContext can be directly used as the context environment of WorkSchedulerExtension, providing the ability to access resources specific to WorkSchedulerExtensionAbility.

> **NOTE**
> 
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> 
> - The APIs of this module can be used only in the stage model.

## How to Use

Obtain the **WorkSchedulerExtensionContext** based on the **context** attribute of a **WorkSchedulerExtensionAbility** child class instance.

```ts
import { WorkSchedulerExtensionAbility, workScheduler } from '@kit.BackgroundTasksKit';

class MyWorkSchedulerExtensionAbility extends WorkSchedulerExtensionAbility {
  onWorkStart(workInfo: workScheduler.WorkInfo) {
    let workSchedulerExtensionContext = this.context; // Obtain the WorkSchedulerExtensionContext.
  }
}
```

## WorkSchedulerExtensionContext

Provides a context environment for the **WorkSchedulerExtensionAbility**.

**System capability**: SystemCapability.ResourceSchedule.WorkScheduler

**Model restriction**: The APIs of this module can be used only in the stage model.
