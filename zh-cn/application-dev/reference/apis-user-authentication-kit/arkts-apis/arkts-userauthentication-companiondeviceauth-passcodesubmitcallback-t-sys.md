# PasscodeSubmitCallback（系统接口）

```TypeScript
type PasscodeSubmitCallback = (passcode: Uint8Array) => void
```

通行码提交回调函数类型。应用通过此回调将用户输入的通行码提交给系统。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-companionDeviceAuth-type PasscodeSubmitCallback = (passcode: Uint8Array) => void--><!--Device-companionDeviceAuth-type PasscodeSubmitCallback = (passcode: Uint8Array) => void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| passcode | Uint8Array | 是 | 用户输入的通行码。 |
