# EnrolledState

Represents the state of a credential enrolled. This API is used to describe the current state of enrolled authentication credentials (such as face, fingerprint, and companion device), including the credential digest and quantity. The application can call the [getEnrolledState](arkts-userauthentication-userauth-getenrolledstate-f.md) API to query the credential status, and check whether the user's credentials have changed (for example, whether a fingerprint, face, or companion device is added or deleted) to perform corresponding service processing.

**Since:** 12

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## credentialCount

```TypeScript
credentialCount: number
```

Number of enrolled credentials. This parameter indicates the number of credentials of a specified type enrolled by the current user, for example, the number of fingerprints or faces.

**Note:**  When an authentication result is reused, if the credential used for the previous authentication has been deleted, the returned value of **credentialCount** may be **0**.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## credentialDigest

```TypeScript
credentialDigest: number
```

Credential digest, which is randomly generated when a credential is added. This value is used to identify the version of the currently registered credential. It changes when a credential is added or deleted. The application can save this value and compare it with the value obtained in subsequent queries to determine whether the credential has changed.

**Note:**  When the authentication result is reused, if the credential used for the previous authentication has been deleted, the return value of **credentialDigest** may be **0**.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core
