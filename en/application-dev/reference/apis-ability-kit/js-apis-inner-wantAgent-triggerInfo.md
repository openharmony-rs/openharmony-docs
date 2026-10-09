# TriggerInfo

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=b3bc27a342923ac4fafa55153b55c4f3b627330f translatedAt=2026-09-03T12:21:27.129Z pushedAt=2026-09-05T10:47:30.903Z -->

As an input parameter of [trigger](js-apis-app-ability-wantAgent.md#wantagenttrigger), defines the information required for executing a WantAgent.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { wantAgent } from '@kit.AbilityKit';
```

## Properties

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name      | Type                | Read-Only| Optional| Description       |
| ---------- | ------------------- | ---- | ---- | ----------- |
| code       | number               | No | No | Common event code to pass. This field takes effect only when the [OperationType](js-apis-app-ability-wantAgent.md#operationtype) of the WantAgent instance is 'SEND_COMMON_EVENT'. It has the same meaning as the `code` field in the [CommonEventPublishData](../../reference/apis-basic-services-kit/js-apis-inner-commonEvent-commonEventPublishData.md) passed by the publisher when publishing a common event through [commonEventManager.publish](../../reference/apis-basic-services-kit/js-apis-commonEventManager.md#commoneventmanagerpublish-1). The value is determined by the common event type. |
| want       | [Want](./js-apis-app-ability-want.md)                 | No| Yes| Carrier for information transfer between objects (application components).   |
| permission | string               | No | Yes | Permission of the common event subscriber. This field takes effect only when the [OperationType](js-apis-app-ability-wantAgent.md#operationtype) of the WantAgent instance is 'SEND_COMMON_EVENT'. If the permission is null, the receiver does not need any permission.   |
| extraInfo  | { [key: string]: any } | No | Yes | Extra data used to pass custom extension information. The parameter is a key-value pair object, where the key is a string and the value can be of any type. You are advised to use the type-safe extraInfos attribute instead. If both extraInfo and extraInfos are set, extraInfos takes effect and extraInfo is ignored. |
| extraInfos<sup>11+</sup>  | Record\<string, Object> | No | Yes | Extra data used to pass custom key-value pair information in a type-safe manner. You are advised to use this attribute instead of extraInfo. When both are set, this attribute takes precedence. Pass this parameter when you need to carry additional custom data when triggering the WantAgent. If it is not passed, the default value is null and no extra data is carried. |