# KeyStatus

表示锁屏下敏感数据密钥状态的枚举。

**起始版本：** 18

**系统能力：** SystemCapability.Security.ScreenLockFileManager

## KEY_NOT_EXIST

```TypeScript
KEY_NOT_EXIST = -2
```

密钥不存在。此状态表示应用未开启锁屏下敏感数据保护功能，或当前设备上该保护功能不可用。

**起始版本：** 18

**系统能力：** SystemCapability.Security.ScreenLockFileManager

## KEY_RELEASED

```TypeScript
KEY_RELEASED = -1
```

密钥已释放。此状态表示锁屏下敏感数据无法被操作。

**起始版本：** 18

**系统能力：** SystemCapability.Security.ScreenLockFileManager

## KEY_EXIST

```TypeScript
KEY_EXIST = 0
```

密钥存在。此状态表示锁屏下敏感数据可以被正常操作。

**起始版本：** 18

**系统能力：** SystemCapability.Security.ScreenLockFileManager

