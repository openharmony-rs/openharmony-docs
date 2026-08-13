# Package

> **说明：** > > 从API version 3开始支持，从API version 9开始废弃。 指示应用包是否已安装。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 9

<!--Device-unnamed-export default class Package--><!--Device-unnamed-export default class Package-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## hasInstalled

```TypeScript
static hasInstalled(options: CheckPackageHasInstalledOptions): void
```

查询指定应用是否存在，或者原生应用是否安装。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 9

**替代接口：** [canOpenLink](arkts-ability-bundlemanager-canopenlink-f.md#canOpenLink)

<!--Device-Package-static hasInstalled(options: CheckPackageHasInstalledOptions): void--><!--Device-Package-static hasInstalled(options: CheckPackageHasInstalledOptions): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CheckPackageHasInstalledOptions](arkts-ability-system-package-checkpackagehasinstalledoptions-i.md) | 是 | Options |

