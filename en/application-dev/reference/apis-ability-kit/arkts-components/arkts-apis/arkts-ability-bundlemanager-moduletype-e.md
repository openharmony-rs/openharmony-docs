# ModuleType

```TypeScript
export enum ModuleType
```

Enumerates the module types.

**Since:** 9

<!--Device-bundleManager-export enum ModuleType--><!--Device-bundleManager-export enum ModuleType-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## ENTRY

```TypeScript
ENTRY = 1
```

Main module of and entry to the application, providing the basic application functionality.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ModuleType-ENTRY = 1--><!--Device-ModuleType-ENTRY = 1-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## FEATURE

```TypeScript
FEATURE = 2
```

Dynamic feature module of the application, extending the application functionality. This type of HAP can be installed based on user needs and device types.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ModuleType-FEATURE = 2--><!--Device-ModuleType-FEATURE = 2-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## SHARED

```TypeScript
SHARED = 3
```

[Dynamic shared library](../../../quick-start/in-app-hsp.md) of the application.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ModuleType-SHARED = 3--><!--Device-ModuleType-SHARED = 3-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
