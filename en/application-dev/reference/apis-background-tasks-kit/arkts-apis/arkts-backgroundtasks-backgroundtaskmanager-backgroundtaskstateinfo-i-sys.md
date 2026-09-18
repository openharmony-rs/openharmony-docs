# BackgroundTaskStateInfo (System API)

Defines the authorization information of a continuous task.

**Since:** 22

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## appIndex

```TypeScript
appIndex: number
```

AppIndex of the application applying for special continuous task.

**Type:** number

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**System API:** This is a system API.

## authResult

```TypeScript
authResult?: UserAuthResult
```

Type of user authorization status.

**Type:** [UserAuthResult](arkts-backgroundtasks-backgroundtaskmanager-userauthresult-e.md)

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**System API:** This is a system API.

## bundleName

```TypeScript
bundleName: string
```

BundleName of the application applying for special continuous task.

**Type:** string

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**System API:** This is a system API.

## userId

```TypeScript
userId: number
```

UserId of the application applying for special continuous task

**Type:** number

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**System API:** This is a system API.
