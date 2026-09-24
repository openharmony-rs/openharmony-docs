# BundleInfo

```TypeScript
export interface BundleInfo
```


> **NOTE:** 
> 
> This API has been supported since API version 7 and deprecated since API version 9. You are advised to use
> [bundleManager-BundleInfo](#bundleinfo) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [BundleInfo](#bundleinfo)

**System capability:** SystemCapability.BundleManager.BundleFramework

## abilityInfos

```TypeScript
readonly abilityInfos: Array<AbilityInfo>
```

Ability configuration information.

The value is obtained by passing in GET_BUNDLE_WITH_ABILITIES to [bundle.getBundleInfo](arkts-ability-bundle-getbundleinfo-f.md#getbundleinfo-2).

**Type:** Array&lt;[AbilityInfo](arkts-ability-abilityinfo-abilityinfo-depr-i.md)&gt;

**Default:** Obtains configuration information about an ability

**Since:** 7

**Deprecated since:** 9

**Substitutes:** abilitiesInfo

**System capability:** SystemCapability.BundleManager.BundleFramework

## appId

```TypeScript
readonly appId: string
```

ID of the application to which the bundle belongs.

**Type:** string

**Default:** Indicates the ID of the application to which this bundle belongs The application ID uniquely identifies an application. It is determined by the bundle name and signature

**Since:** 7

**Deprecated since:** 9

**Substitutes:** appId

**System capability:** SystemCapability.BundleManager.BundleFramework

## appInfo

```TypeScript
readonly appInfo: ApplicationInfo
```

Application configuration information.

**Type:** [ApplicationInfo](arkts-ability-applicationinfo-applicationinfo-depr-i.md)

**Default:** Obtains configuration information about an application

**Since:** 7

**Deprecated since:** 9

**Substitutes:** appInfo

**System capability:** SystemCapability.BundleManager.BundleFramework

## compatibleVersion

```TypeScript
readonly compatibleVersion: number
```

Earliest SDK version required for running the bundle.

**Type:** number

**Default:** Indicates the compatible version number of the bundle

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework

## cpuAbi

```TypeScript
readonly cpuAbi: string
```

CPU and ABI information of the bundle.

**Type:** string

**Default:** Indicates the cpuAbi information of this bundle.

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework

## entryInstallationFree

```TypeScript
readonly entryInstallationFree: boolean
```

Whether installation-free is supported for the entry module. **true** if supported, **false** otherwise.

**Type:** boolean

**Default:** Indicates whether free installation of the entry is supported

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework

## entryModuleName

```TypeScript
readonly entryModuleName: string
```

Name of the entry module.

**Type:** string

**Default:** Indicates entry module name

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework

## hapModuleInfos

```TypeScript
readonly hapModuleInfos: Array<HapModuleInfo>
```

Module configuration information.

**Type:** Array&lt;[HapModuleInfo](arkts-ability-hapmoduleinfo-hapmoduleinfo-depr-i.md)&gt;

**Default:** Obtains configuration information about a module

**Since:** 7

**Deprecated since:** 9

**Substitutes:** hapModulesInfo

**System capability:** SystemCapability.BundleManager.BundleFramework

## installTime

```TypeScript
readonly installTime: number
```

Time when the HAP file was installed.

**Type:** number

**Default:** Indicates the hap install time

**Since:** 7

**Deprecated since:** 9

**Substitutes:** installTime

**System capability:** SystemCapability.BundleManager.BundleFramework

## isCompressNativeLibs

```TypeScript
readonly isCompressNativeLibs: boolean
```

Whether the native libraries in the bundle are compressed. **true** if compressed, **false** otherwise.

**Type:** boolean

**Default:** Indicates is compress native libs

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework

## isSilentInstallation

```TypeScript
readonly isSilentInstallation: string
```

Whether the application can be installed in silent mode.

**Type:** string

**Default:** Indicates is silent installation

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework

## minCompatibleVersionCode

```TypeScript
readonly minCompatibleVersionCode: number
```

Earliest version compatible with the bundle in the distributed scenario.

**Type:** number

**Default:** Indicates the earliest historical version compatible with the bundle

**Since:** 7

**Deprecated since:** 9

**Substitutes:** minCompatibleVersionCode

**System capability:** SystemCapability.BundleManager.BundleFramework

## name

```TypeScript
readonly name: string
```

Bundle name.

**Type:** string

**Default:** Indicates the name of this bundle

**Since:** 7

**Deprecated since:** 9

**Substitutes:** name

**System capability:** SystemCapability.BundleManager.BundleFramework

## reqPermissionDetails

```TypeScript
readonly reqPermissionDetails: Array<ReqPermissionDetail>
```

Detailed information of the permissions to request from the system.

The value is obtained by passing in GET_BUNDLE_WITH_REQUESTED_PERMISSION to [bundle.getBundleInfo](arkts-ability-bundle-getbundleinfo-f.md#getbundleinfo-2).

**Type:** Array&lt;[ReqPermissionDetail](arkts-ability-bundleinfo-reqpermissiondetail-depr-i.md)&gt;

**Default:** Indicates the required permissions details defined in file config.json

**Since:** 7

**Deprecated since:** 9

**Substitutes:** reqPermissionDetails

**System capability:** SystemCapability.BundleManager.BundleFramework

## reqPermissions

```TypeScript
readonly reqPermissions: Array<string>
```

Permissions to request from the system for running the application.

The value is obtained by passing in GET_BUNDLE_WITH_REQUESTED_PERMISSION to [bundle.getBundleInfo](arkts-ability-bundle-getbundleinfo-f.md#getbundleinfo-2).

**Type:** Array&lt;string&gt;

**Default:** Indicates the required permissions name defined in file config.json

**Since:** 7

**Deprecated since:** 9

**Substitutes:** permissions

**System capability:** SystemCapability.BundleManager.BundleFramework

## reqPermissionStates

```TypeScript
readonly reqPermissionStates: Array<number>
```

Permission grant state. The value **0** means that the request is successful, and **-1** means the opposite.

**Type:** Array&lt;number&gt;

**Default:** Indicates the grant status of required permissions

**Since:** 8

**Deprecated since:** 9

**Substitutes:** permissionGrantStates

**System capability:** SystemCapability.BundleManager.BundleFramework

## targetVersion

```TypeScript
readonly targetVersion: number
```

Latest SDK version required for running the bundle.

**Type:** number

**Default:** Indicates the target version number of the bundle

**Since:** 7

**Deprecated since:** 9

**Substitutes:** targetVersion

**System capability:** SystemCapability.BundleManager.BundleFramework

## type

```TypeScript
readonly type: string
```

Bundle type.

**Type:** string

**Default:** Indicates the name of this original bundle

**Since:** 7

**Deprecated since:** 9

**Substitutes:** bundleType

**System capability:** SystemCapability.BundleManager.BundleFramework

## uid

```TypeScript
readonly uid: number
```

UID of the application to which the bundle belongs.

**Type:** number

**Default:** Indicates the UID of the application to which this bundle belongs The UID uniquely identifies an application. It is determined by the process and user IDs of the application After an application is installed, its UID remains unchanged unless it is uninstalled and then reinstalled

**Since:** 7

**Deprecated since:** 9

**Substitutes:** uid

**System capability:** SystemCapability.BundleManager.BundleFramework

## updateTime

```TypeScript
readonly updateTime: number
```

Time when the HAP file was updated.

**Type:** number

**Default:** Indicates the hap update time

**Since:** 7

**Deprecated since:** 9

**Substitutes:** updateTime

**System capability:** SystemCapability.BundleManager.BundleFramework

## vendor

```TypeScript
readonly vendor: string
```

Vendor of the bundle.

**Type:** string

**Default:** Describes the bundle vendor

**Since:** 7

**Deprecated since:** 9

**Substitutes:** vendor

**System capability:** SystemCapability.BundleManager.BundleFramework

## versionCode

```TypeScript
readonly versionCode: number
```

Version number of the bundle.

**Type:** number

**Default:** Indicates the version number of the bundle

**Since:** 7

**Deprecated since:** 9

**Substitutes:** versionCode

**System capability:** SystemCapability.BundleManager.BundleFramework

## versionName

```TypeScript
readonly versionName: string
```

Version description of the bundle.

**Type:** string

**Default:** Indicates the text description of the bundle version

**Since:** 7

**Deprecated since:** 9

**Substitutes:** versionName

**System capability:** SystemCapability.BundleManager.BundleFramework
