# LongTask

Describes a continuous task. **LongTask** inherits from [Task](arkts-arkts-taskpool-task-c.md). No upper limit is set for the execution time of a continuous task, and no timeout exception is thrown if a continuous task runs for a long period of time. However, a continuous task cannot be executed in a task group or executed for multiple times. The thread for executing a continuous task exists until [terminateTask](arkts-arkts-taskpool-terminatetask-f.md) is called after the execution is complete. The thread is reclaimed when it is idle.

**Inheritance/Implementation:** LongTask extends [Task](arkts-arkts-taskpool-task-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { taskpool } from '@kit.ArkTS';
```
