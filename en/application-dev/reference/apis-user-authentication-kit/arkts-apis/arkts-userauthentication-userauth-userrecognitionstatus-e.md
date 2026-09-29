# UserRecognitionStatus

```TypeScript
enum UserRecognitionStatus
```

Enumerates the user recognition status.

**Since:** 26.0.1

<!--Device-userAuth-enum UserRecognitionStatus--><!--Device-userAuth-enum UserRecognitionStatus-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## UNCERTAIN

```TypeScript
UNCERTAIN = 0
```

Uncertain recognition status. It indicates that recognition is in progress or has not reached a conclusion.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.1.

<!--Device-UserRecognitionStatus-UNCERTAIN = 0--><!--Device-UserRecognitionStatus-UNCERTAIN = 0-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## MISMATCH

```TypeScript
MISMATCH = 1
```

The recognized user does not match the active OS user.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.1.

<!--Device-UserRecognitionStatus-MISMATCH = 1--><!--Device-UserRecognitionStatus-MISMATCH = 1-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## MATCH

```TypeScript
MATCH = 2
```

The recognized user matches the active OS user.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.1.

<!--Device-UserRecognitionStatus-MATCH = 2--><!--Device-UserRecognitionStatus-MATCH = 2-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core
