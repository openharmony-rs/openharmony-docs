# AuthTipInfo

Represents the intermediate authentication status. This API is used to describe various intermediate states generated during authentication, including the authentication type and specific status code corresponding to each state. The application can obtain these intermediate states through [AuthTipCallback](arkts-userauthentication-userauth-authtipcallback-t.md) to provide more refined user feedback and status awareness during authentication.

**Since:** 20

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## tipCode

```TypeScript
tipCode: UserAuthTipCode
```

Intermediate status. It indicates the specific intermediate status type, such as authentication failure, timeout, lockout, and UI loading/release. The application should provide feedback or execute the corresponding processing logic based on the value of **tipCode**.

**Type:** [UserAuthTipCode](arkts-userauthentication-userauth-userauthtipcode-e.md)

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## tipType

```TypeScript
tipType: UserAuthType
```

Authentication type of the intermediate status. It indicates the authentication type that generates the current intermediate state, such as face authentication (**FACE**), fingerprint authentication (**FINGERPRINT**), or PIN authentication (**PIN**). The application can provide specific prompts for the user based on the authentication type.

**Type:** [UserAuthType](arkts-userauthentication-userauth-userauthtype-e.md)

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.UserIAM.UserAuth.Core
