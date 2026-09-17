# getTaskPoolInfo

## Modules to Import

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

## getTaskPoolInfo

```TypeScript
function getTaskPoolInfo(): TaskPoolInfo
```

Obtains the thread information and task information of the task pool.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [TaskPoolInfo](arkts-arkts-taskpool-taskpoolinfo-c.md) | Internal information about the task pool. |

**Examples**

```TypeScript
let taskpoolInfo: taskpool.TaskPoolInfo = taskpool.getTaskPoolInfo();
```
