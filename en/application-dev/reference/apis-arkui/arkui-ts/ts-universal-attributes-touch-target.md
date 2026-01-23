# Touch Target
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

You can set the touch target for components. When handling a touch event, ArkUI performs a [hit test](../../../ui/arkts-interaction-basic-principles.md#hit-testing) on the touch point and the component area before the event is triggered to determine the components targeted by the event. Then ArkUI dispatches the event based on the test result. This affects the dispatch of [click](ts-universal-events-click.md), [touch](ts-universal-events-touch.md), [drag](ts-universal-events-drag-drop.md), [mouse](ts-universal-mouse-key.md), [axis](ts-universal-events-axis.md), [hover](ts-universal-events-hover.md), [accessibility hover](ts-universal-accessibility-hover-event.md), and [gesture](ts-gesture-settings.md) events.


>  **NOTE**
>
> - The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - When setting the touch target attributes, you need to press the finger in the touch target. If the event response conditions are met when the finger is lifted, the event is triggered. In addition, if the conditions are met before the current gesture ends, continuously triggerable events will also be activated.

## responseRegion

responseRegion(value: Array&lt;Rectangle&gt; | Rectangle): T

Sets one or more touch targets.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | Array&lt;[Rectangle](#rectangle)&gt;&nbsp;\|&nbsp;[Rectangle](#rectangle) | Yes  | Touch target, including the position and size.<br>The default touch target is the entire component. Default value:<br>{<br>x: 0,<br>y: 0,<br>width: '100%',<br>height: '100%'<br>}<br>|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

## mouseResponseRegion<sup>10+</sup>

mouseResponseRegion(value: Array&lt;Rectangle&gt; | Rectangle): T

Sets one or more mouse response regions.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | Array&lt;[Rectangle](#rectangle)&gt;&nbsp;\|&nbsp;[Rectangle](#rectangle) | Yes  | Mouse response regions, defining the position and size.<br>The default touch target is the entire component. Default value:<br>{<br>x: 0,<br>y: 0,<br>width: '100%',<br>height: '100%'<br>} |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

## responseRegionList<sup>22+</sup>

responseRegionList(regions: Array&lt;ResponseRegion&gt;): T

Sets the touch target list for the component. When this API is called, the [responseRegion](#responseregion) and [mouseResponseRegion](#mouseresponseregion10) APIs do not take effect.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| regions  | Array&lt;[ResponseRegion](#responseregion22)&gt;&nbsp; | Yes  | Array of touch targets for the component.<br>Each touch target contains the input tool type, position, and size.<br>Default value:<br>[{<br>tool: ResponseRegionSupportedTool.ALL,<br>x: LengthMetrics.vp(0),<br>y: LengthMetrics.vp(0),<br>width: LengthMetrics.percent(1),<br>height: LengthMetrics.percent(1)<br>}] |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

## Rectangle

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       | Type                       | Read-Only   |  Optional  |  Description                            |
| ------ | ----------------------------- | -----| -----|-------------------------------- |
| x      | [Length](ts-types.md#length)  | No  | Yes  |X coordinate of the touch point relative to the upper left corner of the component.<br>Default value: **0vp**|
| y      | [Length](ts-types.md#length)  | No  | Yes  |Y coordinate of the touch point relative to the upper left corner of the component.<br>Default value: **0vp**|
| width  | [Length](ts-types.md#length)  | No  | Yes  |Width of the touch target.<br>Default value: **'100%'**|
| height | [Length](ts-types.md#length) | No  | Yes  |Height of the touch target.<br>Default value: **'100%'**|

  >  **NOTE**
  >
  > - **x** and **y** can be set to a positive or negative percentage value. For example, when **x** is set to **'100%'**, the touch target is the offset from the right edge of the component by the component's width. When **x** is set to **'-100%'**, the touch target is the offset from the left edge of the component by the component's width. When **y** is set to **'100%'**, the touch target is the offset from the bottom edge of the component by the component's height. When **y** is set to **'-100%'**, the touch target is the offset from the top edge of the component by the component's height.
  >
  > - **width** and **height** can only be set to positive percentage values. When **width** is set to **'100%'**, the width of the touch target is equal to that of the component. For example, if the width of a component is 100 vp, **'100%'** indicates that the width of the touch target is also 100 vp. when **height** is set to **'100%'**, the height of the touch target is equal to that of the component.
  >
  > - The percentage is measured relative to the component itself.
  >
  > - When the parent component has [clip](ts-universal-attributes-sharp-clipping.md#clip12) set to **true**, child component interaction is affected by the parent component's response region. Children outside the parent component's response region won't respond to gestures or events.
  >
  > - **width** and **height** do not support **calc()** dynamic calculations.

## ResponseRegion<sup>22+</sup>

Defines a touch target consisting of an input tool type, touch position, and size.

  >  **NOTE**
  >
  > - When the parent component has [clip](ts-universal-attributes-sharp-clipping.md#clip12) set to **true**, child component interaction is affected by the parent component's response region. Children outside the parent component's response region won't respond to gestures or events.
  >  
  > - If the input tool type, touch position, and size are not configured for a touch target, default values are used. 
  >  
  > - Positive calculation results for x and y represent shifts to the right and down, respectively. Negative calculation results represent shifts to the left and up, respectively.
  >
  > - If the width and height are of the string type, the string must be in lowercase. Dynamic calculation with **calc()** is supported. The format of the input string for **calc()** is Width/Height scaling ratio ± Width/Height increment, where the scaling ratio is a percentage and the increment unit is px or vp. For example, in **calc(80% + 10vp)**, **80%** is the width/height scaling ratio, and **10vp** is the width/height increment. If the width and height are of the **LengthMetrics** type and the unit is percent, the width and height are calculated relative to the component's own width and height. **percent(1)** indicates 100%. If the calculation result is a negative value, the default value is used.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       | Type                       | Read-Only   |  Optional  |  Description                            |
| ------ | ----------------------------- | -----| -----|-------------------------------- |
| tool   | [ResponseRegionSupportedTool](./ts-appendix-enums.md#responseregionsupportedtool22)  | No  | Yes  |Type of the input tool applicable to the touch target.<br>Default value: **ResponseRegionSupportedTool.ALL**|
| x      | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)  | No  | Yes  |X coordinate of the touch point relative to the upper left corner of the component.<br>Default value: **LengthMetrics.vp(0)**|
| y      | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)  | No  | Yes  |Y coordinate of the touch point relative to the upper left corner of the component.<br>Default value: **LengthMetrics.vp(0)**|
| width  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) \| string | No  | Yes  |Width of the touch target.<br>Default value: **LengthMetrics.percent(1)**|
| height | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) \| string | No  | Yes  |Height of the touch target.<br>Default value: **LengthMetrics.percent(1)**|

## Example

### Example 1: Setting a Touch Target via the responseRegion API

This example demonstrates how to set a touch target for a button using **responseRegion** to respond to click events.

```ts
// xxx.ets
@Entry
@Component
struct TouchTargetExample {
  @State text: string = "";

  build() {
    Column({ space: 20 }) {
      Text("{x:0,y:0,width:'50%',height:'100%'}")
      // The width of the touch target is half of that of the button. The user will get no response if they touch the right of the button.
      Button("button1")
        .responseRegion({ x: 0, y: 0, width: '50%', height: '100%' })
        .onClick(() => {
          this.text = 'button1 clicked'
        })

      // Add multiple touch targets for a component.
      Text("[{x:'100%',y:0,width:'50%',height:'100%'}," +
      "\n{ x: 0, y: 0, width: '50%', height: '100%' }]")
      Button("button2")
        .responseRegion([
          { x: '100%', y: 0, width: '50%', height: '100%' }, // The width of the first touch target is half of that of the button. The touch event is triggered if the half width area on the right of the button is touched.
          { x: 0, y: 0, width: '50%', height: '100%' } // The width of the second touch target is half of the button width. The touch event is triggered if the left half of button2 is touched.
        ])
        .onClick(() => {
          this.text = 'button2 clicked'
        })
      // The touch target is located downward by one button height, with its size equal to the button size. The touch event is triggered if the lower part of button3 is touched.
      Text("{x:0,y:'100%',width:'100%',height:'100%'}")
      Button("button3")
        .responseRegion({ x: 0, y: '100%', width: '100%', height: '100%' })
        .onClick(() => {
          this.text = 'button3 clicked'
        })

      Text(this.text).margin({ top: 50 })
    }.width('100%').margin({ top: 10 })
  }
}
```

![touchtarget.gif](figures/touchtarget.gif)

### Example 2: Setting a Touch Target via the responseRegionList API

This example demonstrates how to set a touch target for a button using [responseRegionList](#responseregionlist22) to respond to click events.

The **responseRegionList** API is supported since API version 22.

```ts
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct TouchTargetExample {
  @State text: string = "";

  build() {
    Column({ space: 20 }) {
      Text("left part of button1")
      // The width of the touch target is half of that of the button. The user will get no response if they touch the right of the button.
      Button("button1")
        .responseRegionList([{
          x: LengthMetrics.vp(0),
          y: LengthMetrics.vp(0),
          width: LengthMetrics.percent(0.5),
          height: LengthMetrics.percent(1),
        }])
        .onClick(() => {
          this.text = 'button1 clicked'
        })

      // Touch target 1 is the entire button size, shifted right by one button width. Clicking the area one button size to the left of button2 triggers the click event.
      // Touch target 2 is the entire button size, shifted down by one button height. Clicking the area one button size below button2 with the mouse triggers the click event.
      Text("one button size right of button2," + "\n one button size below button2")
      Button("button2")
        .responseRegionList([{
          x: LengthMetrics.percent(1),
          y: LengthMetrics.vp(0),
          width: LengthMetrics.percent(1),
          height: LengthMetrics.percent(1),
        }, {
          tool: ResponseRegionSupportedTool.MOUSE,
          x: LengthMetrics.vp(0),
          y: LengthMetrics.percent(1),
          width: 'calc(100% + 0vp)',
          height: 'calc(100% - 0px)',
        }])
        .onClick(() => {
          this.text = 'button2 clicked'
        })

      Text(this.text).margin({ top: 50 })
    }.width('100%').margin({ top: 10 })
  }
}
```


### Example 3: Setting the Mouse Touch Target to Respond to Click Events

This example demonstrates how to set the mouse touch target using [mouseResponseRegion](ts-universal-attributes-touch-target.md#mouseresponseregion10) to respond to click events.

```ts
// xxx.ets
@Entry
@Component
struct MouseResponseRegionExample {
  @State clickInfo: string = 'Click the touch target to trigger an event';

  build() {
    Column({ space: 30 }) {
      // Example 1: Single touch target (only the left half of the button)
      Text ('Touch target: left half of button (click left half to trigger)')
        .fontSize(14)
      Button ('Button1 (Left Half Touch Target)')
        .width(200)
        .height(60)
        // Mouse touch target: only the left half of the button (x/y relative to the component itself, width 50%)
        .mouseResponseRegion({
          // X coordinate of the touch target relative to the component (top-left corner as origin)
          x: 0,
          // Y coordinate of the touch target relative to the component
          y: 0,
          // Width of the touch target (50% of the button)
          width: '50%',
          // Height of the touch target (100% of the button)
          height: '100%'
        })
        .onClick(() => {
          this.clickInfo = 'Left half touch target of Button1 clicked';
        })
      // Example 2: Multiple touch targets (both left half and area below the button)
      Text ('Touch target: left half + area below the button (click either to trigger)')
        .fontSize(14)
      Button('Button2 (Multiple Touch Targets)')
        .width(200)
        .height(60)
        // Mouse touch target: array, containing two independent touch targets
        .mouseResponseRegion([
          // Touch target 1: left half of the button
          {
            x: 0,
            y: 0,
            width: '50%',
            height: '100%'
          },
          // Touch target 2: area below the button (y=100% indicates the bottom of the button, and the height is 60 vp)
          {
            x: 0,
            y: '100%',
            width: '100%',
            height: 60
          }
        ])
        .onClick(() => {
          this.clickInfo = 'Any touch target of Button2 clicked';
        })
      // Example 3: Target outside the button (right side blank area of the button)
      Text ('Touch target: outside the right side of the button (click the blank area to the right of the button to trigger)')
        .fontSize(14)
      Button ('Button3 (Right Outer Touch Target)')
        .width(200)
        .height(60)
        // Mouse touch target: area outside the right side of the button (x=100% indicates the right edge of the button)
        .mouseResponseRegion({
          // X coordinate of the touch target: right edge of the button
          x: '100%',
          y: 0,
          // Touch target width: 80 vp
          width: 80,
          height: '100%'
        })
        .onClick(() => {
          this.clickInfo = 'Right outer touch target of Button3 clicked';
        })
      // Display the click result.
      Text(this.clickInfo)
        .fontSize(16)
        .margin({ top: 20 })
    }
    .width('100%')
    .height('100%')
    // Center the display.
    .justifyContent(FlexAlign.Center)
  }
}
```

