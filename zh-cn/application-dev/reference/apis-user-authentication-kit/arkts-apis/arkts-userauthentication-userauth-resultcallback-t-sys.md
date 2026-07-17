# ResultCallback（系统接口）

```TypeScript
type ResultCallback = (challenge: Uint8Array, result: UserAuthResult) => void
```

调用返回认证结果。如果鉴权成功。UserAuthResult中包含token信息。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-userAuth-type ResultCallback = (challenge: Uint8Array, result: UserAuthResult) => void--><!--Device-userAuth-type ResultCallback = (challenge: Uint8Array, result: UserAuthResult) => void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| challenge | Uint8Array | 是 | 挑战值，可以以Uint8Array([])格式传递。 |
| result | UserAuthResult | 是 | 身份认证结果。 |

