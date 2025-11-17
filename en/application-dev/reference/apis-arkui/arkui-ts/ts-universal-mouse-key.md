# Mouse Event
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiangtao92-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @HelloCrease-->

If a mouse action triggers multiple events, the order of these events is fixed. By default, mouse events are transmitted transparently.

>  **NOTE**
>
>  - The initial APIs of this module are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>  - For the time being, a mouse event can be triggered only by an external mouse device.

## onMouse

onMouse(event: (event: MouseEvent) => void): T

Triggered when the component is clicked by a mouse button or the mouse pointer moves on the component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                             | Mandatory| Description                                                        |
| ------- | --------------------------------- | ---- | ------------------------------------------------------------ |
| event | (event: [MouseEvent](#mouseevent)) => void | Yes  | Timestamp, mouse button, action, coordinates of the clicked point on the entire screen, and coordinates of the clicked point relative to the component when the event is triggered.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

## MouseEvent

Inherits from [BaseEvent](ts-gesture-customize-judge.md#baseevent8).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                   | Type                   | Read-Only   |  Optional  |     Description                         |
| ---------------------- | -------------------------------------- |-------------- |------------- |  --------------------------- |
| x                      | number                                  | No          |  No    |X coordinate of the mouse pointer relative to the upper left corner of the component being clicked.<br>Unit: vp.<br>**Atomic service API**: This API can be used in atomic services since API version 11.        |
| y                      | number                                    |  No        |  No    |Y coordinate of the mouse pointer relative to the upper left corner of the component being clicked.<br>Unit: vp.<br>**Atomic service API**: This API can be used in atomic services since API version 11.        |
| button                 | [MouseButton](ts-appendix-enums.md#mousebutton8)      |  No    |  No    |Mouse button.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                       |
| action                 | [MouseAction](ts-appendix-enums.md#mouseaction8)       |  No  |  No    |Mouse action.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                       |
| stopPropagation        | () => void                            |  No         |  No    |Disables [event bubbling](../../../ui/arkts-interaction-basic-principles.md#event-bubbling) propagation.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                     |
| windowX<sup>10+</sup> | number                           |  No         |  No    |X coordinate of the mouse pointer relative to the upper left corner of the application window.<br>Unit: vp.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| windowY<sup>10+</sup> | number                           |  No        |  No    |Y coordinate of the mouse pointer relative to the upper left corner of the application window.<br>Unit: vp.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| displayX<sup>10+</sup> | number                          |  No        |  No    |X coordinate of the mouse pointer relative to the upper left corner of the application screen.<br>Unit: vp.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| displayY<sup>10+</sup> | number                         |  No         |  No    |Y coordinate of the mouse pointer relative to the upper left corner of the application screen.<br>Unit: vp.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| screenX<sup>(deprecated)</sup> | number                 |  No        |  No    |X coordinate of the mouse pointer relative to the upper left corner of the application window.<br>Unit: vp.<br>This API is deprecated since API version 10. You are advised to use **windowX** instead.|
| screenY<sup>(deprecated)</sup> | number                 |  No         |  No    |Y coordinate of the mouse pointer relative to the upper left corner of the application window.<br>Unit: vp.<br>This API is deprecated since API version 10. You are advised to use **windowY** instead.|
| rawDeltaX<sup>15+</sup> | number      |  No  |  Yes    |X-axis offset relative to the previously reported mouse pointer position. This value may be less than the difference between the two reported X coordinates when the mouse pointer is near the screen edge.<br>Unit: vp.<br>**Atomic service API**: This API can be used in atomic services since API version 15.|
| rawDeltaY<sup>15+</sup> | number      |  No    |  Yes   |Y-axis offset relative to the previously reported mouse pointer position.<br>Unit: vp.<br>**Atomic service API**: This API can be used in atomic services since API version 15.|
| pressedButtons<sup>15+</sup> | MouseButton[]      |  No     | Yes    |Array of all mouse buttons that are currently pressed.<br>**Atomic service API**: This API can be used in atomic services since API version 15.|
| globalDisplayX<sup>20+</sup> | number       |  No   |  Yes   |X coordinate of the mouse pointer position relative to the upper left corner of the global display.<br>Unit: vp.<br>Value range: [0, +∞).<br>**Atomic service API**: This API can be used in atomic services since API version 20.|
| globalDisplayY<sup>20+</sup> | number      | No     |  Yes   |Y coordinate of the mouse pointer position relative to the upper left corner of the global display.<br>Unit: vp.<br>Value range: [0, +∞).<br>**Atomic service API**: This API can be used in atomic services since API version 20.|

## Example

This example demonstrates how to set a mouse event on a button. When the button is clicked using a mouse device, the **onMouse** event is triggered to obtain relevant mouse event parameters.
For mouse wheel event examples, see [Axis Event](ts-universal-events-axis.md#example).

```ts
// xxx.ets
@Entry
@Component
struct MouseEventExample {
  @State hoverText: string = 'no hover';
  @State mouseText: string = '';
  @State action: string = '';
  @State mouseBtn: string = '';
  @State color: Color = Color.Blue;

  build() {
    Column({ space: 20 }) {
      Button(this.hoverText)
        .width(180).height(80)
        .backgroundColor(this.color)
        .onHover((isHover: boolean, event: HoverEvent) => {
          // Use the onHover event to dynamically change the text content and background color of a button when the mouse pointer is hovered on it.
          if (isHover) {
            this.hoverText = 'hover';
            this.color = Color.Pink;
          } else {
            this.hoverText = 'no hover';
            this.color = Color.Blue;
          }
        })
      Button('onMouse')
        .width(180).height(80)
        .onMouse((event: MouseEvent): void => {
          if (event) {
            switch (event.button) {
              case MouseButton.None:
                this.mouseBtn = 'None';
                break;
              case MouseButton.Left:
                this.mouseBtn = 'Left';
                break;
              case MouseButton.Right:
                this.mouseBtn = 'Right';
                break;
              case MouseButton.Back:
                this.mouseBtn = 'Back';
                break;
              case MouseButton.Forward:
                this.mouseBtn = 'Forward';
                break;
              case MouseButton.Middle:
                this.mouseBtn = 'Middle';
                break;
            }
            switch (event.action) {
              case MouseAction.Hover:
                this.action = 'Hover';
                break;
              case MouseAction.Press:
                this.action = 'Press';
                break;
              case MouseAction.Move:
                this.action = 'Move';
                break;
              case MouseAction.Release:
                this.action = 'Release';
                break;
            }
            this.mouseText = 'onMouse:\nButton = ' + this.mouseBtn +
              '\nAction = ' + this.action + '\nXY=(' + event.x + ',' + event.y + ')' +
              '\nwindowXY=(' + event.windowX + ',' + event.windowY + ')' +
              '\ntargetDisplayId = ' + event.targetDisplayId +
              '\nrawDeltaX = ' + event.rawDeltaX +
              '\nrawDeltaY = ' + event.rawDeltaY +
              '\nlength = ' + event.pressedButtons?.length;
          }
        })
      Text(this.mouseText)
    }.padding({ top: 30 }).width('100%')
  }
}
```

 

The figure below shows how the button looks when clicked.

![mouse](figures/mouse.gif)
