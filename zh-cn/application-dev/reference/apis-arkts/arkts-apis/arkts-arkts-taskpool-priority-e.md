# Priority

表示所创建任务（Task）执行时的优先级。工作线程优先级跟随任务优先级更新，对应关系请参考[QoS等级定义](../../../../napi/qos-guidelines.md#qos-level)。

**起始版本：** 9

<!--Device-taskpool-enum Priority--><!--Device-taskpool-enum Priority-End-->

**系统能力：** SystemCapability.Utils.Lang

## HIGH

```TypeScript
HIGH = 0
```

任务为高优先级。

从API version 11开始，该接口支持在原子化服务中使用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Priority-HIGH = 0--><!--Device-Priority-HIGH = 0-End-->

**系统能力：** SystemCapability.Utils.Lang

## MEDIUM

```TypeScript
MEDIUM = 1
```

任务为中优先级。

从API version 11开始，该接口支持在原子化服务中使用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Priority-MEDIUM = 1--><!--Device-Priority-MEDIUM = 1-End-->

**系统能力：** SystemCapability.Utils.Lang

## LOW

```TypeScript
LOW = 2
```

任务为低优先级。

从API version 11开始，该接口支持在原子化服务中使用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Priority-LOW = 2--><!--Device-Priority-LOW = 2-End-->

**系统能力：** SystemCapability.Utils.Lang

## IDLE

```TypeScript
IDLE = 3
```

任务为后台任务。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Priority-IDLE = 3--><!--Device-Priority-IDLE = 3-End-->

**系统能力：** SystemCapability.Utils.Lang

