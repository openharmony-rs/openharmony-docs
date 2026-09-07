# Crown Event
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=b7d29dcb4c10e7f74b8709493d673af25bbc5983 translatedAt=2026-09-02T12:23:36.033Z -->

A crown event is an event triggered when the crown is rotated. Event dispatch relies on application focus, and you can customize event handling through [focus events](ts-universal-focus-event.md).

>  **NOTE**
>
> - The initial APIs of this module are supported since API version 18. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - Default interaction logic exists when the crown is manually rotated to trigger an event. For example, after the crown of a watch is rotated, the scrollbar scrolls in the rotation direction of the crown.
>
> - A component receives a crown event only when it gains focus. Focus control can be managed through [focusable](ts-universal-attributes-focus.md#focusable), [defaultFocus](ts-universal-attributes-focus.md#defaultfocus9), and [focusOnTouch](ts-universal-attributes-focus.md#focusontouch9).
>
> - This event is supported only on wearable devices. You can obtain the device type through deviceInfo.[deviceType](../../apis-basic-services-kit/js-apis-device-info.md#constants) to determine whether the device is a wearable device.
>
> - Components that support crown events by default: [Slider](ts-basic-components-slider.md), [DatePicker](ts-basic-components-datepicker.md), [TextPicker](ts-basic-components-textpicker.md), [TimePicker](ts-basic-components-timepicker.md), [Scroll](ts-container-scroll.md), [List](ts-container-list.md), [Grid](ts-container-grid.md), [WaterFlow](ts-container-waterflow.md), [ArcList](ts-container-arclist.md), [Refresh](ts-container-refresh.md), and [ArcSwiper](ts-container-arcswiper.md).

## onDigitalCrown

onDigitalCrown(handler: Optional&lt;Callback&lt;CrownEvent&gt;&gt;): T

This callback is triggered when the crown is rotated after the component gains focus.

> **NOTE**
>
> This API cannot be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier).

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full


**Parameters**
| Name     | Type                            | Mandatory    | Description                                     |
| ---------- | -------------------------------- | ------- | ----------------------------------------- |
| handler      | Optional&lt;Callback&lt;[CrownEvent](#crownevent)&gt;&gt; | Yes      | [CrownEvent](#crownevent) object.  |


**Return value**
| Type     | Description          |
| --------- | ---------------|
| T         | Current component, used for chained calls.   |

## CrownEvent

Data structure of the crown event received by a component. It includes the timestamp, rotation angular velocity, rotation angle, crown action, and a callback used to stop event bubbling.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                  | Type      | Read-Only   |  Optional  |  Description                                                      |
| --------------------- | ------------- | ---------- |------------ |-------------------------------------- |
| timestamp         | number   |  No     | No    |Timestamp. Time elapsed since system startup when the event is triggered.<br>Unit: ns                                  |
| angularVelocity | number   |  No     | No    |Angular velocity of rotation.<br>Unit: deg/s   |
| degree          | number   |  No     | No    |Relative rotation angle.<br>Unit: deg <br>Value range: [-360, 360].     |
| action          | [CrownAction](ts-appendix-enums.md#crownaction18)   |  No    | No   |Crown action. |
| stopPropagation | Callback\<void>    |  No      | No    |Stops [event bubbling](../../../ui/arkts-interaction-basic-principles.md#event-bubbling). This can be used when the currently focused component has already handled the crown event and the parent component should not continue to respond to crown rotation.                         |

## Example
This example registers a crown event for a component and reports the received crown event data.
```ts
// xxx.ets
@Entry
@Component
struct CityList {
  @State message: string = 'onDigitalCrown';

  build() {
    Column() {
      Row() {
        Stack() {
          Text(this.message)
            .fontSize(20)
            .fontColor(Color.White)
            .backgroundColor('#262626')
            .textAlign(TextAlign.Center)
            .focusable(true)
            .focusOnTouch(true)
            .defaultFocus(true)
            .borderWidth(2)
            .width(223)
            .height(223)
            .borderRadius(110)
            .onDigitalCrown((event: CrownEvent) => {
              event.stopPropagation();
              this.message = 'CrownEvent\n\n' + JSON.stringify(event);
              console.info(`action: ${event.action}, angularVelocity: ${event.angularVelocity}, degree: ${event.degree}, timestamp: ${event.timestamp}`);
            })
        }.width('100%').height('100%')
      }.width('100%').height('100%')
    }
  }
}
```

![crown.gif](figures/crown.gif)
