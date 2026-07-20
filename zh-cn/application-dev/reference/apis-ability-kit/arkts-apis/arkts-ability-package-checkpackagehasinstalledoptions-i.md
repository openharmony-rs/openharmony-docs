# CheckPackageHasInstalledOptions

> **说明：**  
>  
> 从API version 3开始支持，从API version 9开始废弃。

指示应用包是否已安装。

**起始版本：** 3

**废弃版本：** 9

<!--Device-unnamed-export interface CheckPackageHasInstalledOptions--><!--Device-unnamed-export interface CheckPackageHasInstalledOptions-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## 导入模块

```TypeScript
import { CheckPackageHasInstalledResponse, CheckPackageHasInstalledOptions } from '@kit.AbilityKit';
```

## bundleName

```TypeScript
bundleName: string
```

应用Bundle名称。

**类型：** string

**起始版本：** 3

**废弃版本：** 9

<!--Device-CheckPackageHasInstalledOptions-bundleName: string--><!--Device-CheckPackageHasInstalledOptions-bundleName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。

**类型：** () =&gt; void

**起始版本：** 3

**废弃版本：** 9

<!--Device-CheckPackageHasInstalledOptions-complete?: () => void--><!--Device-CheckPackageHasInstalledOptions-complete?: () => void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## fail

```TypeScript
fail?: (data: any, code: number) => void
```

接口调用失败的回调函数。

**类型：** (data: any, code: number) =&gt; void

**起始版本：** 3

**废弃版本：** 9

<!--Device-CheckPackageHasInstalledOptions-fail?: (data: any, code: number) => void--><!--Device-CheckPackageHasInstalledOptions-fail?: (data: any, code: number) => void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## success

```TypeScript
success?: (data: CheckPackageHasInstalledResponse) => void
```

接口调用成功的回调函数。

**类型：** (data: CheckPackageHasInstalledResponse) =&gt; void

**起始版本：** 3

**废弃版本：** 9

<!--Device-CheckPackageHasInstalledOptions-success?: (data: CheckPackageHasInstalledResponse) => void--><!--Device-CheckPackageHasInstalledOptions-success?: (data: CheckPackageHasInstalledResponse) => void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

