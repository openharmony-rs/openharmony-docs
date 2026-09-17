# LastExitReason

Enumerates the reasons for the last exit of the ability. You can use it together with the value of **launchParam.lastExitReason** in [onCreate()](arkts-ability-app-ability-uiability-uiability-c.md#oncreate) of the UIAbility to complete different operations.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## UNKNOWN

```TypeScript
UNKNOWN = 0
```

Unknown reason.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## ABILITY_NOT_RESPONDING

```TypeScript
ABILITY_NOT_RESPONDING = 1
```

The ability does not respond.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [APP_FREEZE](#app_freeze)

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## NORMAL

```TypeScript
NORMAL = 2
```

The ability exits normally because the user closes the application.

Note: If the application process is forcibly terminated using methods not provided by Ability Kit, such as calling process.exit() or using the kernel **kill** command, the reason for the last exit is also reported as **NORMAL**.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## CPP_CRASH

```TypeScript
CPP_CRASH = 3
```

The ability exits due to [process crash](../../../dfx/cppcrash-guidelines.md).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## JS_ERROR

```TypeScript
JS_ERROR = 4
```

The ability exits due to a JS_ERROR fault triggered when an application has a JS syntax error that is not captured by developers.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## APP_FREEZE

```TypeScript
APP_FREEZE = 5
```

The ability exits due to [application freeze](../../../dfx/appfreeze-guidelines.md).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## PERFORMANCE_CONTROL

```TypeScript
PERFORMANCE_CONTROL = 6
```

The ability exits due to system performance problems, for example, insufficient device memory.

Note: This API will be deprecated. You are advised to use **RESOURCE_CONTROL** instead.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## RESOURCE_CONTROL

```TypeScript
RESOURCE_CONTROL = 7
```

The ability exits due to improper use of system resources. The specific error cause can be obtained through [LaunchParam.lastExitMessage](arkts-ability-abilityconstant-launchparam-i.md). The possible causes are as follows:

- **CPU Highload**: The CPU load is high.  
- **CPU_EXT Highload**: A fast CPU load detection is carried out.  
- **IO Manage Control**: An I/O management and control operation is carried out.  
- **App Memory Deterioration**: The application memory usage exceeds the threshold.  
- **Temperature Control**: The temperature is too high or too low.  
- **Memory Pressure**: The system is low on memory, triggering process termination in ascending order of  
priority.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## UPGRADE

```TypeScript
UPGRADE = 8
```

The application exits due to an upgrade.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## USER_REQUEST

```TypeScript
USER_REQUEST = 9
```

The ability exits because it receives a request from the multitasking center.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## SIGNAL

```TypeScript
SIGNAL = 10
```

The ability exits because it receives a kill signal from the system.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
