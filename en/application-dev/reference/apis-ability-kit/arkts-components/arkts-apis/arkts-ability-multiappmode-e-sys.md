# MultiAppMode (System API)

```TypeScript
export enum MultiAppMode
```

The module defines whether an application supports the multi-app mode.

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**System API:** This is a system API.

## NOT_SUPPORTED

```TypeScript
NOT_SUPPORTED = 0
```

The application does not support the multi-app mode.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**System API:** This is a system API.

## MULTI_INSTANCE

```TypeScript
MULTI_INSTANCE = 1
```

The application supports the multi-instance mode. When an application is set to this mode, users can open multiple application instances simultaneously on the same device. Each instance runs independently with its own running environment and resources.

> **NOTE:** 
> 
> Only PC and 2-in-1 devices are supported.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**System API:** This is a system API.

## APP_CLONE

```TypeScript
APP_CLONE = 2
```

The application supports the app-clone mode. The app-clone mode allows creating independent copy instances for the application, with each instance having its own data space, suitable for scenarios that require isolated user data.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**System API:** This is a system API.
