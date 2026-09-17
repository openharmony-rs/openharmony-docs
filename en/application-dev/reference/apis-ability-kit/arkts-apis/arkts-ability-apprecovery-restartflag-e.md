# RestartFlag

Enumerates the application restart flags. This enum is used as an input parameter of [enableAppRecovery](arkts-ability-apprecovery-enableapprecovery-f.md).

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## ALWAYS_RESTART

```TypeScript
ALWAYS_RESTART = 0
```

The application is restarted in all cases.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## RESTART_WHEN_JS_CRASH

```TypeScript
RESTART_WHEN_JS_CRASH = 0x0001
```

The application is restarted in the case of JS_CRASH.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## RESTART_WHEN_APP_FREEZE

```TypeScript
RESTART_WHEN_APP_FREEZE = 0x0002
```

The application is restarted in the case of APP_FREEZE.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## NO_RESTART

```TypeScript
NO_RESTART = 0xFFFF
```

The application is not restarted in any case.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## RESTART_WHEN_CPP_CRASH

```TypeScript
RESTART_WHEN_CPP_CRASH = 0x0004
```

Restart if the current app process encounters a cppcrash

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
