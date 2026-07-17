# OsAccountSubProfile（系统接口）

系统账号子Profile的定义

**起始版本：** 26.0.0

<!--Device-osAccount-interface OsAccountSubProfile--><!--Device-osAccount-interface OsAccountSubProfile-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## distributedInfo

```TypeScript
distributedInfo?: distributedAccount.DistributedInfo
```

系统账号子profile绑定的分布式账号信息。

**类型：** distributedAccount.DistributedInfo

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OsAccountSubProfile-distributedInfo?: distributedAccount.DistributedInfo--><!--Device-OsAccountSubProfile-distributedInfo?: distributedAccount.DistributedInfo-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## id

```TypeScript
id: number
```

系统账号子profile的标识符。取值范围为全体整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OsAccountSubProfile-id: int--><!--Device-OsAccountSubProfile-id: int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## index

```TypeScript
index: number
```

系统账号子profile的位置索引，取值范围：0~子profile个数减1。该索引在每个系统账号下唯一，由系统在创建子Profile时自动分配。取值范围为全体整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OsAccountSubProfile-index: int--><!--Device-OsAccountSubProfile-index: int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## osAccountLocalId

```TypeScript
osAccountLocalId: number
```

子profile所属系统账号的本地标识符。取值范围为全体整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OsAccountSubProfile-osAccountLocalId: int--><!--Device-OsAccountSubProfile-osAccountLocalId: int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

