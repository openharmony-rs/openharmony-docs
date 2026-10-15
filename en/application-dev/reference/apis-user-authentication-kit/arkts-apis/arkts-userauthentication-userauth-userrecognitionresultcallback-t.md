# UserRecognitionResultCallback

```TypeScript
type UserRecognitionResultCallback = (result: UserRecognitionResult) => void
```

Defines the callback for the user recognition result.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-userAuth-type UserRecognitionResultCallback = (result: UserRecognitionResult) => void--><!--Device-userAuth-type UserRecognitionResultCallback = (result: UserRecognitionResult) => void-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| result | [UserRecognitionResult](arkts-userauthentication-userauth-userrecognitionresult-i.md) | Yes | User recognition result. |
