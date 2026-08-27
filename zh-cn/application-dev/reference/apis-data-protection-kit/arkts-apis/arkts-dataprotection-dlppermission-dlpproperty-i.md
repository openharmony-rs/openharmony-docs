# DLPProperty

表示授权相关信息。

**起始版本：** 21

**系统能力：** SystemCapability.Security.DataLossPrevention

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## actionUponExpiry

```TypeScript
actionUponExpiry?: ActionType
```

表示到期后文件是否允许打开（打开后拥有编辑权限），仅在expireTime不为空时生效，默认为空。

**类型：** ActionType

**起始版本：** 21

**系统能力：** SystemCapability.Security.DataLossPrevention

## allowedOpenCount

```TypeScript
allowedOpenCount?: number
```

表示允许打开的次数，默认为0。无范围限制。

**类型：** number

**起始版本：** 21

**系统能力：** SystemCapability.Security.DataLossPrevention

## authUserList

```TypeScript
authUserList?: Array<AuthUser>
```

表示授权用户列表，默认为空。

**类型：** Array&lt;[AuthUser](arkts-dataprotection-dlppermission-authuser-i.md)&gt;

**起始版本：** 21

**系统能力：** SystemCapability.Security.DataLossPrevention

## contactAccount

```TypeScript
contactAccount: string
```

表示联系人账号。长度不超过255字节，超出此范围抛出错误码401。

**类型：** string

**起始版本：** 21

**系统能力：** SystemCapability.Security.DataLossPrevention

## countdown

```TypeScript
countdown?: number
```

表示文件可被查看的有效时间，超时后打开的文件将自动关闭，默认为0，单位：s。取值范围为[-2&lt;sup&gt;31&lt;/sup&gt;, 2&lt;sup&gt;31&lt;/sup&gt;-1]。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.DataLossPrevention

## everyoneAccessList

```TypeScript
everyoneAccessList?: Array<DLPFileAccess>
```

表示授予所有人的权限，默认为空。

**类型：** Array&lt;[DLPFileAccess](arkts-dataprotection-dlppermission-dlpfileaccess-e.md)&gt;

**起始版本：** 21

**系统能力：** SystemCapability.Security.DataLossPrevention

## expireTime

```TypeScript
expireTime?: number
```

表示文件权限到期时间戳，默认为空。取值范围大于等于0，超出此范围抛出错误码。单位：s。

**类型：** number

**起始版本：** 21

**系统能力：** SystemCapability.Security.DataLossPrevention

## extensionFields

```TypeScript
extensionFields?: Record<string, Object>
```

表示DLP文件的扩展属性，默认为空。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.DataLossPrevention

## fileId

```TypeScript
fileId?: string
```

表示文件的标识，默认为空。长度不超过255字节，超出此范围抛出错误码401。

**类型：** string

**起始版本：** 21

**系统能力：** SystemCapability.Security.DataLossPrevention

## offlineAccess

```TypeScript
offlineAccess: boolean
```

表示是否是离线打开。true表示允许离线打开，false表示不可离线打开。

**类型：** boolean

**起始版本：** 21

**系统能力：** SystemCapability.Security.DataLossPrevention

## ownerAccount

```TypeScript
ownerAccount: string
```

表示权限设置者账号。长度不超过255字节，超出此范围抛出错误码401。

**类型：** string

**起始版本：** 21

**系统能力：** SystemCapability.Security.DataLossPrevention

## ownerAccountID

```TypeScript
ownerAccountID: string
```

表示权限设置者账号的ID。长度不超过255字节，超出此范围抛出错误码401。

**类型：** string

**起始版本：** 21

**系统能力：** SystemCapability.Security.DataLossPrevention

## ownerAccountType

```TypeScript
ownerAccountType: AccountType
```

表示权限设置者账号类型。

**类型：** [AccountType](arkts-dataprotection-dlppermission-accounttype-e.md)

**起始版本：** 21

**系统能力：** SystemCapability.Security.DataLossPrevention

## waterMarkConfig

```TypeScript
waterMarkConfig?: boolean
```

表示是否要求添加水印。true表示要求添加水印，false表示不要求添加水印，默认为空。

**类型：** boolean

**起始版本：** 23

**系统能力：** SystemCapability.Security.DataLossPrevention
