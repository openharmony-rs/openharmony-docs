# getEnrolledState

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## getEnrolledState

```TypeScript
function getEnrolledState(authType: UserAuthType): EnrolledState
```

Obtains the credential state. This API is used to obtain the credential enrollment information of a specified authentication type, including the credential digest and quantity. The application can compare the current query result with the previously saved result to determine whether the user has added or deleted credentials, and then perform corresponding service processing.

**Since:** 12

**Required permissions:** ohos.permission.ACCESS_BIOMETRIC

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| authType | [UserAuthType](arkts-userauthentication-userauth-userauthtype-e.md) | Yes | Authentication type. This parameter specifies the credential type to be queried. The options are **FACE**, **FINGERPRINT**, **PIN**, and **COMPANION_DEVICE**. When a PIN is queried, the overall status of the PIN instead of the number of PINs is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [EnrolledState](arkts-userauthentication-userauth-enrolledstate-i.md) | Credential state obtained if the operation is successful. The value contains **credentialDigest** (credential digest) and **credentialCount** (credential count). The application can save the **credentialDigest** value and compare it with the value obtained in subsequent queries to detect credential changes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified. |
| [12500002](../errorcode-useriam.md#12500002-common-error-code-of-the-identity-authentication-system) | General operation error. |
| [12500005](../errorcode-useriam.md#12500005-unsupported-authentication-type) | The authentication type is not supported. |
| [12500010](../errorcode-useriam.md#12500010-credential-not-enrolled) | The type of credential has not been enrolled. |

**Examples**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let enrolledState = userAuth.getEnrolledState(userAuth.UserAuthType.FACE);
  console.info('get current enrolled state successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`get current enrolled state failed, Code is ${err?.code}, message is ${err?.message}`);
}
```
