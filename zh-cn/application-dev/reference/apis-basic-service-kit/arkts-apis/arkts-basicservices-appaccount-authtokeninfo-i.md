# AuthTokenInfo

表示Auth令牌信息。

**起始版本：** 9

<!--Device-appAccount-interface AuthTokenInfo--><!--Device-appAccount-interface AuthTokenInfo-End-->

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

<!--Device-AuthTokenInfo-account?: AppAccountInfo--><!--Device-AuthTokenInfo-account?: AppAccountInfo-End-->

**系统能力：** SystemCapability.Account.AppAccount

## authType

```TypeScript
authType: string
```

令牌的鉴权类型。

**类型：** string

**起始版本：** 9

<!--Device-AuthTokenInfo-authType: string--><!--Device-AuthTokenInfo-authType: string-End-->

**系统能力：** SystemCapability.Account.AppAccount

## token

```TypeScript
token: string
```

令牌的取值。

**类型：** string

**起始版本：** 9

<!--Device-AuthTokenInfo-token: string--><!--Device-AuthTokenInfo-token: string-End-->

**系统能力：** SystemCapability.Account.AppAccount

