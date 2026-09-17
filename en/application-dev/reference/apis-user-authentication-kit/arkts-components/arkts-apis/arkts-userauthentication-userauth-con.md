# Constants

## MAX_ALLOWABLE_REUSE_DURATION

```TypeScript
const MAX_ALLOWABLE_REUSE_DURATION: 300000
```

Maximum reuse duration of the authentication result, in milliseconds. The value is **300000** (5 minutes). This constant is used to limit the maximum duration for reusing an authentication result, preventing security risks caused by reusing expired authentication results for a long time. It can be used as the maximum value of the **reuseDuration** parameter in [ReuseUnlockResult](arkts-userauthentication-userauth-reuseunlockresult-i.md).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## PERMANENT_LOCKOUT_DURATION

```TypeScript
const PERMANENT_LOCKOUT_DURATION: number = 0x7fffffff
```

Permanent lockout duration, in milliseconds. The value is **0x7fffffff**. When the number of failed authentication attempts reaches the upper limit, the authenticator enters the permanent lockout status. In this case, PIN authentication is required for unlocking. This value is used to identify the permanent lockout status of the authenticator, which can be returned by the **lockoutDuration** field in [AuthLockState](arkts-userauthentication-userauth-authlockstate-i.md).

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.UserIAM.UserAuth.Core
