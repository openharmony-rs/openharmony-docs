# MultiAppMode（系统接口）

定义应用是否支持多开模式。

**起始版本：** 12

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

## NOT_SUPPORTED

```TypeScript
NOT_SUPPORTED = 0
```

应用不支持多开模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

## MULTI_INSTANCE

```TypeScript
MULTI_INSTANCE = 1
```

应用支持多实例模式。

**说明：** 只支持2in1设备。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

## APP_CLONE

```TypeScript
APP_CLONE = 2
```

应用支持分身模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

