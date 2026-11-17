# LaunchServiceDescriptor

```TypeScript
declare interface LaunchServiceDescriptor
```

Descriptor describing LaunchService.

**Since:** 26.1.0

<!--Device-unnamed-declare interface LaunchServiceDescriptor--><!--Device-unnamed-declare interface LaunchServiceDescriptor-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## appIndex

```TypeScript
appIndex?: number
```

Index of the application twin. The value ranges from 0 to 1000. The default value 0 indicates the main application. The value must be an integer.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-LaunchServiceDescriptor-appIndex?: int--><!--Device-LaunchServiceDescriptor-appIndex?: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## bundleName

```TypeScript
bundleName: string
```

Package name of the application that has LaunchService.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-LaunchServiceDescriptor-bundleName: string--><!--Device-LaunchServiceDescriptor-bundleName: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## moduleName

```TypeScript
moduleName: string
```

Declare the module name of LaunchService.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-LaunchServiceDescriptor-moduleName: string--><!--Device-LaunchServiceDescriptor-moduleName: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## serviceName

```TypeScript
serviceName: string
```

LaunchService name.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-LaunchServiceDescriptor-serviceName: string--><!--Device-LaunchServiceDescriptor-serviceName: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## userId

```TypeScript
userId?: number
```

User ID. If this parameter is not specified, the current user is used by default. The value should be an integer.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-LaunchServiceDescriptor-userId?: int--><!--Device-LaunchServiceDescriptor-userId?: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
