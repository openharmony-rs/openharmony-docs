# UserRecognitionStatus

Enumerates the user recognition status.

**Since:** 26.1.0

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## UNCERTAIN

```TypeScript
UNCERTAIN = 0
```

Uncertain recognition status. It indicates that recognition is in progress or has not reached a conclusion.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## MISMATCH

```TypeScript
MISMATCH = 1
```

The recognized user does not match the active OS user.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## MATCH

```TypeScript
MATCH = 2
```

The recognized user matches the active OS user.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.UserIAM.UserAuth.Core
