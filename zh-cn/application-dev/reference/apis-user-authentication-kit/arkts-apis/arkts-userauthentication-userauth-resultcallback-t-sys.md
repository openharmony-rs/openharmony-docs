# ResultCallback（系统接口）

```TypeScript
type ResultCallback = (challenge: Uint8Array, result: UserAuthResult) => void
```

返回远程认证结果的回调函数类型。该类型用于远程认证场景，在远程认证完成后，系统会调用此回调函数返回认证结果。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-userAuth-type ResultCallback = (challenge: Uint8Array, result: UserAuthResult) => void--><!--Device-userAuth-type ResultCallback = (challenge: Uint8Array, result: UserAuthResult) => void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| challenge | Uint8Array | 是 | 挑战值。用于防止重放攻击的一次性随机数，与发起认证时传入的challenge值一致。 |
| result | UserAuthResult | 是 | 用户认证结果。包含认证结果码、认证令牌等信息。 |

