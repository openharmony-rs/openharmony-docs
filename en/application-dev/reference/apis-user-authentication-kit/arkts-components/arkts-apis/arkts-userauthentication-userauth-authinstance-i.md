# AuthInstance

Implements user authentication.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [UserAuthInstance](arkts-userauthentication-userauth-userauthinstance-i.md)

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## cancel

```TypeScript
cancel: () => void
```

Cancels this authentication.

> **NOTE:** 
> 
> Use the obtained [AuthInstance](arkts-userauthentication-userauth-authinstance-i.md) object to call this API to cancel authentication.
> This [AuthInstance](arkts-userauthentication-userauth-authinstance-i.md) must be the object that is currently performing
> authentication.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [cancel](arkts-userauthentication-userauth-userauthinstance-i.md#cancel)

**Required permissions:** ohos.permission.ACCESS_BIOMETRIC

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [12500002](../errorcode-useriam.md#12500002-common-error-code-of-the-identity-authentication-system) | General operation error. |

**Examples**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let challenge = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8]);
let authType = userAuth.UserAuthType.FACE;
let authTrustLevel = userAuth.AuthTrustLevel.ATL1;

try {
  let auth = userAuth.getAuthInstance(challenge, authType, authTrustLevel);
  auth.cancel();
  console.info('cancel auth successfully.');
} catch (error) {
  console.error(`cancel auth failed. Code: ${error?.code}, message: ${error?.message}`);
}
```

## off

```TypeScript
off: (name: AuthEventKey) => void
```

Unsubscribes from the user authentication events of the specified type.

- **name**: indicates the authentication event type. The value **result** means to unsubscribe from the  
authentication result, and the value **tip** means to unsubscribe from the authentication tip information. For details, see [AuthEventKey](arkts-userauthentication-userauth-autheventkey-t.md).

> **NOTE:** 
> 
> The [AuthInstance](arkts-userauthentication-userauth-authinstance-i.md) instance used to invoke this API must be the one used to
> subscribe to the event.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [off](arkts-userauthentication-userauth-userauthinstance-i.md#off)

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | [AuthEventKey](arkts-userauthentication-userauth-autheventkey-t.md) | Yes |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [12500002](../errorcode-useriam.md#12500002-common-error-code-of-the-identity-authentication-system) | General operation error. |

**Examples**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let challenge = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8]);
let authType = userAuth.UserAuthType.FACE;
let authTrustLevel = userAuth.AuthTrustLevel.ATL1;
try {
  let auth = userAuth.getAuthInstance(challenge, authType, authTrustLevel);
  // Subscribe to the authentication result.
  auth.on('result', {
    callback: (result: userAuth.AuthResultInfo) => {
      console.info(`result: ${result.result}`);
    }
  });
  // Unsubscribe from the authentication result.
  auth.off('result');
  console.info('cancel subscribe authentication event successfully.');
} catch (error) {
  console.error(`cancel subscribe authentication event failed. Code: ${error?.code}, message: ${error?.message}`);
  // do error.
}
```

## on

```TypeScript
on: (name: AuthEventKey, callback: AuthEvent) => void
```

Subscribes to the user authentication events of the specified type.

- **name**: indicates the authentication event type. The value **result** means that the callback returns the  
authentication result, and the value **tip** means that the callback returns the authentication tip information. For details, see [AuthEventKey](arkts-userauthentication-userauth-autheventkey-t.md).  
- **callback**: callback used to return the authentication result or tip information. For details, see [AuthEvent](arkts-userauthentication-userauth-authevent-i.md).

> **NOTE:** 
> 
> Use the [AuthInstance](arkts-userauthentication-userauth-authinstance-i.md) instance obtained to call this API.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [on](arkts-userauthentication-userauth-userauthinstance-i.md#on)

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | [AuthEventKey](arkts-userauthentication-userauth-autheventkey-t.md) | Yes |  |
| callback | [AuthEvent](arkts-userauthentication-userauth-authevent-i.md) | Yes |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [12500002](../errorcode-useriam.md#12500002-common-error-code-of-the-identity-authentication-system) | General operation error. |

**Examples**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let challenge = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8]);
let authType = userAuth.UserAuthType.FACE;
let authTrustLevel = userAuth.AuthTrustLevel.ATL1;
try {
  let auth = userAuth.getAuthInstance(challenge, authType, authTrustLevel);
  // Subscribe to the authentication result.
  auth.on('result', {
    callback: (result: userAuth.AuthResultInfo) => {
      console.info(`result: ${result.result}`);
    }
  });
  // Subscribe to authentication tip information.
  auth.on('tip', {
    callback : (result : userAuth.TipInfo) => {
      switch (result.tip) {
        case userAuth.FaceTips.FACE_AUTH_TIP_TOO_BRIGHT:
          // Do something.
          break;
        case userAuth.FaceTips.FACE_AUTH_TIP_TOO_DARK:
          // Do something.
          break;
        default:
          // do others.
      }
    }
  } as userAuth.AuthEvent);
  auth.start();
  console.info('auth start successfully.');
} catch (error) {
  console.error(`auth failed. Code: ${error?.code}, message: ${error?.message}`);
  // do error.
}
```

## start

```TypeScript
start: () => void
```

Starts authentication.

> **NOTE:** 
> 
> Use the obtained [AuthInstance](arkts-userauthentication-userauth-authinstance-i.md) object to call this API for authentication.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [start](arkts-userauthentication-userauth-userauthinstance-i.md#start)

**Required permissions:** ohos.permission.ACCESS_BIOMETRIC

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [12500001](../errorcode-useriam.md#12500001-authentication-failed) | Authentication failed. |
| [12500002](../errorcode-useriam.md#12500002-common-error-code-of-the-identity-authentication-system) | General operation error. |
| [12500003](../errorcode-useriam.md#12500003-authentication-canceled) | The operation is canceled. |
| [12500004](../errorcode-useriam.md#12500004-authentication-timed-out) | The operation is time-out. |
| [12500005](../errorcode-useriam.md#12500005-unsupported-authentication-type) | The authentication type is not supported. |
| [12500006](../errorcode-useriam.md#12500006-unsupported-authentication-trust-level) | The authentication trust level is not supported. |
| [12500007](../errorcode-useriam.md#12500007-authentication-service-is-busy) | The authentication task is busy. |
| [12500009](../errorcode-useriam.md#12500009-authentication-locked) | The authenticator is locked. |
| [12500010](../errorcode-useriam.md#12500010-credential-not-enrolled) | The type of credential has not been enrolled. |

**Examples**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let challenge = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8]);
let authType = userAuth.UserAuthType.FACE;
let authTrustLevel = userAuth.AuthTrustLevel.ATL1;

try {
  let auth = userAuth.getAuthInstance(challenge, authType, authTrustLevel);
  auth.start();
  console.info('auth start successfully.');
} catch (error) {
  console.error(`auth failed. Code: ${error?.code}, message: ${error?.message}`);
}
```
