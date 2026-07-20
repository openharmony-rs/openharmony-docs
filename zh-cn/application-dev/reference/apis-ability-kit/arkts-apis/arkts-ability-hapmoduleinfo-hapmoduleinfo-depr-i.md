# HapModuleInfo

Hap模块信息，未做特殊说明的属性，均通过[bundle.getBundleInfo](arkts-ability-bundle-getbundleinfo-f.md#getbundleinfo-1)获取。

> **说明：**  
>  
> 从API version 9开始，该模块不再维护，建议使用[bundleManager-HapModuleInfo](arkts-ability-hapmoduleinfo-hapmoduleinfo-depr-i.md)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [hapModuleInfo:HapModuleInfo](arkts-ability-hapmoduleinfo-hapmoduleinfo-depr-i.md)

<!--Device-unnamed-export interface HapModuleInfo--><!--Device-unnamed-export interface HapModuleInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## abilityInfo

```TypeScript
readonly abilityInfo: Array<AbilityInfo>
```

Ability信息。

**类型：** Array&lt;AbilityInfo&gt;

**默认值：** Obtains configuration information about ability

**起始版本：** 7

**废弃版本：** 9

**替代接口：** abilitiesInfo

<!--Device-HapModuleInfo-readonly abilityInfo: Array<AbilityInfo>--><!--Device-HapModuleInfo-readonly abilityInfo: Array<AbilityInfo>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## backgroundImg

```TypeScript
readonly backgroundImg: string
```

模块背景图片。

**类型：** string

**默认值：** Indicates the background img of this hapmodule

**起始版本：** 7

**废弃版本：** 9

<!--Device-HapModuleInfo-readonly backgroundImg: string--><!--Device-HapModuleInfo-readonly backgroundImg: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## description

```TypeScript
readonly description: string
```

模块描述信息。

**类型：** string

**默认值：** Describes the hapmodule

**起始版本：** 7

**废弃版本：** 9

**替代接口：** description

<!--Device-HapModuleInfo-readonly description: string--><!--Device-HapModuleInfo-readonly description: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## descriptionId

```TypeScript
readonly descriptionId: number
```

描述信息ID。

**类型：** number

**默认值：** Indicates the description of this hapmodule

**起始版本：** 7

**废弃版本：** 9

**替代接口：** descriptionId

<!--Device-HapModuleInfo-readonly descriptionId: number--><!--Device-HapModuleInfo-readonly descriptionId: number-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## deviceTypes

```TypeScript
readonly deviceTypes: Array<string>
```

支持运行的设备类型。

**类型：** Array&lt;string&gt;

**默认值：** The device types that this hapmodule can run on

**起始版本：** 7

**废弃版本：** 9

**替代接口：** deviceTypes

<!--Device-HapModuleInfo-readonly deviceTypes: Array<string>--><!--Device-HapModuleInfo-readonly deviceTypes: Array<string>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## icon

```TypeScript
readonly icon: string
```

模块图标。

**类型：** string

**默认值：** Indicates the icon of this hapmodule

**起始版本：** 7

**废弃版本：** 9

**替代接口：** icon

<!--Device-HapModuleInfo-readonly icon: string--><!--Device-HapModuleInfo-readonly icon: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## iconId

```TypeScript
readonly iconId: number
```

模块图标ID。

**类型：** number

**默认值：** Indicates the icon id of this hapmodule

**起始版本：** 7

**废弃版本：** 9

**替代接口：** iconId

<!--Device-HapModuleInfo-readonly iconId: number--><!--Device-HapModuleInfo-readonly iconId: number-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## installationFree

```TypeScript
readonly installationFree: boolean
```

是否支持免安装，取值为true表示支持免安装，取值为false表示不支持免安装。

**类型：** boolean

**默认值：** Indicates whether free installation of the hapmodule is supported

**起始版本：** 7

**废弃版本：** 9

**替代接口：** installationFree

<!--Device-HapModuleInfo-readonly installationFree: boolean--><!--Device-HapModuleInfo-readonly installationFree: boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## label

```TypeScript
readonly label: string
```

模块标签。

**类型：** string

**默认值：** Indicates the label of this hapmodule

**起始版本：** 7

**废弃版本：** 9

**替代接口：** label

<!--Device-HapModuleInfo-readonly label: string--><!--Device-HapModuleInfo-readonly label: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## labelId

```TypeScript
readonly labelId: number
```

模块标签ID。

**类型：** number

**默认值：** Indicates the label id of this hapmodule

**起始版本：** 7

**废弃版本：** 9

**替代接口：** labelId

<!--Device-HapModuleInfo-readonly labelId: number--><!--Device-HapModuleInfo-readonly labelId: number-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## mainAbilityName

```TypeScript
readonly mainAbilityName: string
```

入口Ability名称。

**类型：** string

**默认值：** Indicates the main ability name of this hapmodule

**起始版本：** 7

**废弃版本：** 9

<!--Device-HapModuleInfo-readonly mainAbilityName: string--><!--Device-HapModuleInfo-readonly mainAbilityName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## moduleName

```TypeScript
readonly moduleName: string
```

模块名。

**类型：** string

**默认值：** Indicates the name of the .hap package to which the capability belongs

**起始版本：** 7

**废弃版本：** 9

**替代接口：** name

<!--Device-HapModuleInfo-readonly moduleName: string--><!--Device-HapModuleInfo-readonly moduleName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## name

```TypeScript
readonly name: string
```

模块名称。

**类型：** string

**默认值：** Indicates the name of this hapmodule

**起始版本：** 7

**废弃版本：** 9

**替代接口：** name

<!--Device-HapModuleInfo-readonly name: string--><!--Device-HapModuleInfo-readonly name: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## reqCapabilities

```TypeScript
readonly reqCapabilities: Array<string>
```

模块运行需要的能力。

**类型：** Array&lt;string&gt;

**默认值：** Indicates the req capabilities of this hapmodule

**起始版本：** 7

**废弃版本：** 9

<!--Device-HapModuleInfo-readonly reqCapabilities: Array<string>--><!--Device-HapModuleInfo-readonly reqCapabilities: Array<string>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## supportedModes

```TypeScript
readonly supportedModes: number
```

模块支持的模式。

**类型：** number

**默认值：** Indicates the supported modes of this hapmodule

**起始版本：** 7

**废弃版本：** 9

<!--Device-HapModuleInfo-readonly supportedModes: number--><!--Device-HapModuleInfo-readonly supportedModes: number-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

