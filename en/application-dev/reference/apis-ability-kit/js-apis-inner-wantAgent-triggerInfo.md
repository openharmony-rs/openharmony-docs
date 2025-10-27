# TriggerInfo

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

The module defines the information required for triggering the WantAgent. The information is used as an input parameter of [trigger](js-apis-app-ability-wantAgent.md#wantagenttrigger).

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
| code       | number               | No| No| Common event code. This field is valid only when [OperationType](js-apis-app-ability-wantAgent.md#operationtype) of the WantAgent instance is **'SEND_COMMON_EVENT'**. The meaning of this field is the same as that of the **code** field set in [CommonEventPublishData](../../reference/apis-basic-services-kit/js-apis-inner-commonEvent-commonEventPublishData.md#properties) when the publisher uses [commonEventManager.publish](../../reference/apis-basic-services-kit/js-apis-commonEventManager.md#commoneventmanagerpublish-1) to publish common events.|
| want       | [Want](./js-apis-app-ability-want.md)                 | No| Yes| Carrier for information transfer between objects (application components).   |
| permission | string               | No| Yes| Permission required for a subscriber to receive the common event. This field is valid only when [OperationType](js-apis-app-ability-wantAgent.md#operationtype) of the WantAgent instance is **'SEND_COMMON_EVENT'**.   |
| extraInfo  | { [key: string]: any } | No| Yes| Extra information.   |
| extraInfos<sup>11+<sup>  | Record\<string, Object> | No| Yes| Extra information. You are advised to use this property to replace **extraInfo**. When this property is set, **extraInfo** does not take effect.   |
