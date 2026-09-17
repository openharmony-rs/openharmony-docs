# WantAgentInfo

Defines the information required for triggering a WantAgent object. The information can be used as an input parameter in [getWantAgent](../../../reference/apis-ability-kit/js-apis-app-ability-wantAgent.md#wantagentgetwantagent) to obtain a specified WantAgent object.

**Since:** 7

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## actionFlags

```TypeScript
actionFlags?: Array<abilityWantAgent.WantAgentFlags>
```

Array of flags for using the WantAgent object.

**Type:** Array&lt;[abilityWantAgent.WantAgentFlags](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-wantagent.md)&gt;

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## actionType

```TypeScript
actionType?: abilityWantAgent.OperationType
```

Operation type.

**Type:** [abilityWantAgent.OperationType](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-wantagent.md)

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## extraInfo

```TypeScript
extraInfo?: { [key: string]: any }
```

Extra information.

**Type:** { [key: string]: any }

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## extraInfos

```TypeScript
extraInfos?: Record<string, Object>
```

Extra information. You are advised to use this property to replace **extraInfo**. When this property is set, **extraInfo** does not take effect.

**Type:** Record&lt;string, Object&gt;

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## operationType

```TypeScript
operationType?: wantAgent.OperationType
```

Operation type.

This attribute is supported since API version 7 and deprecated since API version 11. You are advised to use actionType&lt;sup&gt;11+&lt;/sup&gt; instead.

**Type:** [wantAgent.OperationType](arkts-ability-wantagent-operationtype-depr-e.md)

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [actionType](#actiontype)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## requestCode

```TypeScript
requestCode: number
```

Custom request code, which is used to identify the operation to execute.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## wantAgentFlags

```TypeScript
wantAgentFlags?: Array<wantAgent.WantAgentFlags>
```

Array of flags for using the WantAgent object.

This attribute is supported since API version 7 and deprecated since API version 11. You are advised to use actionFlags&lt;sup&gt;11+&lt;/sup&gt; instead.

**Type:** Array&lt;[wantAgent.WantAgentFlags](arkts-ability-wantagent-wantagentflags-depr-e.md)&gt;

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [actionFlags](#actionflags)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## wants

```TypeScript
wants: Array<Want>
```

Array of all Want objects. Currently, only one Want is supported. The array is reserved for future capability expansion. If multiple values are passed in, only the first member in the array is used.

**Type:** Array&lt;[Want](arkts-ability-app-ability-want-want-c.md)&gt;

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
