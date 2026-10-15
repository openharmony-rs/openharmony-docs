# Constants

## MAX_ALLOWABLE_REUSE_DURATION

```TypeScript
const MAX_ALLOWABLE_REUSE_DURATION: 300000
```

Maximum valid duration of the reuse unlock authentication result, with a value of 300000 milliseconds (5 minutes). It is used to limit the maximum duration for reusing an authentication result, preventing the security risk caused by reusing an expired authentication result for a long time. This constant can be used as the maximum value of the **reuseDuration** parameter in [ReuseUnlockResult](arkts-userauthentication-userauth-reuseunlockresult-i.md).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-userAuth-const MAX_ALLOWABLE_REUSE_DURATION: 300000--><!--Device-userAuth-const MAX_ALLOWABLE_REUSE_DURATION: 300000-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## PERMANENT_LOCKOUT_DURATION

```TypeScript
const PERMANENT_LOCKOUT_DURATION: number = 0x7fffffff
```

Permanent freeze duration, with a value of 0x7fffffff milliseconds. When the number of authentication failures reaches the upper limit, the authenticator enters the permanent freeze state, and PIN authentication is required to unlock it. This value is used to identify the permanent freeze state of the authenticator and can be returned through the **lockoutDuration** field of [AuthLockState](arkts-userauthentication-userauth-authlockstate-i.md).

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-userAuth-const PERMANENT_LOCKOUT_DURATION: int = 0x7fffffff--><!--Device-userAuth-const PERMANENT_LOCKOUT_DURATION: int = 0x7fffffff-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core
