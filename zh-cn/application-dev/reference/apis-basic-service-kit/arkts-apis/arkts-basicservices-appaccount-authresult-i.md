# AuthResult

表示认证结果信息。

**起始版本：** 9

<!--Device-appAccount-interface AuthResult--><!--Device-appAccount-interface AuthResult-End-->

**系统能力：** SystemCapability.Account.AppAccount

## 导入模块

```TypeScript
import { appAccount } from '@kit.BasicServicesKit';
```

## account

```TypeScript
account?: AppAccountInfo
```

令牌所属的账号信息，默认为空。

**类型：** AppAccountInfo

**起始版本：** 9

<!--Device-AuthResult-account?: AppAccountInfo--><!--Device-AuthResult-account?: AppAccountInfo-End-->

**系统能力：** SystemCapability.Account.AppAccount

## tokenInfo

```TypeScript
tokenInfo?: AuthTokenInfo
```

令牌信息，默认为空。

**类型：** AuthTokenInfo

**起始版本：** 9

<!--Device-AuthResult-tokenInfo?: AuthTokenInfo--><!--Device-AuthResult-tokenInfo?: AuthTokenInfo-End-->

**系统能力：** SystemCapability.Account.AppAccount

