# ApplicationInfo

```TypeScript
export interface ApplicationInfo
```

应用程序信息。

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## applicationReservedFlag

```TypeScript
readonly applicationReservedFlag?: bundleManager.ApplicationReservedFlag
```

标识应用的保留标志。

**类型：** [bundleManager.ApplicationReservedFlag](arkts-ability-bundlemanager-applicationreservedflag-e-sys.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## flags

```TypeScript
readonly flags?: number
```

标识当前应用和当前用户之间的状态集合，每一位表示一个特定的布尔状态，取值参考[ApplicationInfoFlag](arkts-ability-bundlemanager-applicationinfoflag-e-sys.md)。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。
