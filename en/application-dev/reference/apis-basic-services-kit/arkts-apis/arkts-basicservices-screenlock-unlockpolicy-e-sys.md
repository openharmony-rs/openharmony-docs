# UnlockPolicy (System API)

```TypeScript
enum UnlockPolicy
```

Indicates the screen lock authentication policy used to unlock the screen.

**Since:** 26.0.0

<!--Device-screenLock-enum UnlockPolicy--><!--Device-screenLock-enum UnlockPolicy-End-->

**System capability:** SystemCapability.MiscServices.ScreenLock

**System API:** This is a system API.

## DEFAULT

```TypeScript
DEFAULT = 0
```

Indicates that the screen lock is unlocked using the default system authentication mode.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UnlockPolicy-DEFAULT = 0--><!--Device-UnlockPolicy-DEFAULT = 0-End-->

**System capability:** SystemCapability.MiscServices.ScreenLock

**System API:** This is a system API.

## EXTENDED_AUTH_AND_SYSTEM

```TypeScript
EXTENDED_AUTH_AND_SYSTEM = 2
```

Indicates that the screen lock is unlocked using the extended and system authentication modes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UnlockPolicy-EXTENDED_AUTH_AND_SYSTEM = 2--><!--Device-UnlockPolicy-EXTENDED_AUTH_AND_SYSTEM = 2-End-->

**System capability:** SystemCapability.MiscServices.ScreenLock

**System API:** This is a system API.

## EXTENDED_AUTH_ONLY

```TypeScript
EXTENDED_AUTH_ONLY = 1
```

Indicates that the screen lock is unlocked using only the extended authentication mode.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UnlockPolicy-EXTENDED_AUTH_ONLY = 1--><!--Device-UnlockPolicy-EXTENDED_AUTH_ONLY = 1-End-->

**System capability:** SystemCapability.MiscServices.ScreenLock

**System API:** This is a system API.
