# BackgroundTaskStateInfo（系统接口）

长时任务授权信息。

**起始版本：** 22

<!--Device-backgroundTaskManager-interface BackgroundTaskStateInfo--><!--Device-backgroundTaskManager-interface BackgroundTaskStateInfo-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## appIndex

```TypeScript
appIndex: number
```

应用分身ID。取值范围为全体整数。

**类型：** number

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackgroundTaskStateInfo-appIndex: int--><!--Device-BackgroundTaskStateInfo-appIndex: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**系统接口：** 此接口为系统接口。

## authResult

```TypeScript
authResult?: UserAuthResult
```

授权结果。

**类型：** UserAuthResult

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackgroundTaskStateInfo-authResult?: UserAuthResult--><!--Device-BackgroundTaskStateInfo-authResult?: UserAuthResult-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName: string
```

应用包名。

**类型：** string

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackgroundTaskStateInfo-bundleName: string--><!--Device-BackgroundTaskStateInfo-bundleName: string-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
userId: number
```

用户ID。取值范围为全体整数。

**类型：** number

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackgroundTaskStateInfo-userId: int--><!--Device-BackgroundTaskStateInfo-userId: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**系统接口：** 此接口为系统接口。

