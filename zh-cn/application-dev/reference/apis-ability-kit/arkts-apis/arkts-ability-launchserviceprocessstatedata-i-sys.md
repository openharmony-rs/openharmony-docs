# LaunchServiceProcessStateData（系统接口）

```TypeScript
declare interface LaunchServiceProcessStateData
```

描述LaunchService进程状态变化数据。用于[LaunchServiceObserver]{./application/LaunchServiceObserver:LaunchServiceObserver}。

**起始版本：** 26.1.0

<!--Device-unnamed-declare interface LaunchServiceProcessStateData--><!--Device-unnamed-declare interface LaunchServiceProcessStateData-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## descriptor

```TypeScript
descriptor: LaunchServiceDescriptor
```

启动服务的描述符。

**类型：** [LaunchServiceDescriptor](arkts-ability-launchservicedescriptor-i.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LaunchServiceProcessStateData-descriptor: LaunchServiceDescriptor--><!--Device-LaunchServiceProcessStateData-descriptor: LaunchServiceDescriptor-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## pid

```TypeScript
pid: number
```

LaunchService进程的pid。0表示进程未在运行，大于0表示正在运行进程的pid。取值限定为整数。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LaunchServiceProcessStateData-pid: int--><!--Device-LaunchServiceProcessStateData-pid: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## state

```TypeScript
state: launchServiceManager.LaunchServiceProcessState
```

LaunchService进程状态。0：LaunchService进程启动。1：LaunchService进程停止。取值限定为整数。

**类型：** [launchServiceManager.LaunchServiceProcessState](arkts-ability-launchservicemanager-launchserviceprocessstate-e-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LaunchServiceProcessStateData-state: launchServiceManager.LaunchServiceProcessState--><!--Device-LaunchServiceProcessStateData-state: launchServiceManager.LaunchServiceProcessState-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。
