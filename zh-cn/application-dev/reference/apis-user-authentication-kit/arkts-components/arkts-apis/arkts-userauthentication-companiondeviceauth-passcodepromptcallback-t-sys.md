# PasscodePromptCallback（系统接口）

```TypeScript
type PasscodePromptCallback =
      (submit: PasscodeSubmitCallback, params: PasscodePromptParams) => void
```

定义当框架需要辅助设备的密码时调用的回调。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| submit | [PasscodeSubmitCallback](arkts-userauthentication-companiondeviceauth-passcodesubmitcallback-t-sys.md) | 是 | 用于提交输入的密码的回调用户。 |
| params | [PasscodePromptParams](arkts-userauthentication-companiondeviceauth-passcodepromptparams-i-sys.md) | 是 | Params carrying contextual information of this prompt request. |
