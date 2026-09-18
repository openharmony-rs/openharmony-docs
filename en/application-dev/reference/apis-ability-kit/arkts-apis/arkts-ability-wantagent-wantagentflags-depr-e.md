# WantAgentFlags

Enumerates flags for using a WantAgent.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [WantAgentFlags](arkts-ability-wantagent-wantagentflags-e.md)

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## ONE_TIME_FLAG

```TypeScript
ONE_TIME_FLAG = 0
```

Indicates that the WantAgent can be used only once. This flag is valid only when OperationType is set to START_ABILITY, START_SERVICE, or SEND_COMMON_EVENT.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [ONE_TIME_FLAG](arkts-ability-wantagent-wantagentflags-e.md#one_time_flag)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## NO_BUILD_FLAG

```TypeScript
NO_BUILD_FLAG
```

Indicates that null is returned if the WantAgent does not exist. This flag is valid only when OperationType is set to START_ABILITY, START_SERVICE, or SEND_COMMON_EVENT.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [NO_BUILD_FLAG](arkts-ability-wantagent-wantagentflags-e.md#no_build_flag)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## CANCEL_PRESENT_FLAG

```TypeScript
CANCEL_PRESENT_FLAG
```

Indicates that the existing WantAgent should be canceled before a new object is generated. This flag is valid only when OperationType is set to START_ABILITY, START_SERVICE, or SEND_COMMON_EVENT.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [CANCEL_PRESENT_FLAG](arkts-ability-wantagent-wantagentflags-e.md#cancel_present_flag)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## UPDATE_PRESENT_FLAG

```TypeScript
UPDATE_PRESENT_FLAG
```

Indicates that the system only replaces the extra data of the existing WantAgent with that of the new object. This flag is valid only when OperationType is set to START_ABILITY, START_SERVICE, or SEND_COMMON_EVENT.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [UPDATE_PRESENT_FLAG](arkts-ability-wantagent-wantagentflags-e.md#update_present_flag)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## CONSTANT_FLAG

```TypeScript
CONSTANT_FLAG
```

Indicates that the created WantAgent should be immutable.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [CONSTANT_FLAG](arkts-ability-wantagent-wantagentflags-e.md#constant_flag)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## REPLACE_ELEMENT

```TypeScript
REPLACE_ELEMENT
```

Indicates that the current value of element can be replaced when the WantAgent is triggered.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [REPLACE_ELEMENT](arkts-ability-wantagent-wantagentflags-e.md#replace_element)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## REPLACE_ACTION

```TypeScript
REPLACE_ACTION
```

Indicates that the current value of action can be replaced when the WantAgent is triggered.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [REPLACE_ACTION](arkts-ability-wantagent-wantagentflags-e.md#replace_action)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## REPLACE_URI

```TypeScript
REPLACE_URI
```

Indicates that the current value of uri can be replaced when the WantAgent is triggered.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [REPLACE_URI](arkts-ability-wantagent-wantagentflags-e.md#replace_uri)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## REPLACE_ENTITIES

```TypeScript
REPLACE_ENTITIES
```

Indicates that the current value of entities can be replaced when the WantAgent is triggered.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [REPLACE_ENTITIES](arkts-ability-wantagent-wantagentflags-e.md#replace_entities)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## REPLACE_BUNDLE

```TypeScript
REPLACE_BUNDLE
```

Indicates that the current value of packageName can be replaced when the WantAgent is triggered.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [REPLACE_BUNDLE](arkts-ability-wantagent-wantagentflags-e.md#replace_bundle)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
