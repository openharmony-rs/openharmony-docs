# Hover Event
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e8a3df3f036267095aa2be3a05bfa4ba7c1727ba translatedAt=2026-09-02T12:27:30.906Z -->

A hover event is triggered when the cursor slides over a component or when a stylus hovers and moves over the screen. It is used to listen for interaction states such as the mouse or stylus entering or exiting a component and hovering over a component, and is suitable for scenarios such as updating component styles and displaying position information based on the hover state.

>  **NOTE**
>
>  - The initial APIs of this module are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
>  - Currently, only an external mouse and a touchpad can trigger hover events. Some styluses<!--RP1--><!--RP1End-->do not support hover events, depending on the hardware capability.

## onHover

onHover(event: (isHover: boolean, event: HoverEvent) => void): T

A hover event is triggered when the mouse or stylus enters or exits a component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name             | Type                               | Mandatory| Description                                                        |
| ------------------- | ----------------------------------- | ---- | ------------------------------------------------------------ |
| event  | (isHover: boolean, event: [HoverEvent](#hoverevent10)) => void  | Yes   | Callback function invoked when the mouse or stylus enters or exits the component. isHover indicates whether the mouse or stylus is hovering over the component; the value is true when it enters and false when it leaves. event is a HoverEvent object used to obtain the coordinates of the position where the mouse or stylus hovers, and to set the property for blocking event bubbling. This is supported since API version 11. |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component, used for chained calls. |

## onHoverMove<sup>15+</sup>

onHoverMove(event: Callback&lt;HoverEvent&gt;): T

Triggered when a stylus hovers over the component.

**Atomic service API**: This API can be used in atomic services since API version 15.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name             | Type                               | Mandatory| Description                                                        |
| ------------------- | ----------------------------------- | ---- | ------------------------------------------------------------ |
| event | Callback<[HoverEvent](#hoverevent10)> | Yes | Callback invoked when the hover move event is triggered. The callback parameter is a HoverEvent object, which is used to obtain the position coordinates of the stylus hover and can be used to set the event bubbling blocking property. |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component, which can be used for chained calls. |

## HoverEvent<sup>10+</sup>

Inherits from [BaseEvent](ts-universal-events-click.md#baseevent8).

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read Only| Optional| Description|
| --------------- | ---------- | ----- | ----- | -------------------- |
| x<sup>15+</sup> |number|No|Yes|X coordinate of the mouse cursor or stylus position in the [component coordinate system](../../../ui/arkui-glossary.md#component-coordinate-system) relative to the current component.<br>Unit: vp<br>Value range: [0, +∞)<br> **Atomic service API:**  Since API version 15, this API is supported in atomic services.|
| y<sup>15+</sup> |number|No|Yes|Y coordinate of the mouse cursor or stylus position in the [component coordinate system](../../../ui/arkui-glossary.md#component-coordinate-system) relative to the current component.<br>Unit: vp<br>Value range: [0, +∞)<br> **Atomic service API:**  Since API version 15, this API is supported in atomic services.|
| windowX<sup>15+</sup> |number|No|Yes|X coordinate of the mouse cursor or stylus position in the coordinate system of the current application window.<br>Unit: vp<br>Value range: [0, +∞)<br> **Atomic service API:**  Since API version 15, this API is supported in atomic services.|
| windowY<sup>15+</sup> |number|No|Yes|Y coordinate of the mouse cursor or stylus position in the coordinate system of the current application window.<br>Unit: vp<br>Value range: [0, +∞)<br> **Atomic service API:**  Since API version 15, this API is supported in atomic services.|
| displayX<sup>15+</sup> |number|No|Yes|X coordinate of the mouse cursor or stylus position in the coordinate system of the current application screen.<br>Unit: vp<br>Value range: [0, +∞)<br> **Atomic service API:**  Since API version 15, this API is supported in atomic services.|
| displayY<sup>15+</sup> |number|No|Yes|Y coordinate of the mouse cursor or stylus position in the coordinate system of the current application screen.<br>Unit: vp<br>Value range: [0, +∞)<br> **Atomic service API:**  Since API version 15, this API is supported in atomic services.|
| stopPropagation | () => void |No|No| Blocks [event bubbling](../../../ui/arkts-interaction-basic-principles.md#event-bubbling). After a component has processed a hover event, this method can be used to prevent the event from being passed to the parent component, avoiding duplicate responses to the same event by the parent component. <br> **Atomic service API:**  Since API version 11, this API is supported in atomic services.|
| globalDisplayX<sup>20+</sup> | number |No|Yes| X coordinate of the mouse cursor or stylus position in the [global coordinate system](../../../windowmanager/window-terminology.md#global-coordinate-system).<br>Unit: vp<br>Value range: (-∞, +∞)<br>**Atomic service API:** Since API version 20, this API is supported in atomic services. |
| globalDisplayY<sup>20+</sup> | number |No|Yes| Y coordinate of the mouse cursor or stylus position in the [global coordinate system](../../../windowmanager/window-terminology.md#global-coordinate-system).<br>Unit: vp<br>Value range: (-∞, +∞)<br>**Atomic service API:** Since API version 20, this API is supported in atomic services. |

## Example

### Example 1: Using onHover

This example demonstrates how to set the [onHover](#onhover) event on a button. When the mouse or stylus hovers over the button, the event is triggered to dynamically change the text content and background color of the button.

```ts
// xxx.ets
@Entry
@Component
struct HoverEventExample {
  @State hoverText: string = 'no hover';
  @State color: Color = Color.Blue;

  build() {
    Column({ space: 20 }) {
      Button(this.hoverText, { type: ButtonType.Capsule })
        .width(180).height(80)
        .backgroundColor(this.color)
        .onHover((isHover: boolean, event: HoverEvent) => {
          // Use the onHover event to dynamically change the text content and background color of a button when the mouse pointer or stylus is hovered on it.
          // Use event.sourceTool to determine whether the device is a mouse device or stylus.
          if (isHover) {
            if (event.sourceTool == SourceTool.Pen) {
              this.hoverText = 'pen hover';
              this.color = Color.Pink;
            } else if (event.sourceTool == SourceTool.MOUSE) {
              this.hoverText = 'mouse hover';
              this.color = Color.Red;
            }
          } else {
            this.hoverText = 'no hover';
            this.color = Color.Blue;
          }
        })
    }.padding({ top: 30 }).width('100%')
  }
}
```

Diagrams:

The figure below shows how the button looks in the non-hovered state.

 ![nohover](figures/no-hover.png)

The figure below shows how the button looks when a stylus hovers on it.

 ![penhover](figures/pen-hover.png)

### Example 2: Using onHoverMove

Since API version 15, this example sets the [onHoverMove](#onhovermove15) event of the button. When a stylus hovers over the button, the UI displays the current hover position of the stylus.

```ts
// xxx.ets
@Entry
@Component
struct OnHoverMoveEventExample {
  @State hoverMoveText: string = '';

  build() {
    Column({ space: 20 }) {
      Button('onHoverMove', { type: ButtonType.Capsule })
        .width(180).height(80)
        .onHoverMove((event: HoverEvent) => {
          this.hoverMoveText = 'onHoverMove:\nXY = (' + event.x + ', ' + event.y + ')' + 
                               '\nwindowXY = (' + event.windowX + ', ' + event.windowY + ')' +
                               '\ndisplayXY = (' + event.displayX + ', ' + event.displayY + ')';
        })

      Text(this.hoverMoveText)
    }.padding({ top: 30 }).width('100%')
  }
}
```

Diagrams:

When a stylus hovers over a button, the UI continuously updates to show the position of the stylus tip.

![onHoverMove](figures/onHoverMove.png)
<!--no_check-->