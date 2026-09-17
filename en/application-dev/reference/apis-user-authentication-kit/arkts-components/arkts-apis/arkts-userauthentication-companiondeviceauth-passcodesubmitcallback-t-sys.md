# PasscodeSubmitCallback (System API)

```TypeScript
type PasscodeSubmitCallback = (passcode: Uint8Array) => void
```

Defines the callback used to submit a passcode entered by the user.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| passcode | Uint8Array | Yes | Passcode entered by the user (for example, the Passcode of a USB security key). |
