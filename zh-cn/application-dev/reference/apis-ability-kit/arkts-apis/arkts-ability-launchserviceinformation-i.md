# LaunchServiceInformation

```TypeScript
declare interface LaunchServiceInformation
```

LaunchService的信息结构体。

**起始版本：** 26.1.0

<!--Device-unnamed-declare interface LaunchServiceInformation--><!--Device-unnamed-declare interface LaunchServiceInformation-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## descriptor

```TypeScript
descriptor: LaunchServiceDescriptor
```

LaunchService的描述符。

**类型：** [LaunchServiceDescriptor](arkts-ability-launchservicedescriptor-i.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LaunchServiceInformation-descriptor: LaunchServiceDescriptor--><!--Device-LaunchServiceInformation-descriptor: LaunchServiceDescriptor-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## pid

```TypeScript
pid: number
```

LaunchService进程的pid。0表示进程未启动，大于0时表示正在运行的进程的pid。取值限定为整数。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LaunchServiceInformation-pid: int--><!--Device-LaunchServiceInformation-pid: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## state

```TypeScript
state: launchServiceManager.LaunchServiceState
```

LaunchService的状态。

**类型：** [launchServiceManager.LaunchServiceState](arkts-ability-launchservicemanager-launchservicestate-e.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LaunchServiceInformation-state: launchServiceManager.LaunchServiceState--><!--Device-LaunchServiceInformation-state: launchServiceManager.LaunchServiceState-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core
