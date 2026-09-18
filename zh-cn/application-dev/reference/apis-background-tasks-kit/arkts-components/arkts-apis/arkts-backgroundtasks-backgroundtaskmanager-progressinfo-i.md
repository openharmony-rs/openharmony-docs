# ProgressInfo

通知进度信息。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## 导入模块

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## fileName

```TypeScript
fileName: string
```

通知内容。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## isMute

```TypeScript
isMute?: boolean
```

通知进度达到100时是否静音，true表示静音，false表示非静音（响铃+震动），默认为false。

**说明：** 该字段仅在progressValue字段值为100时生效。

**类型：** boolean

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## progressValue

```TypeScript
progressValue?: number
```

通知进度。取值范围：[0,100]。

**说明：** 如果该字段存在，则通知有进度环，通知类型为实况窗通知。如果该字段不存在或值为100，则通知无进度环，通知类型为普通通知。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## title

```TypeScript
title: string
```

通知标题。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask
