# AuthCallback

认证器回调类。

**起始版本：** 9

<!--Device-appAccount-interface AuthCallback--><!--Device-appAccount-interface AuthCallback-End-->

**系统能力：** SystemCapability.Account.AppAccount

## 导入模块

```TypeScript
import { appAccount } from '@kit.BasicServicesKit';
```

## onRequestContinued

```TypeScript
onRequestContinued?: () => void
```

通知请求被继续处理。

**类型：** () => void

**起始版本：** 9

<!--Device-AuthCallback-onRequestContinued?: () => void--><!--Device-AuthCallback-onRequestContinued?: () => void-End-->

**系统能力：** SystemCapability.Account.AppAccount

## onRequestRedirected

```TypeScript
onRequestRedirected: (request: Want) => void
```

通知请求被跳转。

**类型：** (request: Want) => void

**起始版本：** 9

<!--Device-AuthCallback-onRequestRedirected: (request: Want) => void--><!--Device-AuthCallback-onRequestRedirected: (request: Want) => void-End-->

**系统能力：** SystemCapability.Account.AppAccount

## onResult

```TypeScript
onResult: (code: number, result?: AuthResult) => void
```

通知请求结果。

**类型：** (code: number, result?: AuthResult) => void

**起始版本：** 9

<!--Device-AuthCallback-onResult: (code: int, result?: AuthResult) => void--><!--Device-AuthCallback-onResult: (code: int, result?: AuthResult) => void-End-->

**系统能力：** SystemCapability.Account.AppAccount

