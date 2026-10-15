# UserRecognitionResult

```TypeScript
interface UserRecognitionResult
```

Enumerates the user recognition result.

**Since:** 26.0.1

<!--Device-userAuth-interface UserRecognitionResult--><!--Device-userAuth-interface UserRecognitionResult-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## authTrustLevel

```TypeScript
authTrustLevel?: AuthTrustLevel
```

Authentication trust level. Valid only when status is MATCH.

**Type:** [AuthTrustLevel](arkts-userauthentication-userauth-authtrustlevel-e.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-UserRecognitionResult-authTrustLevel?: AuthTrustLevel--><!--Device-UserRecognitionResult-authTrustLevel?: AuthTrustLevel-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## status

```TypeScript
status: UserRecognitionStatus
```

Recognition status.

**Type:** [UserRecognitionStatus](arkts-userauthentication-userauth-userrecognitionstatus-e.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-UserRecognitionResult-status: UserRecognitionStatus--><!--Device-UserRecognitionResult-status: UserRecognitionStatus-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## userId

```TypeScript
userId: number
```

System user ID recognized, which is a non-negative integer.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-UserRecognitionResult-userId: int--><!--Device-UserRecognitionResult-userId: int-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## userInfo

```TypeScript
userInfo: string
```

Information about the recognized user.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-UserRecognitionResult-userInfo: string--><!--Device-UserRecognitionResult-userInfo: string-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core
