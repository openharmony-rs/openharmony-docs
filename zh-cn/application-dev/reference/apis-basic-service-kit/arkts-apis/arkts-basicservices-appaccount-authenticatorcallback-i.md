# AuthenticatorCallback

OAuth认证器回调接口。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃。建议使用[AuthCallback](arkts-basicservices-appaccount-authcallback-i.md#AuthCallback)替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [AuthCallback](arkts-basicservices-appaccount-authcallback-i.md#AuthCallback)

<!--Device-appAccount-interface AuthenticatorCallback--><!--Device-appAccount-interface AuthenticatorCallback-End-->

**系统能力：** SystemCapability.Account.AppAccount

## onRequestRedirected

```TypeScript
onRequestRedirected: (request: Want) => void
```

通知请求被跳转。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃。建议使用[onRequestRedirected](#onRequestRedirected)替代。

**类型：** (request: Want) =&gt; void

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** onRequestRedirected

<!--Device-AuthenticatorCallback-onRequestRedirected: (request: Want) => void--><!--Device-AuthenticatorCallback-onRequestRedirected: (request: Want) => void-End-->

**系统能力：** SystemCapability.Account.AppAccount

## onResult

```TypeScript
onResult: (code: number, result: { [key: string]: any }) => void
```

通知请求结果。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃。建议使用[onResult](#onResult)替代。

**类型：** (code: number, result: { [key: string]: any }) =&gt; void

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** onResult

<!--Device-AuthenticatorCallback-onResult: (code: number, result: { [key: string]: any }) => void--><!--Device-AuthenticatorCallback-onResult: (code: number, result: { [key: string]: any }) => void-End-->

**系统能力：** SystemCapability.Account.AppAccount

