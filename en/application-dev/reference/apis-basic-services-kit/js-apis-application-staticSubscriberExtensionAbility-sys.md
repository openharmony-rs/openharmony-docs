# @ohos.application.StaticSubscriberExtensionAbility (StaticSubscriberExtensionAbility) (System API)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

This module provides extension abilities of Basic Services Kit for static subscribers, which can be used to subscribe to common events in static mode. Static subscription enables receiving common events without keeping the app running in the background. This ability is applicable to scenarios where system services or system apps need to perform background processing when specific common events occur.

**StaticSubscriberExtensionAbility** provides the **onReceiveEvent** method and the **context** attribute. The **context** attribute is of the [StaticSubscriberExtensionContext](./js-apis-application-StaticSubscriberExtensionContext-sys.md) type, which is the running context of the extension ability. It is inherited from **ExtensionContext** and provides **startAbility** to start other abilities in the same app during event processing.

**APIs used in combination**

The typical process of this module is as follows: Inherit the base class, override **onReceiveEvent**, start a callback, read the event data, and start the target ability. Note that **context.startAbility** can start only the abilities that belong to the same app as the current **StaticSubscriberExtensionAbility**.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.
>
> The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { StaticSubscriberExtensionAbility } from '@kit.BasicServicesKit';
```

## Attributes

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

| Name   | Type                                                        | Read Only| Optional| Description    |
| ------- | ------------------------------------------------------------ | ---- | ---- | -------- |
| context<sup>10+</sup> | [StaticSubscriberExtensionContext](js-apis-application-StaticSubscriberExtensionContext-sys.md) | No  | No  | Context of the extension ability subscribed to in static mode.|

## StaticSubscriberExtensionAbility.onReceiveEvent

onReceiveEvent(event: CommonEventData): void

Defines a callback to be invoked when a common event is triggered in static mode.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| event | [CommonEventData](./js-apis-inner-commonEvent-commonEventData.md) | Yes| Common event data received through static subscription.|

**Example**
  ```ts
  import { commonEventManager } from '@kit.BasicServicesKit';

  class MyStaticSubscriberExtensionAbility extends StaticSubscriberExtensionAbility {
    onReceiveEvent(event: commonEventManager.CommonEventData) {
      console.info(`onReceiveEvent, event: ${JSON.stringify(event)}`);
    }
  }
  ```
