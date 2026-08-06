# AuthUser

表示授权用户数据。

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-dlpPermission-export interface AuthUser--><!--Device-dlpPermission-export interface AuthUser-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## authAccount

```TypeScript
authAccount: string
```

表示被授权用户账号。不超过255字节，超出此范围抛出错误码401。

**类型：** string

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-AuthUser-authAccount: string--><!--Device-AuthUser-authAccount: string-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## authAccountType

```TypeScript
authAccountType: AccountType
```

表示被授权用户账号类型。

**类型：** AccountType

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-AuthUser-authAccountType: AccountType--><!--Device-AuthUser-authAccountType: AccountType-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## dlpFileAccess

```TypeScript
dlpFileAccess: DLPFileAccess
```

表示被授予的权限。

**类型：** DLPFileAccess

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-AuthUser-dlpFileAccess: DLPFileAccess--><!--Device-AuthUser-dlpFileAccess: DLPFileAccess-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## permExpiryTime

```TypeScript
permExpiryTime: number
```

表示授权到期时间。取值范围大于等于0，超出此范围将被强转为非符号整数。单位：s。

**类型：** number

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-AuthUser-permExpiryTime: number--><!--Device-AuthUser-permExpiryTime: number-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

