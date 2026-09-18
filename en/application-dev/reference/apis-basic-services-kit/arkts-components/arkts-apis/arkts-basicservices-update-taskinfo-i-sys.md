# TaskInfo (System API)

Represents the task information.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## existTask

```TypeScript
existTask: boolean
```

Whether an upgrade task exists, which is used to determine whether an upgrade task is in progress.

Use scenarios: Query the task status before the upgrade to avoid repeated operations. Monitor the task status change during the upgrade. The value **true** indicates that an upgrade task (for example, a download or installation task) is in progress. You need to wait until the task is complete or canceled before executing a new task. The value **false** indicates that no task is running and a new upgrade process can be started.

**Type:** boolean

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## taskBody

```TypeScript
taskBody: TaskBody
```

Task data.

**Type:** [TaskBody](arkts-basicservices-update-taskbody-i-sys.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
