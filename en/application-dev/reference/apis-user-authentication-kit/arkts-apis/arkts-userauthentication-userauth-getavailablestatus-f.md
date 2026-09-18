# getAvailableStatus

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## getAvailableStatus

```TypeScript
function getAvailableStatus(authType: UserAuthType, authTrustLevel: AuthTrustLevel): void
```

Checks whether the specified authentication capability is supported. This API is used to check whether the current device supports the specified authentication type and authentication trust level. It helps an application determine whether the authentication capability is available before initiating authentication, thereby avoiding unnecessary authentication failures. If the query is successful (no error is thrown), the authentication capability is available. If an error is thrown, the application should determine the cause based on the error code and take appropriate measures.

**Since:** 9

**Required permissions:** ohos.permission.ACCESS_BIOMETRIC

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| authType | [UserAuthType](arkts-userauthentication-userauth-userauthtype-e.md) | Yes | Authentication type. This parameter specifies the authentication type to be queried. The options are **FACE**, **FINGERPRINT**, **PIN**, and **COMPANION_DEVICE**.<br>Note: <br>PIN is supported since API version 11. <br>COMPANION_DEVICE query is supported since API version 26.0.0. |
| authTrustLevel | [AuthTrustLevel](arkts-userauthentication-userauth-authtrustlevel-e.md) | Yes | Authentication trust level. This parameter specifies the authentication trust level to be queried. The valid values are **ATL1(10000)**, **ATL2(20000)**, **ATL3(30000)**, and **ATL4(40000)**. A higher level indicates a higher requirement on the liveness detection capability of the authentication solution. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified. |
| [12500002](../errorcode-useriam.md#12500002-common-error-code-of-the-identity-authentication-system) | General operation error. |
| [12500005](../errorcode-useriam.md#12500005-unsupported-authentication-type) | The authentication type is not supported. |
| [12500006](../errorcode-useriam.md#12500006-unsupported-authentication-trust-level) | The authentication trust level is not supported. |
| [12500010](../errorcode-useriam.md#12500010-credential-not-enrolled) | The type of credential has not been enrolled. |
| [12500013](../errorcode-useriam.md#12500013-password-expired) | Operation failed because of PIN expired.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  userAuth.getAvailableStatus(userAuth.UserAuthType.FACE, userAuth.AuthTrustLevel.ATL3);
  console.info('current auth trust level is supported');
} catch (error) {
  console.error(`current auth trust level is not supported. Code: ${error?.code}, message: ${error?.message}`);
}
```
