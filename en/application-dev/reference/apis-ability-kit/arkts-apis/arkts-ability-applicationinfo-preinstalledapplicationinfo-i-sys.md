# PreinstalledApplicationInfo (System API)

```TypeScript
export interface PreinstalledApplicationInfo
```

Indicates the information of preinstalled application.

**Since:** 12

<!--Device-unnamed-export interface PreinstalledApplicationInfo--><!--Device-unnamed-export interface PreinstalledApplicationInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## bundleName

```TypeScript
readonly bundleName: string
```

Name of the application package.

**Type:** string

**Since:** 12

<!--Device-PreinstalledApplicationInfo-readonly bundleName: string--><!--Device-PreinstalledApplicationInfo-readonly bundleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## descriptionId

```TypeScript
readonly descriptionId?: number
```

App description ID.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-PreinstalledApplicationInfo-readonly descriptionId?: long--><!--Device-PreinstalledApplicationInfo-readonly descriptionId?: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## iconId

```TypeScript
readonly iconId: number
```

Application icon ID.

**Type:** number

**Since:** 12

<!--Device-PreinstalledApplicationInfo-readonly iconId: long--><!--Device-PreinstalledApplicationInfo-readonly iconId: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## labelId

```TypeScript
readonly labelId: number
```

Application label ID.

**Type:** number

**Since:** 12

<!--Device-PreinstalledApplicationInfo-readonly labelId: long--><!--Device-PreinstalledApplicationInfo-readonly labelId: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## moduleName

```TypeScript
readonly moduleName: string
```

Module name of the application package. Returns the moduleName of the entry module. If no entry module exists, returns the moduleName of the feature module.

**Type:** string

**Since:** 12

<!--Device-PreinstalledApplicationInfo-readonly moduleName: string--><!--Device-PreinstalledApplicationInfo-readonly moduleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
