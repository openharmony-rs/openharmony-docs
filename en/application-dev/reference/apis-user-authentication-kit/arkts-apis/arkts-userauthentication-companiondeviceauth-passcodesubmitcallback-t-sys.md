# PasscodeSubmitCallback (System API)

```TypeScript
type PasscodeSubmitCallback = (passcode: Uint8Array) => void
```

Defines the passcode submission callback. The application submits the passcode entered by the user to the system through this callback.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-companionDeviceAuth-type PasscodeSubmitCallback = (passcode: Uint8Array) => void--><!--Device-companionDeviceAuth-type PasscodeSubmitCallback = (passcode: Uint8Array) => void-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| passcode | Uint8Array | Yes | Passcode entered by the user. |
