# State

定义任务当前的状态。

**起始版本：** 10

<!--Device-agent-enum State--><!--Device-agent-enum State-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## INITIALIZED

```TypeScript
INITIALIZED = 0x00
```

表示通过配置信息（[Config](arkts-basicservices-agent-config-i.md)）创建的任务已初始化。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-State-INITIALIZED = 0x00--><!--Device-State-INITIALIZED = 0x00-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## WAITING

```TypeScript
WAITING = 0x10
```

表示任务缺少运行或重试的资源，又或是网络状态不匹配。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-State-WAITING = 0x10--><!--Device-State-WAITING = 0x10-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## RUNNING

```TypeScript
RUNNING = 0x20
```

表示任务正在运行中。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-State-RUNNING = 0x20--><!--Device-State-RUNNING = 0x20-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## RETRYING

```TypeScript
RETRYING = 0x21
```

表示任务至少失败一次，现在正在再次处理中。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-State-RETRYING = 0x21--><!--Device-State-RETRYING = 0x21-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## PAUSED

```TypeScript
PAUSED = 0x30
```

表示任务暂停，通常后续会恢复任务。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-State-PAUSED = 0x30--><!--Device-State-PAUSED = 0x30-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## STOPPED

```TypeScript
STOPPED = 0x31
```

表示任务停止。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-State-STOPPED = 0x31--><!--Device-State-STOPPED = 0x31-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## COMPLETED

```TypeScript
COMPLETED = 0x40
```

表示任务完成。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-State-COMPLETED = 0x40--><!--Device-State-COMPLETED = 0x40-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## FAILED

```TypeScript
FAILED = 0x41
```

表示任务失败。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-State-FAILED = 0x41--><!--Device-State-FAILED = 0x41-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## REMOVED

```TypeScript
REMOVED = 0x50
```

表示任务移除。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-State-REMOVED = 0x50--><!--Device-State-REMOVED = 0x50-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

