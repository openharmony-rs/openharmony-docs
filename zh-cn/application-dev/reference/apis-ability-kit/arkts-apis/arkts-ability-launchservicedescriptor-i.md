# LaunchServiceDescriptor

```TypeScript
declare interface LaunchServiceDescriptor
```

描述LaunchService的描述符。

**起始版本：** 26.1.0

<!--Device-unnamed-declare interface LaunchServiceDescriptor--><!--Device-unnamed-declare interface LaunchServiceDescriptor-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## appIndex

```TypeScript
appIndex?: number
```

应用分身的索引。取值范围是[0,1000]，默认值0表示主应用。取值限定为整数。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LaunchServiceDescriptor-appIndex?: int--><!--Device-LaunchServiceDescriptor-appIndex?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## bundleName

```TypeScript
bundleName: string
```

拥有LaunchService的应用程序的包名。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LaunchServiceDescriptor-bundleName: string--><!--Device-LaunchServiceDescriptor-bundleName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## moduleName

```TypeScript
moduleName: string
```

声明LaunchService的模块名。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LaunchServiceDescriptor-moduleName: string--><!--Device-LaunchServiceDescriptor-moduleName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## serviceName

```TypeScript
serviceName: string
```

LaunchService的名称。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LaunchServiceDescriptor-serviceName: string--><!--Device-LaunchServiceDescriptor-serviceName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## userId

```TypeScript
userId?: number
```

用户ID。如果不指定该参数，则默认使用当前用户。取值限定为整数。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LaunchServiceDescriptor-userId?: int--><!--Device-LaunchServiceDescriptor-userId?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core
