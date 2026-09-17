# AuthToken (System API)

Defines the authentication token data. It indicates the parsed **AuthToken** data returned after the verification is successful, including detailed authentication information such as the challenge value, authentication trust level, authentication type, and user ID.

**Since:** 18

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { userAccessCtrl } from '@kit.UserAuthenticationKit';
```

## authTrustLevel

```TypeScript
authTrustLevel: userAuth.AuthTrustLevel
```

Authentication trust level. It indicates the security strength level of the current authentication. The value can be **ATL1 (10000)**, **ATL2 (20000)**, **ATL3 (30000)**, or **ATL4 (40000)**. A higher level indicates a stronger liveness detection capability and more accurate identity recognition.

**Type:** [userAuth.AuthTrustLevel](arkts-userauthentication-userauth-authtrustlevel-e.md)

**Since:** 18

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

## authType

```TypeScript
authType: userAuth.UserAuthType
```

Credential type for the identity authentication. It indicates the authentication mode used for the current authentication, such as **PIN (1)**, **FACE (2)**, and **FINGERPRINT (4)**.

**Type:** [userAuth.UserAuthType](arkts-userauthentication-userauth-userauthtype-e.md)

**Since:** 18

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

## challenge

```TypeScript
challenge: Uint8Array
```

Random challenge value for the authentication. It is used to prevent replay attacks. The challenge value passed during authentication is included in the **AuthToken**. The service can verify this field to confirm the validity of the authentication result.

**Type:** Uint8Array

**Since:** 18

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

## credentialId

```TypeScript
credentialId?: bigint
```

Credential ID. It indicates the ID of the credential that is successfully matched in the current authentication. It is used to associate with the specific authentication credential.

**Type:** bigint

**Since:** 18

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

## enrolledId

```TypeScript
enrolledId?: bigint
```

Credential enrollment ID. It indicates the original value of **credentialDigest** in **enrolledState**, which reflects the credential change.

**Type:** bigint

**Since:** 18

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

## secureUid

```TypeScript
secureUid?: bigint
```

Secure user ID. It indicates the security ID of a user, which is used internally by the system and returned only in specific authentication scenarios.

**Type:** bigint

**Since:** 18

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

## timeInterval

```TypeScript
timeInterval: bigint
```

Time elapsed since the **AuthToken** was issued, in milliseconds.

**Type:** bigint

**Since:** 18

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

## tokenType

```TypeScript
tokenType: AuthTokenType
```

Authentication token type. It identifies the source of the token, such as local authentication, reuse authentication, or collaborative authentication.

**Type:** [AuthTokenType](arkts-userauthentication-useraccessctrl-authtokentype-e-sys.md)

**Since:** 18

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

## userId

```TypeScript
userId: number
```

User ID. It indicates the ID of the user who has completed authentication. The value is a non-negative integer.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.
