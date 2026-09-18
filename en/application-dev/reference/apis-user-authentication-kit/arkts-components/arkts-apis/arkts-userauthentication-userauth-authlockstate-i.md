# AuthLockState

Enumerates the lockout status of an identity authentication type. This API is used to query the lockout status of a specified authentication type (such as face, fingerprint, or PIN), including whether the authentication type is locked out, the number of remaining attempts, and the lockout duration. If a user fails to be authenticated multiple times, the authenticator may enter a temporary or permanent lockout state. The application can notify the user based on the lockout information.

**Since:** 22

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## isLocked

```TypeScript
isLocked: boolean
```

Whether the authentication is locked. The value **true** indicates that the authentication type is locked and cannot be used for authentication, and **false** indicates the opposite. The lockout status is usually triggered by multiple consecutive authentication failures.

**Type:** boolean

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## lockoutDuration

```TypeScript
lockoutDuration: number
```

Remaining lockout duration, in milliseconds. This parameter is valid only when **isLocked** is set to **true**.

If the authenticator is permanently locked, the value is [PERMANENT_LOCKOUT_DURATION](arkts-userauthentication-userauth-con.md#permanent_lockout_duration), indicating that the authenticator has been permanently locked. The user needs to perform PIN authentication before using the authentication type again. If the authenticator is temporarily locked, the value is the actual remaining lockout duration. After the lockout period ends, the user can continue to attempt authentication.

**Type:** number

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## remainingAuthAttempts

```TypeScript
remainingAuthAttempts: number
```

Number of remaining attempts before the authentication is locked. The maximum value is **5**. The value decreases by 1 each time the authentication fails. When the value decreases to 0, the authenticator is locked. This parameter is valid only when **isLocked** is set to **false**.

**Type:** number

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.UserIAM.UserAuth.Core
