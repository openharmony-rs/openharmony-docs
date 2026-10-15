# WantAgentFlags

```TypeScript
export enum WantAgentFlags
```

Enumerates flags for using a WantAgent.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [WantAgentFlags](arkts-ability-wantagent-wantagentflags-e.md)

<!--Device-wantAgent-export enum WantAgentFlags--><!--Device-wantAgent-export enum WantAgentFlags-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## CANCEL_PRESENT_FLAG

```TypeScript
CANCEL_PRESENT_FLAG
```

The existing WantAgent object should be canceled before a new object is generated.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [CANCEL_PRESENT_FLAG](arkts-ability-wantagent-wantagentflags-e.md#cancel_present_flag)

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WantAgentFlags-CANCEL_PRESENT_FLAG--><!--Device-WantAgentFlags-CANCEL_PRESENT_FLAG-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## CONSTANT_FLAG

```TypeScript
CONSTANT_FLAG
```

The WantAgent object is immutable.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [CONSTANT_FLAG](arkts-ability-wantagent-wantagentflags-e.md#constant_flag)

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WantAgentFlags-CONSTANT_FLAG--><!--Device-WantAgentFlags-CONSTANT_FLAG-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## NO_BUILD_FLAG

```TypeScript
NO_BUILD_FLAG
```

The WantAgent object does not exist and hence it is not created. In this case, null is returned.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [NO_BUILD_FLAG](arkts-ability-wantagent-wantagentflags-e.md#no_build_flag)

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WantAgentFlags-NO_BUILD_FLAG--><!--Device-WantAgentFlags-NO_BUILD_FLAG-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## ONE_TIME_FLAG

```TypeScript
ONE_TIME_FLAG = 0
```

The WantAgent object can be used only once.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [ONE_TIME_FLAG](arkts-ability-wantagent-wantagentflags-e.md#one_time_flag)

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WantAgentFlags-ONE_TIME_FLAG = 0--><!--Device-WantAgentFlags-ONE_TIME_FLAG = 0-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## REPLACE_ACTION

```TypeScript
REPLACE_ACTION
```

The action property in the current Want can be replaced by the action property in the Want passed in WantAgent.trigger().

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [REPLACE_ACTION](arkts-ability-wantagent-wantagentflags-e.md#replace_action)

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WantAgentFlags-REPLACE_ACTION--><!--Device-WantAgentFlags-REPLACE_ACTION-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## REPLACE_BUNDLE

```TypeScript
REPLACE_BUNDLE
```

The bundleName property in the current Want can be replaced by the bundleName property in the Want passed in WantAgent.trigger().

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [REPLACE_BUNDLE](arkts-ability-wantagent-wantagentflags-e.md#replace_bundle)

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WantAgentFlags-REPLACE_BUNDLE--><!--Device-WantAgentFlags-REPLACE_BUNDLE-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## REPLACE_ELEMENT

```TypeScript
REPLACE_ELEMENT
```

The element property in the current Want can be replaced by the element property in the Want passed in WantAgent.trigger().

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [REPLACE_ELEMENT](arkts-ability-wantagent-wantagentflags-e.md#replace_element)

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WantAgentFlags-REPLACE_ELEMENT--><!--Device-WantAgentFlags-REPLACE_ELEMENT-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## REPLACE_ENTITIES

```TypeScript
REPLACE_ENTITIES
```

The entities property in the current Want can be replaced by the entities property in the Want passed in WantAgent.trigger().

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [REPLACE_ENTITIES](arkts-ability-wantagent-wantagentflags-e.md#replace_entities)

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WantAgentFlags-REPLACE_ENTITIES--><!--Device-WantAgentFlags-REPLACE_ENTITIES-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## REPLACE_URI

```TypeScript
REPLACE_URI
```

The uri property in the current Want can be replaced by the uri property in the Want passed in WantAgent.trigger().

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [REPLACE_URI](arkts-ability-wantagent-wantagentflags-e.md#replace_uri)

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WantAgentFlags-REPLACE_URI--><!--Device-WantAgentFlags-REPLACE_URI-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## UPDATE_PRESENT_FLAG

```TypeScript
UPDATE_PRESENT_FLAG
```

Extra information of the existing WantAgent object is replaced with that of the new object.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [UPDATE_PRESENT_FLAG](arkts-ability-wantagent-wantagentflags-e.md#update_present_flag)

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WantAgentFlags-UPDATE_PRESENT_FLAG--><!--Device-WantAgentFlags-UPDATE_PRESENT_FLAG-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
