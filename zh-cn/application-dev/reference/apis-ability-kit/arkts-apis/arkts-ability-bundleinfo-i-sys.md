# BundleInfo

```TypeScript
export interface BundleInfo
```

应用包信息，可以通过[bundleManager.getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md)获取自身的应用包信息，其中参数[bundleFlags](arkts-ability-bundlemanager-bundleflag-e.md)指定所返回的[BundleInfo](arkts-ability-bundleinfo-i.md)中所包含的信息。

**起始版本：** 9

<!--Device-unnamed-export interface BundleInfo--><!--Device-unnamed-export interface BundleInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## appSandboxPolicy

```TypeScript
readonly appSandboxPolicy?: bundleManager.AppSandboxPolicy
```

双模式（2in1/平板）场景下的应用沙箱策略。

**类型：** [bundleManager.AppSandboxPolicy](arkts-ability-bundlemanager-appsandboxpolicy-e-sys.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BundleInfo-readonly appSandboxPolicy?: bundleManager.AppSandboxPolicy--><!--Device-BundleInfo-readonly appSandboxPolicy?: bundleManager.AppSandboxPolicy-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## deviceModeDistributionPolicy

```TypeScript
readonly deviceModeDistributionPolicy?: bundleManager.DeviceModeDistributionPolicy
```

定义设备模式分发策略的枚举，用于指定应用程序如何分布在设备上。

**类型：** [bundleManager.DeviceModeDistributionPolicy](arkts-ability-bundlemanager-devicemodedistributionpolicy-e-sys.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BundleInfo-readonly deviceModeDistributionPolicy?: bundleManager.DeviceModeDistributionPolicy--><!--Device-BundleInfo-readonly deviceModeDistributionPolicy?: bundleManager.DeviceModeDistributionPolicy-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## sandboxCreatorBundleName

```TypeScript
readonly sandboxCreatorBundleName?: string
```

定义设备模式分发策略枚举，用于指定应用程序如何分发到设备上。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BundleInfo-readonly sandboxCreatorBundleName?: string--><!--Device-BundleInfo-readonly sandboxCreatorBundleName?: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。
