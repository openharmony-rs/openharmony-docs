# AuthOptions（系统接口）

表示[认证用户](arkts-basicservices-osaccount-userauth-c-sys.md#auth-2)的可选参数集合。

**起始版本：** 12

<!--Device-osAccount-interface AuthOptions--><!--Device-osAccount-interface AuthOptions-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## accountId

```TypeScript
accountId?: number
```

系统账号标识，默认为undefined。

**类型：** number

**起始版本：** 12

<!--Device-AuthOptions-accountId?: int--><!--Device-AuthOptions-accountId?: int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## additionalInfo

```TypeScript
additionalInfo?: string
```

表示有关身份验证选项的附加信息。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AuthOptions-additionalInfo?: string--><!--Device-AuthOptions-additionalInfo?: string-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## authIntent

```TypeScript
authIntent?: AuthIntent
```

认证意图，默认为undefined。

**类型：** AuthIntent

**起始版本：** 12

<!--Device-AuthOptions-authIntent?: AuthIntent--><!--Device-AuthOptions-authIntent?: AuthIntent-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## remoteAuthOptions

```TypeScript
remoteAuthOptions?: RemoteAuthOptions
```

远程认证选项，默认为undefined。

**类型：** RemoteAuthOptions

**起始版本：** 12

<!--Device-AuthOptions-remoteAuthOptions?: RemoteAuthOptions--><!--Device-AuthOptions-remoteAuthOptions?: RemoteAuthOptions-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

