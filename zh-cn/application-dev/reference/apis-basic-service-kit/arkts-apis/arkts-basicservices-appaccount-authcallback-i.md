# AuthCallback

认证器回调类。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-appAccount-interface AuthCallback--><!--Device-appAccount-interface AuthCallback-End-->

**系统能力：** SystemCapability.Account.AppAccount

## onRequestContinued

```TypeScript
onRequestContinued?: () => void
```

通知请求被继续处理。

**类型：** () =&gt; void

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-AuthCallback-onRequestContinued?: () => void--><!--Device-AuthCallback-onRequestContinued?: () => void-End-->

**系统能力：** SystemCapability.Account.AppAccount

## onRequestRedirected

```TypeScript
onRequestRedirected: (request: Want) => void
```

通知请求被跳转。

**类型：** (request: Want) =&gt; void

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-AuthCallback-onRequestRedirected: (request: Want) => void--><!--Device-AuthCallback-onRequestRedirected: (request: Want) => void-End-->

**系统能力：** SystemCapability.Account.AppAccount

## onResult

```TypeScript
onResult: (code: int, result?: AuthResult) => void
```

通知请求结果。

**类型：** (code: int, result?: AuthResult) =&gt; void

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-AuthCallback-onResult: (code: int, result?: AuthResult) => void--><!--Device-AuthCallback-onResult: (code: int, result?: AuthResult) => void-End-->

**系统能力：** SystemCapability.Account.AppAccount

