# DLPProperty（系统接口）

表示授权相关信息。

**起始版本：** 21

<!--Device-dlpPermission-export interface DLPProperty--><!--Device-dlpPermission-export interface DLPProperty-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

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

<!--Device-DLPProperty-actionUponExpiry?: ActionType--><!--Device-DLPProperty-actionUponExpiry?: ActionType-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## authUserList

```TypeScript
authUserList?: Array<AuthUser>
```

表示授权用户列表，默认为空。

**类型：** Array&lt;AuthUser&gt;

**起始版本：** 21

<!--Device-DLPProperty-authUserList?: Array<AuthUser>--><!--Device-DLPProperty-authUserList?: Array<AuthUser>-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## contactAccount

```TypeScript
contactAccount: string
```

表示联系人账号。长度不超过255字节，超出此范围抛出错误码401。

**类型：** string

**起始版本：** 21

<!--Device-DLPProperty-contactAccount: string--><!--Device-DLPProperty-contactAccount: string-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## everyoneAccessList

```TypeScript
everyoneAccessList?: Array<DLPFileAccess>
```

表示授予所有人的权限，默认为空。

**类型：** Array&lt;DLPFileAccess&gt;

**起始版本：** 21

<!--Device-DLPProperty-everyoneAccessList?: Array<DLPFileAccess>--><!--Device-DLPProperty-everyoneAccessList?: Array<DLPFileAccess>-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## expireTime

```TypeScript
expireTime?: number
```

表示文件权限到期时间戳，默认为空。取值范围大于等于0，超出此范围抛出错误码。单位：s。

**类型：** number

**起始版本：** 21

<!--Device-DLPProperty-expireTime?: number--><!--Device-DLPProperty-expireTime?: number-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## offlineAccess

```TypeScript
offlineAccess: boolean
```

表示是否是离线打开。true表示允许离线打开，false表示不可离线打开。

**类型：** boolean

**起始版本：** 21

<!--Device-DLPProperty-offlineAccess: boolean--><!--Device-DLPProperty-offlineAccess: boolean-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## ownerAccount

```TypeScript
ownerAccount: string
```

表示权限设置者账号。长度不超过255字节，超出此范围抛出错误码401。

**类型：** string

**起始版本：** 21

<!--Device-DLPProperty-ownerAccount: string--><!--Device-DLPProperty-ownerAccount: string-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## ownerAccountID

```TypeScript
ownerAccountID: string
```

表示权限设置者账号的ID。长度不超过255字节，超出此范围抛出错误码401。

**类型：** string

**起始版本：** 21

<!--Device-DLPProperty-ownerAccountID: string--><!--Device-DLPProperty-ownerAccountID: string-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## ownerAccountType

```TypeScript
ownerAccountType: AccountType
```

表示权限设置者账号类型。

**类型：** AccountType

**起始版本：** 21

<!--Device-DLPProperty-ownerAccountType: AccountType--><!--Device-DLPProperty-ownerAccountType: AccountType-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

