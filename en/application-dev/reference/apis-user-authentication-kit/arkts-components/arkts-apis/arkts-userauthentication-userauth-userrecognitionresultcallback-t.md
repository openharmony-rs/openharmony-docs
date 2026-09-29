# UserRecognitionResultCallback

```TypeScript
type UserRecognitionResultCallback = (result: UserRecognitionResult) => void
```

Defines the callback used to receive the user recognition result.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.1.

<!--Device-userAuth-type UserRecognitionResultCallback = (result: UserRecognitionResult) => void--><!--Device-userAuth-type UserRecognitionResultCallback = (result: UserRecognitionResult) => void-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| result | [UserRecognitionResult](arkts-userauthentication-userauth-userrecognitionresult-i.md) | Yes | Recognition result. |
