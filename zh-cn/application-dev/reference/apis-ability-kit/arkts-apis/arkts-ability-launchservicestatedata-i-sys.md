# LaunchServiceStateData（系统接口）

```TypeScript
declare interface LaunchServiceStateData
```

描述LaunchService状态变化数据。用于[LaunchServiceObserver]{./application/LaunchServiceObserver:LaunchServiceObserver}。

**起始版本：** 26.1.0

<!--Device-unnamed-declare interface LaunchServiceStateData--><!--Device-unnamed-declare interface LaunchServiceStateData-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## descriptor

```TypeScript
descriptor: LaunchServiceDescriptor
```

LaunchService的描述符。

**类型：** [LaunchServiceDescriptor](arkts-ability-launchservicedescriptor-i.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LaunchServiceStateData-descriptor: LaunchServiceDescriptor--><!--Device-LaunchServiceStateData-descriptor: LaunchServiceDescriptor-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## registered

```TypeScript
registered: boolean
```

LaunchService注册状态发生变化后的最新状态。true表示已注册，false表示未注册。

**类型：** boolean

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LaunchServiceStateData-registered: boolean--><!--Device-LaunchServiceStateData-registered: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。
