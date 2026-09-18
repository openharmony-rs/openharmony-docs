# @ohos.WorkSchedulerExtensionAbility(Deferred Task Scheduling Callbacks)

The **WorkSchedulerExtensionAbility** module provides callbacks for deferred task scheduling. You can override the
 APIs provided by this module. When a deferred task is triggered, the system calls back the application through the
 APIs and processes the task logic in the callback.



## Modules to Import

```TypeScript
import { WorkSchedulerExtensionAbility, WorkSchedulerExtensionContext } from '@kit.BackgroundTasksKit';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [WorkSchedulerExtensionAbility](arkts-backgroundtasks-workschedulerextensionability-c.md) | Provides callbacks to be invoked when the scheduling conditions are met or the scheduling ends, for example, [onWorkStart()](arkts-backgroundtasks-workschedulerextensionability-c.md#onworkstart) or [onWorkStop()](arkts-backgroundtasks-workschedulerextensionability-c.md#onworkstop) in WorkSchedulerExtensionAbility. |

### Types

| Name | Description |
| --- | --- |
| [WorkSchedulerExtensionContext](arkts-backgroundtasks-workschedulerextensioncontext-t.md) | WorkSchedulerExtensionContext represents the context of WorkSchedulerExtensionAbility and is inherited from [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md). |
