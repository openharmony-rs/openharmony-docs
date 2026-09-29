# UserRecognitionResult

```TypeScript
interface UserRecognitionResult
```

Defines the user recognition result.

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

Authentication trust level. Only returned when the status is [MATCH](arkts-userauthentication-userauth-userrecognitionstatus-e.md#match). For details about the values, see [AuthTrustLevel](arkts-userauthentication-userauth-authtrustlevel-e.md).

**Type:** [AuthTrustLevel](arkts-userauthentication-userauth-authtrustlevel-e.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.1.

<!--Device-UserRecognitionResult-authTrustLevel?: AuthTrustLevel--><!--Device-UserRecognitionResult-authTrustLevel?: AuthTrustLevel-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## status

```TypeScript
status: UserRecognitionStatus
```

Recognition status. For details about the values, see [UserRecognitionStatus](arkts-userauthentication-userauth-userrecognitionstatus-e.md).

**Type:** [UserRecognitionStatus](arkts-userauthentication-userauth-userrecognitionstatus-e.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.1.

<!--Device-UserRecognitionResult-status: UserRecognitionStatus--><!--Device-UserRecognitionResult-status: UserRecognitionStatus-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## userId

```TypeScript
userId: number
```

ID of the recognized OS user. The value is a non-negative integer.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.1.

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

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.1.

<!--Device-UserRecognitionResult-userInfo: string--><!--Device-UserRecognitionResult-userInfo: string-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core
