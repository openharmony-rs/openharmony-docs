# AuthResultInfo

```TypeScript
interface AuthResultInfo
```

Represents the authentication result.

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [UserAuthResult](arkts-userauthentication-userauth-userauthresult-i.md)

<!--Device-userAuth-interface AuthResultInfo--><!--Device-userAuth-interface AuthResultInfo-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## lockoutDuration

```TypeScript
lockoutDuration?: number
```

Lock duration of the authentication operation, in ms.

**Type:** number

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [lockoutDuration](arkts-userauthentication-userauth-authlockstate-i.md#lockoutduration)

<!--Device-AuthResultInfo-lockoutDuration?: number--><!--Device-AuthResultInfo-lockoutDuration?: number-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## remainAttempts

```TypeScript
remainAttempts?: number
```

Number of remaining authentication attempts.

**Type:** number

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [remainingAuthAttempts](arkts-userauthentication-userauth-authlockstate-i.md#remainingauthattempts)

<!--Device-AuthResultInfo-remainAttempts?: number--><!--Device-AuthResultInfo-remainAttempts?: number-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## result

```TypeScript
result: number
```

Authentication result.

**Type:** number

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [result](arkts-userauthentication-userauth-userauthresult-i.md#result)

<!--Device-AuthResultInfo-result: number--><!--Device-AuthResultInfo-result: number-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## token

```TypeScript
token?: Uint8Array
```

Token that has passed the user identity authentication.

**Type:** Uint8Array

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [token](arkts-userauthentication-userauth-userauthresult-i.md#token)

<!--Device-AuthResultInfo-token?: Uint8Array--><!--Device-AuthResultInfo-token?: Uint8Array-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core
