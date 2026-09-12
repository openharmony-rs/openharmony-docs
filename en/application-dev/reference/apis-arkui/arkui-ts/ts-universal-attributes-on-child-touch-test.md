# Custom Event Dispatch
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=9430c77017ca73641537d932a3d7d8a4c99c078b translatedAt=2026-09-02T11:56:11.176Z -->

When handling a touch event, ArkUI performs [hit testing](../../../ui/arkts-interaction-basic-principles.md#hit-testing) on the touch point and the component area before the event is triggered – to determine the components targeted by the event – and dispatches the event based on the test result. You can use **onChildTouchTest** on a parent node to specify how to perform the hit test on child nodes and thereby exert an impact on touch event dispatch. For details about the impact, see [TouchTestStrategy](#touchteststrategy11).

> **NOTE**
>
> - Supported since API version 10. For newly added APIs in later versions, the initial version is marked separately with a superscript.
>
> - The APIs of this module can be used only in the stage model.
>
> - After custom event dispatch, the onClick event and rotation and pinch gestures may fail to respond because the touch hot zone is not hit.

## onChildTouchTest<sup>11+</sup>

onChildTouchTest(event: (value: Array&lt;TouchTestInfo&gt;) => TouchResult): T

Allows the current component to customize the hit test and control child component behavior during the test by setting a callback.

> **NOTE**
>
> - The array of child node information only includes information about named nodes, that is, nodes for which the **id** attribute is explicitly set.
>
> - This API can be called in [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 20.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                      | Mandatory| Description                  |
| ------ | ------------------------------------------ | ---- | ---------------------- |
| event | (value: Array<[TouchTestInfo](#touchtestinfo11)>) => [TouchResult](#touchresult11) | Yes | Callback invoked for the custom touch test. It receives an array **value** that contains the touch test information of child nodes. The array contains only the information of named nodes whose IDs are set through the **id** attribute. It returns a **TouchResult** to control the event dispatch policy of child nodes. |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component, used for chained calls. |

## TouchTestInfo<sup>11+</sup>

Provides information about the coordinate system, ID, and size of the component where the current touch point is located.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Type | Read-Only   | Optional  |  Description                                      |
| ------------- | ------ | ------ | ------ | ---------------------------------------- |
| windowX | number | No | No | X-axis coordinate of the press point relative to the window's top-left corner.<br>Unit: vp |
| windowY   | number| No |No|Y-axis coordinate of the press point relative to the window's top-left corner.<br>Unit: vp|
| parentX   | number| No  |No|X-axis coordinate of the press point relative to the parent component's top-left corner.<br>Unit: vp  |
| parentY   | number| No |No|Y-axis coordinate of the press point relative to the parent component's top-left corner.<br>Unit: vp  |
| x   | number| No  | No|X-axis coordinate of the press point relative to the child component's top-left corner.<br>Unit: vp |
| y   | number| No  |No| Y-axis coordinate of the press point relative to the child component's top-left corner.<br>Unit: vp |
| rect   | [RectResult](#rectresult)| No |No|Position, width, and height of the child component. |
| [id](ts-universal-attributes-component-id.md#id)   | string| No  | No|Unique identifier of the child component. |

## RectResult

Describes the position, width, and height of a component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type  | Read-Only| Optional | Description|
| ------- | ------ | ----- | -------- | ---------- |
| x     | number | No | No | Horizontal coordinate.<br>Unit: vp |
| y     | number |  No | No | Vertical coordinate.<br>Unit: vp |
| width | number | No | No | Content width.<br>Unit: vp |
| height | number | No | No | Content height.<br>Unit: vp |

## TouchResult<sup>11+</sup>

Defines the custom event dispatch result. You can influence event dispatch by returning specific results.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type                                    | Read-Only   | Optional  |  Description                               |
| --------- | --------- | ---- |--------------------------------------- | ---- |
| strategy  | [TouchTestStrategy](#touchteststrategy11) | No    | No |Event dispatch strategy.                    |
| id  | string | No    | Yes  |Unique identifier of the child component.<br>When strategy is TouchTestStrategy.DEFAULT, id is optional; when strategy is TouchTestStrategy.FORWARD_COMPETITION or TouchTestStrategy.FORWARD, id is required (if no id is returned, it is processed as TouchTestStrategy.DEFAULT). |

## TouchTestStrategy<sup>11+</sup>

Event dispatch strategy.

**Widget capability**: This API can be used in ArkTS widgets since API version 11.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Value   |Description                                      |
| ------------| ---------| ----------------------------------------- |
| DEFAULT   | 0  | Custom dispatch has no effect; the system dispatches events based on the hit status of the current node.|
| FORWARD_COMPETITION  | 1  | The application specifies dispatching events to a child node, and the system decides whether to continue dispatching events to other sibling nodes. |
| FORWARD |2 | The application specifies dispatching events to a child node, and the system no longer dispatches events to other sibling nodes. |

## Example

### Example 1: Setting the Event Dispatch Strategy to FORWARD_COMPETITION

In this example, click the blank area below the List and drag to make the List scroll. When the Button is pressed, the Button responds to the onClick event.

```ts
// xxx.ets
import { PromptAction } from '@kit.ArkUI';

@Entry
@Component
struct ListExample {
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12];
  promptAction: PromptAction = this.getUIContext().getPromptAction();
  @State text: string = 'Button';

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
        console.info(`first ${start}`);
        console.info(`last ${end}`);
      })
      .onDidScroll((scrollOffset: number, scrollState: ScrollState) => {
        console.info(`onScroll scrollState = ScrollState ${scrollState.toString()}, scrollOffset = ${scrollOffset}`);
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
          this.text = 'click the button';
          this.promptAction.showToast({ message: 'you click the button.', duration: 3000 });
        })
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xF1F3F5)
    .justifyContent(FlexAlign.End)
    .padding({ left: 12, right: 12, bottom: 24 })
    .onChildTouchTest((touchInfo) => {
      for (let info of touchInfo) {
        if (info.id === 'MyList') {
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
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12];
  promptAction: PromptAction = this.getUIContext().getPromptAction();
  @State text: string = 'Button';

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
        console.info(`first ${start}`);
        console.info(`last ${end}`);
      })
      .onDidScroll((scrollOffset: number, scrollState: ScrollState) => {
        console.info(`onScroll scrollState = ScrollState ${scrollState.toString()}, scrollOffset = ${scrollOffset}`);
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
          this.text = 'click the button';
          this.promptAction.showToast({ message: 'you click the button.', duration: 3000 });
        })
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xF1F3F5)
    .justifyContent(FlexAlign.End)
    .padding({ left: 12, right: 12, bottom: 24 })
    .onChildTouchTest((touchInfo) => {
      for (let info of touchInfo) {
        if (info.id === 'MyList') {
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
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12];
  promptAction: PromptAction = this.getUIContext().getPromptAction();
  @State text: string = 'Button';

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
        console.info(`first ${start}`);
        console.info(`last ${end}`);
      })
      .onDidScroll((scrollOffset: number, scrollState: ScrollState) => {
        console.info(`onScroll scrollState = ScrollState ${scrollState.toString()}, scrollOffset = ${scrollOffset}`);
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
          this.text = 'click the button';
          this.promptAction.showToast({ message: 'you click the button.', duration: 3000 });
        })
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xF1F3F5)
    .justifyContent(FlexAlign.End)
    .padding({ left: 12, right: 12, bottom: 24 })
    .onChildTouchTest(() => {
      return { strategy: TouchTestStrategy.DEFAULT }
    })
  }
}
```

![onchildtouchtest](figures/on-child-touch-test-default.gif)