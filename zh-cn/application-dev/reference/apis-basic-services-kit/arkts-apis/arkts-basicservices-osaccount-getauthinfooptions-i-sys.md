# GetAuthInfoOptions（系统接口）

表示查询认证凭据信息[getAuthInfo](arkts-basicservices-osaccount-useridentitymanager-c-sys.md#getauthinfo)的可选参数集合。

**起始版本：** 12

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

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## authType

```TypeScript
authType?: AuthType
```

认证类型，默认为undefined。

**类型：** AuthType

**起始版本：** 12

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。
