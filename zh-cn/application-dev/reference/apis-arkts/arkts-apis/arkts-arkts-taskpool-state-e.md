# State

表示任务（Task）状态的枚举。状态转换规则如下：  
- 当任务创建成功后，调用execute，任务进入taskpool等待队列，状态设置为WAITING。  
- 任务从等待队列出来进入taskpool工作线程中，任务状态更新为RUNNING。  
- 当任务执行完成，返回结果后，如果任务再次被执行，则状态重置为WAITING。  
- 当主动cancel任务时，将任务状态更新为CANCELED。

**起始版本：** 10

**系统能力：** SystemCapability.Utils.Lang

## WAITING

```TypeScript
WAITING = 1
```

任务正在等待。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## RUNNING

```TypeScript
RUNNING = 2
```

任务正在执行。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## CANCELED

```TypeScript
CANCELED = 3
```

任务已被取消。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang
