# UserAuthResult

Represents the user authentication result. If the authentication is successful, the authentication type and token information are returned. If the authentication fails, the corresponding error code is returned. This API is used to describe the result information after the authentication is complete. The application can obtain the result through the **onResult** callback of [IAuthCallback](arkts-userauthentication-userauth-iauthcallback-i.md).

**Since:** 10

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## authType

```TypeScript
authType?: UserAuthType
```

Authentication type that is actually used when the authentication is successful. If multiple authentication types are specified in the **authType** field of [AuthParam](arkts-userauthentication-userauth-authparam-i.md), this field identifies the authentication type that the user selects and completes.

**Type:** [UserAuthType](arkts-userauthentication-userauth-userauthtype-e.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## enrolledState

```TypeScript
enrolledState?: EnrolledState
```

Enrolled credential status returned when the authentication is successful. It contains the digest and quantity of the current authentication types. The application can compare this value with the previously saved value to determine whether the user credential has changed. If authentication result reuse is enabled and the credential (face or fingerprint) used for the previous authentication has been deleted, the values of **credentialCount** and **credentialDigest** in the returned **enrolledState** are both **0**.

**Type:** [EnrolledState](arkts-userauthentication-userauth-enrolledstate-i.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## result

```TypeScript
result: number
```

User authentication result. If the operation is successful, **SUCCESS(12500000)** is returned. If the operation fails, the corresponding error code is returned. The error codes are as follows:

- **FAIL(12500001)**: The authentication fails.  
- **CANCELED(12500003)**: The authentication is canceled.  
- **TIMEOUT(12500004)**: The authentication times out.  
- **LOCKED(12500009)**: The authenticator is locked.  
- **NOT_ENROLLED(12500010)**: The credential is not registered.  
- **PIN_EXPIRED(12500013)**: The screen lock PIN has expired.

For details about the complete error code list, see [UserAuthResultCode](arkts-userauthentication-userauth-userauthresultcode-e.md).

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## token

```TypeScript
token?: Uint8Array
```

Token information returned when the authentication is successful. The token contains the credentials for user authentication and can be used for subsequent security operation verification (such as payment confirmation and sensitive data access). The maximum length of a token is 1024 bytes. The token contains the challenge value used during authentication. The service can verify the challenge value to prevent replay attacks.

**Type:** Uint8Array

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core
