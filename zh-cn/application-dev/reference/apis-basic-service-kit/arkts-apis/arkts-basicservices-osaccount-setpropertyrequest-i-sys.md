# SetPropertyRequest（系统接口）

提供设置属性请求的信息。

**起始版本：** 8

<!--Device-osAccount-interface SetPropertyRequest--><!--Device-osAccount-interface SetPropertyRequest-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## authType

```TypeScript
authType: AuthType
```

身份验证凭据类型。

**类型：** AuthType

**起始版本：** 8

<!--Device-SetPropertyRequest-authType: AuthType--><!--Device-SetPropertyRequest-authType: AuthType-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## key

```TypeScript
key: SetPropertyType
```

指示要设置的属性类型。

**类型：** SetPropertyType

**起始版本：** 8

<!--Device-SetPropertyRequest-key: SetPropertyType--><!--Device-SetPropertyRequest-key: SetPropertyType-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## setInfo

```TypeScript
setInfo: Uint8Array
```

指示要设置的信息。

**类型：** Uint8Array

**起始版本：** 8

<!--Device-SetPropertyRequest-setInfo: Uint8Array--><!--Device-SetPropertyRequest-setInfo: Uint8Array-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

