# AuthUser

```TypeScript
export interface AuthUser
```

表示授权用户数据。

**起始版本：** 21

<!--Device-dlpPermission-export interface AuthUser--><!--Device-dlpPermission-export interface AuthUser-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## atomicDlpFileAccess

```TypeScript
atomicDlpFileAccess?: number
```

DLP文件的原子权限控制位掩码。值是由DlpAtomicPermissionType标志的按位或运算符（|）形成的掩码，来控制读取、编辑、复制、截图、打印和应用级权限。例如，`DlpAtomicPermissionType.ATOMIC_READ | DlpAtomicPermissionType.ATOMIC_COPY`同时授予读取和复制权限。默认值为0，表示不授予任何原子权限。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AuthUser-atomicDlpFileAccess?: number--><!--Device-AuthUser-atomicDlpFileAccess?: number-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## authAccount

```TypeScript
authAccount: string
```

表示被授权用户账号。不超过255字节，超出此范围抛出错误码401。

**类型：** string

**起始版本：** 21

<!--Device-AuthUser-authAccount: string--><!--Device-AuthUser-authAccount: string-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## authAccountType

```TypeScript
authAccountType: AccountType
```

表示被授权用户账号类型。

**类型：** [AccountType](arkts-dataprotection-dlppermission-accounttype-e.md)

**起始版本：** 21

<!--Device-AuthUser-authAccountType: AccountType--><!--Device-AuthUser-authAccountType: AccountType-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## dlpFileAccess

```TypeScript
dlpFileAccess: DLPFileAccess
```

表示被授予的权限。

**类型：** [DLPFileAccess](arkts-dataprotection-dlppermission-dlpfileaccess-e.md)

**起始版本：** 21

<!--Device-AuthUser-dlpFileAccess: DLPFileAccess--><!--Device-AuthUser-dlpFileAccess: DLPFileAccess-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## permExpiryTime

```TypeScript
permExpiryTime: number
```

表示授权到期时间。取值范围大于等于0，超出此范围将被强转为无符号整数。单位：s。

**类型：** number

**起始版本：** 21

<!--Device-AuthUser-permExpiryTime: number--><!--Device-AuthUser-permExpiryTime: number-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention
