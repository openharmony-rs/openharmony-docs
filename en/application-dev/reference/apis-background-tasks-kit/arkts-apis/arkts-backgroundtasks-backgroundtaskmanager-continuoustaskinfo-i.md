# ContinuousTaskInfo

Describes the continuous task information.

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## Modules to Import

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## abilityId

```TypeScript
abilityId: number
```

UIAbility ID.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## abilityName

```TypeScript
abilityName: string
```

UIAbility name.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## appIndex

```TypeScript
appIndex?: number
```

Index of an application clone.

**Type:** number

**Since:** 23

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## backgroundModes

```TypeScript
backgroundModes: string[]
```

[Type of a continuous task](arkts-backgroundtasks-backgroundtaskmanager-backgroundmode-e.md).

**Type:** string[]

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## backgroundSubModes

```TypeScript
backgroundSubModes: string[]
```

[Subtype of a continuous task](arkts-backgroundtasks-backgroundtaskmanager-backgroundsubmode-e.md).

**Type:** string[]

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## bundleName

```TypeScript
bundleName?: string
```

Application bundle name.

**Type:** string

**Since:** 23

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## continuousTaskId

```TypeScript
continuousTaskId: number
```

Continuous task ID.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## isFromWebView

```TypeScript
isFromWebView: boolean
```

Whether to request a continuous task in WebView mode, that is, whether to request a continuous task through the system proxy application. The value **true** indicates that the Webview mode is used, and the value **false** indicates that the Webview mode is not used.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## notificationId

```TypeScript
notificationId: number
```

Notification ID.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## pid

```TypeScript
pid: number
```

Application PID.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## suspendState

```TypeScript
suspendState: boolean
```

Whether the requested continuous task is suspended. The value **true** indicates that the task is suspended, and the value **false** indicates that the task is activated.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## uid

```TypeScript
uid: number
```

Application UID.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## wantAgentAbilityName

```TypeScript
wantAgentAbilityName: string
```

Ability name configured in [WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-n.md). **WantAgent** is a notification parameter used to specify the target page when a continuous task notification is tapped.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## wantAgentBundleName

```TypeScript
wantAgentBundleName: string
```

Bundle name configured in [WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-n.md). **WantAgent** is a notification parameter used to specify the target page when a continuous task notification is tapped.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask
