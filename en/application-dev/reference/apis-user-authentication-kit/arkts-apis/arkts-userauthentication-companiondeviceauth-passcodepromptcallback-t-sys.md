# PasscodePromptCallback (System API)

```TypeScript
type PasscodePromptCallback =
      (submit: PasscodeSubmitCallback, params: PasscodePromptParams) => void
```

Defines the callback invoked when the framework needs a passcode for a companion device.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| submit | [PasscodeSubmitCallback](arkts-userauthentication-companiondeviceauth-passcodesubmitcallback-t-sys.md) | Yes | Callback used to submit the passcode entered by the user. |
| params | [PasscodePromptParams](arkts-userauthentication-companiondeviceauth-passcodepromptparams-i-sys.md) | Yes | Params carrying contextual information of this prompt request. |
