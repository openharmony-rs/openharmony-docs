# ModuleConfigInfo（系统接口）

包的module配置信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface ModuleConfigInfo--><!--Device-unnamed-export interface ModuleConfigInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## abilities

```TypeScript
readonly abilities: Array<ModuleAbilityInfo>
```

module包含的ability组件信息。

**类型：** Array&lt;[ModuleAbilityInfo](arkts-ability-bundlepackinfo-moduleabilityinfo-i-sys.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ModuleConfigInfo-readonly abilities: Array<ModuleAbilityInfo>--><!--Device-ModuleConfigInfo-readonly abilities: Array<ModuleAbilityInfo>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## apiVersion

```TypeScript
readonly apiVersion: ApiVersion
```

module的api版本。

**类型：** [ApiVersion](arkts-ability-bundlepackinfo-apiversion-i-sys.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ModuleConfigInfo-readonly apiVersion: ApiVersion--><!--Device-ModuleConfigInfo-readonly apiVersion: ApiVersion-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## deviceTypes

```TypeScript
readonly deviceTypes: Array<string>
```

module的设备类型。

**类型：** Array&lt;string&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ModuleConfigInfo-readonly deviceTypes: Array<string>--><!--Device-ModuleConfigInfo-readonly deviceTypes: Array<string>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## distro

```TypeScript
readonly distro: ModuleDistroInfo
```

module发行版信息。

**类型：** [ModuleDistroInfo](arkts-ability-bundlepackinfo-moduledistroinfo-i-sys.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ModuleConfigInfo-readonly distro: ModuleDistroInfo--><!--Device-ModuleConfigInfo-readonly distro: ModuleDistroInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## extensionAbilities

```TypeScript
readonly extensionAbilities: Array<ExtensionAbility>
```

描述extensionAbilities的配置信息。

**类型：** Array&lt;[ExtensionAbility](arkts-ability-bundlepackinfo-extensionability-i-sys.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ModuleConfigInfo-readonly extensionAbilities: Array<ExtensionAbility>--><!--Device-ModuleConfigInfo-readonly extensionAbilities: Array<ExtensionAbility>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## mainAbility

```TypeScript
readonly mainAbility: string
```

应用主ability的名称。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ModuleConfigInfo-readonly mainAbility: string--><!--Device-ModuleConfigInfo-readonly mainAbility: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

