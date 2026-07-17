# TaskInfo

任务的内部信息。

**起始版本：** 10

<!--Device-taskpool-class TaskInfo--><!--Device-taskpool-class TaskInfo-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

## duration

```TypeScript
duration?: number
```

任务执行至当前所用的时间，默认为0，单位为ms。当返回为0时，表示任务未执行；返回为空时，表示没有任务执行。不建议修改此值。<br>从API version 11开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TaskInfo-duration?: number--><!--Device-TaskInfo-duration?: number-End-->

**系统能力：** SystemCapability.Utils.Lang

## name

```TypeScript
name: string
```

任务的名字，不建议修改此值。<br>从API version 12开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TaskInfo-name: string--><!--Device-TaskInfo-name: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## state

```TypeScript
state: State
```

任务的状态。不建议修改此值。<br>从API version 11开始，该接口支持在原子化服务中使用。

**类型：** State

**默认值：** State::WAITING

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TaskInfo-state: State--><!--Device-TaskInfo-state: State-End-->

**系统能力：** SystemCapability.Utils.Lang

## taskId

```TypeScript
taskId: number
```

任务ID。任务的标识符，系统默认提供全局唯一值，不建议修改此值。<br>从API version 11开始，该接口支持在原子化服务中使用。

**类型：** number

**默认值：** 0

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TaskInfo-taskId: number--><!--Device-TaskInfo-taskId: number-End-->

**系统能力：** SystemCapability.Utils.Lang

