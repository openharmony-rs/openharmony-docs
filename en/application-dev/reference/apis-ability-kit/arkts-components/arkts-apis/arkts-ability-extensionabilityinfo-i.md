# ExtensionAbilityInfo

```TypeScript
export interface ExtensionAbilityInfo
```

The module defines the ExtensionAbility information. An application can obtain its own ExtensionAbility information through [bundleManager.getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md), with **GET_BUNDLE_INFO_WITH_HAP_MODULE** and **GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY** passed in to [bundleFlags](arkts-ability-bundlemanager-bundleflag-e.md).

**Since:** 9

<!--Device-unnamed-export interface ExtensionAbilityInfo--><!--Device-unnamed-export interface ExtensionAbilityInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## appIndex

```TypeScript
readonly appIndex: number
```

Index of an application clone. It takes effect only for cloned applications.

**Type:** number

**Since:** 12

<!--Device-ExtensionAbilityInfo-readonly appIndex: int--><!--Device-ExtensionAbilityInfo-readonly appIndex: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## applicationInfo

```TypeScript
readonly applicationInfo: ApplicationInfo
```

Application configuration information <!--Del-->. The information can be obtained by passing in **GET_EXTENSION_ABILITY_INFO_WITH_APPLICATION** to the **extensionAbilityFlags** parameter of [queryExtensionAbilityInfo](arkts-ability-bundlemanager-queryextensionabilityinfo-f-sys.md) <!--DelEnd-->.

This field is not returned when the [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md) or [getBundleInfo](arkts-ability-bundlemanager-getbundleinfo-f.md) is used to obtain ExtensionAbilityInfo information. You can obtain the related information by obtaining the [bundleInfo](arkts-ability-bundleinfo-i.md).appInfo object.

**Type:** [ApplicationInfo](arkts-ability-applicationinfo-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ExtensionAbilityInfo-readonly applicationInfo: ApplicationInfo--><!--Device-ExtensionAbilityInfo-readonly applicationInfo: ApplicationInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## bundleName

```TypeScript
readonly bundleName: string
```

Bundle name.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ExtensionAbilityInfo-readonly bundleName: string--><!--Device-ExtensionAbilityInfo-readonly bundleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## descriptionId

```TypeScript
readonly descriptionId: number
```

ID of the ExtensionAbility description.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ExtensionAbilityInfo-readonly descriptionId: long--><!--Device-ExtensionAbilityInfo-readonly descriptionId: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## enabled

```TypeScript
readonly enabled: boolean
```

Whether the ExtensionAbility is enabled. **true** if enabled, **false** otherwise.

**Type:** boolean

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ExtensionAbilityInfo-readonly enabled: boolean--><!--Device-ExtensionAbilityInfo-readonly enabled: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## exported

```TypeScript
readonly exported: boolean
```

Whether the ExtensionAbility can be called by other applications. **true** if the ExtensionAbility can be called by other applications, **false** otherwise.

**Type:** boolean

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ExtensionAbilityInfo-readonly exported: boolean--><!--Device-ExtensionAbilityInfo-readonly exported: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## extensionAbilityType

```TypeScript
readonly extensionAbilityType: bundleManager.ExtensionAbilityType
```

Type of the ExtensionAbility.

**Type:** [bundleManager.ExtensionAbilityType](arkts-ability-bundlemanager-extensionabilitytype-e.md)

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ExtensionAbilityInfo-readonly extensionAbilityType: bundleManager.ExtensionAbilityType--><!--Device-ExtensionAbilityInfo-readonly extensionAbilityType: bundleManager.ExtensionAbilityType-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## extensionAbilityTypeName

```TypeScript
readonly extensionAbilityTypeName: string
```

Type of the ExtensionAbility. For details about available values, see [the type field under the extensionabilities tag](../../../quick-start/module-configuration-file.md#extensionabilities).

**Type:** string

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ExtensionAbilityInfo-readonly extensionAbilityTypeName: string--><!--Device-ExtensionAbilityInfo-readonly extensionAbilityTypeName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## iconId

```TypeScript
readonly iconId: number
```

ID of the ExtensionAbility icon.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ExtensionAbilityInfo-readonly iconId: long--><!--Device-ExtensionAbilityInfo-readonly iconId: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## labelId

```TypeScript
readonly labelId: number
```

ID of the ExtensionAbility label.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ExtensionAbilityInfo-readonly labelId: long--><!--Device-ExtensionAbilityInfo-readonly labelId: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## metadata

```TypeScript
readonly metadata: Array<Metadata>
```

Metadata of the ExtensionAbility. The information can be obtained by passing in **GET_BUNDLE_INFO_WITH_HAP_MODULE**, **GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY**, and **GET_BUNDLE_INFO_WITH_METADATA** to the **bundleFlags** parameter of [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md).

**Type:** Array&lt;[Metadata](arkts-ability-metadata-i.md)&gt;

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ExtensionAbilityInfo-readonly metadata: Array<Metadata>--><!--Device-ExtensionAbilityInfo-readonly metadata: Array<Metadata>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## moduleName

```TypeScript
readonly moduleName: string
```

Name of the HAP file to which the ExtensionAbility belongs.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ExtensionAbilityInfo-readonly moduleName: string--><!--Device-ExtensionAbilityInfo-readonly moduleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
readonly name: string
```

Name of the ExtensionAbility.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ExtensionAbilityInfo-readonly name: string--><!--Device-ExtensionAbilityInfo-readonly name: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## permissions

```TypeScript
readonly permissions: Array<string>
```

Permissions required for other bundles to call the ExtensionAbility.

**Type:** Array&lt;string&gt;

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ExtensionAbilityInfo-readonly permissions: Array<string>--><!--Device-ExtensionAbilityInfo-readonly permissions: Array<string>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## readPermission

```TypeScript
readonly readPermission: string
```

Permission required for reading data from the ExtensionAbility.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ExtensionAbilityInfo-readonly readPermission: string--><!--Device-ExtensionAbilityInfo-readonly readPermission: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## skills

```TypeScript
readonly skills: Array<Skill>
```

Skills of the ExtensionAbility.

**Type:** Array&lt;[Skill](arkts-ability-skill-i.md)&gt;

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ExtensionAbilityInfo-readonly skills: Array<Skill>--><!--Device-ExtensionAbilityInfo-readonly skills: Array<Skill>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## writePermission

```TypeScript
readonly writePermission: string
```

Permission required for writing data to the ExtensionAbility.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ExtensionAbilityInfo-readonly writePermission: string--><!--Device-ExtensionAbilityInfo-readonly writePermission: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
