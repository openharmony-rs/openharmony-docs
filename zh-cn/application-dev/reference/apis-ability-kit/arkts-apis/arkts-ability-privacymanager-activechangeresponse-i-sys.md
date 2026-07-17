# ActiveChangeResponse（系统接口）

表示某次权限使用状态变化的详情。

**起始版本：** 9

<!--Device-privacyManager-interface ActiveChangeResponse--><!--Device-privacyManager-interface ActiveChangeResponse-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
```

## activeStatus

```TypeScript
activeStatus: PermissionActiveStatus
```

权限使用状态变化类型。

**类型：** PermissionActiveStatus

**起始版本：** 9

<!--Device-ActiveChangeResponse-activeStatus: PermissionActiveStatus--><!--Device-ActiveChangeResponse-activeStatus: PermissionActiveStatus-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## callingTokenId

```TypeScript
callingTokenId?: number
```

接口调用方的应用身份标识，当activeStatus为INACTIVE时该值无效。

默认值：0。

**类型：** number

**起始版本：** 18

<!--Device-ActiveChangeResponse-callingTokenId?: int--><!--Device-ActiveChangeResponse-callingTokenId?: int-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## deviceId

```TypeScript
deviceId: string
```

权限使用状态发生变化时所在设备的ID。

**类型：** string

**起始版本：** 9

<!--Device-ActiveChangeResponse-deviceId: string--><!--Device-ActiveChangeResponse-deviceId: string-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## enhancedIdentity

```TypeScript
enhancedIdentity?: string
```

扩展身份，用于标识调用方的附加身份信息。当需要区分同一应用下不同调用来源的权限使用记录时返回此字段。最大长度为48。默认值：空字符串。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActiveChangeResponse-enhancedIdentity?: string--><!--Device-ActiveChangeResponse-enhancedIdentity?: string-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## permissionName

```TypeScript
permissionName: Permissions
```

权限使用状态发生变化的权限名。

**类型：** Permissions

**起始版本：** 9

<!--Device-ActiveChangeResponse-permissionName: Permissions--><!--Device-ActiveChangeResponse-permissionName: Permissions-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## tokenId

```TypeScript
tokenId: number
```

被订阅的应用身份标识。

**类型：** number

**起始版本：** 9

<!--Device-ActiveChangeResponse-tokenId: int--><!--Device-ActiveChangeResponse-tokenId: int-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## usedType

```TypeScript
usedType?: PermissionUsedType
```

敏感权限使用类型，当activeStatus为INACTIVE时该值无效。

默认值：NORMAL_TYPE。

**类型：** PermissionUsedType

**起始版本：** 18

<!--Device-ActiveChangeResponse-usedType?: PermissionUsedType--><!--Device-ActiveChangeResponse-usedType?: PermissionUsedType-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

