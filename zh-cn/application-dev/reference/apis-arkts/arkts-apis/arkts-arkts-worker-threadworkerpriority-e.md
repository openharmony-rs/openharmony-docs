# ThreadWorkerPriority

Worker线程的优先级枚举，各优先级对应关系请参考QoS等级定义。

**起始版本：** 18

<!--Device-unnamed-export enum ThreadWorkerPriority--><!--Device-unnamed-export enum ThreadWorkerPriority-End-->

**系统能力：** SystemCapability.Utils.Lang

## HIGH

```TypeScript
HIGH = 0
```

适用于打开文档等用户触发并且可以看到进展的任务，任务在几秒钟之内完成。对应QOS_USER_INITIATED。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorkerPriority-HIGH = 0--><!--Device-ThreadWorkerPriority-HIGH = 0-End-->

**系统能力：** SystemCapability.Utils.Lang

## MEDIUM

```TypeScript
MEDIUM = 1
```

任务完成需要几秒钟。是ThreadWorkerPriority的默认值。对应QOS_DEFAULT。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorkerPriority-MEDIUM = 1--><!--Device-ThreadWorkerPriority-MEDIUM = 1-End-->

**系统能力：** SystemCapability.Utils.Lang

## LOW

```TypeScript
LOW = 2
```

适用于下载等不需要立即看到响应效果的任务，任务完成需要几秒到几分钟。对应QOS_UTILITY。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorkerPriority-LOW = 2--><!--Device-ThreadWorkerPriority-LOW = 2-End-->

**系统能力：** SystemCapability.Utils.Lang

## IDLE

```TypeScript
IDLE = 3
```

适用于数据同步等用户不可见的后台任务，任务完成需要几分钟甚至几小时。对应QOS_BACKGROUND。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorkerPriority-IDLE = 3--><!--Device-ThreadWorkerPriority-IDLE = 3-End-->

**系统能力：** SystemCapability.Utils.Lang

## DEADLINE

```TypeScript
DEADLINE = 4
```

适用于页面加载等越快越好的关键任务，任务几乎是瞬间完成的。对应QOS_DEADLINE_REQUEST。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorkerPriority-DEADLINE = 4--><!--Device-ThreadWorkerPriority-DEADLINE = 4-End-->

**系统能力：** SystemCapability.Utils.Lang

## VIP

```TypeScript
VIP = 5
```

适用于UI线程、动画渲染等用户交互任务，任务是即时的。对应QOS_USER_INTERACTIVE。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorkerPriority-VIP = 5--><!--Device-ThreadWorkerPriority-VIP = 5-End-->

**系统能力：** SystemCapability.Utils.Lang

