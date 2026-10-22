# TriggerInfo

```TypeScript
export interface TriggerInfo
```

The module defines the information required for triggering the WantAgent. The information is used as an input parameter of [trigger](../../../reference/apis-ability-kit/js-apis-app-ability-wantAgent.md#wantagenttrigger).

**Since:** 7

<!--Device-unnamed-export interface TriggerInfo--><!--Device-unnamed-export interface TriggerInfo-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## code

```TypeScript
code: number
```

Common event code to pass. This field takes effect only when the [OperationType](arkts-ability-wantagent-operationtype-e.md) of the WantAgent instance is'SEND_COMMON_EVENT'. It has the same meaning as the code field in the [CommonEventPublishData](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-commoneventpublishdata-i.md) passed by the publisher when publishing a common event through [commonEventManager.publish](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-commoneventmanager-publish-f.md#publish-2). The value is determined by the common event type.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TriggerInfo-code: int--><!--Device-TriggerInfo-code: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## extraInfo

```TypeScript
extraInfo?: { [key: string]: any }
```

Extra data used to pass custom extension information. The parameter is a key-value pair object, where the key is a string and the value can be of any type. You are advised to use the type-safe extraInfos attribute instead. If both extraInfo and extraInfos are set, extraInfos takes effect and extraInfo is ignored.

**Type:** { [key: string]: any }

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TriggerInfo-extraInfo?: { [key: string]: any }--><!--Device-TriggerInfo-extraInfo?: { [key: string]: any }-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## extraInfos

```TypeScript
extraInfos?: Record<string, Object>
```

Extra data used to pass custom key-value pair information in a type-safe manner. You are advised to use this attribute instead of extraInfo. When both are set, this attribute takes precedence. Pass this parameter when you need to carry additional custom data when triggering the WantAgent. If it is not passed, the default value is null and no extra data is carried.

**Type:** Record&lt;string, Object&gt;

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TriggerInfo-extraInfos?: Record<string, Object>--><!--Device-TriggerInfo-extraInfos?: Record<string, Object>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## permission

```TypeScript
permission?: string
```

Permission of the common event subscriber. This field takes effect only when the [OperationType](arkts-ability-wantagent-operationtype-e.md) of the WantAgent instance is'SEND_COMMON_EVENT'. If the permission is null, the receiver does not need any permission.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TriggerInfo-permission?: string--><!--Device-TriggerInfo-permission?: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## want

```TypeScript
want?: Want
```

Carrier for information transfer between objects (application components).

**Type:** [Want](arkts-ability-app-ability-want-want-c.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TriggerInfo-want?: Want--><!--Device-TriggerInfo-want?: Want-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
