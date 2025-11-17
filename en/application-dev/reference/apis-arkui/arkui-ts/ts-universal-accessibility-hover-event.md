# Accessibility Hover Event
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhanghangkai10241-->
<!--Designer: @lmleon-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

When accessibility mode is enabled, touch events are converted into accessibility hover events.

>  **NOTE**
>
>  - This event is supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.
>  - Currently, conversion into accessibility hover events can only be initiated by enabling accessibility mode.

## onAccessibilityHover

onAccessibilityHover(callback: AccessibilityCallback): T

Invoked in accessibility mode when a single finger touches the bound component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name       | Type                   | Mandatory | Description                         |
| ---------- | -------------------------- | ------- | ----------------------------- |
| callback      | [AccessibilityCallback](#accessibilitycallback) | Yes  |  Callback invoked in accessibility mode when a single finger touches the bound component.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

## AccessibilityCallback

type AccessibilityCallback = (isHover: boolean, event: AccessibilityHoverEvent) => void

Represents the accessibility hover event callback, which is effective when accessibility mode is enabled.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name             | Type                               | Mandatory| Description                                                        |
| ------------------- | ----------------------------------- | ---- | ------------------------------------------------------------ |
| isHover             | boolean                             | Yes  | Whether a finger is hovering over the component in accessibility mode. The accessibility hover event is converted from a touch event, with the value **true** when the finger enters the component and **false** when it exits.|
| event | [AccessibilityHoverEvent](#accessibilityhoverevent) | Yes  | **AccessibilityHoverEvent** object.                                  |

## AccessibilityHoverEvent

Inherits from [BaseEvent](ts-gesture-customize-judge.md#baseevent8).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name             | Type      | Read-Only| Optional| Description     |
| --------------- | ---------- | ------- | ------- | ------- |
| type             | [AccessibilityHoverType](ts-appendix-enums.md#accessibilityhovertype12) | No| No| Accessibility hover type.               |
| x                      | number                         | No| No| X coordinate of the finger's position relative to the upper left corner of the component being touched.<br>Unit: vp<br>|
| y                      | number                         | No| No| Y coordinate of the finger's position relative to the upper left corner of the component being touched.<br>Unit: vp<br>|
| windowX                | number                         | No| No| X coordinate of the finger's position relative to the upper left corner of the application window.<br>Unit: vp<br>|
| windowY                | number                         | No| No| Y coordinate of the finger's position relative to the upper left corner of the application window.<br>Unit: vp<br>|
| displayX               | number                         | No| No| X coordinate of the finger's position relative to the upper left corner of the display.<br>Unit: vp<br>|
| displayY               | number                         | No| No| Y coordinate of the finger's position relative to the upper left corner of the display.<br>Unit: vp<br>|
| globalDisplayX<sup>20+</sup> | number                   | No| Yes| X coordinate of the finger position relative to the upper left corner of the global screen.<br>Unit: vp<br>Value range: [0, +∞).<br>**Atomic service API**: This API can be used in atomic services since API version 20.|
| globalDisplayY<sup>20+</sup> | number                   | No| Yes| Y coordinate of the finger position relative to the upper left corner of the global screen.<br>Unit: vp<br>Value range: [0, +∞).<br>**Atomic service API**: This API can be used in atomic services since API version 20.|

## onAccessibilityHoverTransparent<sup>20+</sup>

onAccessibilityHoverTransparent(callback: AccessibilityTransparentCallback): T

The current touch position is in the component area where the callback API is registered, but the accessibility floating event is not responded. Only finger touch is supported. The following components cannot be connected to a third-party UI framework in the touch position: [UIExtension](../../apis-arkui/js-apis-arkui-uiExtension.md), [Web](../../apis-arkweb/arkts-basic-components-web.md), <!--Del-->[FormComponent](ts-basic-components-formcomponent-sys.md) and <!--DelEnd-->[XComponent](ts-basic-components-xcomponent.md). In the preceding scenario, the callback does not take effect.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**
| Name       | Type                   | Mandatory | Description                         |
| ---------- | -------------------------- | ------- | ----------------------------- |
| callback      | [AccessibilityTransparentCallback](ts-universal-accessibility-hover-event.md#accessibilitytransparentcallback20) | Yes  |  Provides the touch event that does not respond to the user input after the accessibility mode is enabled. This callback is triggered when the single-finger touch does not respond to the accessibility floating event after the accessibility mode is enabled.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

## AccessibilityTransparentCallback<sup>20+</sup>

type AccessibilityTransparentCallback = (event: TouchEvent) => void

Provides touch events that fail to respond to user input after the accessibility mode is enabled.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name             | Type                               | Mandatory| Description                                                        |
| ------------------- | ----------------------------------- | ---- | ------------------------------------------------------------ |
| event | [TouchEvent] (ts-universal-events-touch.md#touchevent object description)| Yes  | Original touch event.<br>Note: A touch event type [TouchType] (ts-appendix-enums.md#touchtype) of the TouchEvent object is one of four accessibility floating event types, and the four accessibility floating event types are HOVER_ENTER, HOVER_MOVE, HOVER_EXIT, and HOVER_CANCEL.

## Example

### Example 1 (using the onAccessibilityHover event)

This example demonstrates how to use the **onAccessibilityHover** event to customize a button in accessibility mode.

```ts
// xxx.ets
@Entry
@Component
struct OnAccessibilityHoverEventExample {
  @State hoverText: string = 'no hover';
  @State color: Color = Color.Blue;

  build() {
    Column({ space: 20 }) {
      Button(this.hoverText)
        .width(180).height(80)
        .backgroundColor(this.color)
        .onAccessibilityHover((isHover: boolean, event: AccessibilityHoverEvent) => {
          // Use the onAccessibilityHover event to dynamically change the text content and background color of a button when the finger is hovered on it.
          if (isHover) {
            this.hoverText = 'hover';
            this.color = Color.Pink;
          } else {
            this.hoverText = 'no hover';
            this.color = Color.Blue;
          }
        })
    }.padding({ top: 30 }).width('100%')
  }
}
```

### Example 2 (Capturing a Touch Event of a Component That Cannot Be Focused Without Accessibility)

The sample code captures touch events of components that cannot be focused in accessible mode and displays the event information in the text below the component.

```ts
@Entry
@Component
struct TestExample {
  @State text: string = '';
  @State eventType: string = '';

  build() {
    Column({ space: 50 }) {
      Column() {
        Button("Test Button")
          .accessibilityLevel("no")
      }.margin({ top: 20 })

      Text(this.text)
    }
    .width('100%')
    .height('100%')
    .onAccessibilityHoverTransparent((event?: TouchEvent) => {
      if (event) {
        if (event.type === TouchType.HOVER_ENTER) {
          this.eventType = 'HOVER_ENTER';
        }
        if (event.type === TouchType.HOVER_MOVE) {
          this.eventType = 'HOVER_MOVE';
        }
        if (event.type === TouchType.HOVER_EXIT) {
          this.eventType = 'HOVER_EXIT';
        }
        if (event.type === TouchType.HOVER_CANCEL) {
          this.eventType = 'HOVER_CANCEL';
        }
        this.text = 'TouchType:' + this.eventType + '\nDistance between touch point and touch element:\nx: '
          + event.touches[0].x + '\n' + 'y: ' + event.touches[0].y + '\nComponent globalPos:('
          + event.target.area.globalPosition.x + ',' + event.target.area.globalPosition.y + ')\nwidth:'
          + event.target.area.width + '\nheight:' + event.target.area.height;
      }
    })
  }
}
```
