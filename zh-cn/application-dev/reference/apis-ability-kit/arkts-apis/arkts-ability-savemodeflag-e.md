# SaveModeFlag

状态保存标志，[enableAppRecovery](arkts-ability-enableapprecovery-f.md#enableapprecovery-1)接口状态保存方式的参数，该类型为枚举。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## SAVE_WITH_FILE

```TypeScript
SAVE_WITH_FILE = 0x0001
```

每次状态保存都会写入到本地文件缓存。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## SAVE_WITH_SHARED_MEMORY

```TypeScript
SAVE_WITH_SHARED_MEMORY = 0x0002
```

状态先保存在内存中，应用故障退出时写入到本地文件缓存。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

