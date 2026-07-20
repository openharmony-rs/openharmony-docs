# ReqPermissionDetail

应用运行时需向系统申请的权限集合的详细信息。

> **说明：**  
>  
> - 如果应用内多包申请的权限名称一样，但是权限申请理由不一致，系统只会返回一个权限申请理由，优先级从高到低顺序为entry类型HAP、feature类型HAP、应用内HSP。

**起始版本：** 9

<!--Device-unnamed-export interface ReqPermissionDetail--><!--Device-unnamed-export interface ReqPermissionDetail-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## moduleName

```TypeScript
moduleName: string
```

申请该权限的module名称。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ReqPermissionDetail-moduleName: string--><!--Device-ReqPermissionDetail-moduleName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
name: string
```

需要使用的[权限名称](docroot://security/AccessToken/app-permissions.md)。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ReqPermissionDetail-name: string--><!--Device-ReqPermissionDetail-name: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## reason

```TypeScript
reason: string
```

描述申请权限的原因。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ReqPermissionDetail-reason: string--><!--Device-ReqPermissionDetail-reason: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## reasonId

```TypeScript
reasonId: number
```

描述申请权限的原因ID。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ReqPermissionDetail-reasonId: long--><!--Device-ReqPermissionDetail-reasonId: long-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## usedScene

```TypeScript
usedScene: UsedScene
```

权限使用的场景和时机。

**类型：** UsedScene

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ReqPermissionDetail-usedScene: UsedScene--><!--Device-ReqPermissionDetail-usedScene: UsedScene-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

