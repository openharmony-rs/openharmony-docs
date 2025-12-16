# Custom Event Dispatch
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiangtao92-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

When handling a touch event, ArkUI performs [hit testing](../../../ui/arkts-interaction-basic-principles.md#hit-testing) on the touch point and the component area before the event is triggered – to determine the components targeted by the event – and dispatches the event based on the test result. You can use **onChildTouchTest** on a parent node to specify how to perform the hit test on child nodes and thereby exert an impact on touch event dispatch. For details about the impact, see [TouchTestStrategy](#touchteststrategy11).

>  **NOTE**
>
>  - The initial APIs of this module are supported since API version 10. Updates will be marked with a superscript to indicate their earliest API version.
>
>  - With use of **onChildTouchTest**, the **onClick**, rotation, and pinch gesture events may receive no response due to the touch target not being hit.

## onChildTouchTest<sup>11+</sup>

onChildTouchTest(event: (value: Array&lt;TouchTestInfo&gt;) => TouchResult): T

Allows the current component to customize the hit test and control child component behavior during the test by setting a callback.

>**NOTE**
>
>- The array of child node information only includes information about named nodes, that is, nodes for which the **id** attribute is explicitly set.
>
>- This API can be called in [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 20.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                      | Mandatory| Description                  |
| ------ | ------------------------------------------ | ---- | ---------------------- |
| event  | (value: Array<[TouchTestInfo>](#touchtestinfo11)) => TouchResult | Yes  | Touch event information. **value**: array of child node information.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

## TouchTestInfo<sup>11+</sup>

Provides information about the coordinate system, ID, and size of the component where the current touch point is located.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Type | Read-Only   | Optional  |  Description                                      |
| ------------- | ------ | ------ | ------ | ---------------------------------------- |
| windowX | number | No| No| X-coordinate of the touch point relative to the upper left corner of the window.<br>Unit: vp.|
| windowY   | number| No|No|Y-coordinate of the touch point relative to the upper left corner of the window.<br>Unit: vp.|
| parentX   | number| No |No|X-coordinate of the touch point relative to the upper left corner of the parent component.<br>Unit: vp. |
| parentY   | number| No|No|Y-coordinate of the touch point relative to the upper left corner of the parent component.<br>Unit: vp. |
| x   | number| No | No|X-coordinate of the touch point relative to the upper left corner of the child component.<br>Unit: vp.|
| y   | number| No |No| Y-coordinate of the touch point relative to the upper left corner of the child component.<br>Unit: vp.|
| rect   | [RectResult](#rectresult)| No |No|Position, width, and height of the child component. |
| [id](ts-universal-attributes-component-id.md)   | string| No | No|Unique ID of the child component.|

## RectResult

Describes the position, width, and height of a component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type  | Read-Only| Optional | Description|
| ------- | ------ | ----- | -------- | ---------- |
| x     | number | No| No| X-coordinate.|
| y     | number |  No| No| Y-coordinate.|
| width | number | No| No| Content width.|
| height | number | No| No| Content height.|

## TouchResult<sup>11+</sup>

Defines the custom event dispatch result. You can influence event dispatch by returning specific results.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type                                    | Read-Only   | Optional  |  Description                               |
| --------- | --------- | ---- |--------------------------------------- | ---- |
| strategy  | [TouchTestStrategy](#touchteststrategy11) | No    | No |Event dispatch strategy.                    |
| id  | string | No   | Yes |Unique ID of the child component.<br>If **strategy** is set to **TouchTestStrategy.DEFAULT**, **id** is optional. If **strategy** is set to **TouchTestStrategy.FORWARD_COMPETITION** or **TouchTestStrategy.FORWARD**, **id** is mandatory. If **id** is not returned, the strategy **TouchTestStrategy.DEFAULT** is used.|

## TouchTestStrategy<sup>11+</sup>

Event dispatch strategy.

**Widget capability**: This API can be used in ArkTS widgets since API version 11.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Value   |Description                                      |
| ------------| ---------| ----------------------------------------- |
| DEFAULT   | 0  | Custom dispatch has no effect; the system dispatches events based on the hit status of the current node.|
| FORWARD_COMPETITION  | 1  | The event is dispatched to a specified child node, and the system determines whether to dispatch events to other sibling nodes.|
| FORWARD |2 | The event is dispatched to a specified child node, and the system will not dispatch events to other sibling nodes.|

## Example

### Example 1: Setting the Event Dispatch Strategy to FORWARD_COMPETITION

In this example, clicking and dragging in the blank area below the **List** component causes the **List** component to scroll. The **Button** component still responds to **onClick** events.

```ts
// xxx.ets
import { PromptAction } from '@kit.ArkUI';

@Entry
@Component
struct ListExample {
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]
  promptAction: PromptAction = this.getUIContext().getPromptAction();
  @State text: string = 'Button'

  build() {
    Column() {
      List({ space: 12, initialIndex: 0 }) {
        ForEach(this.arr, (item: number) => {
          ListItem() {
            Text('Item ' + item)
              .width('100%')
              .height(56)
              .fontSize(16)
              .textAlign(TextAlign.Start)
          }.borderRadius(24)
          .backgroundColor(Color.White)
          .padding({ left: 12, right: 12 })
        }, (item: number) => item.toString())
      }
      .listDirection(Axis.Vertical)
      .scrollBar(BarState.Off)
      .edgeEffect(EdgeEffect.Spring)
      .onScrollIndex((start: number, end: number) => {
        console.info('first' + start)
        console.info('last' + end)
      })
      .onDidScroll((scrollOffset: number, scrollState: ScrollState) => {
        console.info(`onScroll scrollState = ScrollState` + scrollState.toString() + `, scrollOffset = ` + scrollOffset)
      })
      .width('100%')
      .height('65%')
      .id('MyList')

      Button(this.text)
        .width(312)
        .height(40)
        .id('MyButton')
        .fontSize(16)
        .fontWeight(FontWeight.Medium)
        .margin({ top: 80 })
        .onClick(() => {
          this.text = 'click the button'
          this.promptAction.showToast({ message: 'you click the button.', duration: 3000 })
        })
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xF1F3F5)
    .justifyContent(FlexAlign.End)
    .padding({ left: 12, right: 12, bottom: 24 })
    .onChildTouchTest((touchInfo) => {
      for (let info of touchInfo) {
        if (info.id == 'MyList') {
          return { id: info.id, strategy: TouchTestStrategy.FORWARD_COMPETITION }
        }
      }
      return { strategy: TouchTestStrategy.DEFAULT }
    })
  }
}
```

![onchildtouchtest](figures/on-child-touch-test-competition.gif)

### Example 2: Setting the Event Dispatch Strategy to FORWARD

In this example, clicking and dragging in the blank area below the **List** component causes the **List** component to scroll. The **Button** component does not respond to **onClick** events.

```ts
// xxx.ets
import { PromptAction } from '@kit.ArkUI';

@Entry
@Component
struct ListExample {
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]
  promptAction: PromptAction = this.getUIContext().getPromptAction();
  @State text: string = 'Button'

  build() {
    Column() {
      List({ space: 12, initialIndex: 0 }) {
        ForEach(this.arr, (item: number) => {
          ListItem() {
            Text('Item ' + item)
              .width('100%')
              .height(56)
              .fontSize(16)
              .textAlign(TextAlign.Start)
          }.borderRadius(24)
          .backgroundColor(Color.White)
          .padding({ left: 12, right: 12 })
        }, (item: number) => item.toString())
      }
      .listDirection(Axis.Vertical)
      .scrollBar(BarState.Off)
      .edgeEffect(EdgeEffect.Spring)
      .onScrollIndex((start: number, end: number) => {
        console.info('first' + start)
        console.info('last' + end)
      })
      .onDidScroll((scrollOffset: number, scrollState: ScrollState) => {
        console.info(`onScroll scrollState = ScrollState` + scrollState + `, scrollOffset = ` + scrollOffset)
      })
      .width('100%')
      .height('65%')
      .id('MyList')

      Button(this.text)
        .width(312)
        .height(40)
        .id('MyButton')
        .fontSize(16)
        .fontWeight(FontWeight.Medium)
        .margin({ top: 80 })
        .onClick(() => {
          this.text = 'click the button'
          this.promptAction.showToast({ message: 'you click the button.', duration: 3000 })
        })
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xF1F3F5)
    .justifyContent(FlexAlign.End)
    .padding({ left: 12, right: 12, bottom: 24 })
    .onChildTouchTest((touchInfo) => {
      for (let info of touchInfo) {
        if (info.id == 'MyList') {
          return { id: info.id, strategy: TouchTestStrategy.FORWARD }
        }
      }
      return { strategy: TouchTestStrategy.DEFAULT }
    })
  }
}
```

![onchildtouchtest](figures/on-child-touch-test-forward.gif)

### Example 3: Setting the Event Dispatch Strategy to DEFAULT

In this example, clicking and dragging in the blank area below the **List** component does not cause the **List** component to scroll. The **Button** component still responds to **onClick** events.

```ts
// xxx.ets
import { PromptAction } from '@kit.ArkUI';

@Entry
@Component
struct ListExample {
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]
  promptAction: PromptAction = this.getUIContext().getPromptAction();
  @State text: string = 'Button'

  build() {
    Column() {
      List({ space: 12, initialIndex: 0 }) {
        ForEach(this.arr, (item: number) => {
          ListItem() {
            Text('Item ' + item)
              .width('100%')
              .height(56)
              .fontSize(16)
              .textAlign(TextAlign.Start)
          }.borderRadius(24)
          .backgroundColor(Color.White)
          .padding({ left: 12, right: 12 })
        }, (item: number) => item.toString())
      }
      .listDirection(Axis.Vertical)
      .scrollBar(BarState.Off)
      .edgeEffect(EdgeEffect.Spring)
      .onScrollIndex((start: number, end: number) => {
        console.info('first' + start)
        console.info('last' + end)
      })
      .onDidScroll((scrollOffset: number, scrollState: ScrollState) => {
        console.info(`onScroll scrollState = ScrollState` + scrollState.toString() + `, scrollOffset = ` + scrollOffset)
      })
      .width('100%')
      .height('65%')
      .id('MyList')

      Button(this.text)
        .width(312)
        .height(40)
        .id('MyButton')
        .fontSize(16)
        .fontWeight(FontWeight.Medium)
        .margin({ top: 80 })
        .onClick(() => {
          this.text = 'click the button'
          this.promptAction.showToast({ message: 'you click the button.', duration: 3000 })
        })
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xF1F3F5)
    .justifyContent(FlexAlign.End)
    .padding({ left: 12, right: 12, bottom: 24 })
    .onChildTouchTest((touchInfo) => {
      return { strategy: TouchTestStrategy.DEFAULT }
    })
  }
}
```

![onchildtouchtest](figures/on-child-touch-test-default.gif)
