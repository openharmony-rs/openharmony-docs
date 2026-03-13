# Hit Test Control
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

You can configure the [hit test](../../../ui/arkts-interaction-basic-principles.md#hit-testing) behavior for components. In the ArkUI framework, before processing touchscreen events and mouse events, the system performs hit testing between the touch point and the component's response area to identify components that should respond to events. Then ArkUI dispatches the event based on the test result. The **hitTestBehavior** attribute sets different hit test modes, which affects both the hit test results and subsequent event dispatch. For details about the impact, see [HitTestMode](./ts-appendix-enums.md#hittestmode9). This affects the dispatch of [click](ts-universal-events-click.md), [touch](ts-universal-events-touch.md), [drag](ts-universal-events-drag-drop.md), [mouse](ts-universal-mouse-key.md), [axis](ts-universal-events-axis.md), [hover](ts-universal-events-hover.md), [accessibility hover](ts-universal-accessibility-hover-event.md), and [gesture](ts-gesture-settings.md) events.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - When multiple nodes in a **Stack** component have overlapping touch areas, if the touch point hits a child component of the topmost node, only the topmost node will undergo hit testing by default. In this case, to enable hit testing for nodes below, the topmost node must have its **hitTestBehavior** set to **HitTestMode.Transparent**.

## hitTestBehavior

hitTestBehavior(value: HitTestMode): T

Sets the hit test mode for a component. If **hitTestBehavior** is not set, the component defaults to **HitTestMode.Default**.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name           | Type    | Mandatory                            | Description                              |
| -------------------- | -------- | ---------------------------------------- | ---------------------------------------- |
| value | [HitTestMode](./ts-appendix-enums.md#hittestmode9) | Yes| Hit hit test mode for the current component.|

**Return values**

| Type| Description|
| -------- | -------- |
| T | Current component.|

## Example

### Example 1: Understanding Hit Test Effects for Block and Transparent Modes

This example demonstrates the hit test effects of **Block** and **Transparent** hit test modes by setting different [HitTestMode](./ts-appendix-enums.md#hittestmode9) values.

```ts
// xxx.ets
@Entry
@Component
struct HitTestBehaviorExample {
  build() {
    // outer stack
    Stack() {
      Button('outer button')
        .onTouch((event) => {
          console.info('outer button touched type: ' + (event as TouchEvent).type)
        })
      // inner stack
      Stack() {
        Button('inner button')
          .onTouch((event) => {
            console.info('inner button touched type: ' + (event as TouchEvent).type)
          })
      }
      .width("100%").height("100%")
      .hitTestBehavior(HitTestMode.Block)
      .onTouch((event) => {
        console.info('stack touched type: ' + (event as TouchEvent).type)
      })

      Text('Transparent')
        .hitTestBehavior(HitTestMode.Transparent)
        .width("100%").height("100%")
        .onTouch((event) => {
          console.info('text touched type: ' + (event as TouchEvent).type)
        })
    }.width(300).height(300)
  }
}
```

### Example 2: Understanding the Hit Test Effect When the Hit Test Type is BLOCK_HIERARCHY

This example demonstrates the hit test effect when the hit test type is set to **BLOCK_HIERARCHY**, supported since API version 20.

```ts
// xxx.ets
@Entry
@Component
struct BlockHierarchy {
  build() {
    // outer stack
    Stack() {
      Stack() {
        Button('outer button')
          .onTouch((event) => {
            console.info('HitTestMode outer button touched type: ' + (event as TouchEvent).type);
          })
          .width(200)
          .height(200)
          .backgroundColor('#D5D5D5')
        // inner stack
        Stack() {
          Button()
            .id('button150')
            .backgroundColor('#F7F7F7')
            .width(150)
            .height(150)
            .onTouch((event) => {
              console.info('HitTestMode button150 touched type: ' + (event as TouchEvent).type);
            })
            .hitTestBehavior(HitTestMode.Transparent)
          Button()
            .id('button100')
            .backgroundColor('#707070')
            .width(100)
            .height(100)
            .onTouch((event) => {
              console.info('HitTestMode button100 touched type: ' + (event as TouchEvent).type);
            })
            .hitTestBehavior(HitTestMode.Transparent)
          Button()
            .id('button050')
            .backgroundColor('#D5D5D5')
            .width(50)
            .height(50)
            .onTouch((event) => {
              console.info('HitTestMode button050 touched type: ' + (event as TouchEvent).type);
            })
            .hitTestBehavior(HitTestMode.Transparent)
        }
        .width("100%").height("100%")
        // Set the hit test mode: The node itself and its child nodes respond to the hit test, preventing all sibling nodes and parent nodes with lower priority from participating in the hit test.
        .hitTestBehavior(HitTestMode.BLOCK_HIERARCHY)
        .onTouch((event) => {
          console.info('HitTestMode stack touched type: ' + (event as TouchEvent).type);
        })

        Text('Transparent')
          .hitTestBehavior(HitTestMode.Transparent)
          .width("100%").height("100%")
          .onTouch((event) => {
            console.info('HitTestMode text touched type: ' + (event as TouchEvent).type);
          })
      }.width(300).height(300)
      .borderWidth(2)
      .onTouch((event) => {
        console.info('HitTestMode father stack touched type: ' + (event as TouchEvent).type);
      })
    }.width(500).height(500)
    .borderWidth(2)
    .onTouch((event) => {
      console.info('HitTestMode grandfather stack touched type: ' + (event as TouchEvent).type);
    })
  }
}
```

### Example 3: Understanding the Hit Test Effect When the Hit Test Type is BLOCK_DESCENDANTS

This example demonstrates the hit test effect when the hit test type is set to **BLOCK_DESCENDANTS**, supported since API version 20.

```ts
// xxx.ets
@Entry
@Component
struct BlockDescendants {
  build() {
    // outer stack
    Stack() {
      Stack() {
        Button('outer button')
          .onTouch((event) => {
            console.info('HitTestMode outer button touched type: ' + (event as TouchEvent).type);
          })
          .width(200)
          .height(200)
          .backgroundColor('#D5D5D5')
        // inner stack
        Stack() {
          Button('inner button')
            .width(100)
            .height(100)
            .onTouch((event) => {
              console.info('HitTestMode inner button touched type: ' + (event as TouchEvent).type);
            })
        }
        .width("100%").height("100%")
        // Set the hit test mode: The node does not respond to hit tests, and none of its descendants (including children and grandchildren) participate in hit tests either.
        .hitTestBehavior(HitTestMode.BLOCK_DESCENDANTS)
        .onTouch((event) => {
          console.info('HitTestMode stack touched type: ' + (event as TouchEvent).type);
        })

        Text('Transparent')
          .hitTestBehavior(HitTestMode.Transparent)
          .width("100%").height("100%")
          .onTouch((event) => {
            console.info('HitTestMode text touched type: ' + (event as TouchEvent).type);
          })
      }.width(300).height(300)
      .borderWidth(2)
      .onTouch((event) => {
        console.info('HitTestMode father stack touched type: ' + (event as TouchEvent).type);
      })
    }.width(500).height(500)
    .borderWidth(2)
    .onTouch((event) => {
      console.info('HitTestMode grandfather stack touched type: ' + (event as TouchEvent).type);
    })
  }
}
```

### Example 4: Understanding the Hit Test Effect When Multiple Nodes Overlap in the Stack Component

This example demonstrates the hit testing effect when multiple nodes have overlapping touch areas within a **Stack** component. If [HitTestMode](./ts-appendix-enums.md#hittestmode9) is set to **None**, the overlapping background area cannot respond to hit testing. The background area respond to hit testing only when the attribute is set to **Transparent**.

```ts
// xxx.ets
@Entry
@Component
struct Index {
  @State @Watch('onModeChange') mode: number = HitTestMode.None;
  @State modeStr: string = 'None';

  onModeChange() {
    this.modeStr = this.mode === HitTestMode.None ? 'None' : 'Transparent';
  }

  build() {
    Stack() {
      Column()
        .height('100%')
        .width('100%')
        .onTouch(() => {
          console.info('background hit test!')
        })
      Stack() {
        // Click the button to perform hit testing.
        Button('HitTest')
        // Click the button to switch between different hit test modes.
        Button('HitTestMode: ' + this.modeStr)
          .margin({ top: 100 })
          .onClick(() => {
            this.mode = this.mode === HitTestMode.None ?
              HitTestMode.Transparent : HitTestMode.None;
          })
      }
      .height('100%')
      .width('100%')
      //The lower node can respond to hit testing only when HitTestMode of the upper node is set to Transparent.
      .hitTestBehavior(this.mode)
    }
    .height('100%')
    .width('100%')
  }
}
```
