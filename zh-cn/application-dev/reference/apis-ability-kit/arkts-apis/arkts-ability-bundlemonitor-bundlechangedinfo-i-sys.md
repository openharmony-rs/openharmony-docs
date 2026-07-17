# BundleChangedInfo（系统接口）

应用变更信息。

**起始版本：** 9

<!--Device-bundleMonitor-interface BundleChangedInfo--><!--Device-bundleMonitor-interface BundleChangedInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { bundleMonitor } from '@kit.AbilityKit';
```

## appIndex

```TypeScript
readonly appIndex: number
```

应用状态发生变化的应用分身索引。

**类型：** number

**起始版本：** 12

<!--Device-BundleChangedInfo-readonly appIndex: int--><!--Device-BundleChangedInfo-readonly appIndex: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
readonly bundleName: string
```

应用状态发生变化的应用Bundle名称。

**类型：** string

**起始版本：** 9

<!--Device-BundleChangedInfo-readonly bundleName: string--><!--Device-BundleChangedInfo-readonly bundleName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
readonly userId: number
```

应用状态发生变化的用户ID，可以通过getOsAccountLocalId接口获取。

**类型：** number

**起始版本：** 9

<!--Device-BundleChangedInfo-readonly userId: int--><!--Device-BundleChangedInfo-readonly userId: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

