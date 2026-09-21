# MultiAppMode（系统接口）

```TypeScript
export enum MultiAppMode
```

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

应用支持多实例模式。当应用设置为此模式时，用户可以在同一设备上同时打开多个应用实例，各实例独立运行，拥有各自的运行环境和资源。

**说明：** 只支持PC/2in1设备。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

## APP_CLONE

```TypeScript
APP_CLONE = 2
```

应用支持分身模式。分身模式允许为应用创建独立的副本实例，每个实例拥有独立的数据空间，适用于需要隔离用户数据的场景。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。
