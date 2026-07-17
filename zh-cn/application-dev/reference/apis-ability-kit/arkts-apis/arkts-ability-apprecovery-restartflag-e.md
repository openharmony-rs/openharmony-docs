# RestartFlag

应用重启标志，[enableAppRecovery](arkts-ability-apprecovery-enableapprecovery-f.md#enableapprecovery-1)接口重启选项参数，该类型为枚举。

**起始版本：** 9

<!--Device-appRecovery-enum RestartFlag--><!--Device-appRecovery-enum RestartFlag-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## ALWAYS_RESTART

```TypeScript
ALWAYS_RESTART = 0
```

总是重启应用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RestartFlag-ALWAYS_RESTART = 0--><!--Device-RestartFlag-ALWAYS_RESTART = 0-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## RESTART_WHEN_JS_CRASH

```TypeScript
RESTART_WHEN_JS_CRASH = 0x0001
```

发生JS_CRASH时重启应用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RestartFlag-RESTART_WHEN_JS_CRASH = 0x0001--><!--Device-RestartFlag-RESTART_WHEN_JS_CRASH = 0x0001-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## RESTART_WHEN_APP_FREEZE

```TypeScript
RESTART_WHEN_APP_FREEZE = 0x0002
```

发生APP_FREEZE时重启应用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RestartFlag-RESTART_WHEN_APP_FREEZE = 0x0002--><!--Device-RestartFlag-RESTART_WHEN_APP_FREEZE = 0x0002-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## NO_RESTART

```TypeScript
NO_RESTART = 0xFFFF
```

总是不重启应用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RestartFlag-NO_RESTART = 0xFFFF--><!--Device-RestartFlag-NO_RESTART = 0xFFFF-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## RESTART_WHEN_CPP_CRASH

```TypeScript
RESTART_WHEN_CPP_CRASH = 0x0004
```

发生CPP_CRASH时重启应用。

**模型约束**：此接口仅可在Stage模型下使用。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-RestartFlag-RESTART_WHEN_CPP_CRASH = 0x0004--><!--Device-RestartFlag-RESTART_WHEN_CPP_CRASH = 0x0004-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

