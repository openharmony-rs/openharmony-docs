# OsAccountSubProfile（系统接口）

系统账号子身份资料的定义。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## createTime

```TypeScript
createTime: number
```

子身份资料的创建时间，单位为ms。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## distributedInfo

```TypeScript
distributedInfo?: distributedAccount.DistributedInfo
```

系统账号子身份资料绑定的分布式账号信息，默认为undefined。

**类型：** [distributedAccount.DistributedInfo](arkts-basicservices-distributedaccount-distributedinfo-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## id

```TypeScript
id: number
```

系统账号子身份资料的标识符。取值范围为全体整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## index

```TypeScript
index: number
```

系统账号子身份资料的位置索引，取值范围：0~子身份资料个数减1。该索引在每个系统账号下唯一，由系统在创建子身份资料时自动分配。取值范围为全体整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## osAccountLocalId

```TypeScript
osAccountLocalId: number
```

子身份资料所属系统账号的本地标识符。取值范围为全体整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。
