# Accessibility Hover Event
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhanghangkai10241-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

In accessibility mode, touch events are converted to accessibility hover events.

>  **NOTE**
>
>  - This event is supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.
>  - Currently, accessibility hover events are only triggered when accessibility mode is enabled.

## onAccessibilityHover

onAccessibilityHover(callback: AccessibilityCallback): T

Triggered in accessibility mode when a single finger touches the bound component.

> **NOTE**
>
> This API cannot be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier).

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

Defines the callback type for accessibility hover events, active in accessibility mode.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name             | Type                               | Mandatory| Description                                                        |
| ------------------- | ----------------------------------- | ---- | ------------------------------------------------------------ |
| isHover             | boolean                             | Yes  | Hover state. **true**: The finger enters the component. **false**: The finger exits the component.|
| event | [AccessibilityHoverEvent](#accessibilityhoverevent) | Yes  | **AccessibilityHoverEvent** object.                                  |

## AccessibilityHoverEvent

Inherits from [BaseEvent](ts-gesture-customize-judge.md#baseevent8).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name             | Type      | Read-Only| Optional| Description     |
| --------------- | ---------- | ------- | ------- | ------- |
| type             | [AccessibilityHoverType](ts-appendix-enums.md#accessibilityhovertype12) | No| No| Accessibility hover type.               |
| x                      | number                         | No| No| X-coordinate of the finger's position relative to the upper left corner of the component.<br>Unit: vp<br>|
| y                      | number                         | No| No| Y-coordinate of the finger's position relative to the upper left corner of the component.<br>Unit: vp<br>|
| windowX                | number                         | No| No| X-coordinate of the finger's position relative to the upper left corner of the application window.<br>Unit: vp<br>|
| windowY                | number                         | No| No| Y-coordinate of the finger's position relative to the upper left corner of the application window.<br>Unit: vp<br>|
| displayX               | number                         | No| No| X-coordinate of the finger's position relative to the upper left corner of the application screen.<br>Unit: vp<br>|
| displayY               | number                         | No| No| Y-coordinate of the finger's position relative to the upper left corner of the application screen.<br>Unit: vp<br>|
| globalDisplayX<sup>20+</sup> | number                   | No| Yes| X-coordinate of the finger position relative to the upper left corner of the global display.<br>Unit: vp<br>Value range: [0, +∞).<br>**Atomic service API**: This API can be used in atomic services since API version 20.|
| globalDisplayY<sup>20+</sup> | number                   | No| Yes| Y-coordinate of the finger position relative to the upper left corner of the global display.<br>Unit: vp<br>Value range: [0, +∞).<br>**Atomic service API**: This API can be used in atomic services since API version 20.|

## onAccessibilityHoverTransparent<sup>20+</sup>

onAccessibilityHoverTransparent(callback: AccessibilityTransparentCallback): T

This callback is triggered if a finger touch occurs within the component area while an accessibility service is running, but the accessibility system finds no focusable elements within the component hierarchy. It then returns an accessibility hover event. This callback only supports finger touches. It has no effect in the following senarios: [UIExtension](../../apis-arkui/js-apis-arkui-uiExtension.md), [Web](../../apis-arkweb/arkts-basic-components-web.md), <!--Del-->[FormComponent](ts-basic-components-formcomponent-sys.md), <!--DelEnd-->and [XComponent](ts-basic-components-xcomponent.md) integrated with a third-party UI framework.  

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**
| Name       | Type                   | Mandatory | Description                         |
| ---------- | -------------------------- | ------- | ----------------------------- |
| callback      | [AccessibilityTransparentCallback](ts-universal-accessibility-hover-event.md#accessibilitytransparentcallback20) | Yes  |  Callback invoked when a touch interaction occurs within the area of the component that does not respond to the accessibility hover event.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

## AccessibilityTransparentCallback<sup>20+</sup>

type AccessibilityTransparentCallback = (event: TouchEvent) => void

Defines the callback type for touch events that do not trigger accessibility responses in accessibility mode.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name             | Type                               | Mandatory| Description                                                        |
| ------------------- | ----------------------------------- | ---- | ------------------------------------------------------------ |
| event | [TouchEvent](ts-universal-events-touch.md#touchevent)| Yes  | Original touch event.<br>Note: The **TouchEvent** object's [TouchType](ts-appendix-enums.md#touchtype) corresponds to four accessibility hover event types: **HOVER_ENTER**, **HOVER_MOVE**, **HOVER_EXIT**, and HOVER_CANCEL.|

## Example

### Example 1: Using the onAccessibilityHover Event

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

### Example 2: Capturing a Touch Event on a Non-Focusable Component

This example shows how to capture touch events from a component that cannot receive focus in accessibility mode and display event details in the text area below.

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
        // Triggered on finger press.
        if (event.type === TouchType.HOVER_ENTER) {
          this.eventType = 'HOVER_ENTER';
        }
        // Triggered on touch move.
        if (event.type === TouchType.HOVER_MOVE) {
          this.eventType = 'HOVER_MOVE';
        }
        // Triggered on hand raise.
        if (event.type === TouchType.HOVER_EXIT) {
          this.eventType = 'HOVER_EXIT';
        }
        // Cancel the current event.
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
