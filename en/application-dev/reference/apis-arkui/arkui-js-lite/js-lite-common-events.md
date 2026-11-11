# Universal Events
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=9c92183287fa23162e04874223c3b068eb1f8a4d translatedAt=2026-11-10T07:54:07.103Z pushedAt=2026-11-10T10:56:17.039Z nl=1 -->

## Event Description

Unlike private events, universal events, such as tap, long press, and swipe, can be bound to most components to respond to basic user interactions. For details, check the corresponding component documentation.

| Name| Parameter| Description|
| -------- | -------- | -------- |
| click | - | Triggered when the component is clicked.|
| longpress | - | Triggered when the component is long pressed.|
| swipe<sup>5+</sup> | [SwipeEvent](#swipeevent) | Triggered when a user quickly swipes on the component. |

## BaseEvent

**BaseEvent** defines the basic event type, providing common event information such as the event type, trigger time, device information, and target object and obtaining the unified event context during event processing.

| Attribute                 | Type                  | Description                                    |
| --------------------- | ---------------------- | ---------------------------------------- |
| type                  | string                 | Event type, such as **click** and **longpress**.|
| timestamp             | number                 | Timestamp when the event is triggered.<br>Unit: ms                  |
| deviceId<sup>8+</sup> | number                 | ID of the device that triggers the event.                |
| target<sup>12+</sup>   | [Target](../arkui-js/js-components-common-events.md#target6)| Target object that triggers the event.                  |

## SwipeEvent

**SwipeEvent** inherits from [BaseEvent](#baseevent), which is used to describe event information triggered by a quick swipe on a component. It includes the swipe direction attribute and is suitable for handling component swipe interactions.

| Attribute| Type| Description|
| -------- | -------- | -------- |
| direction | string | Swipe direction. The value can be one of the following:<br>1.&nbsp;**left**: Swipe left.<br>2.&nbsp;**right**: Swipe right.<br>3.&nbsp;**up**: Swipe up.<br>4.&nbsp;**down**: Swipe down. |
