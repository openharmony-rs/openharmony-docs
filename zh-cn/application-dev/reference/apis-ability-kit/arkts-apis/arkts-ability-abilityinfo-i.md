# AbilityInfo

Ability信息。

**起始版本：** 9

<!--Device-unnamed-export interface AbilityInfo--><!--Device-unnamed-export interface AbilityInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## appIndex

```TypeScript
readonly appIndex: number
```

应用包的分身索引标识，仅在[分身应用](../../../../quick-start/app-clone.md)中生效。

**类型：** number

**起始版本：** 12

<!--Device-AbilityInfo-readonly appIndex: int--><!--Device-AbilityInfo-readonly appIndex: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## applicationInfo

```TypeScript
readonly applicationInfo: ApplicationInfo
```

应用程序的配置信息<!--Del-->，可以通过调用[queryAbilityInfo](arkts-ability-bundlemanager-queryabilityinfo-f-sys.md#queryabilityinfo-2)接口，abilityFlags参数传入GET_ABILITY_INFO_WITH_APPLICATION获取<!--DelEnd-->。

[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getbundleinfoforself-1)或者[getBundleInfo](arkts-ability-bundlemanager-getbundleinfo-f.md#getbundleinfo-2)接口获取AbilityInfo信息时不会返回该字段内容，可以通过获取[bundleInfo](arkts-ability-bundleinfo-i.md).appInfo对象来获取相关信息。

**类型：** ApplicationInfo

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityInfo-readonly applicationInfo: ApplicationInfo--><!--Device-AbilityInfo-readonly applicationInfo: ApplicationInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## bundleName

```TypeScript
readonly bundleName: string
```

应用Bundle名称。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityInfo-readonly bundleName: string--><!--Device-AbilityInfo-readonly bundleName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## description

```TypeScript
readonly description: string
```

Ability的描述，对应[module.json5](../../../../quick-start/module-configuration-file.md)中abilities下配置的description字段，用于描述当前ability提供的页面内容和功能作用。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityInfo-readonly description: string--><!--Device-AbilityInfo-readonly description: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## descriptionId

```TypeScript
readonly descriptionId: number
```

Ability的描述资源id，是编译构建时根据应用配置abilities下的description自动生成的资源id。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityInfo-readonly descriptionId: long--><!--Device-AbilityInfo-readonly descriptionId: long-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## deviceTypes

```TypeScript
readonly deviceTypes: Array<string>
```

Ability支持的设备类型，来源于module.json5配置的[deviceTypes](../../../../quick-start/module-configuration-file.md#devicetypes标签)。

**类型：** Array<string>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityInfo-readonly deviceTypes: Array<string>--><!--Device-AbilityInfo-readonly deviceTypes: Array<string>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## enabled

```TypeScript
readonly enabled: boolean
```

Ability是否可用，可用表示可以拉起或者查询，不可用时调用[getAbilityInfo](arkts-ability-bundlemanager-getabilityinfo-f.md#getabilityinfo-1)查询ability需要携带GET_ABILITY_INFO_WITH_DISABLE的AbilityFlag，取值为true表示Ability可用，取值为false表示Ability不可用。

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityInfo-readonly enabled: boolean--><!--Device-AbilityInfo-readonly enabled: boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## excludeFromDock

```TypeScript
readonly excludeFromDock: boolean
```

判断Ability是否可以在dock区域隐藏图标，取值为true表示可以隐藏，取值为false不可以隐藏。

**说明：** 该字段不生效。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityInfo-readonly excludeFromDock: boolean--><!--Device-AbilityInfo-readonly excludeFromDock: boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## exported

```TypeScript
readonly exported: boolean
```

判断Ability是否可以被其他应用拉起，取值为true表示Ability可以被其他应用拉起，取值为false表示Ability不可以被其他应用拉起。

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityInfo-readonly exported: boolean--><!--Device-AbilityInfo-readonly exported: boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## icon

```TypeScript
readonly icon: string
```

Ability的图标资源描述符，对应[module.json5](../../../../quick-start/module-configuration-file.md)中abilities下配置的icon字段。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityInfo-readonly icon: string--><!--Device-AbilityInfo-readonly icon: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## iconId

```TypeScript
readonly iconId: number
```

Ability的图标资源id，是编译构建时根据应用配置abilities下的icon自动生成的资源id。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityInfo-readonly iconId: long--><!--Device-AbilityInfo-readonly iconId: long-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## label

```TypeScript
readonly label: string
```

Ability对用户显示的名称的资源描述符，对应[module.json5](../../../../quick-start/module-configuration-file.md)中abilities下配置的label字段。

**说明：** 从API version 20开始，如果是通过[bundleManager.getAbilityInfo](arkts-ability-bundlemanager-getabilityinfo-f.md#getabilityinfo-1)获取Ability信息，该字段为Ability对用户显示的名称。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityInfo-readonly label: string--><!--Device-AbilityInfo-readonly label: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## labelId

```TypeScript
readonly labelId: number
```

Ability的标签资源id，是编译构建时根据应用配置abilities下的label自动生成的资源id。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityInfo-readonly labelId: long--><!--Device-AbilityInfo-readonly labelId: long-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## launchType

```TypeScript
readonly launchType: bundleManager.LaunchType
```

Ability的启动模式，在启动的时候是否以多实例启动，详情参考[启动模式枚举](arkts-ability-bundlemanager-launchtype-e.md) 。

**类型：** bundleManager.LaunchType

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityInfo-readonly launchType: bundleManager.LaunchType--><!--Device-AbilityInfo-readonly launchType: bundleManager.LaunchType-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## metadata

```TypeScript
readonly metadata: Array<Metadata>
```

Ability的元信息。可以配置成系统定义的参数，使用系统提供的能力，例如[快捷方式](../../../../quick-start/module-configuration-file.md#shortcuts标签)、[窗口元数据配置](../../../../windowmanager/window-config-m.md)等。也可以自定义配置参数，通过调用[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getbundleinfoforself-1)接口，bundleFlags参数传入GET_BUNDLE_INFO_WITH_HAP_MODULE、GET_BUNDLE_INFO_WITH_ABILITY和GET_BUNDLE_INFO_WITH_METADATA获取。

**类型：** Array<Metadata>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityInfo-readonly metadata: Array<Metadata>--><!--Device-AbilityInfo-readonly metadata: Array<Metadata>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## moduleName

```TypeScript
readonly moduleName: string
```

Ability所属的模块名称。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityInfo-readonly moduleName: string--><!--Device-AbilityInfo-readonly moduleName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
readonly name: string
```

Ability名称。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityInfo-readonly name: string--><!--Device-AbilityInfo-readonly name: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## orientation

```TypeScript
readonly orientation: bundleManager.DisplayOrientation
```

Ability的显示模式。来源于[module.json5](../../../../quick-start/module-configuration-file.md)中abilities标签下配置的orientation字段，如果module.json5配置文件中orientation配置枚举，orientation属性有值且非0，取值详情参考[显示模式枚举](arkts-ability-bundlemanager-displayorientation-e.md)；如果配置文件中配置的是资源索引，orientation属性值为0。

**类型：** bundleManager.DisplayOrientation

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityInfo-readonly orientation: bundleManager.DisplayOrientation--><!--Device-AbilityInfo-readonly orientation: bundleManager.DisplayOrientation-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## orientationId

```TypeScript
readonly orientationId: number
```

Ability的显示模式资源id。来源于[module.json5](../../../../quick-start/module-configuration-file.md)中abilities标签下的orientation字段，如果module.json5配置文件中orientation配置枚举，orientationId属性值为0；如果配置文件中配置的是资源索引，orientationId属性值为非0，为编译构建时生成的资源id索引。当orientationId不为0时表示当前显示模式为自定义配置，需要使用orientationId去资源管理获取对应的资源，当orientationId为0时表示未配置资源。

**类型：** number

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityInfo-readonly orientationId: long--><!--Device-AbilityInfo-readonly orientationId: long-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## permissions

```TypeScript
readonly permissions: Array<string>
```

被其他应用拉起/访问时，其他应用需要申请的权限集合，只有当前AbilityInfo的exported为true，即当前Ability可以被其他应用拉起时，才会查看其他应用是否存在拉起/访问的权限。

**类型：** Array<string>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityInfo-readonly permissions: Array<string>--><!--Device-AbilityInfo-readonly permissions: Array<string>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## process

```TypeScript
readonly process: string
```

Ability的进程名称。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityInfo-readonly process: string--><!--Device-AbilityInfo-readonly process: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## readPermission

```TypeScript
readonly readPermission: string
```

读取Ability数据所需的权限。

**模型约束：** 此接口仅可在FA模型下使用。

**类型：** string

**起始版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-AbilityInfo-readonly readPermission: string--><!--Device-AbilityInfo-readonly readPermission: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## skills

```TypeScript
readonly skills: Array<Skill>
```

Ability的Skills信息，标识UIAbility组件或者ExtensionAbility组件能够接收的[Want](../../../../application-models/want-overview.md)的特征。

**类型：** Array<Skill>

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityInfo-readonly skills: Array<Skill>--><!--Device-AbilityInfo-readonly skills: Array<Skill>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## supportWindowModes

```TypeScript
readonly supportWindowModes: Array<bundleManager.SupportWindowMode>
```

Ability支持的窗口模式。

**类型：** Array<bundleManager.SupportWindowMode>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityInfo-readonly supportWindowModes: Array<bundleManager.SupportWindowMode>--><!--Device-AbilityInfo-readonly supportWindowModes: Array<bundleManager.SupportWindowMode>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## type

```TypeScript
readonly type: bundleManager.AbilityType
```

Ability类型。

**模型约束：** 此接口仅可在FA模型下使用。

**类型：** bundleManager.AbilityType

**起始版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-AbilityInfo-readonly type: bundleManager.AbilityType--><!--Device-AbilityInfo-readonly type: bundleManager.AbilityType-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## uri

```TypeScript
readonly uri: string
```

获取Ability的统一资源标识符（URI）。

**模型约束：** 此接口仅可在FA模型下使用。

**类型：** string

**起始版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-AbilityInfo-readonly uri: string--><!--Device-AbilityInfo-readonly uri: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## windowSize

```TypeScript
readonly windowSize: WindowSize
```

Ability窗口尺寸。

**类型：** WindowSize

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityInfo-readonly windowSize: WindowSize--><!--Device-AbilityInfo-readonly windowSize: WindowSize-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## writePermission

```TypeScript
readonly writePermission: string
```

向Ability写数据所需的权限。

**模型约束：** 此接口仅可在FA模型下使用。

**类型：** string

**起始版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-AbilityInfo-readonly writePermission: string--><!--Device-AbilityInfo-readonly writePermission: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

