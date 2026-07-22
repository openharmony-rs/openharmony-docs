# GetAuthInfoOptions（系统接口）

表示[查询认证凭据信息](arkts-basicservices-osaccount-useridentitymanager-c-sys.md#getauthinfo)的可选参数集合。

**起始版本：** 12

<!--Device-osAccount-interface GetAuthInfoOptions--><!--Device-osAccount-interface GetAuthInfoOptions-End-->

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

<!--Device-GetAuthInfoOptions-accountId?: int--><!--Device-GetAuthInfoOptions-accountId?: int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## authType

```TypeScript
authType?: AuthType
```

认证类型，默认为undefined。

**类型：** AuthType

**起始版本：** 12

<!--Device-GetAuthInfoOptions-authType?: AuthType--><!--Device-GetAuthInfoOptions-authType?: AuthType-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

