# IUserAuthCallback

Provides callbacks to return the authentication result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [AuthEvent](arkts-userauthentication-userauth-authevent-i.md)

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## onAcquireInfo

```TypeScript
onAcquireInfo?: (module: number, acquire: number, extraInfo: any) => void
```

Called to acquire authentication tip information. This API is optional.

- **module**: ID of the module that sends the tip information.  
- **acquire**: Authentication tip information.  
- **extraInfo**: Reserved field.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [callback](arkts-userauthentication-userauth-authevent-i.md#callback)

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| module | number | Yes |  |
| acquire | number | Yes |  |
| extraInfo | any | Yes |  |

**Examples**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let auth = new userAuth.UserAuth();
let challenge = new Uint8Array([]);
auth.auth(challenge, userAuth.UserAuthType.FACE, userAuth.AuthTrustLevel.ATL1, {
  onResult: (result, extraInfo) => {
    try {
      console.info(`auth onResult result = ${result}`);
      if (result == userAuth.ResultCode.SUCCESS) {
        // Add the logic to be executed when the authentication is successful.
      }  else {
        // Add the logic to be executed when the authentication fails.
      }
    } catch (error) {
      console.error(`auth onResult failed. Code: ${error?.code}, message: ${error?.message}`);
    }
  },
  onAcquireInfo: (module, acquire, extraInfo : userAuth.AuthResult) => {
    try {
      console.info('auth onAcquireInfo successfully.');
    } catch (error) {
      console.error(`auth onAcquireInfo failed. Code: ${error?.code}, message: ${error?.message}`);
    }
  }
});
```

## onResult

```TypeScript
onResult: (result: number, extraInfo: AuthResult) => void
```

Called to return the authentication result.

- **result**: Authentication result. For details, see [ResultCode](arkts-userauthentication-userauth-resultcode-e.md).  
- **extraInfo**: Extended information, which varies depending on the authentication result. If the authentication  
is successful, the user authentication token will be returned in **extraInfo**. If the authentication fails, the remaining number of authentication times will be returned in **extraInfo**. If the authentication executor is locked, the freeze time will be returned in **extraInfo**.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [callback](arkts-userauthentication-userauth-authevent-i.md#callback)

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| result | number | Yes |  |
| extraInfo | [AuthResult](arkts-userauthentication-userauth-authresult-i.md) | Yes |  |

**Examples**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let auth = new userAuth.UserAuth();
let challenge = new Uint8Array([]);
auth.auth(challenge, userAuth.UserAuthType.FACE, userAuth.AuthTrustLevel.ATL1, {
  onResult: (result, extraInfo) => {
    try {
      console.info(`auth onResult result = ${result}`);
      if (result == userAuth.ResultCode.SUCCESS) {
        // Add the logic to be executed when the authentication is successful.
      }  else {
        // Add the logic to be executed when the authentication fails.
      }
    } catch (error) {
      console.error(`auth onResult failed. Code: ${error?.code}, message: ${error?.message}`);
    }
  }
});
```
