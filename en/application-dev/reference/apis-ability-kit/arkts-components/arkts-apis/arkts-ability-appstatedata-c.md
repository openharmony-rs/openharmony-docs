# AppStateData

The module defines the application state information. Once an application state change listener is registered using [on](arkts-ability-appmanager-on-f.md#onapplicationstate), the system triggers the [onForegroundApplicationChanged](../../../reference/apis-ability-kit/js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronforegroundapplicationchanged) callback of ApplicationStateObserver to deliver notifications whenever the state of an application, process, or ability changes.

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## bundleName

```TypeScript
bundleName: string
```

Bundle name.

**Type:** string

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## isFloatingWindowMode

```TypeScript
isFloatingWindowMode: boolean
```

Whether the application is in floating window mode.

**true**: The application is in floating window mode.

**false**: The application is not in floating window mode.

**Type:** boolean

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## isSplitScreenMode

```TypeScript
isSplitScreenMode: boolean
```

Whether the application is in split-screen mode.

**true**: The application is in split-screen mode.

**false**: The application is not in split-screen mode.

**Type:** boolean

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## state

```TypeScript
state: number
```

Application state.

**0**: The application is being initialized.

**1**: The application has been initialized and is ready.

**2**: The application is running in the foreground.

**3**: The application is having the focus. (This state is reserved.)

**4**: The application is running in the background.

**5**: The application has exited.

**Type:** number

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## uid

```TypeScript
uid: number
```

UID of the application.

**Type:** number

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
