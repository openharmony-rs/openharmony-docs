# AuthEvent

Provides an asynchronous callback to return the authentication event information.

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [IAuthCallback](arkts-userauthentication-userauth-iauthcallback-i.md)

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## callback

```TypeScript
callback(result: EventInfo): void
```

Called to return the authentication result or authentication tip information.

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [onResult](arkts-userauthentication-userauth-iauthcallback-i.md#onresult)(result: UserAuthResult)

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| result | [EventInfo](arkts-userauthentication-userauth-eventinfo-t.md) | Yes | Authentication result or tip information. |

**Examples**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let challenge = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8]);
let authType = userAuth.UserAuthType.FACE;
let authTrustLevel = userAuth.AuthTrustLevel.ATL1;
// Obtain the authentication result via a callback.
try {
  let auth = userAuth.getAuthInstance(challenge, authType, authTrustLevel);
  auth.on('result', {
    callback: (result: userAuth.AuthResultInfo) => {
      console.info(`result: ${result.result}`);
    }
  } as userAuth.AuthEvent);
  auth.start();
  console.info('auth start successfully.');
} catch (error) {
  console.error(`auth failed. Code: ${error?.code}, message: ${error?.message}`);
  // do error.
}
// Obtain the authentication tip information via a callback.
try {
  let auth = userAuth.getAuthInstance(challenge, authType, authTrustLevel);
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
