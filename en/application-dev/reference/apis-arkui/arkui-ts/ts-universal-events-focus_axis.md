# Focus Axis Event
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e8a3df3f036267095aa2be3a05bfa4ba7c1727ba translatedAt=2026-09-02T12:26:18.659Z -->

A focus axis event is an event triggered by interacting with a game controller through the directional pad or joystick. This type of event is dispatched to the component that currently has focus and is then passed back to the application. Components that are focusable by default, such as **Button**, do not require additional attributes to handle focus axis events. For components that are not focusable by default, such as **Text** and **Image**, you can enable focus axis events by setting the [focusable](./ts-universal-attributes-focus.md#focusable) attribute to **true**.

>  **NOTE**
>
> - The initial APIs of this module are supported since API version 15. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## onFocusAxisEvent

onFocusAxisEvent(event: Callback\<FocusAxisEvent>): T

Binds a focus axis event callback to the component. After the component bound with this method is focused, operations on the joystick, d-pad, and other controls of the game controller trigger this callback. If the component is not focusable by default, set the [focusable](./ts-universal-attributes-focus.md#focusable) attribute to true to enable the focus axis event.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                         | Mandatory| Description              |
| ------ | ----------------------------- | ---- | ------------------ |
| event  | Callback\<[FocusAxisEvent](#focusaxisevent) | Yes   | Focus Axis Event callback. Triggered when the component bound to this method is focused. |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component, used for chained calls. |

## FocusAxisEvent

Describes the focus axis event object, which inherits from [BaseEvent](ts-universal-events-click.md#baseevent8).

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                                     | Type                 | Read-Only   |  Optional  |         Description                |
| ------------------------------------- | ---------------------------------------     | ------------- | ------------- | ------------------------- |
| axisMap                               | Map<[AxisModel](ts-appendix-enums.md#axismodel15), number>      |  No   |  No    | Axis value table of the focus axis event.         |
| stopPropagation                       | Callback\<void>                      |     No         |  No     |Prevents [event bubbling](../../../ui/arkts-interaction-basic-principles.md#event-bubbling) from being propagated. It can be used in scenarios where the current component does not want the parent component to continue responding to the event after handling the focus axis event.            |

## Example

This example demonstrates how to set up a focus axis event on a button. When the button gains focus, operating the game controller's directional pad or joystick will trigger the **onFocusAxisEvent** callback.

```ts
// xxx.ets
@Entry
@Component
struct FocusAxisEventExample {
  @State text: string = ''
  @State axisValue: string = ''

  aboutToAppear(): void {
    this.getUIContext().getFocusController().activate(true);
  }

  aboutToDisappear(): void {
    this.getUIContext().getFocusController().activate(false);
  }

  build() {
    Column() {
      Button('FocusAxisEvent')
        .defaultFocus(true)
        .onFocusAxisEvent((event: FocusAxisEvent) => {
          // Obtain the axis values in the focus axis event and update the page display content.
          let absX = event.axisMap.get(AxisModel.ABS_X);
          let absY = event.axisMap.get(AxisModel.ABS_Y);
          let absZ = event.axisMap.get(AxisModel.ABS_Z);
          let absRz = event.axisMap.get(AxisModel.ABS_RZ);
          let absGas = event.axisMap.get(AxisModel.ABS_GAS);
          let absBrake = event.axisMap.get(AxisModel.ABS_BRAKE);
          let absHat0X = event.axisMap.get(AxisModel.ABS_HAT0X);
          let absHat0Y = event.axisMap.get(AxisModel.ABS_HAT0Y);
          this.axisValue =
            'absX: ' + absX + '; absY: ' + absY + '; absZ: ' + absZ + '; absRz: ' + absRz + '; absGas: ' + absGas +
              '; absBrake: ' + absBrake + '; absHat0X: ' + absHat0X + '; absHat0Y: ' + absHat0Y;
          this.text = JSON.stringify(event);
        })
      Text(this.axisValue).padding(15)
      Text(this.text).padding(15)
    }.height(300).width('100%').padding(35)
  }
}
```

When the joystick of the game controller moves:

![onFocusAxisEvent](figures/onFocusAxisEvent.png)
<!--no_check-->