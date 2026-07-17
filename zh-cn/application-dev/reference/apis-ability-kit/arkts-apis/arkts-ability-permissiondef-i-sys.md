# PermissionDef（系统接口）

[module.json5配置文件](../../../../quick-start/module-configuration-file.md)中定义的权限详细信息，通过接口[bundleManager.getPermissionDef](arkts-ability-bundlemanager-getpermissiondef-f-sys.md#getpermissiondef-1)获取。

> **说明：**  
>  
> 本模块为系统接口。

**起始版本：** 9

<!--Device-unnamed-export interface PermissionDef--><!--Device-unnamed-export interface PermissionDef-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## descriptionId

```TypeScript
readonly descriptionId: number
```

描述权限的ID。

**类型：** number

**起始版本：** 9

<!--Device-PermissionDef-readonly descriptionId: long--><!--Device-PermissionDef-readonly descriptionId: long-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## grantMode

```TypeScript
readonly grantMode: number
```

[权限的授予方式](../../../../security/AccessToken/app-permission-mgmt-overview.md#授权方式)。0：表示用户授权，1：表示系统授权。

**类型：** number

**起始版本：** 9

<!--Device-PermissionDef-readonly grantMode: int--><!--Device-PermissionDef-readonly grantMode: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## labelId

```TypeScript
readonly labelId: number
```

权限的标签ID。

**类型：** number

**起始版本：** 9

<!--Device-PermissionDef-readonly labelId: long--><!--Device-PermissionDef-readonly labelId: long-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## permissionName

```TypeScript
readonly permissionName: string
```

用户权限名称。

**类型：** string

**起始版本：** 9

<!--Device-PermissionDef-readonly permissionName: string--><!--Device-PermissionDef-readonly permissionName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

