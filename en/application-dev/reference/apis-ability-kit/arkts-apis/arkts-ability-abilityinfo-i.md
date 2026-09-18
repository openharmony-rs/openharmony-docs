# AbilityInfo

The module defines the ability information.

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## appIndex

```TypeScript
readonly appIndex: number
```

Index of an application clone. It takes effect only for [application clones](../../../quick-start/app-clone.md).

**Type:** number

**Since:** 12

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## applicationInfo

```TypeScript
readonly applicationInfo: ApplicationInfo
```

Application configuration information <!--Del-->. The information can be obtained by passing in **GET_ABILITY_INFO_WITH_APPLICATION** to the **abilityFlags** parameter of [queryAbilityInfo](arkts-ability-bundlemanager-queryabilityinfo-f-sys.md) <!--DelEnd-->.

This field is not returned when the [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md) or [getBundleInfo](arkts-ability-bundlemanager-getbundleinfo-f.md) is used to obtain ability information. You can obtain the related information by obtaining the [bundleInfo](arkts-ability-bundleinfo-i.md).appInfo object.

**Type:** [ApplicationInfo](arkts-ability-applicationinfo-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## bundleName

```TypeScript
readonly bundleName: string
```

Bundle name.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## description

```TypeScript
readonly description: string
```

Ability description, which describes the content and functions of the current ability. It corresponds to the **description** field under **abilities** in the [module.json5](../../../quick-start/module-configuration-file.md) file.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## descriptionId

```TypeScript
readonly descriptionId: number
```

Resource ID of the ability description. It is automatically generated during compilation and build based on the description configured in **abilities** of the application.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## deviceTypes

```TypeScript
readonly deviceTypes: Array<string>
```

Device types supported by the ability. The value is derived from that of [deviceTypes](../../../quick-start/module-configuration-file.md#devicetypes) in the **module.json5** file.

**Type:** Array&lt;string&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## enabled

```TypeScript
readonly enabled: boolean
```

Whether the ability is available, that is, whether it can be started or queried. **true** if available, **false** otherwise. If the ability is unavailable, you must call [getAbilityInfo](arkts-ability-bundlemanager-getabilityinfo-f.md) with **AbilityFlag** set to **GET_ABILITY_INFO_WITH_DISABLE** to query the ability.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## excludeFromDock

```TypeScript
readonly excludeFromDock: boolean
```

Whether the ability icon can be hidden in the dock area. **true** if the ability icon can be hidden in the dock area, **false** otherwise.

Note: This field does not take effect.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## exported

```TypeScript
readonly exported: boolean
```

Whether the ability can be launched by other applications. **true** if the ability can be launched by other applications, **false** otherwise.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## icon

```TypeScript
readonly icon: string
```

Resource descriptor of the ability icon. It corresponds to the **icon** field under **abilities** in the [module.json5](../../../quick-start/module-configuration-file.md) file.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## iconId

```TypeScript
readonly iconId: number
```

Resource ID of the ability icon. It is automatically generated during compilation and build based on the icon configured in **abilities** of the application.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## label

```TypeScript
readonly label: string
```

Resource descriptor of the ability name visible to users. It corresponds to the **label** field under **abilities** in the [module.json5](../../../quick-start/module-configuration-file.md) file.

Note: Starting from API version 20, if [bundleManager.getAbilityInfo](arkts-ability-bundlemanager-getabilityinfo-f.md) is used to obtain ability information, this field is the ability name visible to users.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## labelId

```TypeScript
readonly labelId: number
```

Resource ID of the ability label. It is automatically generated during compilation and build based on the label configured in **abilities** of the application.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## launchType

```TypeScript
readonly launchType: bundleManager.LaunchType
```

Ability launch mode, that is, whether it can be started in multiton mode. For details, see [LaunchType](arkts-ability-bundlemanager-launchtype-e.md).

**Type:** [bundleManager.LaunchType](arkts-ability-bundlemanager-launchtype-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## metadata

```TypeScript
readonly metadata: Array<Metadata>
```

Metadata of the ability. You can configure the system-defined parameters to use the capabilities provided by the system, for example, [shortcuts](../../../quick-start/module-configuration-file.md#shortcuts) and [window metadata configuration](../../../windowmanager/window-config-m.md). You can also customize the parameters and call [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md) to obtain the parameters by passing **GET_BUNDLE_INFO_WITH_HAP_MODULE**, **GET_BUNDLE_INFO_WITH_ABILITY**, and **GET_BUNDLE_INFO_WITH_METADATA** to **bundleFlags**.

**Type:** Array&lt;[Metadata](arkts-ability-metadata-i.md)&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## moduleName

```TypeScript
readonly moduleName: string
```

Module name to which the ability belongs.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
readonly name: string
```

Ability name.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## orientation

```TypeScript
readonly orientation: bundleManager.DisplayOrientation
```

Ability display orientation. It is derived from the **orientation** field under **abilities** in the [module.json5](../../../quick-start/module-configuration-file.md) file. If **orientation** in the file is set to an enumerated value, this property is a non-zero value. For details about the available values, see [displayOrientation](arkts-ability-bundlemanager-displayorientation-e.md). If **orientation** in the file is set to a resource index, the value of this property is **0**.

**Type:** [bundleManager.DisplayOrientation](arkts-ability-bundlemanager-displayorientation-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## orientationId

```TypeScript
readonly orientationId: number
```

Resource ID of the ability display mode. It is derived from the **orientation** field under **abilities** in the [module.json5](../../../quick-start/module-configuration-file.md) file. If the **orientation** field in the file is set to an enumerated value, **orientationId** is **0**. If the **orientation** field is set to a resource index, **orientationId** is a non-zero value, which is the resource ID generated during building. If **orientationId** is set to a value other than **0**, the current display mode is customized, and this ID must be used to obtain the corresponding resource from the resource manager module. If **orientationId** is set to **0**, no resource is configured.

**Type:** number

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## permissions

```TypeScript
readonly permissions: Array<string>
```

Array of permissions that other applications must request to start or access this ability. The system checks whether the caller has these permissions only if the **exported** property in **AbilityInfo** is **true** (meaning that the ability allows itself to be started by other applications).

**Type:** Array&lt;string&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## process

```TypeScript
readonly process: string
```

Process name of the ability.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## readPermission

```TypeScript
readonly readPermission: string
```

Permission required for reading the ability data.

**Model restriction**: This API can be used only in the FA model.

**Type:** string

**Since:** 9

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## skills

```TypeScript
readonly skills: Array<Skill>
```

Skills information of the ability. It represents the feature set of [wants](../../../application-models/want-overview.md) that can be received by the UIAbility or ExtensionAbility.

**Type:** Array&lt;[Skill](arkts-ability-skill-i.md)&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## supportWindowModes

```TypeScript
readonly supportWindowModes: Array<bundleManager.SupportWindowMode>
```

Window modes supported by the ability.

**Type:** Array&lt;[bundleManager.SupportWindowMode](arkts-ability-bundlemanager-supportwindowmode-e.md)&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## type

```TypeScript
readonly type: bundleManager.AbilityType
```

Ability type.

**Model restriction**: This API can be used only in the FA model.

**Type:** [bundleManager.AbilityType](arkts-ability-bundlemanager-abilitytype-e.md)

**Since:** 9

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## uri

```TypeScript
readonly uri: string
```

URI of the ability.

**Model restriction**: This API can be used only in the FA model.

**Type:** string

**Since:** 9

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## windowSize

```TypeScript
readonly windowSize: WindowSize
```

Window size.

**Type:** [WindowSize](arkts-ability-abilityinfo-windowsize-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## writePermission

```TypeScript
readonly writePermission: string
```

Permission required for writing data to the ability.

**Model restriction**: This API can be used only in the FA model.

**Type:** string

**Since:** 9

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
