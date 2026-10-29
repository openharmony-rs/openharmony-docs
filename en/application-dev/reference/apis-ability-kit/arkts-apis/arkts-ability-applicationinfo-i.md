# ApplicationInfo

```TypeScript
export interface ApplicationInfo
```

The module defines the application information. An application can obtain its own application information through [bundleManager.getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md), with **GET_BUNDLE_INFO_WITH_APPLICATION** passed in to [bundleFlags](arkts-ability-bundlemanager-bundleflag-e.md).

**Since:** 9

<!--Device-unnamed-export interface ApplicationInfo--><!--Device-unnamed-export interface ApplicationInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## accessTokenId

```TypeScript
readonly accessTokenId: number
```

accessTokenId of the application, which is the identity identifier of the application and is used in [checkAccessToken](arkts-ability-abilityaccessctrl-atmanager-i.md#checkaccesstoken).

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationInfo-readonly accessTokenId: long--><!--Device-ApplicationInfo-readonly accessTokenId: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## appDistributionType

```TypeScript
readonly appDistributionType: string
```

Distribution type of the application signing certificate, which is divided into: <li>app_gallery: application installed from the application market. <!--RP1--><!--RP1End--> <li> enterprise: enterprise internal application, which is developed by the enterprise itself and used only by its internal employees. It is not released through public channels such as the application market, but distributed internally through the enterprise's own channels. <!--RP2--><!--RP2End--><li> enterprise_mdm: enterprise [MDM app](../../../mdm/mdm-kit-term.md#mdm-app). <!--Del--> It can be installed only after the administrator privilege is activated by calling [enableAdmin](../../../reference/apis-mdm-kit/js-apis-enterprise-adminManager-sys.md#adminmanagerenableadmin). <!--DelEnd--><!--RP3--><!--RP3End--> <li>enterprise_normal: normal enterprise application, which does not need to be listed on the Huawei application market and can be distributed and installed through the enterprise [MDM app](../../../mdm/mdm-kit-term.md#mdm-app) and offline installer. <!--RP4--><!--RP4End--><li>os_integration: preset application, which cannot be applied for or configured by third-party applications.<li>crowdtesting: crowdtesting application, which is a specific application distributed by the application market to some users with a certain validity period. When the system detects that the validity period of the application has expired, it notifies the user to update to the release version of the application in the application market. Deprecated since API version 11.<li>internaltesting: application under internal testing in the application market. <!--RP5--> <!--RP5End--><li>none: others.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationInfo-readonly appDistributionType: string--><!--Device-ApplicationInfo-readonly appDistributionType: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## appIndex

```TypeScript
readonly appIndex: number
```

Clone index identifier of the application bundle, which takes effect only in clone applications. The value is an integer in the range [0-5], where 0 indicates the main application and 1-5 indicate clone applications.

**Type:** number

**Since:** 12

<!--Device-ApplicationInfo-readonly appIndex: int--><!--Device-ApplicationInfo-readonly appIndex: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## appProvisionType

```TypeScript
readonly appProvisionType: string
```

Type of the application signing certificate file, which is divided into 'debug' and 'release'. The 'debug' type is used in the development and testing phase for debugging and verifying functions; the 'release' type is used for applications officially released in the production environment.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationInfo-readonly appProvisionType: string--><!--Device-ApplicationInfo-readonly appProvisionType: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## bundleType

```TypeScript
readonly bundleType: bundleManager.BundleType
```

Type of the bundle, whose value is APP (application) or ATOMIC_SERVICE (atomic service). APP is the traditional application form and requires the user to install it proactively; ATOMIC_SERVICE is the atomic service form, which is ready to use without installation. Developers can determine the type of the current application based on this field and perform differentiated processing.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** [bundleManager.BundleType](arkts-ability-bundlemanager-bundletype-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationInfo-readonly bundleType: bundleManager.BundleType--><!--Device-ApplicationInfo-readonly bundleType: bundleManager.BundleType-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## cloudFileSyncEnabled

```TypeScript
readonly cloudFileSyncEnabled: boolean
```

Whether device-cloud file synchronization is enabled for the application. **true** if enabled, **false** otherwise.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ApplicationInfo-readonly cloudFileSyncEnabled: boolean--><!--Device-ApplicationInfo-readonly cloudFileSyncEnabled: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## cloudStructuredDataSyncEnabled

```TypeScript
readonly cloudStructuredDataSyncEnabled?: boolean
```

Whether device-cloud structured data synchronization is enabled for the application. **true** if enabled, **false** otherwise.

**Type:** boolean

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ApplicationInfo-readonly cloudStructuredDataSyncEnabled?: boolean--><!--Device-ApplicationInfo-readonly cloudStructuredDataSyncEnabled?: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## codePath

```TypeScript
readonly codePath: string
```

Installation directory of the application.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationInfo-readonly codePath: string--><!--Device-ApplicationInfo-readonly codePath: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## dataUnclearable

```TypeScript
readonly dataUnclearable: boolean
```

Whether the application data is unclearable. **true** if unclearable, **false** otherwise.

**Type:** boolean

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationInfo-readonly dataUnclearable: boolean--><!--Device-ApplicationInfo-readonly dataUnclearable: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## debug

```TypeScript
readonly debug: boolean
```

Whether the application is running in debug mode. **true** if in debug mode, **false** otherwise.

**Type:** boolean

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationInfo-readonly debug: boolean--><!--Device-ApplicationInfo-readonly debug: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## description

```TypeScript
readonly description: string
```

Description of the application. It corresponds to the **description** field in the [app.json5](../../../quick-start/app-configuration-file.md). For details about **description**, see the **descriptionResource** field in this table.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationInfo-readonly description: string--><!--Device-ApplicationInfo-readonly description: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## descriptionId

```TypeScript
readonly descriptionId: number
```

Resource ID of the application description. It is automatically generated during compilation and build based on the description configured for the application.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationInfo-readonly descriptionId: long--><!--Device-ApplicationInfo-readonly descriptionId: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## descriptionResource

```TypeScript
readonly descriptionResource: Resource
```

Description resource information of the application, which contains the bundleName, moduleName, and id of the resource. You can call the globalization API [getStringValue](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md#getstringvalue) and pass in descriptionResource.id to obtain the detailed resource data information.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationInfo-readonly descriptionResource: Resource--><!--Device-ApplicationInfo-readonly descriptionResource: Resource-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## enabled

```TypeScript
readonly enabled: boolean
```

Whether the application is enabled. **true** if enabled, **false** otherwise.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationInfo-readonly enabled: boolean--><!--Device-ApplicationInfo-readonly enabled: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## icon

```TypeScript
readonly icon: string
```

Application icon. It corresponds to the **icon** field in the [app.json5](../../../quick-start/app-configuration-file.md) file. For details about **icon**, see the **iconResource** field in this table.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationInfo-readonly icon: string--><!--Device-ApplicationInfo-readonly icon: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## iconId

```TypeScript
readonly iconId: number
```

Resource ID of the application icon. It is automatically generated during compilation and build based on the icon configured for the application.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationInfo-readonly iconId: long--><!--Device-ApplicationInfo-readonly iconId: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## iconResource

```TypeScript
readonly iconResource: Resource
```

Icon resource information of the application, which contains the bundleName, moduleName, and id of the resource. You can call the globalization API [getMediaContentBase64](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md#getmediacontentbase64) and pass in iconResource.id to obtain the detailed resource data information.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationInfo-readonly iconResource: Resource--><!--Device-ApplicationInfo-readonly iconResource: Resource-End-->

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

<!--Device-ApplicationInfo-readonly installSource: string--><!--Device-ApplicationInfo-readonly installSource: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## label

```TypeScript
readonly label: string
```

Application label. It corresponds to the **label** field in the [app.json5](../../../quick-start/app-configuration-file.md) file. For details about **label**, see the **labelResource** field in this table. Starting from API version 20, if [bundleManager.getAbilityInfo](arkts-ability-bundlemanager-getabilityinfo-f.md) is used to obtain application information, this field is the application name visible to users, instead of the resource descriptor.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationInfo-readonly label: string--><!--Device-ApplicationInfo-readonly label: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## labelId

```TypeScript
readonly labelId: number
```

Resource ID of the application label. It is automatically generated during compilation and build based on the label configured for the application.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationInfo-readonly labelId: long--><!--Device-ApplicationInfo-readonly labelId: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## labelResource

```TypeScript
readonly labelResource: Resource
```

Name resource information of the application, which contains the bundleName, moduleName, and id of the resource. You can call the globalization API [getStringValue](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md#getstringvalue) and pass in labelResource.id to obtain the detailed resource data information.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationInfo-readonly labelResource: Resource--><!--Device-ApplicationInfo-readonly labelResource: Resource-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## metadataArray

```TypeScript
readonly metadataArray: Array<ModuleMetadata>
```

Metadata of the application. The information can be obtained by passing in **GET_BUNDLE_INFO_WITH_APPLICATION** and **GET_BUNDLE_INFO_WITH_METADATA** to the **bundleFlags** parameter of [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md).

**Type:** Array&lt;[ModuleMetadata](arkts-ability-applicationinfo-modulemetadata-i.md)&gt;

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationInfo-readonly metadataArray: Array<ModuleMetadata>--><!--Device-ApplicationInfo-readonly metadataArray: Array<ModuleMetadata>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## multiAppMode

```TypeScript
readonly multiAppMode: MultiAppMode
```

Application multi-instance mode. It is applicable to scenarios where multiple application instances need to run simultaneously, such as managing multiple enterprise accounts (for example, work account and personal account logged in at the same time), running multiple environments in parallel (for example, test environment and production environment), and multiple social identities (for example, personal account and work account).

**Type:** [MultiAppMode](arkts-ability-applicationinfo-multiappmode-i.md)

**Since:** 12

<!--Device-ApplicationInfo-readonly multiAppMode: MultiAppMode--><!--Device-ApplicationInfo-readonly multiAppMode: MultiAppMode-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
readonly name: string
```

Name of the application bundle. It corresponds to the **bundleName** field in the [app.json5](../../../quick-start/app-configuration-file.md) file.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationInfo-readonly name: string--><!--Device-ApplicationInfo-readonly name: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## nativeLibraryPath

```TypeScript
readonly nativeLibraryPath: string
```

Local library file path of the application.

**Type:** string

**Since:** 12

<!--Device-ApplicationInfo-readonly nativeLibraryPath: string--><!--Device-ApplicationInfo-readonly nativeLibraryPath: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## permissions

```TypeScript
readonly permissions: Array<string>
```

List of permissions required to access the application<!--Del-->, which can be obtained by calling [getApplicationInfo](arkts-ability-bundlemanager-getapplicationinfo-f-sys.md) with the appFlags parameter set to GET_APPLICATION_INFO_WITH_PERMISSION<!--DelEnd-->.

When [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md) or [getBundleInfo](arkts-ability-bundlemanager-getbundleinfo-f.md) is called to obtain ApplicationInfo information, this field is not returned. You can obtain the permission list from [bundleInfo](arkts-ability-bundleinfo-i.md).reqPermissionDetails.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** Array&lt;string&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationInfo-readonly permissions: Array<string>--><!--Device-ApplicationInfo-readonly permissions: Array<string>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## process

```TypeScript
readonly process: string
```

Process name.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationInfo-readonly process: string--><!--Device-ApplicationInfo-readonly process: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## releaseType

```TypeScript
readonly releaseType: string
```

Release type of the SDK used when the application is packaged. The current SDK release types are Canary, Beta, and Release, where Canary and Beta are further subdivided by sequence number, for example, Canary1, Canary2, Beta1, and Beta2. Developers can determine compatibility by comparing the SDK release type that the application packaging depends on with the OS release type ([deviceInfo.distributionOSReleaseType](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-deviceinfo.md)).

**Atomic service API:** Since API version 12, this API is supported in atomic services.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ApplicationInfo-readonly releaseType: string--><!--Device-ApplicationInfo-readonly releaseType: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## removable

```TypeScript
readonly removable: boolean
```

Whether the application is removable. **true** if removable, **false** otherwise.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationInfo-readonly removable: boolean--><!--Device-ApplicationInfo-readonly removable: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## systemApp

```TypeScript
readonly systemApp: boolean
```

Whether the application is a system application. **true** if it is a system application, **false** otherwise.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationInfo-readonly systemApp: boolean--><!--Device-ApplicationInfo-readonly systemApp: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## uid

```TypeScript
readonly uid: number
```

UID of the application.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ApplicationInfo-readonly uid: int--><!--Device-ApplicationInfo-readonly uid: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## metadata

```TypeScript
readonly metadata: Map<string, Array<Metadata>>
```

Metadata of the application, which can be obtained by calling [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md) with the bundleFlags parameter set to GET_BUNDLE_INFO_WITH_APPLICATION and GET_BUNDLE_INFO_WITH_METADATA.

**Note:** Supported since API version 9 and deprecated since API version 10. You are advised to use metadataArray instead.

**Type:** Map&lt;string, Array&lt;[Metadata](arkts-ability-metadata-i.md)&gt;&gt;

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [metadataArray](#metadataarray)

<!--Device-ApplicationInfo-readonly metadata: Map<string, Array<Metadata>>--><!--Device-ApplicationInfo-readonly metadata: Map<string, Array<Metadata>>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
