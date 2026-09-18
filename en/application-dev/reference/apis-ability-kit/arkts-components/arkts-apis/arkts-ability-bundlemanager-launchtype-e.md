# LaunchType

Enumerates the [launch types](../../../application-models/uiability-launch-type.md) of the UIAbility.

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## SINGLETON

```TypeScript
SINGLETON = 0
```

The UIAbility can have only one instance.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## MULTITON

```TypeScript
MULTITON = 1
```

The UIAbility can have multiple instances.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## SPECIFIED

```TypeScript
SPECIFIED = 2
```

The UIAbility can have one or multiple instances, depending on the internal service of the ability.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
