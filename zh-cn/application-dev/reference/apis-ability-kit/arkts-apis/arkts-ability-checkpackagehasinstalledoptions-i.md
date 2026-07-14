# CheckPackageHasInstalledOptions

> **说明：**
>
> 从API version 3开始支持，从API version 9开始废弃。

指示应用包是否已安装。

**起始版本：** 3

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

## bundleName

```TypeScript
bundleName: string
```

应用Bundle名称。

**类型：** string

**起始版本：** 3

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。

**类型：** () => void

**起始版本：** 3

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

## fail

```TypeScript
fail?: (data: any, code: number) => void
```

接口调用失败的回调函数。

**类型：** (data: any, code: number) => void

**起始版本：** 3

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

## success

```TypeScript
success?: (data: CheckPackageHasInstalledResponse) => void
```

接口调用成功的回调函数。

**类型：** (data: CheckPackageHasInstalledResponse) => void

**起始版本：** 3

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

