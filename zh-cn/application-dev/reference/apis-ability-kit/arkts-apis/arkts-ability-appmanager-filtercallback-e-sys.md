# FilterCallback（系统接口）

表示要监听的回调函数，该类型为枚举。可配合[AppStateFilter](arkts-ability-appmanager-appstatefilter-i-sys.md)过滤想要监听的回调函数。

**起始版本：** 21

<!--Device-appManager-export enum FilterCallback--><!--Device-appManager-export enum FilterCallback-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## ON_FOREGROUND_APPLICATION_CHANGED

```TypeScript
ON_FOREGROUND_APPLICATION_CHANGED = 1 << 0
```

该枚举对应应用前后台状态发生变化时执行的回调函数[ApplicationStateObserver.onForegroundApplicationChanged](../../../../reference/apis-ability-kit/js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronforegroundapplicationchanged)。

**起始版本：** 21

<!--Device-FilterCallback-ON_FOREGROUND_APPLICATION_CHANGED = 1 << 0--><!--Device-FilterCallback-ON_FOREGROUND_APPLICATION_CHANGED = 1 << 0-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## ON_ABILITY_STATE_CHANGED

```TypeScript
ON_ABILITY_STATE_CHANGED = 1 << 1
```

该枚举对应Ability状态发生变化时执行的回调函数[ApplicationStateObserver.onAbilityStateChanged](../../../../reference/apis-ability-kit/js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronabilitystatechanged)。

**起始版本：** 21

<!--Device-FilterCallback-ON_ABILITY_STATE_CHANGED = 1 << 1--><!--Device-FilterCallback-ON_ABILITY_STATE_CHANGED = 1 << 1-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## ON_PROCESS_CREATED

```TypeScript
ON_PROCESS_CREATED = 1 << 2
```

该枚举对应进程创建时执行的回调函数[ApplicationStateObserver.onProcessCreated](../../../../reference/apis-ability-kit/js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronprocesscreated)。

**起始版本：** 21

<!--Device-FilterCallback-ON_PROCESS_CREATED = 1 << 2--><!--Device-FilterCallback-ON_PROCESS_CREATED = 1 << 2-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## ON_PROCESS_DIED

```TypeScript
ON_PROCESS_DIED = 1 << 3
```

该枚举对应进程销毁时执行的回调函数[ApplicationStateObserver.onProcessDied](../../../../reference/apis-ability-kit/js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronprocessdied)。

**起始版本：** 21

<!--Device-FilterCallback-ON_PROCESS_DIED = 1 << 3--><!--Device-FilterCallback-ON_PROCESS_DIED = 1 << 3-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## ON_PROCESS_STATE_CHANGED

```TypeScript
ON_PROCESS_STATE_CHANGED = 1 << 4
```

该枚举对应进程状态更新时执行的回调函数[ApplicationStateObserver.onProcessStateChanged](../../../../reference/apis-ability-kit/js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronprocessstatechanged)。

**起始版本：** 21

<!--Device-FilterCallback-ON_PROCESS_STATE_CHANGED = 1 << 4--><!--Device-FilterCallback-ON_PROCESS_STATE_CHANGED = 1 << 4-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## ON_APP_STARTED

```TypeScript
ON_APP_STARTED = 1 << 5
```

该枚举对应应用第一个进程创建时执行的回调函数[ApplicationStateObserver.onAppStarted](../../../../reference/apis-ability-kit/js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronappstarted)。

**起始版本：** 21

<!--Device-FilterCallback-ON_APP_STARTED = 1 << 5--><!--Device-FilterCallback-ON_APP_STARTED = 1 << 5-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## ON_APP_STOPPED

```TypeScript
ON_APP_STOPPED = 1 << 6
```

该枚举对应应用最后一个进程销毁时执行的回调函数[ApplicationStateObserver.onAppStopped](../../../../reference/apis-ability-kit/js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronappstopped)。

**起始版本：** 21

<!--Device-FilterCallback-ON_APP_STOPPED = 1 << 6--><!--Device-FilterCallback-ON_APP_STOPPED = 1 << 6-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

