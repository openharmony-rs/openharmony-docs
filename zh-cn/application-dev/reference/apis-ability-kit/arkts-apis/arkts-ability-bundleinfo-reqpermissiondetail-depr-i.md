# ReqPermissionDetail

> **说明：**  
>  
> 从API version 7开始支持，从API version 9开始废弃，建议使用[ReqPermissionDetail](arkts-ability-bundleinfo-reqpermissiondetail-depr-i.md)替代。

应用运行时需向系统申请的权限集合的详细信息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [bundleInfo](arkts-ability-bundleinfo-i.md)

<!--Device-unnamed-export interface ReqPermissionDetail--><!--Device-unnamed-export interface ReqPermissionDetail-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## name

```TypeScript
name: string
```

需要使用的权限名称。

**类型：** string

**默认值：** Indicates the name of this required permissions

**起始版本：** 7

**废弃版本：** 9

**替代接口：** name

<!--Device-ReqPermissionDetail-name: string--><!--Device-ReqPermissionDetail-name: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## reason

```TypeScript
reason: string
```

描述申请权限的原因。

**类型：** string

**默认值：** Indicates the reason of this required permissions

**起始版本：** 7

**废弃版本：** 9

**替代接口：** reason

<!--Device-ReqPermissionDetail-reason: string--><!--Device-ReqPermissionDetail-reason: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## usedScene

```TypeScript
usedScene: UsedScene
```

权限使用的场景和时机。

**类型：** UsedScene

**默认值：** Indicates the used scene of this required permissions

**起始版本：** 7

**废弃版本：** 9

**替代接口：** usedScene

<!--Device-ReqPermissionDetail-usedScene: UsedScene--><!--Device-ReqPermissionDetail-usedScene: UsedScene-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

