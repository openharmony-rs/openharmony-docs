# UserRecognitionResultCallback

```TypeScript
type UserRecognitionResultCallback = (result: UserRecognitionResult) => void
```

定义接收用户识别结果的回调。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | [UserRecognitionResult](arkts-userauthentication-userauth-userrecognitionresult-i.md) | 是 | 识别结果。 |
