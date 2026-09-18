# Flags

Enumerates the flags that specify how the Want will be handled.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [Flags](arkts-ability-wantconstant-flags-e.md)

**System capability:** SystemCapability.Ability.AbilityBase

## FLAG_AUTH_READ_URI_PERMISSION

```TypeScript
FLAG_AUTH_READ_URI_PERMISSION = 0x00000001
```

Grants the permission to read the URI.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [FLAG_AUTH_READ_URI_PERMISSION](arkts-ability-wantconstant-flags-e.md#flag_auth_read_uri_permission)

**System capability:** SystemCapability.Ability.AbilityBase

## FLAG_AUTH_WRITE_URI_PERMISSION

```TypeScript
FLAG_AUTH_WRITE_URI_PERMISSION = 0x00000002
```

Grants the permission to write data to the URI.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [FLAG_AUTH_WRITE_URI_PERMISSION](arkts-ability-wantconstant-flags-e.md#flag_auth_write_uri_permission)

**System capability:** SystemCapability.Ability.AbilityBase

## FLAG_ABILITY_FORWARD_RESULT

```TypeScript
FLAG_ABILITY_FORWARD_RESULT = 0x00000004
```

Returns the result to the ability.

**Since:** 6

**Deprecated since:** 9

**System capability:** SystemCapability.Ability.AbilityBase

## FLAG_ABILITY_CONTINUATION

```TypeScript
FLAG_ABILITY_CONTINUATION = 0x00000008
```

Indicates whether the ability on the local device can be continued on a remote device.

**Since:** 6

**Deprecated since:** 9

**System capability:** SystemCapability.Ability.AbilityBase

## FLAG_NOT_OHOS_COMPONENT

```TypeScript
FLAG_NOT_OHOS_COMPONENT = 0x00000010
```

Indicates that a component does not belong to OHOS.

**Since:** 6

**Deprecated since:** 9

**System capability:** SystemCapability.Ability.AbilityBase

## FLAG_ABILITY_FORM_ENABLED

```TypeScript
FLAG_ABILITY_FORM_ENABLED = 0x00000020
```

Indicates that an ability is enabled.

**Since:** 6

**Deprecated since:** 9

**System capability:** SystemCapability.Ability.AbilityBase

## FLAG_ABILITYSLICE_MULTI_DEVICE

```TypeScript
FLAG_ABILITYSLICE_MULTI_DEVICE = 0x00000100
```

Indicates the support for cross-device startup in the distributed scheduler.

**Since:** 6

**Deprecated since:** 9

**System capability:** SystemCapability.Ability.AbilityBase

## FLAG_START_FOREGROUND_ABILITY

```TypeScript
FLAG_START_FOREGROUND_ABILITY = 0x00000200
```

Indicates that the ServiceAbility is started regardless of whether the host application has been started.

**Since:** 6

**Deprecated since:** 9

**System capability:** SystemCapability.Ability.AbilityBase

## FLAG_INSTALL_ON_DEMAND

```TypeScript
FLAG_INSTALL_ON_DEMAND = 0x00000800
```

Indicates that the specific ability will be installed if it has not been installed.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [FLAG_INSTALL_ON_DEMAND](arkts-ability-wantconstant-flags-e.md#flag_install_on_demand)

**System capability:** SystemCapability.Ability.AbilityBase

## FLAG_INSTALL_WITH_BACKGROUND_MODE

```TypeScript
FLAG_INSTALL_WITH_BACKGROUND_MODE = 0x80000000
```

Indicates that the specific ability will be installed in the background if it has not been installed.

**Since:** 6

**Deprecated since:** 9

**System capability:** SystemCapability.Ability.AbilityBase

## FLAG_ABILITY_CLEAR_MISSION

```TypeScript
FLAG_ABILITY_CLEAR_MISSION = 0x00008000
```

Clears other operation missions. This flag can be set for the Want passed in [startAbility](arkts-ability-featureability-startability-f.md). It must be used together with **FLAG_ABILITY_NEW_MISSION**.

**Since:** 6

**Deprecated since:** 9

**System capability:** SystemCapability.Ability.AbilityBase

## FLAG_ABILITY_NEW_MISSION

```TypeScript
FLAG_ABILITY_NEW_MISSION = 0x10000000
```

Creates a mission on the history mission stack.

**Since:** 6

**Deprecated since:** 9

**System capability:** SystemCapability.Ability.AbilityBase

## FLAG_ABILITY_MISSION_TOP

```TypeScript
FLAG_ABILITY_MISSION_TOP = 0x20000000
```

Reuses an ability instance if it is on the top of an existing mission stack; creates an ability instance otherwise.

**Since:** 6

**Deprecated since:** 9

**System capability:** SystemCapability.Ability.AbilityBase
