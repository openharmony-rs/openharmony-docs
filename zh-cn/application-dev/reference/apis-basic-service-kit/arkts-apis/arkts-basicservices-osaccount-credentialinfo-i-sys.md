# CredentialInfo（系统接口）

表示凭证信息。

**起始版本：** 8

<!--Device-osAccount-interface CredentialInfo--><!--Device-osAccount-interface CredentialInfo-End-->

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

<!--Device-CredentialInfo-accountId?: int--><!--Device-CredentialInfo-accountId?: int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## additionalInfo

```TypeScript
additionalInfo?: string
```

凭据的附加信息，默认为空字符串。

**类型：** string

**起始版本：** 23

<!--Device-CredentialInfo-additionalInfo?: string--><!--Device-CredentialInfo-additionalInfo?: string-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## credSubType

```TypeScript
credSubType: AuthSubType
```

指示凭据子类型。

**类型：** AuthSubType

**起始版本：** 8

<!--Device-CredentialInfo-credSubType: AuthSubType--><!--Device-CredentialInfo-credSubType: AuthSubType-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## credType

```TypeScript
credType: AuthType
```

指示凭据类型。

**类型：** AuthType

**起始版本：** 8

<!--Device-CredentialInfo-credType: AuthType--><!--Device-CredentialInfo-credType: AuthType-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## token

```TypeScript
token: Uint8Array
```

指示认证令牌，默认为空。

**类型：** Uint8Array

**起始版本：** 8

<!--Device-CredentialInfo-token: Uint8Array--><!--Device-CredentialInfo-token: Uint8Array-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

