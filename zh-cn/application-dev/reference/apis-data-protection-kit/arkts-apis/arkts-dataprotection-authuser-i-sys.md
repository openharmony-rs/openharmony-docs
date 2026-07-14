# AuthUser（系统接口）

表示授权用户数据。

**起始版本：** 21

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## authAccount

```TypeScript
authAccount: string
```

表示被授权用户账号。不超过255字节，超出此范围抛出错误码19100001。

**类型：** string

**起始版本：** 21

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## authAccountType

```TypeScript
authAccountType: AccountType
```

表示被授权用户账号类型。

**类型：** AccountType

**起始版本：** 21

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## dlpFileAccess

```TypeScript
dlpFileAccess: DLPFileAccess
```

表示被授予的权限。

**类型：** DLPFileAccess

**起始版本：** 21

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## permExpiryTime

```TypeScript
permExpiryTime: number
```

表示授权到期时间。取值范围大于等于0，超出此范围将被强转为非符号整数。单位：s。

**类型：** number

**起始版本：** 21

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

