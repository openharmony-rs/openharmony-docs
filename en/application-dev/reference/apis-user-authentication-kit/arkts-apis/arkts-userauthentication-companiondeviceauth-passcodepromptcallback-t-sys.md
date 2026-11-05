# PasscodePromptCallback (System API)

```TypeScript
type PasscodePromptCallback =
      (submit: PasscodeSubmitCallback, params: PasscodePromptParams) => void
```

Defines the callback type for a passcode request. When the system requires the user to enter a passcode, this callback is invoked, and the application needs to submit the passcode entered by the user through the **submit** callback.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-companionDeviceAuth-type PasscodePromptCallback =      (submit: PasscodeSubmitCallback, params: PasscodePromptParams) => void--><!--Device-companionDeviceAuth-type PasscodePromptCallback =      (submit: PasscodeSubmitCallback, params: PasscodePromptParams) => void-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| submit | [PasscodeSubmitCallback](arkts-userauthentication-companiondeviceauth-passcodesubmitcallback-t-sys.md) | Yes | Callback invoked to submit the passcode. After receiving the passcode entered by the user, the application submits the passcode to the system through this callback. |
| params | [PasscodePromptParams](arkts-userauthentication-companiondeviceauth-passcodepromptparams-i-sys.md) | Yes | Parameters of the passcode input request, including the challenge value and other information. |
