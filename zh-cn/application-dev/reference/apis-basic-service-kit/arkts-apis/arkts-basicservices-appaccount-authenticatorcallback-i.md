# AuthenticatorCallback

OAuth认证器回调接口。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃。建议使用[AuthCallback]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [appAccount.AuthCallback](arkts-basicservices-appaccount-authcallback-i.md)

<!--Device-appAccount-interface AuthenticatorCallback--><!--Device-appAccount-interface AuthenticatorCallback-End-->

**系统能力：** SystemCapability.Account.AppAccount

## onRequestRedirected

```TypeScript
onRequestRedirected: (request: Want) => void
```

通知请求被跳转。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃。建议使用\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_替代。

**类型：** (request: Want) =&gt; void

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [AppAccount.AuthCallback.onRequestRedirected](arkts-basicservices-appaccount-authcallback-i.md#onrequestredirected)

<!--Device-AuthenticatorCallback-onRequestRedirected: (request: Want) => void--><!--Device-AuthenticatorCallback-onRequestRedirected: (request: Want) => void-End-->

**系统能力：** SystemCapability.Account.AppAccount

## onResult

```TypeScript
onResult: (code: number, result: { [key: string]: any }) => void
```

通知请求结果。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃。建议使用\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_替代。

**类型：** (code: number, result: { [key: string]: any }) =&gt; void

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [AppAccount.AuthCallback.onResult](arkts-basicservices-appaccount-authcallback-i.md#onresult)

<!--Device-AuthenticatorCallback-onResult: (code: number, result: { [key: string]: any }) => void--><!--Device-AuthenticatorCallback-onResult: (code: number, result: { [key: string]: any }) => void-End-->

**系统能力：** SystemCapability.Account.AppAccount

