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

下载进度达到100%时是否静音。

**类型：** boolean

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## progressValue

```TypeScript
progressValue?: number
```

通知进度。如果该字段不存在，则不显示通知进度环，显示为普通通知。 取值限定为整数。

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
