# AbilityInfo

```TypeScript
export interface AbilityInfo
```

The module provides information about an ability. Unless otherwise specified, the information is obtained through [bundle.getAbilityInfo](arkts-ability-bundle-getabilityinfo-f.md#getabilityinfo-1).

> **NOTE:** 
> 
> The APIs of this module have been deprecated since API version 9. You are advised to use
> [bundleManager-AbilityInfo](arkts-ability-abilityinfo-abilityinfo-depr-i.md) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [AbilityInfo](arkts-ability-abilityinfo-abilityinfo-depr-i.md)

<!--Device-unnamed-export interface AbilityInfo--><!--Device-unnamed-export interface AbilityInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## applicationInfo

```TypeScript
readonly applicationInfo: ApplicationInfo
```

Application configuration information.

The value is obtained by passing in GET_ABILITY_INFO_WITH_APPLICATION to [bundle.getAbilityInfo](arkts-ability-bundle-getabilityinfo-f.md#getabilityinfo-1).

**Type:** [ApplicationInfo](arkts-ability-applicationinfo-applicationinfo-depr-i.md)

**Default:** Obtains configuration information about an application

**Since:** 7

**Deprecated since:** 9

**Substitutes:** applicationInfo

<!--Device-AbilityInfo-readonly applicationInfo: ApplicationInfo--><!--Device-AbilityInfo-readonly applicationInfo: ApplicationInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## backgroundModes

```TypeScript
readonly backgroundModes: number
```

Background service mode of the ability.

**Model restriction**: This API can be used only in the FA model.

**Type:** number

**Default:** Indicates the background service addressing a specific usage scenario

**Since:** 7

**Deprecated since:** 9

**Model restriction:** This API can be used only in the FA model.

<!--Device-AbilityInfo-readonly backgroundModes: number--><!--Device-AbilityInfo-readonly backgroundModes: number-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## bundleName

```TypeScript
readonly bundleName: string
```

Bundle name.

**Type:** string

**Default:** Indicates the name of the bundle containing the ability

**Since:** 7

**Deprecated since:** 9

**Substitutes:** bundleName

<!--Device-AbilityInfo-readonly bundleName: string--><!--Device-AbilityInfo-readonly bundleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## description

```TypeScript
readonly description: string
```

Ability description.

**Type:** string

**Default:** Describes the ability

**Since:** 7

**Deprecated since:** 9

**Substitutes:** description

<!--Device-AbilityInfo-readonly description: string--><!--Device-AbilityInfo-readonly description: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## descriptionId

```TypeScript
readonly descriptionId: number
```

ID of the ability description.

**Type:** number

**Default:** Indicates the description id of the ability

**Since:** 7

**Deprecated since:** 9

**Substitutes:** descriptionId

<!--Device-AbilityInfo-readonly descriptionId: number--><!--Device-AbilityInfo-readonly descriptionId: number-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## deviceCapabilities

```TypeScript
readonly deviceCapabilities: Array<string>
```

Device capabilities required for the ability.

**Type:** Array&lt;string&gt;

**Default:** The device capability that this ability needs

**Since:** 7

**Deprecated since:** 9

<!--Device-AbilityInfo-readonly deviceCapabilities: Array<string>--><!--Device-AbilityInfo-readonly deviceCapabilities: Array<string>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## deviceTypes

```TypeScript
readonly deviceTypes: Array<string>
```

Device types supported by the ability.

**Type:** Array&lt;string&gt;

**Default:** The device types that this ability can run on

**Since:** 7

**Deprecated since:** 9

**Substitutes:** deviceTypes

<!--Device-AbilityInfo-readonly deviceTypes: Array<string>--><!--Device-AbilityInfo-readonly deviceTypes: Array<string>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## enabled

```TypeScript
readonly enabled: boolean
```

Whether the ability is enabled. **true** if enabled, **false** otherwise.

**Type:** boolean

**Default:** Indicates whether the ability is enabled

**Since:** 8

**Deprecated since:** 9

**Substitutes:** enabled

<!--Device-AbilityInfo-readonly enabled: boolean--><!--Device-AbilityInfo-readonly enabled: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## formEnabled

```TypeScript
readonly formEnabled: boolean
```

Whether the ability provides the service widget capability. **true** if the ability provides the service widget capability, **false** otherwise.

**Model restriction**: This API can be used only in the FA model.

**Type:** boolean

**Default:** Indicates whether the ability provides the embedded card capability

**Since:** 7

**Deprecated since:** 9

**Model restriction:** This API can be used only in the FA model.

<!--Device-AbilityInfo-readonly formEnabled: boolean--><!--Device-AbilityInfo-readonly formEnabled: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## icon

```TypeScript
readonly icon: string
```

Index of the ability icon resource file.

**Type:** string

**Default:** Indicates the icon of the ability

**Since:** 7

**Deprecated since:** 9

**Substitutes:** icon

<!--Device-AbilityInfo-readonly icon: string--><!--Device-AbilityInfo-readonly icon: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## iconId

```TypeScript
readonly iconId: number
```

ID of the ability icon.

**Type:** number

**Default:** Indicates the icon id of the ability

**Since:** 7

**Deprecated since:** 9

**Substitutes:** iconId

<!--Device-AbilityInfo-readonly iconId: number--><!--Device-AbilityInfo-readonly iconId: number-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## isVisible

```TypeScript
readonly isVisible: boolean
```

Whether the ability can be called by other applications. **true** if the ability can be called by other applications, **false** otherwise.

**Type:** boolean

**Default:** Indicates whether an ability can be called by other abilities

**Since:** 7

**Deprecated since:** 9

**Substitutes:** exported

<!--Device-AbilityInfo-readonly isVisible: boolean--><!--Device-AbilityInfo-readonly isVisible: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## label

```TypeScript
readonly label: string
```

Ability name visible to users.

**Type:** string

**Default:** Indicates the label of the ability

**Since:** 7

**Deprecated since:** 9

**Substitutes:** label

<!--Device-AbilityInfo-readonly label: string--><!--Device-AbilityInfo-readonly label: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## labelId

```TypeScript
readonly labelId: number
```

ID of the ability label.

**Type:** number

**Default:** Indicates the label id of the ability

**Since:** 7

**Deprecated since:** 9

**Substitutes:** labelId

<!--Device-AbilityInfo-readonly labelId: number--><!--Device-AbilityInfo-readonly labelId: number-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## launchMode

```TypeScript
readonly launchMode: bundle.LaunchMode
```

Ability launch mode.

**Type:** [bundle.LaunchMode](arkts-ability-bundle-launchmode-e.md)

**Default:** Enumerates ability launch modes

**Since:** 7

**Deprecated since:** 9

**Substitutes:** launchType

<!--Device-AbilityInfo-readonly launchMode: bundle.LaunchMode--><!--Device-AbilityInfo-readonly launchMode: bundle.LaunchMode-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## metaData

```TypeScript
readonly metaData: Array<CustomizeData>
```

Metadata of the ability.

The value is obtained by passing in GET_ABILITY_INFO_WITH_METADATA to [bundle.getAbilityInfo](arkts-ability-bundle-getabilityinfo-f.md#getabilityinfo-1).

**Type:** Array&lt;[CustomizeData](arkts-ability-customizedata-customizedata-depr-i.md)&gt;

**Default:** Indicates the metadata of ability

**Since:** 8

**Deprecated since:** 9

**Substitutes:** metadata

<!--Device-AbilityInfo-readonly metaData: Array<CustomizeData>--><!--Device-AbilityInfo-readonly metaData: Array<CustomizeData>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## moduleName

```TypeScript
readonly moduleName: string
```

Name of the HAP file to which the ability belongs.

**Type:** string

**Default:** Indicates the name of the .hap package to which the capability belongs

**Since:** 7

**Deprecated since:** 9

**Substitutes:** moduleName

<!--Device-AbilityInfo-readonly moduleName: string--><!--Device-AbilityInfo-readonly moduleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## name

```TypeScript
readonly name: string
```

Ability name.

**Type:** string

**Default:** Ability simplified class name

**Since:** 7

**Deprecated since:** 9

**Substitutes:** name

<!--Device-AbilityInfo-readonly name: string--><!--Device-AbilityInfo-readonly name: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## orientation

```TypeScript
readonly orientation: bundle.DisplayOrientation
```

Ability display orientation.

**Type:** [bundle.DisplayOrientation](arkts-ability-bundle-displayorientation-e.md)

**Default:** Enumerates ability display orientations

**Since:** 7

**Deprecated since:** 9

**Substitutes:** orientation

<!--Device-AbilityInfo-readonly orientation: bundle.DisplayOrientation--><!--Device-AbilityInfo-readonly orientation: bundle.DisplayOrientation-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## permissions

```TypeScript
readonly permissions: Array<string>
```

Permissions required for other applications to call the ability.

The value is obtained by passing in GET_ABILITY_INFO_WITH_PERMISSION to [bundle.getAbilityInfo](arkts-ability-bundle-getabilityinfo-f.md#getabilityinfo-1).

**Type:** Array&lt;string&gt;

**Default:** The permissions that others need to launch this ability

**Since:** 7

**Deprecated since:** 9

**Substitutes:** permissions

<!--Device-AbilityInfo-readonly permissions: Array<string>--><!--Device-AbilityInfo-readonly permissions: Array<string>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## process

```TypeScript
readonly process: string
```

Process name of the ability.

**Type:** string

**Default:** Process of ability, if user do not set it ,the value equal application process

**Since:** 7

**Deprecated since:** 9

**Substitutes:** process

<!--Device-AbilityInfo-readonly process: string--><!--Device-AbilityInfo-readonly process: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## readPermission

```TypeScript
readonly readPermission: string
```

Permission required for reading the ability data.

**Model restriction**: This API can be used only in the FA model.

**Type:** string

**Default:** Indicates the permission required for reading ability data

**Since:** 7

**Deprecated since:** 9

**Model restriction:** This API can be used only in the FA model.

<!--Device-AbilityInfo-readonly readPermission: string--><!--Device-AbilityInfo-readonly readPermission: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## subType

```TypeScript
readonly subType: bundle.AbilitySubType
```

Subtype of the template that can be used by the ability.

**Model restriction**: This API can be used only in the FA model.

**Type:** [bundle.AbilitySubType](arkts-ability-bundle-abilitysubtype-e.md)

**Default:** Enumerates the subType of templates used by an ability

**Since:** 7

**Deprecated since:** 9

**Model restriction:** This API can be used only in the FA model.

<!--Device-AbilityInfo-readonly subType: bundle.AbilitySubType--><!--Device-AbilityInfo-readonly subType: bundle.AbilitySubType-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## targetAbility

```TypeScript
readonly targetAbility: string
```

Target ability that the ability alias points to.

**Model restriction**: This API can be used only in the FA model.

**Type:** string

**Default:** Info about which ability is this nick point to

**Since:** 7

**Deprecated since:** 9

**Model restriction:** This API can be used only in the FA model.

<!--Device-AbilityInfo-readonly targetAbility: string--><!--Device-AbilityInfo-readonly targetAbility: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## type

```TypeScript
readonly type: bundle.AbilityType
```

Ability type.

**Model restriction**: This API can be used only in the FA model.

**Type:** [bundle.AbilityType](arkts-ability-bundle-abilitytype-e.md)

**Default:** Enumerates types of templates that can be used by an ability

**Since:** 7

**Deprecated since:** 9

**Model restriction:** This API can be used only in the FA model.

<!--Device-AbilityInfo-readonly type: bundle.AbilityType--><!--Device-AbilityInfo-readonly type: bundle.AbilityType-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## uri

```TypeScript
readonly uri: string
```

URI of the ability.

**Model restriction**: This API can be used only in the FA model.

**Type:** string

**Default:** Uri of ability

**Since:** 7

**Deprecated since:** 9

**Model restriction:** This API can be used only in the FA model.

<!--Device-AbilityInfo-readonly uri: string--><!--Device-AbilityInfo-readonly uri: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## writePermission

```TypeScript
readonly writePermission: string
```

Permission required for writing data to the ability.

**Model restriction**: This API can be used only in the FA model.

**Type:** string

**Default:** Indicates the permission required for writing data to the ability

**Since:** 7

**Deprecated since:** 9

**Model restriction:** This API can be used only in the FA model.

<!--Device-AbilityInfo-readonly writePermission: string--><!--Device-AbilityInfo-readonly writePermission: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework
