# ApplicationInfo

```TypeScript
export interface ApplicationInfo
```

应用程序信息，可以通过[bundleManager.getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md)获取自身的应用程序信息，其中参数[bundleFlags](arkts-ability-bundlemanager-bundleflag-e.md)至少包含GET_BUNDLE_INFO_WITH_APPLICATION。

**起始版本：** 9

<!--Device-unnamed-export interface ApplicationInfo--><!--Device-unnamed-export interface ApplicationInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## applicationReservedFlag

```TypeScript
readonly applicationReservedFlag?: bundleManager.ApplicationReservedFlag
```

应用预留标志。

**类型：** [bundleManager.ApplicationReservedFlag](arkts-ability-bundlemanager-applicationreservedflag-e-sys.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly applicationReservedFlag?: bundleManager.ApplicationReservedFlag--><!--Device-ApplicationInfo-readonly applicationReservedFlag?: bundleManager.ApplicationReservedFlag-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## flags

```TypeScript
readonly flags?: number
```

标识当前应用和当前用户之间的状态集合，每一位表示一个特定的布尔状态，取值参考[ApplicationInfoFlag](arkts-ability-bundlemanager-applicationinfoflag-e-sys.md)。

**类型：** number

**起始版本：** 12

<!--Device-ApplicationInfo-readonly flags?: int--><!--Device-ApplicationInfo-readonly flags?: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。
