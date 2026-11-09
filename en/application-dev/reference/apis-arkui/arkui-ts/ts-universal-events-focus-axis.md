# Focus Axis Event
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=a306693f0f46e5633c549769b8338f6bd7c191f4 translatedAt=2026-09-20T10:08:13.477Z pushedAt=2026-09-20T10:15:10.098Z -->

A focus axis event is an axis event reported through the D-pad or joystick when interacting with a gamepad. The axis event is distributed and called back to the application through the focused component. If a component is focusable by default, such as Button, no additional attribute settings are required. If a component is not focusable by default, such as Text and Image, you can set the [focusable](./ts-universal-attributes-focus.md#focusable) attribute to true to enable the focus axis event.

>  **NOTE**
>
> - The initial APIs of this module are supported since API version 15. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## onFocusAxisEvent

onFocusAxisEvent(event: Callback\<FocusAxisEvent>): T

Binds a focus axis event callback to a component. After the component bound with this method is focused, operations on the joystick, D-pad, and the like of a gamepad trigger this callback. If the component cannot be focused by default, set the [focusable](./ts-universal-attributes-focus.md#focusable) attribute to true first to enable the focus axis event.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                          | Mandatory | Description               |
| ------ | ----------------------------- | ---- | ------------------ |
| event  | Callback\<[FocusAxisEvent](#focusaxisevent)> | Yes   | Callback for the focus axis event. It is triggered after the component bound with this method is focused. |

**Return value**

| Type | Description |
| -------- | -------- |
| T | Current component, used for chained calls. |

## FocusAxisEvent

Describes the focus axis event object, which inherits from [BaseEvent](ts-universal-events-click.md#baseevent8).

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                                      | Type                  | Read-only    |  Optional   |         Description                 |
| ------------------------------------- | ---------------------------------------     | ------------- | ------------- | ------------------------- |
| axisMap                               | Map<[AxisModel](ts-appendix-enums.md#axismodel15), number>      |  No    |  No     | Axis value table of the focus axis event.          |
| stopPropagation                       | Callback\<void>                      |     No         |  No     |Used to prevent [event bubbling](../../../ui/arkts-interaction-basic-principles.md#event-bubbling) from being passed. It can be used in the scenario where the current component does not want the parent component to continue responding to the event after handling the focus axis event.            |

## Example

This example sets a focus axis event on a button. When the button is focused, moving the D-pad or joystick of the gamepad triggers the **onFocusAxisEvent** callback.

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
          // Obtain the axis values in the focus axis event and update the content displayed on the page.
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

When the gamepad joystick moves:

![onFocusAxisEvent](figures/onFocusAxisEvent.png)
