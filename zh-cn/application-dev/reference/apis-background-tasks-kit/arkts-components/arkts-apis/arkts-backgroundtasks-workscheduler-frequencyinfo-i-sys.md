# FrequencyInfo（系统接口）

执行频率的具体信息，用于设置应用所在活跃分组的执行频率。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { workScheduler } from '@kit.BackgroundTasksKit';
```

## interval

```TypeScript
interval: number
```

活跃分组执行频率，单位：ms，取值限定为整数，取值范围[7200000, 2147483647)。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
uid: number
```

由系统自动分配的uid，取值限定为整数。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**系统接口：** 此接口为系统接口。

## workId

```TypeScript
workId: number
```

用于任务调度系统的延迟任务ID，取值限定为整数。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**系统接口：** 此接口为系统接口。
