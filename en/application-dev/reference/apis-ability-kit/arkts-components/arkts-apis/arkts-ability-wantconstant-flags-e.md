# Flags

Enumerates the common preset keywords of the [Want.flags](arkts-ability-app-ability-want-want-c.md) field. You can use these predefined keywords to set or retrieve additional flag information carried in application transitions.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityBase

## FLAG_AUTH_READ_URI_PERMISSION

```TypeScript
FLAG_AUTH_READ_URI_PERMISSION = 0x00000001
```

Temporarily grants the receiver read permission for the URI.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## FLAG_AUTH_WRITE_URI_PERMISSION

```TypeScript
FLAG_AUTH_WRITE_URI_PERMISSION = 0x00000002
```

Temporarily grants the receiver write permission for the URI.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## FLAG_AUTH_PERSISTABLE_URI_PERMISSION

```TypeScript
FLAG_AUTH_PERSISTABLE_URI_PERMISSION = 0x00000040
```

The URI can be persisted by the receiver. It takes effect only on 2-in-1 devices and tablets.

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityBase

## FLAG_INSTALL_ON_DEMAND

```TypeScript
FLAG_INSTALL_ON_DEMAND = 0x00000800
```

Enables on-demand installation when launching an atomic service.

- If enabled, the system automatically installs the atomic service if it is not already installed before  
proceeding with the launch.  
- If disabled, the launch fails if the atomic service is not installed.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## FLAG_ABILITY_ON_COLLABORATE

```TypeScript
FLAG_ABILITY_ON_COLLABORATE = 0x00002000
```

In multi-device collaboration scenario, the caller application must initiate a request through the DMS, with this flag included in the **Flags** field, in order to invoke the lifecycle callback [onCollaborate()](arkts-ability-app-ability-uiability-uiability-c.md#oncollaborate) of the target application.

**Since:** 18

**System capability:** SystemCapability.Ability.AbilityBase

## FLAG_START_WITHOUT_TIPS

```TypeScript
FLAG_START_WITHOUT_TIPS = 0x40000000
```

Disables the "No available applications" prompt during implicit application launches.

When [launching an application implicitly](../../../application-models/app-startup-overview.md), a prompt saying "No available applications" will appear if no matching application is found. You can use this flag to prevent this prompt from appearing.

**Since:** 11

**System capability:** SystemCapability.Ability.AbilityBase
