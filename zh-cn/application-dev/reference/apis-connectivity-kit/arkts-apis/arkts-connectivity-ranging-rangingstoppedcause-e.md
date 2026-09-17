# RangingStoppedCause

枚举，测距停止原因。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## NO_ERROR

```TypeScript
NO_ERROR = 0
```

正常停止，无错误。通常由应用主动调用stopRanging或stopPassiveRanging触发。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## INTERNAL_ERROR

```TypeScript
INTERNAL_ERROR = 1
```

发生内部错误，测距服务异常导致停止。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## BUSINESS_CONFLICT

```TypeScript
BUSINESS_CONFLICT = 2
```

发生业务冲突，其他服务占用导致测距停止。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## BACKGROUND_PAUSED

```TypeScript
BACKGROUND_PAUSED = 3
```

应用退到后台时测距暂停。应用回到前台会自动恢复测距。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core
