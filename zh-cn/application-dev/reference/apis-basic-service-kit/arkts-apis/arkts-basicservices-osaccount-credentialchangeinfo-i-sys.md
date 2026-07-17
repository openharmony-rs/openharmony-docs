# CredentialChangeInfo（系统接口）

表示凭据变更信息。

**起始版本：** 23

<!--Device-osAccount-interface CredentialChangeInfo--><!--Device-osAccount-interface CredentialChangeInfo-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## accountId

```TypeScript
accountId: number
```

表示系统账号标识。

**类型：** number

**起始版本：** 23

<!--Device-CredentialChangeInfo-accountId: int--><!--Device-CredentialChangeInfo-accountId: int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## addedCredentialId

```TypeScript
addedCredentialId?: Uint8Array
```

表示添加的凭据ID，添加凭据和更新凭据操作都会返回该ID。默认为undefined。

**类型：** Uint8Array

**起始版本：** 23

<!--Device-CredentialChangeInfo-addedCredentialId?: Uint8Array--><!--Device-CredentialChangeInfo-addedCredentialId?: Uint8Array-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## changeType

```TypeScript
changeType: CredentialChangeType
```

表示凭据变更的类型。

**类型：** CredentialChangeType

**起始版本：** 23

<!--Device-CredentialChangeInfo-changeType: CredentialChangeType--><!--Device-CredentialChangeInfo-changeType: CredentialChangeType-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## credentialType

```TypeScript
credentialType: AuthType
```

表示凭据类型。

**类型：** AuthType

**起始版本：** 23

<!--Device-CredentialChangeInfo-credentialType: AuthType--><!--Device-CredentialChangeInfo-credentialType: AuthType-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## deletedCredentialId

```TypeScript
deletedCredentialId?: Uint8Array
```

表示删除的凭据ID，删除凭据和更新凭据操作都会返回该ID。默认为undefined。

**类型：** Uint8Array

**起始版本：** 23

<!--Device-CredentialChangeInfo-deletedCredentialId?: Uint8Array--><!--Device-CredentialChangeInfo-deletedCredentialId?: Uint8Array-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## isSilent

```TypeScript
isSilent: boolean
```

表示是否为静默变更，静默变更表示变更由系统在后台自动地发起。

**类型：** boolean

**起始版本：** 23

<!--Device-CredentialChangeInfo-isSilent: boolean--><!--Device-CredentialChangeInfo-isSilent: boolean-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

