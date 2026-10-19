# Universal Events

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=828befee530895124aaf1637c9402999a598c883 translatedAt=2026-07-31T01:11:15.222Z pushedAt=2026-07-31T12:04:26.558Z -->

## Event Description

Components that support universal events can be bound to universal events such as click, long press, and swipe to respond to basic user interactions. This cannot be achieved with private events. For details, see the corresponding component documentation.

| Name| Parameter| Description|
| -------- | -------- | -------- |
| click | - | Triggered when the component is clicked.|
| longpress | - | Triggered when the component is long pressed.|
| swipe<sup>5+</sup> | [SwipeEvent](#swipeevent) | Triggered when a user quickly swipes on the component. |

## BaseEvent

Defines a basic event type, which describes common event information such as the event type, trigger time, device information, and target object. This method can obtain a unified event context during event processing.

| Attribute                 | Type                  | Description                                    |
| --------------------- | ---------------------- | ---------------------------------------- |
| type                  | string                 | Event type, such as **click** and **longpress**.|
| timestamp             | number                 | Timestamp when the event is triggered.<br>Unit: ms                  |
| deviceId<sup>8+</sup> | number                 | ID of the device that triggers the event.                |
| target<sup>12+</sup>   | [Target](../arkui-js/js-components-common-events.md#target6)| Target object that triggers the event.                  |

## SwipeEvent

Inherits from [BaseEvent](#baseevent), which is used to describe the event information triggered by quick swiping on a component, including the swiping direction. It is applicable to component swiping interactions.

| Attribute| Type| Description|
| -------- | -------- | -------- |
| direction | string | Swiping direction. The value can be one of the following:<br>1.&nbsp;**left**: Swipe left.<br>2.&nbsp;**right**: Swipe right.<br>3.&nbsp;**up**: Swipe up.<br>4.&nbsp;**down**: Swipe down. |