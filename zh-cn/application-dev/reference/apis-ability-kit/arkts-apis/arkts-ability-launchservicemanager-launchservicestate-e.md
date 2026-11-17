# LaunchServiceState

```TypeScript
export enum LaunchServiceState
```

定义LaunchService状态的枚举类型，用于[LaunchServiceInformation](arkts-ability-launchserviceinformation-i.md)。

**起始版本：** 26.1.0

<!--Device-launchServiceManager-export enum LaunchServiceState--><!--Device-launchServiceManager-export enum LaunchServiceState-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## DISABLED

```TypeScript
DISABLED = 2
```

LaunchService已注册，但被禁用。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LaunchServiceState-DISABLED = 2--><!--Device-LaunchServiceState-DISABLED = 2-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## ENABLED

```TypeScript
ENABLED = 1
```

已注册并启用LaunchService。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LaunchServiceState-ENABLED = 1--><!--Device-LaunchServiceState-ENABLED = 1-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## NOT_REGISTERED

```TypeScript
NOT_REGISTERED = 0
```

LaunchService未注册。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LaunchServiceState-NOT_REGISTERED = 0--><!--Device-LaunchServiceState-NOT_REGISTERED = 0-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core
