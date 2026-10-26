# Result（系统接口）

```TypeScript
export enum Result
```

旋转执行结果的枚举

**起始版本：** 20

<!--Device-mechanicManager-export enum Result--><!--Device-mechanicManager-export enum Result-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## COMPLETED

```TypeScript
COMPLETED = 0
```

执行完成

**起始版本：** 20

<!--Device-Result-COMPLETED = 0--><!--Device-Result-COMPLETED = 0-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## INTERRUPTED

```TypeScript
INTERRUPTED = 1
```

执行被打断

**起始版本：** 20

<!--Device-Result-INTERRUPTED = 1--><!--Device-Result-INTERRUPTED = 1-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## LIMITED

```TypeScript
LIMITED = 2
```

执行受最大旋转角度限制

**起始版本：** 20

<!--Device-Result-LIMITED = 2--><!--Device-Result-LIMITED = 2-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## SYSTEM_ERROR

```TypeScript
SYSTEM_ERROR = 100
```

系统错误

**起始版本：** 20

<!--Device-Result-SYSTEM_ERROR = 100--><!--Device-Result-SYSTEM_ERROR = 100-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## TERMINATE_CLIFF

```TypeScript
TERMINATE_CLIFF = 5
```

悬崖导致终止

**起始版本：** 26.0.0

<!--Device-Result-TERMINATE_CLIFF = 5--><!--Device-Result-TERMINATE_CLIFF = 5-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## TERMINATE_OBSTACLE

```TypeScript
TERMINATE_OBSTACLE  = 4
```

障碍物导致终止

**起始版本：** 26.0.0

<!--Device-Result-TERMINATE_OBSTACLE  = 4--><!--Device-Result-TERMINATE_OBSTACLE  = 4-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## TIMEOUT

```TypeScript
TIMEOUT = 3
```

执行超时

**起始版本：** 20

<!--Device-Result-TIMEOUT = 3--><!--Device-Result-TIMEOUT = 3-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。
