# RecoverableApplicationInfo（系统接口）

预置应用被卸载后可以恢复的预置应用信息，通过接口[bundleManager.getRecoverableApplicationInfo](arkts-ability-bundlemanager-getrecoverableapplicationinfo-f-sys.md#getrecoverableapplicationinfo-1)获取。

> **说明：**  
>  
> 本模块为系统接口。

**起始版本：** 11

<!--Device-unnamed-export interface RecoverableApplicationInfo--><!--Device-unnamed-export interface RecoverableApplicationInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
readonly bundleName: string
```

应用包的名称。

**类型：** string

**起始版本：** 11

<!--Device-RecoverableApplicationInfo-readonly bundleName: string--><!--Device-RecoverableApplicationInfo-readonly bundleName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## bundleType

```TypeScript
readonly bundleType: bundleManager.BundleType
```

标识应用类型。

**类型：** bundleManager.BundleType

**起始版本：** 12

<!--Device-RecoverableApplicationInfo-readonly bundleType: bundleManager.BundleType--><!--Device-RecoverableApplicationInfo-readonly bundleType: bundleManager.BundleType-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## codePaths

```TypeScript
readonly codePaths: Array<string>
```

应用程序的安装目录。

**类型：** Array<string>

**起始版本：** 12

<!--Device-RecoverableApplicationInfo-readonly codePaths: Array<string>--><!--Device-RecoverableApplicationInfo-readonly codePaths: Array<string>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## iconId

```TypeScript
readonly iconId: number
```

模块图标的资源ID值。

**类型：** number

**起始版本：** 11

<!--Device-RecoverableApplicationInfo-readonly iconId: long--><!--Device-RecoverableApplicationInfo-readonly iconId: long-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## labelId

```TypeScript
readonly labelId: number
```

模块标签的资源ID值。

**类型：** number

**起始版本：** 11

<!--Device-RecoverableApplicationInfo-readonly labelId: long--><!--Device-RecoverableApplicationInfo-readonly labelId: long-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## moduleName

```TypeScript
readonly moduleName: string
```

模块名称。

**类型：** string

**起始版本：** 11

<!--Device-RecoverableApplicationInfo-readonly moduleName: string--><!--Device-RecoverableApplicationInfo-readonly moduleName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## systemApp

```TypeScript
readonly systemApp: boolean
```

标识应用是否为系统应用，取值为true表示系统应用，取值为false表示非系统应用。

**类型：** boolean

**起始版本：** 12

<!--Device-RecoverableApplicationInfo-readonly systemApp: boolean--><!--Device-RecoverableApplicationInfo-readonly systemApp: boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

