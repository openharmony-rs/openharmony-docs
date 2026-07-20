# GetPropertyRequest（系统接口）

提供获取属性请求的信息。

**起始版本：** 8

<!--Device-osAccount-interface GetPropertyRequest--><!--Device-osAccount-interface GetPropertyRequest-End-->

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

<!--Device-GetPropertyRequest-accountId?: int--><!--Device-GetPropertyRequest-accountId?: int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## authType

```TypeScript
authType: AuthType
```

身份验证凭据类型。

**类型：** AuthType

**起始版本：** 8

<!--Device-GetPropertyRequest-authType: AuthType--><!--Device-GetPropertyRequest-authType: AuthType-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## keys

```TypeScript
keys: Array<GetPropertyType>
```

指示要获取的属性类型数组。

**类型：** Array&lt;GetPropertyType&gt;

**起始版本：** 8

<!--Device-GetPropertyRequest-keys: Array<GetPropertyType>--><!--Device-GetPropertyRequest-keys: Array<GetPropertyType>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

