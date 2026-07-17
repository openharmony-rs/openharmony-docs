# EnrolledCredInfo（系统接口）

表示已注册凭据的信息。

**起始版本：** 8

<!--Device-osAccount-interface EnrolledCredInfo--><!--Device-osAccount-interface EnrolledCredInfo-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## authSubType

```TypeScript
authSubType: AuthSubType
```

指示认证凭据子类型。

**类型：** AuthSubType

**起始版本：** 8

<!--Device-EnrolledCredInfo-authSubType: AuthSubType--><!--Device-EnrolledCredInfo-authSubType: AuthSubType-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## authType

```TypeScript
authType: AuthType
```

身份验证凭据类型。

**类型：** AuthType

**起始版本：** 8

<!--Device-EnrolledCredInfo-authType: AuthType--><!--Device-EnrolledCredInfo-authType: AuthType-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## credentialId

```TypeScript
credentialId: Uint8Array
```

指示凭据索引，默认为空。

**类型：** Uint8Array

**起始版本：** 8

<!--Device-EnrolledCredInfo-credentialId: Uint8Array--><!--Device-EnrolledCredInfo-credentialId: Uint8Array-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## isAbandoned

```TypeScript
isAbandoned?: boolean
```

指示凭据是否废弃。废弃后的凭据可能作为备份凭据保存一段时间。true表示已废弃，false表示未废弃。默认为undefined，表示是否废弃未定义。

**类型：** boolean

**起始版本：** 20

<!--Device-EnrolledCredInfo-isAbandoned?: boolean--><!--Device-EnrolledCredInfo-isAbandoned?: boolean-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## templateId

```TypeScript
templateId: Uint8Array
```

指示凭据模板ID。

**类型：** Uint8Array

**起始版本：** 8

<!--Device-EnrolledCredInfo-templateId: Uint8Array--><!--Device-EnrolledCredInfo-templateId: Uint8Array-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## validityPeriod

```TypeScript
validityPeriod?: number
```

指示凭据有效期，单位为ms。默认为undefined，表示有效期未定义。

**类型：** number

**起始版本：** 20

<!--Device-EnrolledCredInfo-validityPeriod?: long--><!--Device-EnrolledCredInfo-validityPeriod?: long-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

