# OverlayModuleInfo

OverlayModuleInfo信息，可以通过[overlay.getOverlayModuleInfo](arkts-ability-overlay-getoverlaymoduleinfo-f.md#getoverlaymoduleinfo)接口获取当前应用中具有overlay特征模块的OverlayModuleInfo信息。

**起始版本：** 10

<!--Device-unnamed-export interface OverlayModuleInfo--><!--Device-unnamed-export interface OverlayModuleInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## bundleName

```TypeScript
readonly bundleName: string
```

overlay特征module所属的应用的bundle名称。

**类型：** string

**起始版本：** 10

<!--Device-OverlayModuleInfo-readonly bundleName: string--><!--Device-OverlayModuleInfo-readonly bundleName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## moduleName

```TypeScript
readonly moduleName: string
```

overlay特征module的名称。

**类型：** string

**起始版本：** 10

<!--Device-OverlayModuleInfo-readonly moduleName: string--><!--Device-OverlayModuleInfo-readonly moduleName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## priority

```TypeScript
readonly priority: number
```

overlay特征module的优先级。取值为整数，取值范围1 ~ 100，数值越大优先级越高。

**类型：** number

**起始版本：** 10

<!--Device-OverlayModuleInfo-readonly priority: int--><!--Device-OverlayModuleInfo-readonly priority: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## state

```TypeScript
readonly state: number
```

overlay特征module的[禁用使能状态](arkts-ability-overlay-setoverlayenabled-f.md#setoverlayenabled)。0代表禁用状态，1代表使能状态。

**类型：** number

**起始版本：** 10

<!--Device-OverlayModuleInfo-readonly state: int--><!--Device-OverlayModuleInfo-readonly state: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## targetModuleName

```TypeScript
readonly targetModuleName: string
```

overlay特征指定的目标module的名称，表示当前overlay包的资源需要替换生效的模块名称。

**类型：** string

**起始版本：** 10

<!--Device-OverlayModuleInfo-readonly targetModuleName: string--><!--Device-OverlayModuleInfo-readonly targetModuleName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

