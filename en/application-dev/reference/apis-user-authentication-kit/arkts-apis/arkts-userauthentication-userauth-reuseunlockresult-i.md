# ReuseUnlockResult

Represents information about the authentication result reuse. This API is used to configure parameters related to authentication result reuse, including the reuse mode and validity period. By properly configuring authentication result reuse, you can ensure security while avoiding repeated authentication, improving user experience.

> **NOTE:** 

> If the credential changes within the reuse duration after a successful identity authentication (including device
> unlock authentication), the authentication result can still be reused and the actual **EnrolledState** is
> returned in the authentication result. When the authentication credential used in the previous authentication has
> been deleted when the authentication result is reused:
> 
> - If the face or fingerprint credential is deleted, the authentication result can still be reused, but the values of **credentialCount** and **credentialDigest** in the returned **EnrolledState** are both **0**.
> 
> - If the screen lock password is deleted, the reuse will fail.

**Since:** 12

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## reuseDuration

```TypeScript
reuseDuration: number
```

Reuse duration of the authentication result, in milliseconds. The value must be greater than 0 and the maximum value is [MAX_ALLOWABLE_REUSE_DURATION](arkts-userauthentication-userauth-con.md#max_allowable_reuse_duration) (300,000 milliseconds, that is, 5 minutes). You are advised to set a proper duration based on the service scenario:

- Advanced security scenarios (such as payment): A short duration (for example, 30 seconds to 1 minute) is  
recommended.  
- Medium security scenarios (such as application login): A medium duration (for example, 2 to 3 minutes) is  
recommended.  
- Low security scenarios (such as data query): The maximum duration can be used.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## reuseMode

```TypeScript
reuseMode: ReuseMode
```

Authentication result reuse mode. Select a proper reuse mode based on the security requirements of the service scenario:

- **AUTH_TYPE_RELEVANT(1)**: Only the device unlock result that matches the authentication type is reused,  
providing the highest security.  
- **AUTH_TYPE_IRRELEVANT(2)**: Any type of device unlock result is reused, which is applicable to medium-security  
scenarios.  
- **CALLER_IRRELEVANT_AUTH_TYPE_RELEVANT(3)**: Any authentication result that matches the authentication type is  
reused, which is applicable to cross-application scenarios.  
- **CALLER_IRRELEVANT_AUTH_TYPE_IRRELEVANT(4)**: Any authentication result is reused, which provides the lowest  
security but the best user experience.

**Type:** [ReuseMode](arkts-userauthentication-userauth-reusemode-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core
