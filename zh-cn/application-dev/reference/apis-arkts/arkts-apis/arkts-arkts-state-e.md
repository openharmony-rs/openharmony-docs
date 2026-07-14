# State

表示任务（Task）状态的枚举。当任务创建成功后，调用**execute()**，任务进入taskpool等待队列，状态设置为**WAITING**；
任务从等待队列出来进入taskpool工作线程中，任务状态更新为**RUNNING**；当任务执行完成，返回结果后任务状态重置为**WAITING**；
当主动cancel任务时，将任务状态更新为**CANCELED**。

**起始版本：** 10

**系统能力：** SystemCapability.Utils.Lang

## WAITING

```TypeScript
WAITING = 1
```

任务正在等待。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## RUNNING

```TypeScript
RUNNING = 2
```

任务正在执行。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## CANCELED

```TypeScript
CANCELED = 3
```

任务已被取消。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

