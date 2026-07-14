# HapModuleInfo

HAP信息。

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## abilitiesInfo

```TypeScript
readonly abilitiesInfo: Array<AbilityInfo>
```

当前模块所有Ability的信息。通过调用
[getBundleInfoForSelf](arkts-ability-getbundleinfoforself-f.md#getbundleinfoforself-1)接
口，bundleFlags参数传入GET_BUNDLE_INFO_WITH_HAP_MODULE和GET_BUNDLE_INFO_WITH_ABILITY获取。

**类型：** Array<AbilityInfo>

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## codePath

```TypeScript
readonly codePath: string
```

模块的安装路径。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## dependencies

```TypeScript
readonly dependencies: Array<Dependency>
```

模块运行依赖的动态共享库列表。

**类型：** Array<Dependency>

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## description

```TypeScript
readonly description: string
```

模块描述信息。

**类型：** string

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## descriptionId

```TypeScript
readonly descriptionId: number
```

描述信息的资源ID值。

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## deviceTypes

```TypeScript
readonly deviceTypes: Array<string>
```

模块支持安装运行的[设备类型](../../../../quick-start/module-configuration-file.md#devicetypes标签)的集合。

**类型：** Array<string>

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## extensionAbilitiesInfo

```TypeScript
readonly extensionAbilitiesInfo: Array<ExtensionAbilityInfo>
```

当前模块所有ExtensionAbility的信息。通过调用
[getBundleInfoForSelf](arkts-ability-getbundleinfoforself-f.md#getbundleinfoforself-1)接
口，bundleFlags参数传入GET_BUNDLE_INFO_WITH_HAP_MODULE和GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY获取。

**类型：** Array<ExtensionAbilityInfo>

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## fileContextMenuConfig

```TypeScript
readonly fileContextMenuConfig: string
```

模块的文件菜单配置。通过调用
[getBundleInfoForSelf](arkts-ability-getbundleinfoforself-f.md#getbundleinfoforself-1)接
口，bundleFlags参数传入GET_BUNDLE_INFO_WITH_HAP_MODULE和GET_BUNDLE_INFO_WITH_MENU获取。

**类型：** string

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## hashValue

```TypeScript
readonly hashValue: string
```

模块的Hash值。

**类型：** string

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## icon

```TypeScript
readonly icon: string
```

当前模块入口Ability的[图标](../../../../quick-start/layered-image.md)，取值为图标资源文件的索引，与模块配置文件中
[abilities标签](../../../../quick-start/module-configuration-file.md#abilities标签)或
[extensionAbilities标签](../../../../quick-start/module-configuration-file.md#extensionabilities标签)的icon字段值一致。若未配置入口
Ability，则为空。

**类型：** string

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## iconId

```TypeScript
readonly iconId: number
```

当前模块入口Ability的图标[资源ID](../../../../quick-start/resource-categories-and-access.md#资源目录)值。若未配置入口Ability，则为0。

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## installationFree

```TypeScript
readonly installationFree: boolean
```

模块是否支持免安装（无需用户通过应用市场显式安装），取值为true表示支持免安装，取值为false表示不支持免安装。

**类型：** boolean

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## label

```TypeScript
readonly label: string
```

当前模块入口Ability的名称，取值为字符串资源的索引，与模块配置文件中[abilities标签](../../../../quick-start/module-configuration-file.md#abilities标签)或
[extensionAbilities标签](../../../../quick-start/module-configuration-file.md#extensionabilities标签)的label字段值一致。若未配置入口
Ability，则为空。

**类型：** string

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## labelId

```TypeScript
readonly labelId: number
```

当前模块入口Ability名称的[资源ID](../../../../quick-start/resource-categories-and-access.md#资源目录)值。若未配置入口Ability，则为0。

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## mainElementName

```TypeScript
readonly mainElementName: string
```

当前模块的入口UIAbility名称或者ExtensionAbility名称。

**类型：** string

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## metadata

```TypeScript
readonly metadata: Array<Metadata>
```

当前模块的元数据。通过调用
[getBundleInfoForSelf](arkts-ability-getbundleinfoforself-f.md#getbundleinfoforself-1)接
口，bundleFlags参数传入GET_BUNDLE_INFO_WITH_HAP_MODULE和GET_BUNDLE_INFO_WITH_METADATA获取。

**类型：** Array<Metadata>

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
readonly name: string
```

模块名称。

**类型：** string

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## nativeLibraryPath

```TypeScript
readonly nativeLibraryPath: string
```

应用程序内模块本地库文件路径。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## preloads

```TypeScript
readonly preloads: Array<PreloadItem>
```

原子化服务中模块的预加载列表。

**类型：** Array<PreloadItem>

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## routerMap

```TypeScript
readonly routerMap: Array<RouterItem>
```

[模块的路由表配置](../../../../quick-start/module-configuration-file.md#routermap标签)。通过调用
[getBundleInfoForSelf](arkts-ability-getbundleinfoforself-f.md#getbundleinfoforself-1)接
口，bundleFlags参数传入GET_BUNDLE_INFO_WITH_HAP_MODULE和GET_BUNDLE_INFO_WITH_ROUTER_MAP获取。

**类型：** Array<RouterItem>

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## type

```TypeScript
readonly type: bundleManager.ModuleType
```

标识当前模块的类型。

**类型：** bundleManager.ModuleType

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

