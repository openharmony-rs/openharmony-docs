# OverlayModuleInfo

The module provides information about a module with the overlay feature. An application can obtain such information through [overlay.getOverlayModuleInfo](arkts-ability-overlay-getoverlaymoduleinfo-f.md).

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## bundleName

```TypeScript
readonly bundleName: string
```

Bundle name of the application to which the module with the overlay feature belongs.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## moduleName

```TypeScript
readonly moduleName: string
```

Name of the module with the overlay feature.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## priority

```TypeScript
readonly priority: number
```

Priority of the module with the overlay feature. The value is an integer ranging from 1 to 100. A larger value indicates a higher priority.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## state

```TypeScript
readonly state: number
```

Whether the module with the overlay feature is [disabled](arkts-ability-overlay-setoverlayenabled-f.md). The value **0** means that the module with the overlay feature is disabled, and **1** means the opposite.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## targetModuleName

```TypeScript
readonly targetModuleName: string
```

Name of the target module specified by the overlay feature, that is, the name of the module whose resources are to be replaced by the overlay package.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
