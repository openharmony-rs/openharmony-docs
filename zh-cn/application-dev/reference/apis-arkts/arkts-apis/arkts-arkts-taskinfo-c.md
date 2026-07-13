# TaskInfo

任务的内部信息。

**起始版本：** 10

**系统能力：** SystemCapability.Utils.Lang

## duration

```TypeScript
duration?: number
```

任务执行至当前所用的时间，默认为0，单位为ms。当返回为0时，表示任务未执行；返回为空时，表示没有任务执行。不建议修改此值。<br>
从API version 11开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## name

```TypeScript
name: string
```

任务的名字，不建议修改此值。<br>
从API version 12开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## state

```TypeScript
state: State
```

任务的状态。不建议修改此值。<br>
从API version 11开始，该接口支持在原子化服务中使用。

**类型：** State

**默认值：** State::WAITING

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## taskId

```TypeScript
taskId: number
```

任务ID。任务的标识符，系统默认提供全局唯一值，不建议修改此值。<br>
从API version 11开始，该接口支持在原子化服务中使用。

**类型：** number

**默认值：** 0

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

