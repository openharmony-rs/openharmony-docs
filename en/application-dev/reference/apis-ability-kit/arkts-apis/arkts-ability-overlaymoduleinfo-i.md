# OverlayModuleInfo

```TypeScript
export interface OverlayModuleInfo
```

The OverlayModuleInfo information can be obtained through [overlay.getOverlayModuleInfo](arkts-ability-overlay-getoverlaymoduleinfo-f.md) to get the OverlayModuleInfo information of the module with the overlay feature in the current application.

**Since:** 10

<!--Device-unnamed-export interface OverlayModuleInfo--><!--Device-unnamed-export interface OverlayModuleInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## bundleName

```TypeScript
readonly bundleName: string
```

Bundle name of the application to which the overlay feature module belongs.

**Type:** string

**Since:** 10

<!--Device-OverlayModuleInfo-readonly bundleName: string--><!--Device-OverlayModuleInfo-readonly bundleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## moduleName

```TypeScript
readonly moduleName: string
```

Name of the overlay feature module.

**Type:** string

**Since:** 10

<!--Device-OverlayModuleInfo-readonly moduleName: string--><!--Device-OverlayModuleInfo-readonly moduleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## priority

```TypeScript
readonly priority: number
```

Priority of the overlay feature module. The value is an integer ranging from 1 to 100. A larger value indicates a higher priority.

**Type:** number

**Since:** 10

<!--Device-OverlayModuleInfo-readonly priority: int--><!--Device-OverlayModuleInfo-readonly priority: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## state

```TypeScript
readonly state: number
```

Enabled or disabled state of the overlay feature module. The value is an integer ranging from 0 to 2, where 0 indicates the disabled state, 1 indicates the enabled state, and 2 indicates the invalid state.

**Type:** number

**Since:** 10

<!--Device-OverlayModuleInfo-readonly state: int--><!--Device-OverlayModuleInfo-readonly state: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## targetModuleName

```TypeScript
readonly targetModuleName: string
```

Name of the target module on which the overlay feature module takes effect, indicating the module whose resources are to be replaced by the current overlay package.

**Type:** string

**Since:** 10

<!--Device-OverlayModuleInfo-readonly targetModuleName: string--><!--Device-OverlayModuleInfo-readonly targetModuleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
