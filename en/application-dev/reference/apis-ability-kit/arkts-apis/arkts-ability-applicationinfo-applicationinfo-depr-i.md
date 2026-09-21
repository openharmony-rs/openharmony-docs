# ApplicationInfo

```TypeScript
export interface ApplicationInfo
```

The module provides application information. Unless otherwise specified, the information is obtained through [bundle.getApplicationInfo](arkts-ability-bundle-getapplicationinfo-f.md#getapplicationinfo-2).

> **NOTE:** 
> 
> The APIs of this module have been deprecated since API version 9. You are advised to use
> [bundleManager-ApplicationInfo](#applicationinfo) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [ApplicationInfo](#applicationinfo)

**System capability:** SystemCapability.BundleManager.BundleFramework

## accessTokenId

```TypeScript
readonly accessTokenId: number
```

Access token ID of the application.

**Type:** number

**Default:** Indicates the access token of the application

**Since:** 8

**Deprecated since:** 9

**Substitutes:** accessTokenId

**System capability:** SystemCapability.BundleManager.BundleFramework

## codePath

```TypeScript
readonly codePath: string
```

Installation directory of the application. Do not access resource files using concatenated paths. Use [@ohos.resourceManager](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager.md) instead.

**Type:** string

**Default:** Indicates the application source code path

**Since:** 8

**Deprecated since:** 9

**Substitutes:** codePath

**System capability:** SystemCapability.BundleManager.BundleFramework

## description

```TypeScript
readonly description: string
```

Application description.

**Type:** string

**Default:** Description of application

**Since:** 7

**Deprecated since:** 9

**Substitutes:** description

**System capability:** SystemCapability.BundleManager.BundleFramework

## descriptionId

```TypeScript
readonly descriptionId: number
```

ID of the application description.

**Type:** number

**Default:** Indicates the description id of the application

**Since:** 7

**Deprecated since:** 9

**Substitutes:** descriptionId

**System capability:** SystemCapability.BundleManager.BundleFramework

## enabled

```TypeScript
readonly enabled: boolean
```

Whether the application is enabled. **true** if enabled, **false** otherwise.

**Type:** boolean

**Default:** Indicates whether or not this application may be instantiated

**Since:** 7

**Deprecated since:** 9

**Substitutes:** enabled

**System capability:** SystemCapability.BundleManager.BundleFramework

## entityType

```TypeScript
readonly entityType: string
```

Type of the application, for example, gaming, social networking, movies, and news.

**Type:** string

**Default:** Indicates entity type of the application

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework

## entryDir

```TypeScript
readonly entryDir: string
```

Path for storing application files. Do not access resource files using concatenated paths. Use [@ohos.resourceManager](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager.md) instead.

**Type:** string

**Default:** Indicates the path where the `Entry.hap` file of the application is saved

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework

## icon

```TypeScript
readonly icon: string
```

Application icon.

**Type:** string

**Default:** Indicates the icon of the application

**Since:** 7

**Deprecated since:** 9

**Substitutes:** icon

**System capability:** SystemCapability.BundleManager.BundleFramework

## iconId

```TypeScript
readonly iconId: string
```

ID of the application icon.

**Type:** string

**Default:** Indicates the icon id of the application

**Since:** 7

**Deprecated since:** 9

**Substitutes:** iconId

**System capability:** SystemCapability.BundleManager.BundleFramework

## label

```TypeScript
readonly label: string
```

Application label.

**Type:** string

**Default:** Indicates the label of the application

**Since:** 7

**Deprecated since:** 9

**Substitutes:** label

**System capability:** SystemCapability.BundleManager.BundleFramework

## labelId

```TypeScript
readonly labelId: string
```

ID of the application label.

**Type:** string

**Default:** Indicates the label id of the application

**Since:** 7

**Deprecated since:** 9

**Substitutes:** labelId

**System capability:** SystemCapability.BundleManager.BundleFramework

## metaData

```TypeScript
readonly metaData: Map<string, Array<CustomizeData>>
```

Custom metadata of the application.

The value is obtained by passing in GET_APPLICATION_INFO_WITH_METADATA to [bundle.getApplicationInfo](arkts-ability-bundle-getapplicationinfo-f.md#getapplicationinfo-2).

**Type:** Map&lt;string, Array&lt;[CustomizeData](arkts-ability-customizedata-customizedata-depr-i.md)&gt;&gt;

**Default:** Indicates the metadata of module

**Since:** 8

**Deprecated since:** 9

**Substitutes:** metadataArray

**System capability:** SystemCapability.BundleManager.BundleFramework

## moduleInfos

```TypeScript
readonly moduleInfos: Array<ModuleInfo>
```

Application module information.

**Type:** Array&lt;[ModuleInfo](arkts-ability-moduleinfo-moduleinfo-depr-i.md)&gt;

**Default:** Indicates module information about an application

**Since:** 7

**Deprecated since:** 9

**Substitutes:** hapModulesInfo

**System capability:** SystemCapability.BundleManager.BundleFramework

## moduleSourceDirs

```TypeScript
readonly moduleSourceDirs: Array<string>
```

Relative paths for storing application resources. Do not access resource files using concatenated paths. Use [@ohos.resourceManager](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager.md) instead.

**Type:** Array&lt;string&gt;

**Default:** Indicates the path storing the module resources of the application

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework

## name

```TypeScript
readonly name: string
```

Application name.

**Type:** string

**Default:** Indicates the application name, which is the same as `bundleName`

**Since:** 7

**Deprecated since:** 9

**Substitutes:** name

**System capability:** SystemCapability.BundleManager.BundleFramework

## permissions

```TypeScript
readonly permissions: Array<string>
```

Permissions required for accessing the application.

The value is obtained by passing in GET_APPLICATION_INFO_WITH_PERMISSION to [bundle.getApplicationInfo](arkts-ability-bundle-getapplicationinfo-f.md#getapplicationinfo-2).

**Type:** Array&lt;string&gt;

**Default:** Indicates the permissions required for accessing the application.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** permissions

**System capability:** SystemCapability.BundleManager.BundleFramework

## process

```TypeScript
readonly process: string
```

Process name.

**Type:** string

**Default:** Process of application, if user do not set it ,the value equal bundleName

**Since:** 7

**Deprecated since:** 9

**Substitutes:** process

**System capability:** SystemCapability.BundleManager.BundleFramework

## removable

```TypeScript
readonly removable: boolean
```

Whether the application is removable. **true** if removable, **false** otherwise.

**Type:** boolean

**Default:** Indicates whether or not this application may be removable

**Since:** 8

**Deprecated since:** 9

**Substitutes:** removable

**System capability:** SystemCapability.BundleManager.BundleFramework

## supportedModes

```TypeScript
readonly supportedModes: number
```

Modes supported by the application. Currently, only the **drive** mode is defined. This attribute applies only to telematics devices.

**Type:** number

**Default:** Indicates the running mode supported by the application

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework

## systemApp

```TypeScript
readonly systemApp: boolean
```

Whether the application is a system application. **true** if yes, **false** otherwise.

**Type:** boolean

**Default:** Indicates whether the application is a system application

**Since:** 7

**Deprecated since:** 9

**Substitutes:** systemApp

**System capability:** SystemCapability.BundleManager.BundleFramework

## uid

```TypeScript
readonly uid: number
```

UID of the application.

**Type:** number

**Default:** Indicates the uid of the application

**Since:** 8

**Deprecated since:** 9

**Substitutes:** uid

**System capability:** SystemCapability.BundleManager.BundleFramework
