# HapModuleInfo

```TypeScript
export interface HapModuleInfo
```

HAP信息，可以通过[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md)获取自身的HAP信息，其中参数[bundleFlags](arkts-ability-bundlemanager-bundleflag-e.md)至少包含GET_BUNDLE_INFO_WITH_HAP_MODULE。

**起始版本：** 9

<!--Device-unnamed-export interface HapModuleInfo--><!--Device-unnamed-export interface HapModuleInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## codePhysicalPath

```TypeScript
readonly codePhysicalPath?: string
```

模块的物理安装路径。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HapModuleInfo-readonly codePhysicalPath?: string--><!--Device-HapModuleInfo-readonly codePhysicalPath?: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。
