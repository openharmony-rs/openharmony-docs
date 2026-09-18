# FilterCallback (System API)

Enumerates the callbacks to filter. It can be used with [AppStateFilter](arkts-ability-appmanager-appstatefilter-i-sys.md) to filter the callbacks you want to listen for.

**Since:** 21

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## ON_FOREGROUND_APPLICATION_CHANGED

```TypeScript
ON_FOREGROUND_APPLICATION_CHANGED = 1 << 0
```

Corresponds to the [ApplicationStateObserver.onForegroundApplicationChanged](../../../reference/apis-ability-kit/js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronforegroundapplicationchanged) callback, which is executed when the application's foreground/background state changes.

**Since:** 21

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## ON_ABILITY_STATE_CHANGED

```TypeScript
ON_ABILITY_STATE_CHANGED = 1 << 1
```

Corresponds to the [ApplicationStateObserver.onAbilityStateChanged](../../../reference/apis-ability-kit/js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronabilitystatechanged) callback, which is executed when the ability state changes.

**Since:** 21

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## ON_PROCESS_CREATED

```TypeScript
ON_PROCESS_CREATED = 1 << 2
```

Corresponds to the [ApplicationStateObserver.onProcessCreated](../../../reference/apis-ability-kit/js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronprocesscreated) callback, which is executed when a process is created.

**Since:** 21

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## ON_PROCESS_DIED

```TypeScript
ON_PROCESS_DIED = 1 << 3
```

Corresponds to the [ApplicationStateObserver.onProcessDied](../../../reference/apis-ability-kit/js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronprocessdied) callback, which is executed when a process is destroyed.

**Since:** 21

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## ON_PROCESS_STATE_CHANGED

```TypeScript
ON_PROCESS_STATE_CHANGED = 1 << 4
```

Corresponds to the [ApplicationStateObserver.onProcessStateChanged](../../../reference/apis-ability-kit/js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronprocessstatechanged) callback, which is executed when the process state is updated.

**Since:** 21

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## ON_APP_STARTED

```TypeScript
ON_APP_STARTED = 1 << 5
```

Corresponds to the [ApplicationStateObserver.onAppStarted](../../../reference/apis-ability-kit/js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronappstarted) callback, which is executed when the application's first process is created.

**Since:** 21

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## ON_APP_STOPPED

```TypeScript
ON_APP_STOPPED = 1 << 6
```

Corresponds to the [ApplicationStateObserver.onAppStopped](../../../reference/apis-ability-kit/js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronappstopped) callback, which is executed when the application's last process is destroyed.

**Since:** 21

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
