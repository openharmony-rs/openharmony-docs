# getAuthInstance

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## getAuthInstance

```TypeScript
function getAuthInstance(challenge: Uint8Array, authType: UserAuthType, authTrustLevel: AuthTrustLevel): AuthInstance
```

Obtains an **AuthInstance** instance for user authentication.

> **NOTE:** 
> 
> Each **AuthInstance** can perform authentication only once. To perform authentication again, obtain a new
> **AuthInstance**.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [getUserAuthInstance](arkts-userauthentication-userauth-getuserauthinstance-f.md)

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| challenge | Uint8Array | Yes | Challenge value. It cannot exceed 32 bytes and can be passed in Uint8Array([]) format. |
| authType | [UserAuthType](arkts-userauthentication-userauth-userauthtype-e.md) | Yes | Authentication type. Currently, **FACE** and **FINGERPRINT** are supported. |
| authTrustLevel | [AuthTrustLevel](arkts-userauthentication-userauth-authtrustlevel-e.md) | Yes | Authentication trust level. |

**Return value:**

| Type | Description |
| --- | --- |
| [AuthInstance](arkts-userauthentication-userauth-authinstance-i.md) | **AuthInstance** instance obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [12500002](../errorcode-useriam.md#12500002-common-error-code-of-the-identity-authentication-system) | General operation error. |
| [12500005](../errorcode-useriam.md#12500005-unsupported-authentication-type) | The authentication type is not supported. |
| [12500006](../errorcode-useriam.md#12500006-unsupported-authentication-trust-level) | The authentication trust level is not supported. |

**Examples**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let challenge = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8]);
let authType = userAuth.UserAuthType.FACE;
let authTrustLevel = userAuth.AuthTrustLevel.ATL1;

try {
  let auth = userAuth.getAuthInstance(challenge, authType, authTrustLevel);
  console.info('get auth instance successfully.');
} catch (error) {
  console.error(`get auth instance failed. Code: ${error?.code}, message: ${error?.message}`);
}
```
