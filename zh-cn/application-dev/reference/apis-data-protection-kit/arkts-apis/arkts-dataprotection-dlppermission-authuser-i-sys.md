# AuthUser（系统接口）

表示授权用户数据。

**起始版本：** 10

<!--Device-dlpPermission-export interface AuthUser--><!--Device-dlpPermission-export interface AuthUser-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## authAccount

```TypeScript
authAccount: string
```

表示被授权用户账号。不超过255字节，超出此范围抛出错误码401。

**类型：** string

**起始版本：** 10

<!--Device-AuthUser-authAccount: string--><!--Device-AuthUser-authAccount: string-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## authAccountType

```TypeScript
authAccountType: AccountType
```

表示被授权用户账号类型。

**类型：** [AccountType](arkts-dataprotection-dlppermission-accounttype-e.md)

**起始版本：** 10

<!--Device-AuthUser-authAccountType: AccountType--><!--Device-AuthUser-authAccountType: AccountType-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## dlpFileAccess

```TypeScript
dlpFileAccess: DLPFileAccess
```

表示被授予的权限。

**类型：** [DLPFileAccess](arkts-dataprotection-dlppermission-dlpfileaccess-e.md)

**起始版本：** 10

<!--Device-AuthUser-dlpFileAccess: DLPFileAccess--><!--Device-AuthUser-dlpFileAccess: DLPFileAccess-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## permExpiryTime

```TypeScript
permExpiryTime: number
```

表示授权到期时间。取值范围大于等于0，超出此范围将被强转为非符号整数。单位：s。

**类型：** number

**起始版本：** 10

<!--Device-AuthUser-permExpiryTime: number--><!--Device-AuthUser-permExpiryTime: number-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

