# GetDomainAccountInfoOptions（系统接口）

表示查询域账号信息的选项。

**起始版本：** 10

<!--Device-osAccount-interface GetDomainAccountInfoOptions--><!--Device-osAccount-interface GetDomainAccountInfoOptions-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

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

**起始版本：** 10

<!--Device-GetDomainAccountInfoOptions-accountName: string--><!--Device-GetDomainAccountInfoOptions-accountName: string-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## domain

```TypeScript
domain?: string
```

域名。默认为undefined。

**类型：** string

**起始版本：** 10

<!--Device-GetDomainAccountInfoOptions-domain?: string--><!--Device-GetDomainAccountInfoOptions-domain?: string-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## serverConfigId

```TypeScript
serverConfigId?: string
```

域账号所属服务器标识。默认为undefined。

**类型：** string

**起始版本：** 12

<!--Device-GetDomainAccountInfoOptions-serverConfigId?: string--><!--Device-GetDomainAccountInfoOptions-serverConfigId?: string-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

