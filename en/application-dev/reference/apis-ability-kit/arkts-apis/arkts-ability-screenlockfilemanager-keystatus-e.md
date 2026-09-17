# KeyStatus

Enumerates the statuses of sensitive data keys under the lock screen.

**Since:** 18

**System capability:** SystemCapability.Security.ScreenLockFileManager

## KEY_NOT_EXIST

```TypeScript
KEY_NOT_EXIST = -2
```

The key does not exist. This status indicates that the app has not enabled the sensitive data protection function under lock screen, or the protection function is unavailable on the current device.

**Since:** 18

**System capability:** SystemCapability.Security.ScreenLockFileManager

## KEY_RELEASED

```TypeScript
KEY_RELEASED = -1
```

The key has been released. This status indicates that sensitive data under lock screen cannot be operated.

**Since:** 18

**System capability:** SystemCapability.Security.ScreenLockFileManager

## KEY_EXIST

```TypeScript
KEY_EXIST = 0
```

The key exists. This status indicates that sensitive data under lock screen can be operated normally.

**Since:** 18

**System capability:** SystemCapability.Security.ScreenLockFileManager
