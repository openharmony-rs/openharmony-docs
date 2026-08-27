# BatteryCapacityLevel

表示电池电量等级的枚举。可用于根据电量等级执行差异化策略，例如在低电量（LEVEL_LOW）或极低电量（LEVEL_CRITICAL）时限制后台任务和高功耗功能，在满电量（LEVEL_FULL）时解除限制。

**起始版本：** 9

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## LEVEL_NONE

```TypeScript
LEVEL_NONE
```

表示电池电量等级为未知电量。说明系统无法获得当前的电池电量等级。

**起始版本：** 23

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## LEVEL_FULL

```TypeScript
LEVEL_FULL
```

表示电池电量等级为满电量。

**起始版本：** 9

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## LEVEL_HIGH

```TypeScript
LEVEL_HIGH
```

表示电池电量等级为高电量。

**起始版本：** 9

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## LEVEL_NORMAL

```TypeScript
LEVEL_NORMAL
```

表示电池电量等级为正常电量。

**起始版本：** 9

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## LEVEL_LOW

```TypeScript
LEVEL_LOW
```

表示电池电量等级为低电量。

**起始版本：** 9

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## LEVEL_WARNING

```TypeScript
LEVEL_WARNING
```

表示电池电量等级为告警电量。

**起始版本：** 9

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## LEVEL_CRITICAL

```TypeScript
LEVEL_CRITICAL
```

表示电池电量等级为极低电量。

**起始版本：** 9

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

## LEVEL_SHUTDOWN

```TypeScript
LEVEL_SHUTDOWN
```

表示电池电量等级为关机电量。

**起始版本：** 9

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core
