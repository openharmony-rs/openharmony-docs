# ModuleDistroInfo（系统接口）

module发行版信息。

**起始版本：** 9

<!--Device-unnamed-export interface ModuleDistroInfo--><!--Device-unnamed-export interface ModuleDistroInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## deliveryWithInstall

```TypeScript
readonly deliveryWithInstall: boolean
```

是否跟随应用一起安装。true表示跟随应用一起安装，false表示不跟随应用一起安装。

**类型：** boolean

**起始版本：** 9

<!--Device-ModuleDistroInfo-readonly deliveryWithInstall: boolean--><!--Device-ModuleDistroInfo-readonly deliveryWithInstall: boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## installationFree

```TypeScript
readonly installationFree: boolean
```

表示当前HAP是否支持免安装特性。true表示支持免安装特性，且符合免安装约束，false表示不支持免安装特性。

**类型：** boolean

**起始版本：** 9

<!--Device-ModuleDistroInfo-readonly installationFree: boolean--><!--Device-ModuleDistroInfo-readonly installationFree: boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## moduleName

```TypeScript
readonly moduleName: string
```

module名称。

**类型：** string

**起始版本：** 9

<!--Device-ModuleDistroInfo-readonly moduleName: string--><!--Device-ModuleDistroInfo-readonly moduleName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## moduleType

```TypeScript
readonly moduleType: string
```

module类型。

**类型：** string

**起始版本：** 9

<!--Device-ModuleDistroInfo-readonly moduleType: string--><!--Device-ModuleDistroInfo-readonly moduleType: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

