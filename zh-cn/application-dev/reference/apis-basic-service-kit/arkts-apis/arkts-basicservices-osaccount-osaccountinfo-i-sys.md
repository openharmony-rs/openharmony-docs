# OsAccountInfo

表示系统账号信息。

**起始版本：** 7

<!--Device-osAccount-interface OsAccountInfo--><!--Device-osAccount-interface OsAccountInfo-End-->

**系统能力：** SystemCapability.Account.OsAccount

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## isLoggedIn

```TypeScript
isLoggedIn?: boolean
```

是否登录。true表示已登录；false表示未登录。

此接口为系统接口，默认为false。

**类型：** boolean

**起始版本：** 12

<!--Device-OsAccountInfo-isLoggedIn?: boolean--><!--Device-OsAccountInfo-isLoggedIn?: boolean-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## shortName

```TypeScript
shortName?: string
```

系统账号的短名称。

此接口为系统接口，默认为空。

**类型：** string

**起始版本：** 12

<!--Device-OsAccountInfo-shortName?: string--><!--Device-OsAccountInfo-shortName?: string-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

