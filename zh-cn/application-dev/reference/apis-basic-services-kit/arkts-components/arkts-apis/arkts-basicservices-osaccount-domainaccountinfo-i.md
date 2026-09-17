# DomainAccountInfo

表示域账号信息。

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## accountName

```TypeScript
accountName: string
```

域账号名。

**类型：** string

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

## additionalInfo

```TypeScript
additionalInfo?: Record<string, Object>
```

域账号附加信息，默认为空。

此接口仅可在Stage模型下使用。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

## domain

```TypeScript
domain: string
```

域名。

**类型：** string

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

## serverConfigId

```TypeScript
serverConfigId?: string
```

域账号配置ID，默认为空字符串。

**类型：** string

**起始版本：** 18

**系统能力：** SystemCapability.Account.OsAccount
