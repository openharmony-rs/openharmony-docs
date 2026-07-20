# AuthenticatorCallback

OAuth认证器回调接口。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃。建议使用[AuthCallback](arkts-basicservices-appaccount-authcallback-i.md)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [AuthCallback](arkts-basicservices-appaccount-authcallback-i.md)

<!--Device-appAccount-interface AuthenticatorCallback--><!--Device-appAccount-interface AuthenticatorCallback-End-->

**系统能力：** SystemCapability.Account.AppAccount

## 导入模块

```TypeScript
import { appAccount } from '@kit.BasicServicesKit';
```

## onRequestRedirected

```TypeScript
onRequestRedirected: (request: Want) => void
```

通知请求被跳转。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃。建议使用[onRequestRedirected](#onrequestredirected9)替代。

**类型：** (request: Want) =&gt; void

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [onRequestRedirected](arkts-basicservices-appaccount-authcallback-i.md#onrequestredirected)

<!--Device-AuthenticatorCallback-onRequestRedirected: (request: Want) => void--><!--Device-AuthenticatorCallback-onRequestRedirected: (request: Want) => void-End-->

**系统能力：** SystemCapability.Account.AppAccount

## onResult

```TypeScript
onResult: (code: number, result: { [key: string]: any }) => void
```

通知请求结果。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃。建议使用[onResult](#onresult9)替代。

**类型：** (code: number, result: { [key: string]: any }) =&gt; void

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [onResult](arkts-basicservices-appaccount-authcallback-i.md#onresult)

<!--Device-AuthenticatorCallback-onResult: (code: number, result: { [key: string]: any }) => void--><!--Device-AuthenticatorCallback-onResult: (code: number, result: { [key: string]: any }) => void-End-->

**系统能力：** SystemCapability.Account.AppAccount

