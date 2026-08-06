# ModuleInfo

应用程序的模块信息。 > **说明：** > > 从API version 9开始，该模块不再维护，建议使用[bundleManager-HapModuleInfo]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_替代。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [hapModuleInfo:HapModuleInfo](../arkts-ability-bundlemanager/hapmoduleinfo-hapmoduleinfo-i.md)

<!--Device-unnamed-export interface ModuleInfo--><!--Device-unnamed-export interface ModuleInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## moduleName

```TypeScript
readonly moduleName: string
```

模块名称。

**类型：** string

**默认值：** Indicates the name of the .hap package to which the capability belongs

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** ohos.bundle.bundleManager/bundleManager.HapModuleInfo#name

<!--Device-ModuleInfo-readonly moduleName: string--><!--Device-ModuleInfo-readonly moduleName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## moduleSourceDir

```TypeScript
readonly moduleSourceDir: string
```

安装目录。不能拼接路径访问资源文件，请使用[资源管理接口]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_访问资源。

**类型：** string

**默认值：** Indicates the module source dir of this module

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

<!--Device-ModuleInfo-readonly moduleSourceDir: string--><!--Device-ModuleInfo-readonly moduleSourceDir: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

