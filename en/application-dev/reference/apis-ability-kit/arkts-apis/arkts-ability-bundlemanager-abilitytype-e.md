# AbilityType

```TypeScript
export enum AbilityType
```

Enumerates the types of ability components.

**Since:** 9

<!--Device-bundleManager-export enum AbilityType--><!--Device-bundleManager-export enum AbilityType-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## DATA

```TypeScript
DATA = 3
```

It represents a [ParticleAbility](arkts-ability-ability-particleability.md) developed based on the Data template, used to provide a unified data access object to the outside.

**Since:** 9

**Model restriction:** This API can be used only in the FA model.

<!--Device-AbilityType-DATA = 3--><!--Device-AbilityType-DATA = 3-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## PAGE

```TypeScript
PAGE = 1
```

Ability that has the UI. FA developed using the Page template to provide the capability of interacting with users.

**Since:** 9

**Model restriction:** This API can be used only in the FA model.

<!--Device-AbilityType-PAGE = 1--><!--Device-AbilityType-PAGE = 1-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## SERVICE

```TypeScript
SERVICE = 2
```

Ability of the background service type, without a UI. It represents a [ParticleAbility](arkts-ability-ability-particleability.md) developed based on the Service template, used to provide the capability of running background tasks, such as background download or music playback.

**Since:** 9

**Model restriction:** This API can be used only in the FA model.

<!--Device-AbilityType-SERVICE = 2--><!--Device-AbilityType-SERVICE = 2-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
