# UserAuthResultCode

Enumerates the authentication result codes. They include all success codes and error codes for user authentication operations. The application can determine the authentication result based on the return code and take corresponding measures.

**Since:** 9

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## AUTH_TOKEN_CHECK_FAILED

```TypeScript
AUTH_TOKEN_CHECK_FAILED = 12500015
```

Failed to verify the **AuthToken**. It is an error code of the system API **verifyAuthToken**, indicating that the integrity verification of the verified **AuthToken** fails and the token may be tampered or damaged.

**Since:** 18

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

## AUTH_TOKEN_EXPIRED

```TypeScript
AUTH_TOKEN_EXPIRED = 12500016
```

The **AuthToken** has expired. It is an error code of the system API **verifyAuthToken**, indicating that the interval between the **AuthToken** issuance time and the **AuthToken** verification time exceeds the maximum validity period (**allowableDuration**).

**Since:** 18

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

## REUSE_AUTH_RESULT_FAILED

```TypeScript
REUSE_AUTH_RESULT_FAILED = 12500017
```

Failed to reuse the authentication result. It is an error code of the system API **queryReusableAuthResult**, indicating that the reusable authentication result fails to be queried. The possible causes are as follows: No authentication result that meets the reuse conditions exists, the authentication result has expired, or the credential has been changed.

**Since:** 20

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.
