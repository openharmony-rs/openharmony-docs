# WantAgentInfo

```TypeScript
export interface WantAgentInfo
```

Defines the information required for triggering a WantAgent object. The information can be used as an input parameter in [getWantAgent](../../../reference/apis-ability-kit/js-apis-app-ability-wantAgent.md#wantagentgetwantagent) to obtain a specified WantAgent object.

**Since:** 7

<!--Device-unnamed-export interface WantAgentInfo--><!--Device-unnamed-export interface WantAgentInfo-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## actionFlags

```TypeScript
actionFlags?: Array<abilityWantAgent.WantAgentFlags>
```

Array of flags for using the WantAgent object.

**Type:** Array&lt;[abilityWantAgent.WantAgentFlags](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-wantagent.md)&gt;

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WantAgentInfo-actionFlags?: Array<abilityWantAgent.WantAgentFlags>--><!--Device-WantAgentInfo-actionFlags?: Array<abilityWantAgent.WantAgentFlags>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## actionType

```TypeScript
actionType?: abilityWantAgent.OperationType
```

Action execution attribute. If this parameter is not set, no execution attribute is used.

**Type:** [abilityWantAgent.OperationType](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-wantagent.md)

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WantAgentInfo-actionType?: abilityWantAgent.OperationType--><!--Device-WantAgentInfo-actionType?: abilityWantAgent.OperationType-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## extraInfo

```TypeScript
extraInfo?: { [key: string]: any }
```

Extra data used to pass custom extended information. This parameter is a key-value pair object, where key is a string key name and value is a value of any type. You are advised to use the type-safe extraInfos attribute instead. If both extraInfo and extraInfos are set, extraInfos takes effect and extraInfo is ignored.

**Type:** { [key: string]: any }

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WantAgentInfo-extraInfo?: { [key: string]: any }--><!--Device-WantAgentInfo-extraInfo?: { [key: string]: any }-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## extraInfos

```TypeScript
extraInfos?: Record<string, Object>
```

Extra data used to pass custom key-value pair information in a type-safe manner. You are advised to use this attribute instead of extraInfo. When both are set, this attribute takes precedence. Pass this parameter when you need to carry additional custom data when triggering the WantAgent. If this parameter is not passed, it defaults to null and no extra data is carried.

**Type:** Record&lt;string, Object&gt;

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WantAgentInfo-extraInfos?: Record<string, Object>--><!--Device-WantAgentInfo-extraInfos?: Record<string, Object>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## requestCode

```TypeScript
requestCode: number
```

Request code defined by the developer, used to identify the action to be executed.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WantAgentInfo-requestCode: int--><!--Device-WantAgentInfo-requestCode: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## wants

```TypeScript
wants: Array<Want>
```

The wants array is a reserved capability. Currently, only one want is supported. If multiple wants are passed in, only the first member of the wants array is used.

**Type:** Array&lt;[Want](arkts-ability-app-ability-want-want-c.md)&gt;

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WantAgentInfo-wants: Array<Want>--><!--Device-WantAgentInfo-wants: Array<Want>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## operationType

```TypeScript
operationType?: wantAgent.OperationType
```

Operation type. If this parameter is not set, no default operation type is used.

This attribute is supported since API version 7 and deprecated since API version 11. You are advised to use actionType<sup>11+</sup> instead.

**Type:** [wantAgent.OperationType](arkts-ability-wantagent-operationtype-depr-e.md)

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [actionType](#actiontype)

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WantAgentInfo-operationType?: wantAgent.OperationType--><!--Device-WantAgentInfo-operationType?: wantAgent.OperationType-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## wantAgentFlags

```TypeScript
wantAgentFlags?: Array<wantAgent.WantAgentFlags>
```

Action execution attribute. If this parameter is not set, no execution attribute is used.

This attribute is supported since API version 7 and deprecated since API version 11. You are advised to use actionFlags<sup>11+</sup> instead.

**Type:** Array&lt;[wantAgent.WantAgentFlags](arkts-ability-wantagent-wantagentflags-depr-e.md)&gt;

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [actionFlags](#actionflags)

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WantAgentInfo-wantAgentFlags?: Array<wantAgent.WantAgentFlags>--><!--Device-WantAgentInfo-wantAgentFlags?: Array<wantAgent.WantAgentFlags>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
