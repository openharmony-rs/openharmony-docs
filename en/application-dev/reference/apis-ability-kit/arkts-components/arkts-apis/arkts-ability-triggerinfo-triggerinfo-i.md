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

Common event code. This field is valid only when [OperationType](../../../reference/apis-ability-kit/js-apis-app-ability-wantAgent.md#operationtype) of the WantAgent instance is **'SEND_COMMON_EVENT'**. The meaning of this field is the same as that of the **code** field set in [CommonEventPublishData](../../../reference/apis-basic-services-kit/js-apis-inner-commonEvent-commonEventPublishData.md#properties) when the publisher uses [commonEventManager.publish](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-commoneventmanager-publish-f.md#publish-1) to publish common events.

**Type:** number

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-TriggerInfo-code: int--><!--Device-TriggerInfo-code: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## extraInfo

```TypeScript
extraInfo?: { [key: string]: any }
```

Extra information.

**Type:** { [key: string]: any }

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TriggerInfo-extraInfo?: { [key: string]: any }--><!--Device-TriggerInfo-extraInfo?: { [key: string]: any }-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## extraInfos

```TypeScript
extraInfos?: Record<string, Object>
```

Extra information. You are advised to use this property to replace **extraInfo**. When this property is set, **extraInfo** does not take effect.

**Type:** Record&lt;string, Object&gt;

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TriggerInfo-extraInfos?: Record<string, Object>--><!--Device-TriggerInfo-extraInfos?: Record<string, Object>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## permission

```TypeScript
permission?: string
```

Permission required for a subscriber to receive the common event. This field is valid only when [OperationType](../../../reference/apis-ability-kit/js-apis-app-ability-wantAgent.md#operationtype) of the WantAgent instance is **'SEND_COMMON_EVENT'**.

**Type:** string

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-TriggerInfo-permission?: string--><!--Device-TriggerInfo-permission?: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## want

```TypeScript
want?: Want
```

Carrier for information transfer between objects (application components).

**Type:** [Want](arkts-ability-app-ability-want-want-c.md)

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-TriggerInfo-want?: Want--><!--Device-TriggerInfo-want?: Want-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
