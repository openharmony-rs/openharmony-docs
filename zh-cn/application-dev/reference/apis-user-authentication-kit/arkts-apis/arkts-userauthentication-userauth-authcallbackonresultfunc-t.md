# AuthCallbackOnResultFunc

```TypeScript
type AuthCallbackOnResultFunc = (result: UserAuthResult) => void
```

回调函数，返回认证结果。认证成功时，可以通过UserAuthResult获取到认证成功的令牌信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-userAuth-type AuthCallbackOnResultFunc = (result: UserAuthResult) => void--><!--Device-userAuth-type AuthCallbackOnResultFunc = (result: UserAuthResult) => void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | UserAuthResult | 是 | Authentication result information. |

