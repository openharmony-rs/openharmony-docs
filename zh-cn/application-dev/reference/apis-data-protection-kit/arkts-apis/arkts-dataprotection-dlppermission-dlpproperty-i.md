# DLPProperty

表示授权相关信息。

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-dlpPermission-export interface DLPProperty--><!--Device-dlpPermission-export interface DLPProperty-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## actionUponExpiry

```TypeScript
actionUponExpiry?: ActionType
```

表示到期后文件是否允许打开（打开后拥有编辑权限），仅在expireTime不为空时生效，默认为空。

**类型：** ActionType

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-DLPProperty-actionUponExpiry?: ActionType--><!--Device-DLPProperty-actionUponExpiry?: ActionType-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## allowedOpenCount

```TypeScript
allowedOpenCount?: number
```

表示允许打开的次数，默认为0。无范围限制。

**类型：** number

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为21。

<!--Device-DLPProperty-allowedOpenCount?: number--><!--Device-DLPProperty-allowedOpenCount?: number-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## authUserList

```TypeScript
authUserList?: Array<AuthUser>
```

表示授权用户列表，默认为空。

**类型：** Array&lt;AuthUser&gt;

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-DLPProperty-authUserList?: Array<AuthUser>--><!--Device-DLPProperty-authUserList?: Array<AuthUser>-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## contactAccount

```TypeScript
contactAccount: string
```

表示联系人账号。长度不超过255字节，超出此范围抛出错误码401。

**类型：** string

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-DLPProperty-contactAccount: string--><!--Device-DLPProperty-contactAccount: string-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## countdown

```TypeScript
countdown?: number
```

表示文件可被查看的有效时间，超时后打开的文件将自动关闭，默认为0，单位：s。取值范围为[-2\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_31\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_, 2\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_31\_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_-1]。

**类型：** number

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DLPProperty-countdown?: number--><!--Device-DLPProperty-countdown?: number-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## everyoneAccessList

```TypeScript
everyoneAccessList?: Array<DLPFileAccess>
```

表示授予所有人的权限，默认为空。

**类型：** Array&lt;DLPFileAccess&gt;

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-DLPProperty-everyoneAccessList?: Array<DLPFileAccess>--><!--Device-DLPProperty-everyoneAccessList?: Array<DLPFileAccess>-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## expireTime

```TypeScript
expireTime?: number
```

表示文件权限到期时间戳，默认为空。取值范围大于等于0，超出此范围抛出错误码。单位：s。

**类型：** number

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

<!--Device-DLPProperty-expireTime?: number--><!--Device-DLPProperty-expireTime?: number-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## extensionFields

```TypeScript
extensionFields?: Record<string, Object>
```

表示DLP文件的扩展属性，默认为空。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DLPProperty-extensionFields?: Record<string, Object>--><!--Device-DLPProperty-extensionFields?: Record<string, Object>-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## fileId

```TypeScript
fileId?: string
```

表示文件的标识，默认为空。长度不超过255字节，超出此范围抛出错误码401。

**类型：** string

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为21。

<!--Device-DLPProperty-fileId?: string--><!--Device-DLPProperty-fileId?: string-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## offlineAccess

```TypeScript
offlineAccess: boolean
```

表示是否是离线打开。true表示允许离线打开，false表示不可离线打开。

**类型：** boolean

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-DLPProperty-offlineAccess: boolean--><!--Device-DLPProperty-offlineAccess: boolean-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## ownerAccount

```TypeScript
ownerAccount: string
```

表示权限设置者账号。长度不超过255字节，超出此范围抛出错误码401。

**类型：** string

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-DLPProperty-ownerAccount: string--><!--Device-DLPProperty-ownerAccount: string-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## ownerAccountID

```TypeScript
ownerAccountID: string
```

表示权限设置者账号的ID。长度不超过255字节，超出此范围抛出错误码401。

**类型：** string

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-DLPProperty-ownerAccountID: string--><!--Device-DLPProperty-ownerAccountID: string-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## ownerAccountType

```TypeScript
ownerAccountType: AccountType
```

表示权限设置者账号类型。

**类型：** AccountType

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-DLPProperty-ownerAccountType: AccountType--><!--Device-DLPProperty-ownerAccountType: AccountType-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## waterMarkConfig

```TypeScript
waterMarkConfig?: boolean
```

表示是否要求添加水印。true表示要求添加水印，false表示不要求添加水印，默认为空。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

<!--Device-DLPProperty-waterMarkConfig?: boolean--><!--Device-DLPProperty-waterMarkConfig?: boolean-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

