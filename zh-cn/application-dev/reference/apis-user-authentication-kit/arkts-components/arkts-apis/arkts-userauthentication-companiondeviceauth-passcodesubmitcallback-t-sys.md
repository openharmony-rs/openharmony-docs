# PasscodeSubmitCallback（系统接口）

```TypeScript
type PasscodeSubmitCallback = (passcode: Uint8Array) => void
```

定义用于提交用户输入的密码的回调。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| passcode | Uint8Array | 是 | 用户输入的密码(例如USB的密码安全密钥)。 |
