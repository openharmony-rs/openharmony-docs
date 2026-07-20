# BundleStatusCallback（系统接口）

应用状态发生变化时回调的信息。  
> **说明：**  
>  
> 本模块首批接口从API version 8 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。  
>  
> 从API version 9开始，该模块不再维护，暂无替代接口。  
>  
> 本模块为系统接口。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** bundleMonitor/bundleMonitor

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

<!--Device-unnamed-export interface BundleStatusCallback--><!--Device-unnamed-export interface BundleStatusCallback-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

## add

```TypeScript
add: (bundleName: string, userId: number) => void
```

获取应用安装时的信息。

**类型：** (bundleName: string, userId: number) =&gt; void

**起始版本：** 8

**废弃版本：** 9

**替代接口：** BundleChangedInfo

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

<!--Device-BundleStatusCallback-add: (bundleName: string, userId: number) => void--><!--Device-BundleStatusCallback-add: (bundleName: string, userId: number) => void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

## remove

```TypeScript
remove: (bundleName: string, userId: number) => void
```

获取应用卸载时的信息。

**类型：** (bundleName: string, userId: number) =&gt; void

**起始版本：** 8

**废弃版本：** 9

**替代接口：** BundleChangedInfo

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

<!--Device-BundleStatusCallback-remove: (bundleName: string, userId: number) => void--><!--Device-BundleStatusCallback-remove: (bundleName: string, userId: number) => void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

## update

```TypeScript
update: (bundleName: string, userId: number) => void
```

获取应用更新时的信息。

**类型：** (bundleName: string, userId: number) =&gt; void

**起始版本：** 8

**废弃版本：** 9

**替代接口：** BundleChangedInfo

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

<!--Device-BundleStatusCallback-update: (bundleName: string, userId: number) => void--><!--Device-BundleStatusCallback-update: (bundleName: string, userId: number) => void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

