# Universal Events
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

## Event Description

Different from private events, universal events can be bound to most components.

| Name| Parameter| Description|
| -------- | -------- | -------- |
| click | - | Triggered when the component is clicked.|
| longpress | - | Triggered when the component is long pressed.|
| swipe<sup>5+</sup> | SwipeEvent | Triggered when a user quickly swipes on the component.|

## BaseEvent

Defines the basic event type.

| Attribute                 | Type                  | Description                                    |
| --------------------- | ---------------------- | ---------------------------------------- |
| type                  | string                 | Event type, such as **click** and **longpress**.|
| timestamp             | number                 | Timestamp when the event is triggered.<br>Unit: ms                  |
| deviceId<sup>8+</sup> | number                 | ID of the device that triggers the event.                |
| target<sup>12+</sup>   | [Target](../arkui-js/js-components-common-events.md#target6)| Target object that triggers the event.                  |

## SwipeEvent

Inherits from [BaseEvent](#baseevent).

| Attribute| Type| Description|
| -------- | -------- | -------- |
| direction | string | Swiping direction. The value can be one of the following:<br>1. **left**: Swipe left.<br>2. **right**: Swipe right.<br>3. **up**: Swipe up.<br>4. **down**: Swipe down.|
