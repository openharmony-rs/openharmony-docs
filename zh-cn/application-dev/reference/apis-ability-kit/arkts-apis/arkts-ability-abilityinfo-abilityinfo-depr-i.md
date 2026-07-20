# AbilityInfo

Ability信息，未做特殊说明的属性，均通过[bundle.getAbilityInfo](arkts-ability-bundle-getabilityinfo-f.md#getabilityinfo-1)获取。

> **说明：**  
>  
> 从API version 9开始，该模块不再维护，建议使用[bundleManager-AbilityInfo](arkts-ability-abilityinfo-abilityinfo-depr-i.md)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [abilityInfo:AbilityInfo](arkts-ability-abilityinfo-abilityinfo-depr-i.md)

<!--Device-unnamed-export interface AbilityInfo--><!--Device-unnamed-export interface AbilityInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## applicationInfo

```TypeScript
readonly applicationInfo: ApplicationInfo
```

应用程序的配置信息。

通过调用[bundle.getAbilityInfo](arkts-ability-bundle-getabilityinfo-f.md#getabilityinfo-1)接口时，传入GET_ABILITY_INFO_WITH_APPLICATION获取。

**类型：** ApplicationInfo

**默认值：** Obtains configuration information about an application

**起始版本：** 7

**废弃版本：** 9

**替代接口：** applicationInfo

<!--Device-AbilityInfo-readonly applicationInfo: ApplicationInfo--><!--Device-AbilityInfo-readonly applicationInfo: ApplicationInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## backgroundModes

```TypeScript
readonly backgroundModes: number
```

表示后台服务的类型。

**模型约束：** 此接口仅可在FA模型下使用。

**类型：** number

**默认值：** Indicates the background service addressing a specific usage scenario

**起始版本：** 7

**废弃版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-AbilityInfo-readonly backgroundModes: number--><!--Device-AbilityInfo-readonly backgroundModes: number-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## bundleName

```TypeScript
readonly bundleName: string
```

应用Bundle名称。

**类型：** string

**默认值：** Indicates the name of the bundle containing the ability

**起始版本：** 7

**废弃版本：** 9

**替代接口：** bundleName

<!--Device-AbilityInfo-readonly bundleName: string--><!--Device-AbilityInfo-readonly bundleName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## description

```TypeScript
readonly description: string
```

Ability的描述。

**类型：** string

**默认值：** Describes the ability

**起始版本：** 7

**废弃版本：** 9

**替代接口：** description

<!--Device-AbilityInfo-readonly description: string--><!--Device-AbilityInfo-readonly description: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## descriptionId

```TypeScript
readonly descriptionId: number
```

Ability的描述的资源id值。

**类型：** number

**默认值：** Indicates the description id of the ability

**起始版本：** 7

**废弃版本：** 9

**替代接口：** descriptionId

<!--Device-AbilityInfo-readonly descriptionId: number--><!--Device-AbilityInfo-readonly descriptionId: number-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## deviceCapabilities

```TypeScript
readonly deviceCapabilities: Array<string>
```

Ability需要的设备能力。

**类型：** Array&lt;string&gt;

**默认值：** The device capability that this ability needs

**起始版本：** 7

**废弃版本：** 9

<!--Device-AbilityInfo-readonly deviceCapabilities: Array<string>--><!--Device-AbilityInfo-readonly deviceCapabilities: Array<string>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## deviceTypes

```TypeScript
readonly deviceTypes: Array<string>
```

Ability支持的设备类型。

**类型：** Array&lt;string&gt;

**默认值：** The device types that this ability can run on

**起始版本：** 7

**废弃版本：** 9

**替代接口：** deviceTypes

<!--Device-AbilityInfo-readonly deviceTypes: Array<string>--><!--Device-AbilityInfo-readonly deviceTypes: Array<string>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## enabled

```TypeScript
readonly enabled: boolean
```

Ability是否可用，取值为true表示Ability可用，取值为false表示Ability不可用。

**类型：** boolean

**默认值：** Indicates whether the ability is enabled

**起始版本：** 8

**废弃版本：** 9

**替代接口：** enabled

<!--Device-AbilityInfo-readonly enabled: boolean--><!--Device-AbilityInfo-readonly enabled: boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## formEnabled

```TypeScript
readonly formEnabled: boolean
```

判断Ability是否提供卡片能力，取值为true表示Ability提供卡片能力，取值为false表示Ability不提供卡片能力。

**模型约束：** 此接口仅可在FA模型下使用。

**类型：** boolean

**默认值：** Indicates whether the ability provides the embedded card capability

**起始版本：** 7

**废弃版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-AbilityInfo-readonly formEnabled: boolean--><!--Device-AbilityInfo-readonly formEnabled: boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## icon

```TypeScript
readonly icon: string
```

Ability的图标资源文件索引。

**类型：** string

**默认值：** Indicates the icon of the ability

**起始版本：** 7

**废弃版本：** 9

**替代接口：** icon

<!--Device-AbilityInfo-readonly icon: string--><!--Device-AbilityInfo-readonly icon: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## iconId

```TypeScript
readonly iconId: number
```

Ability的图标的资源id值。

**类型：** number

**默认值：** Indicates the icon id of the ability

**起始版本：** 7

**废弃版本：** 9

**替代接口：** iconId

<!--Device-AbilityInfo-readonly iconId: number--><!--Device-AbilityInfo-readonly iconId: number-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## isVisible

```TypeScript
readonly isVisible: boolean
```

判断Ability是否可以被其他应用调用，取值为true表示Ability可以被其他应用调用，取值为false表示Ability不可以被其他应用调用。

**类型：** boolean

**默认值：** Indicates whether an ability can be called by other abilities

**起始版本：** 7

**废弃版本：** 9

**替代接口：** exported

<!--Device-AbilityInfo-readonly isVisible: boolean--><!--Device-AbilityInfo-readonly isVisible: boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## label

```TypeScript
readonly label: string
```

Ability对用户显示的名称。

**类型：** string

**默认值：** Indicates the label of the ability

**起始版本：** 7

**废弃版本：** 9

**替代接口：** label

<!--Device-AbilityInfo-readonly label: string--><!--Device-AbilityInfo-readonly label: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## labelId

```TypeScript
readonly labelId: number
```

Ability的标签的资源id值。

**类型：** number

**默认值：** Indicates the label id of the ability

**起始版本：** 7

**废弃版本：** 9

**替代接口：** labelId

<!--Device-AbilityInfo-readonly labelId: number--><!--Device-AbilityInfo-readonly labelId: number-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## launchMode

```TypeScript
readonly launchMode: bundle.LaunchMode
```

Ability的启动模式。

**类型：** bundle.LaunchMode

**默认值：** Enumerates ability launch modes

**起始版本：** 7

**废弃版本：** 9

**替代接口：** launchType

<!--Device-AbilityInfo-readonly launchMode: bundle.LaunchMode--><!--Device-AbilityInfo-readonly launchMode: bundle.LaunchMode-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## metaData

```TypeScript
readonly metaData: Array<CustomizeData>
```

Ability的元信息。

通过调用[bundle.getAbilityInfo](arkts-ability-bundle-getabilityinfo-f.md#getabilityinfo-1)接口时，传入GET_ABILITY_INFO_WITH_METADATA获取。

**类型：** Array&lt;CustomizeData&gt;

**默认值：** Indicates the metadata of ability

**起始版本：** 8

**废弃版本：** 9

**替代接口：** metadata

<!--Device-AbilityInfo-readonly metaData: Array<CustomizeData>--><!--Device-AbilityInfo-readonly metaData: Array<CustomizeData>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## moduleName

```TypeScript
readonly moduleName: string
```

Ability所属的HAP的名称。

**类型：** string

**默认值：** Indicates the name of the .hap package to which the capability belongs

**起始版本：** 7

**废弃版本：** 9

**替代接口：** moduleName

<!--Device-AbilityInfo-readonly moduleName: string--><!--Device-AbilityInfo-readonly moduleName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## name

```TypeScript
readonly name: string
```

Ability名称。

**类型：** string

**默认值：** Ability simplified class name

**起始版本：** 7

**废弃版本：** 9

**替代接口：** name

<!--Device-AbilityInfo-readonly name: string--><!--Device-AbilityInfo-readonly name: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## orientation

```TypeScript
readonly orientation: bundle.DisplayOrientation
```

Ability的显示模式。

**类型：** bundle.DisplayOrientation

**默认值：** Enumerates ability display orientations

**起始版本：** 7

**废弃版本：** 9

**替代接口：** orientation

<!--Device-AbilityInfo-readonly orientation: bundle.DisplayOrientation--><!--Device-AbilityInfo-readonly orientation: bundle.DisplayOrientation-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## permissions

```TypeScript
readonly permissions: Array<string>
```

被其他应用Ability调用时需要申请的权限集合。

通过调用[bundle.getAbilityInfo](arkts-ability-bundle-getabilityinfo-f.md#getabilityinfo-1)接口时，传入GET_ABILITY_INFO_WITH_PERMISSION获取。

**类型：** Array&lt;string&gt;

**默认值：** The permissions that others need to launch this ability

**起始版本：** 7

**废弃版本：** 9

**替代接口：** permissions

<!--Device-AbilityInfo-readonly permissions: Array<string>--><!--Device-AbilityInfo-readonly permissions: Array<string>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## process

```TypeScript
readonly process: string
```

Ability的进程名称。

**类型：** string

**默认值：** Process of ability, if user do not set it ,the value equal application process

**起始版本：** 7

**废弃版本：** 9

**替代接口：** process

<!--Device-AbilityInfo-readonly process: string--><!--Device-AbilityInfo-readonly process: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## readPermission

```TypeScript
readonly readPermission: string
```

读取Ability数据所需的权限。

**模型约束：** 此接口仅可在FA模型下使用。

**类型：** string

**默认值：** Indicates the permission required for reading ability data

**起始版本：** 7

**废弃版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-AbilityInfo-readonly readPermission: string--><!--Device-AbilityInfo-readonly readPermission: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## subType

```TypeScript
readonly subType: bundle.AbilitySubType
```

Ability中枚举使用的模板的子类型。

**模型约束：** 此接口仅可在FA模型下使用。

**类型：** bundle.AbilitySubType

**默认值：** Enumerates the subType of templates used by an ability

**起始版本：** 7

**废弃版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-AbilityInfo-readonly subType: bundle.AbilitySubType--><!--Device-AbilityInfo-readonly subType: bundle.AbilitySubType-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## targetAbility

```TypeScript
readonly targetAbility: string
```

当前Ability重用的目标Ability。

**模型约束：** 此接口仅可在FA模型下使用。

**类型：** string

**默认值：** Info about which ability is this nick point to

**起始版本：** 7

**废弃版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-AbilityInfo-readonly targetAbility: string--><!--Device-AbilityInfo-readonly targetAbility: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## type

```TypeScript
readonly type: bundle.AbilityType
```

Ability类型。

**模型约束：** 此接口仅可在FA模型下使用。

**类型：** bundle.AbilityType

**默认值：** Enumerates types of templates that can be used by an ability

**起始版本：** 7

**废弃版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-AbilityInfo-readonly type: bundle.AbilityType--><!--Device-AbilityInfo-readonly type: bundle.AbilityType-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## uri

```TypeScript
readonly uri: string
```

获取Ability的统一资源标识符（URI）。

**模型约束：** 此接口仅可在FA模型下使用。

**类型：** string

**默认值：** Uri of ability

**起始版本：** 7

**废弃版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-AbilityInfo-readonly uri: string--><!--Device-AbilityInfo-readonly uri: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## writePermission

```TypeScript
readonly writePermission: string
```

向Ability写数据所需的权限。

**模型约束：** 此接口仅可在FA模型下使用。

**类型：** string

**默认值：** Indicates the permission required for writing data to the ability

**起始版本：** 7

**废弃版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-AbilityInfo-readonly writePermission: string--><!--Device-AbilityInfo-readonly writePermission: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

