# AbilityStateData

The AbilityStateData module defines a struct for ability state information. Once a lifecycle change listener is registered using [on](arkts-ability-appmanager-on-f.md#onapplicationstate), you can obtain an instance of this struct from the input parameter of the **onAbilityStateChanged** callback of ApplicationStateObserver.

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## abilityName

```TypeScript
abilityName: string
```

Ability name.

**Type:** string

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## abilityType

```TypeScript
abilityType: number
```

[Ability type](../../../reference/apis-ability-kit/js-apis-inner-application-abilityStateData.md#ability-types), which can be [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) or [ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md).

**Type:** number

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## appCloneIndex

```TypeScript
appCloneIndex?: number
```

Index of an [application clone](../../../quick-start/app-clone.md).

**Type:** number

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## bundleName

```TypeScript
bundleName: string
```

Bundle name.

**Type:** string

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## callerBundleName

```TypeScript
callerBundleName?: string
```

Bundle name of the application that triggers the creation of the ability.

**Type:** string

**Since:** 23

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## isAtomicService

```TypeScript
isAtomicService: boolean
```

Whether the ability belongs to an atomic service.

**true**: The ability belongs to an atomic service.

**false**: The ability does not belong to an atomic service.

**Type:** boolean

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## moduleName

```TypeScript
moduleName: string
```

Module name to which the ability belongs.

**Type:** string

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## pid

```TypeScript
pid: number
```

Process ID.

**Type:** number

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## state

```TypeScript
state: number
```

Ability state.

- [Stage model](../../../application-models/ability-terminology.md#stage-model): For the [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md), see [UIAbility States](../../../reference/apis-ability-kit/js-apis-inner-application-abilityStateData.md#uiability-states). For the [ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md), see [ExtensionAbility States](../../../reference/apis-ability-kit/js-apis-inner-application-abilityStateData.md#extensionability-states). For the [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md), see [UIExtensionAbility States](../../../reference/apis-ability-kit/js-apis-inner-application-abilityStateData.md#uiextensionability-states).  
- [FA model](../../../application-models/ability-terminology.md#fa-model): For the ability, see [Ability States](../../../reference/apis-ability-kit/js-apis-inner-application-abilityStateData.md#ability-states).

**Type:** number

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## uid

```TypeScript
uid: number
```

UID of the application.

**Type:** number

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
