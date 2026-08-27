# WidgetParamCallback（系统接口）

```TypeScript
type WidgetParamCallback = (challenge: Uint8Array) => WidgetParam
```

获取远程认证页面参数的回调函数类型。该类型用于远程认证场景，在需要获取远程认证界面的配置参数时，系统会调用此回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| challenge | Uint8Array | 是 | 随机挑战值，可用于防重放攻击。字节，可传Uint8Array([])。建议使用 [加解密算法库框架](../../apis-crypto-architecture-kit/arkts-apis/arkts-security-cryptoframework.md)生成的随机数作为挑战值，以增强安全性。  最大长度为32。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WidgetParam](arkts-userauthentication-userauth-widgetparam-i.md) | 用户认证界面配置参数。包含认证界面的标题、导航按钮文本等配置信息。 |
