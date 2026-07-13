# ContinuousTaskInfo

长时任务信息。

**起始版本：** 20

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## abilityId

```TypeScript
abilityId: number
```

UIAbility ID.

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## abilityName

```TypeScript
abilityName: string
```

UIAbility名称。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## appIndex

```TypeScript
appIndex?: number
```

应用分身ID。
取值范围为全体整数。

**类型：** number

**起始版本：** 23

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## backgroundModes

```TypeScript
backgroundModes: string[]
```

[长时任务类型](arkts-backgroundtasks-backgroundmode-e.md)。

**类型：** string[]

**起始版本：** 20

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## backgroundSubModes

```TypeScript
backgroundSubModes: string[]
```

[长时任务子类型](arkts-backgroundtasks-backgroundsubmode-e.md)。

**类型：** string[]

**起始版本：** 20

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## bundleName

```TypeScript
bundleName?: string
```

应用包名。

**类型：** string

**起始版本：** 23

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## continuousTaskId

```TypeScript
continuousTaskId: number
```

长时任务ID。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## isFromWebView

```TypeScript
isFromWebView: boolean
```

是否通过Webview方式申请，即通过系统代理应用申请长时任务。true表示通过Webview方式申请，false表示不通过Webview方式申请。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## notificationId

```TypeScript
notificationId: number
```

通知 Id。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## pid

```TypeScript
pid: number
```

应用进程的PID。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## suspendState

```TypeScript
suspendState: boolean
```

申请的长时任务是否处于暂停状态。true表示处于暂停状态，false表示处于激活状态。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## uid

```TypeScript
uid: number
```

应用的UID。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## wantAgentAbilityName

```TypeScript
wantAgentAbilityName: string
```

[WantAgent](../../apis-ability-kit/arkts-apis/arkts-app-ability-wantagent.md) 配置的ability名称。WantAgent为通知参数，用于指定点击长时任务通知后跳转的界面，在申请长时任务时作为参数传入。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## wantAgentBundleName

```TypeScript
wantAgentBundleName: string
```

[WantAgent](../../apis-ability-kit/arkts-apis/arkts-app-ability-wantagent.md) 配置的包名。WantAgent为通知参数，用于指定点击长时任务通知后跳转的界面，在申请长时任务时作为参数传入。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

