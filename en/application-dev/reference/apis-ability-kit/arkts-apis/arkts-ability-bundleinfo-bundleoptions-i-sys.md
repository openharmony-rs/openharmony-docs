# BundleOptions (System API)

```TypeScript
export interface BundleOptions
```

Describes the bundle options used to set or query application information.

**Since:** 20

<!--Device-unnamed-export interface BundleOptions--><!--Device-unnamed-export interface BundleOptions-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## abilityName

```TypeScript
abilityName?: string
```

Ability name. Default Value: Empty String.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleOptions-abilityName?: string--><!--Device-BundleOptions-abilityName?: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## appIndex

```TypeScript
appIndex?: number
```

Index of an application clone. The default value is **0**, indicating the main application.

**Type:** number

**Since:** 20

<!--Device-BundleOptions-appIndex?: int--><!--Device-BundleOptions-appIndex?: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## bundleName

```TypeScript
bundleName?: string
```

Application bundle name. Default Value: Empty String.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleOptions-bundleName?: string--><!--Device-BundleOptions-bundleName?: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## moduleName

```TypeScript
moduleName?: string
```

Name of the module to which the ability belongs. Default Value: Empty String.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleOptions-moduleName?: string--><!--Device-BundleOptions-moduleName?: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## userId

```TypeScript
userId?: number
```

User ID. By default, the user is the current caller.

**Type:** number

**Since:** 20

<!--Device-BundleOptions-userId?: int--><!--Device-BundleOptions-userId?: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
