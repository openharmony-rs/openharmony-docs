# ApplicationInfo

```TypeScript
export interface ApplicationInfo
```

The module defines the application information.

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## accessTokenId

```TypeScript
readonly accessTokenId: number
```

Access token ID of the application, which is used in the [application access control verification API](../../../reference/apis-ability-kit/js-apis-abilityAccessCtrl.md#checkaccesstoken9).

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## appDistributionType

```TypeScript
readonly appDistributionType: string
```

Distribution type of the application signing certificate. The options are as follows:&lt;li&gt;**app_gallery**: application installed from AppGallery. &lt;!--RP1--&gt;&lt;!--RP1End--&gt;&lt;li&gt;**enterprise**: enterprise internal application. These are applications developed by an enterprise for its internal use by employees only. They are not distributed through public channels like AppGallery but are distributed internally via the enterprise's own channels. <!--RP2-- ><!--RP2End-->&lt;li&gt;**enterprise_mdm**: enterprise [Mobile Device Management (MDM) application](../../../mdm/mdm-kit-term.md#mdm-app). <!--Del-->To install a common enterprise application, you must have [administrator privileges](../../apis-mdm-kit/arkts-apis/arkts-mdm-adminmanager-enableadmin-f-sys.md). <!--DelEnd-->&lt;!--RP3--&gt;&lt;!--RP3End--&gt;&lt;li&gt;**enterprise_normal**: standard enterprise application. These applications do not need to be released to AppGallery. Instead, they can be distributed and installed through an enterprise [MDM application](../../../mdm/mdm-kit-term.md#mdm-app) and offline installer. &lt;!--RP4--&gt;&lt;!--RP4End--&gt;&lt;li&gt;**os_integration**: pre-installed application. They are not available for third-party applications. &lt;li&gt;crowdtesting: application under crowdtesting, which is distributed by AppGallery to a limited number of users and come with a set expiration date. When the system detects that the validity period of the application expires, it prompts the user to update to the release version available on AppGallery. This API is deprecated since API version 11. &lt;li&gt;**internaltesting**: application under internal testing of AppGallery. <!-- RP5-->&lt;!--RP5End--&gt;&lt;li&gt;none: others.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## appIndex

```TypeScript
readonly appIndex: number
```

Index of an application clone. It takes effect only for cloned applications.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## appProvisionType

```TypeScript
readonly appProvisionType: string
```

Type of the application signing certificate file. The options are **debug** and **release**.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## bundleType

```TypeScript
readonly bundleType: bundleManager.BundleType
```

Bundle type, which can be **APP** (application) or **ATOMIC_SERVICE** (atomic service).

**Type:** [bundleManager.BundleType](arkts-ability-bundlemanager-bundletype-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## cloudFileSyncEnabled

```TypeScript
readonly cloudFileSyncEnabled: boolean
```

Whether device-cloud file synchronization is enabled for the application. **true** if enabled, **false** otherwise.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## cloudStructuredDataSyncEnabled

```TypeScript
readonly cloudStructuredDataSyncEnabled?: boolean
```

Whether device-cloud structured data synchronization is enabled for the application. **true** if enabled, **false** otherwise.

**Type:** boolean

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## codePath

```TypeScript
readonly codePath: string
```

Installation directory of the application.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## dataUnclearable

```TypeScript
readonly dataUnclearable: boolean
```

Whether the application data is unclearable. **true** if unclearable, **false** otherwise.

**Type:** boolean

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## debug

```TypeScript
readonly debug: boolean
```

Whether the application is running in debug mode. **true** if in debug mode, **false** otherwise.

**Type:** boolean

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## description

```TypeScript
readonly description: string
```

Description of the application. It corresponds to the **description** field in the [app.json5](../../../quick-start/app-configuration-file.md). For details about **description**, see the **descriptionResource** field in this table.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## descriptionId

```TypeScript
readonly descriptionId: number
```

Resource ID of the application description. It is automatically generated during compilation and build based on the description configured for the application.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## descriptionResource

```TypeScript
readonly descriptionResource: Resource
```

Resource information of the application description. The resource information obtained contains the bundle name, module name, and ID of the resource. You can call [getMediaContent](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md#getmediacontent) to obtain the resource details.

**Type:** [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## enabled

```TypeScript
readonly enabled: boolean
```

Whether the application is enabled. **true** if enabled, **false** otherwise.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## icon

```TypeScript
readonly icon: string
```

Application icon. It corresponds to the **icon** field in the [app.json5](../../../quick-start/app-configuration-file.md) file. For details about **icon**, see the **iconResource** field in this table.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## iconId

```TypeScript
readonly iconId: number
```

Resource ID of the application icon. It is automatically generated during compilation and build based on the icon configured for the application.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## iconResource

```TypeScript
readonly iconResource: Resource
```

Resource information of the application icon. The resource information obtained contains the bundle name, module name, and ID of the resource. You can call [getMediaContent](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md#getmediacontent) to obtain the resource details.

**Type:** [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## installSource

```TypeScript
readonly installSource: string
```

Installation source of an application. The options are as follows:

- **pre-installed**: pre-installed application installed during the first boot.  
- **ota**: pre-installed application added during system upgrade.  
- **recovery**: pre-installed application manually restored by the user after uninstallation.  
- **bundleName**: installation by the application corresponding to this bundle name. **bundleName** represents a  
variable, subject to the actual value.  
- **unknown**: unknown application installation source.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## label

```TypeScript
readonly label: string
```

Application label. It corresponds to the **label** field in the [app.json5](../../../quick-start/app-configuration-file.md) file. For details about **label**, see the **labelResource** field in this table. Starting from API version 20, if [bundleManager.getAbilityInfo](arkts-ability-bundlemanager-getabilityinfo-f.md) is used to obtain application information, this field is the application name visible to users, instead of the resource descriptor.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## labelId

```TypeScript
readonly labelId: number
```

Resource ID of the application label. It is automatically generated during compilation and build based on the label configured for the application.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## labelResource

```TypeScript
readonly labelResource: Resource
```

Resource information of the application label. The resource information obtained contains the bundle name, module name, and ID of the resource. You can call [getMediaContent](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md#getmediacontent) to obtain the resource details.

**Type:** [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## metadata

```TypeScript
readonly metadata: Map<string, Array<Metadata>>
```

Metadata of the application. The information can be obtained by passing in **GET_BUNDLE_INFO_WITH_APPLICATION** and **GET_BUNDLE_INFO_WITH_METADATA** to the **bundleFlags** parameter of [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md).

Note: Supported since API version 9 and deprecated since API version 10. You are advised to use **metadataArray** instead.

**Type:** Map&lt;string, Array&lt;[Metadata](arkts-ability-metadata-i.md)&gt;&gt;

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [metadataArray](#metadataarray)

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## metadataArray

```TypeScript
readonly metadataArray: Array<ModuleMetadata>
```

Metadata of the application. The information can be obtained by passing in **GET_BUNDLE_INFO_WITH_APPLICATION** and **GET_BUNDLE_INFO_WITH_METADATA** to the **bundleFlags** parameter of [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md).

**Type:** Array&lt;[ModuleMetadata](arkts-ability-applicationinfo-modulemetadata-i.md)&gt;

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## multiAppMode

```TypeScript
readonly multiAppMode: MultiAppMode
```

Multi-app mode.

**Type:** [MultiAppMode](arkts-ability-applicationinfo-multiappmode-i.md)

**Since:** 12

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
readonly name: string
```

Name of the application bundle. It corresponds to the **bundleName** field in the [app.json5](../../../quick-start/app-configuration-file.md) file.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## nativeLibraryPath

```TypeScript
readonly nativeLibraryPath: string
```

Local library file path of the application.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## permissions

```TypeScript
readonly permissions: Array<string>
```

Permissions required for accessing the application. The permissions can be obtained by passing in **GET_BUNDLE_INFO_WITH_APPLICATION** and **GET_BUNDLE_INFO_WITH_REQUESTED_PERMISSION** to the **bundleFlags** parameter of [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md).

**Type:** Array&lt;string&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## process

```TypeScript
readonly process: string
```

Process name.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## releaseType

```TypeScript
readonly releaseType: string
```

Release type of the SDK used for application packing. Currently, the SDK release types include Canary, Beta, and Release. Each of the Canary and Beta releases can be distinguished by a sequential number, such as Canary1, Canary2, Beta1, and Beta2. You can compare the SDK release type on which application packaging depends and the OS release type (specified by [deviceInfo.distributionOSReleaseType](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-deviceinfo.md)) to determine the compatibility.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## removable

```TypeScript
readonly removable: boolean
```

Whether the application is removable. **true** if removable, **false** otherwise.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## systemApp

```TypeScript
readonly systemApp: boolean
```

Whether the application is a system application. **true** if it is a system application, **false** otherwise.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## uid

```TypeScript
readonly uid: number
```

UID of the application.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
