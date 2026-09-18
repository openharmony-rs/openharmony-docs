# ProcessData

The module defines process data. If a lifecycle change listener is registered by calling [appManager.on('applicationState')](arkts-ability-appmanager-on-f.md#onapplicationstate), the [onProcessCreated](../../../reference/apis-ability-kit/js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronprocesscreated) callback in ApplicationStateObserver is invoked when the lifecycle of an application or ability changes.

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the application.

**Type:** string

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## isContinuousTask

```TypeScript
isContinuousTask: boolean
```

Whether the task is a continuous task. **true** if yes, **false** otherwise.

**Type:** boolean

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## isKeepAlive

```TypeScript
isKeepAlive: boolean
```

Whether the process is a resident task. **true** if yes, **false** otherwise.

**Type:** boolean

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## pid

```TypeScript
pid: number
```

Process ID.

**Type:** number

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## state

```TypeScript
state: number
```

Application state. The options are as follows:

**0**: The application process is being initialized.

**1**: The application process has been initialized and is ready.

**2**: The application is running in the foreground.

**4**: The application is running in the background.

**5**: The application process is terminated.

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
