# AbilityInfo

```TypeScript
export interface AbilityInfo
```

The module provides information about an ability. Unless otherwise specified, the information is obtained through [bundle.getAbilityInfo](arkts-ability-bundle-getabilityinfo-f.md#getabilityinfo-1).

> **NOTE:** 
> 
> The APIs of this module have been deprecated since API version 9. You are advised to use
> [bundleManager-AbilityInfo](#abilityinfo) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [AbilityInfo](#abilityinfo)

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

**System capability:** SystemCapability.BundleManager.BundleFramework
