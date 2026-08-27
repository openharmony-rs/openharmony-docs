# CheckPackageHasInstalledOptions


> **说明：**
> 
> 从API version 3开始支持，从API version 9开始废弃。
指示应用包是否已安装。

**起始版本：** 3

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

## 导入模块

```TypeScript
import { Package, CheckPackageHasInstalledOptions, CheckPackageHasInstalledResponse } from '@kit.AbilityKit';
```

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。

**起始版本：** 3

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

## fail

```TypeScript
fail?: (data: any, code: number) => void
```

接口调用失败的回调函数。

**起始版本：** 3

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | any | 是 |  |
| code | number | 是 |  |

## success

```TypeScript
success?: (data: CheckPackageHasInstalledResponse) => void
```

接口调用成功的回调函数。

**起始版本：** 3

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [CheckPackageHasInstalledResponse](arkts-ability-system-package-checkpackagehasinstalledresponse-i.md) | 是 |  |

## bundleName

```TypeScript
bundleName: string
```

应用Bundle名称。

**类型：** string

**起始版本：** 3

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework
