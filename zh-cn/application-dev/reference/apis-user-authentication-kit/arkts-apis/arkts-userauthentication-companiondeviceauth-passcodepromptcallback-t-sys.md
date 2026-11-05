# PasscodePromptCallback（系统接口）

```TypeScript
type PasscodePromptCallback =
      (submit: PasscodeSubmitCallback, params: PasscodePromptParams) => void
```

通行码请求回调函数类型。当系统需要用户输入通行码时，会调用此回调，应用需通过submit回调提交用户输入的通行码。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-companionDeviceAuth-type PasscodePromptCallback =      (submit: PasscodeSubmitCallback, params: PasscodePromptParams) => void--><!--Device-companionDeviceAuth-type PasscodePromptCallback =      (submit: PasscodeSubmitCallback, params: PasscodePromptParams) => void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| submit | [PasscodeSubmitCallback](arkts-userauthentication-companiondeviceauth-passcodesubmitcallback-t-sys.md) | 是 | 通行码提交回调。应用接收用户输入的通行码后，通过此回调将通行码提交给系统。 |
| params | [PasscodePromptParams](arkts-userauthentication-companiondeviceauth-passcodepromptparams-i-sys.md) | 是 | 通行码输入请求的参数，包含挑战值等信息。 |
