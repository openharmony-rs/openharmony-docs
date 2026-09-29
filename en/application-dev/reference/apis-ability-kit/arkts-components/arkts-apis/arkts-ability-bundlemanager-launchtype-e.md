# LaunchType

```TypeScript
export enum LaunchType
```

Enumerates the [launch types](../../../application-models/uiability-launch-type.md) of the UIAbility.

**Since:** 9

<!--Device-bundleManager-export enum LaunchType--><!--Device-bundleManager-export enum LaunchType-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## SINGLETON

```TypeScript
SINGLETON = 0
```

The UIAbility can have only one instance.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-LaunchType-SINGLETON = 0--><!--Device-LaunchType-SINGLETON = 0-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## MULTITON

```TypeScript
MULTITON = 1
```

The UIAbility can have multiple instances.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-LaunchType-MULTITON = 1--><!--Device-LaunchType-MULTITON = 1-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## SPECIFIED

```TypeScript
SPECIFIED = 2
```

The UIAbility can have one or multiple instances, depending on the internal service of the ability.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-LaunchType-SPECIFIED = 2--><!--Device-LaunchType-SPECIFIED = 2-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
