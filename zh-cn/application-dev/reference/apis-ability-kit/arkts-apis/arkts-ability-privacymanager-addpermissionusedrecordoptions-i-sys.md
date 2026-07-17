# AddPermissionUsedRecordOptions（系统接口）

添加权限使用记录可选参数集。

**起始版本：** 12

<!--Device-privacyManager-interface AddPermissionUsedRecordOptions--><!--Device-privacyManager-interface AddPermissionUsedRecordOptions-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
```

## enhancedIdentity

```TypeScript
enhancedIdentity?: string
```

扩展身份，用于标识调用方的附加身份信息。当需要区分同一应用下不同调用来源的权限使用记录时传入此字段。长度不超过48个字符，调用[addPermissionUsedRecord](arkts-ability-privacymanager-addpermissionusedrecord-f-sys.md#addpermissionusedrecord-1)时传入超长值会返回错误码12100001。最大长度为48。默认值：空字符串。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AddPermissionUsedRecordOptions-enhancedIdentity?: string--><!--Device-AddPermissionUsedRecordOptions-enhancedIdentity?: string-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## usedType

```TypeScript
usedType?: PermissionUsedType
```

敏感权限使用类型。

默认值：NORMAL_TYPE。

**类型：** PermissionUsedType

**起始版本：** 12

<!--Device-AddPermissionUsedRecordOptions-usedType?: PermissionUsedType--><!--Device-AddPermissionUsedRecordOptions-usedType?: PermissionUsedType-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

