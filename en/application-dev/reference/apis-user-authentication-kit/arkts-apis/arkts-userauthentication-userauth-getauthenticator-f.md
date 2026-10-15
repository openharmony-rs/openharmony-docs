# getAuthenticator

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## getAuthenticator

```TypeScript
function getAuthenticator(): Authenticator
```

Obtains an **Authenticator** instance for user authentication.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [getAuthInstance](arkts-userauthentication-userauth-getauthinstance-f.md)

<!--Device-userAuth-function getAuthenticator(): Authenticator--><!--Device-userAuth-function getAuthenticator(): Authenticator-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Return value:**

| Type | Description |
| --- | --- |
| [Authenticator](arkts-userauthentication-userauth-authenticator-i.md) | **Authenticator** instance obtained. |

**Examples**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
  
let authenticator = userAuth.getAuthenticator();
```
