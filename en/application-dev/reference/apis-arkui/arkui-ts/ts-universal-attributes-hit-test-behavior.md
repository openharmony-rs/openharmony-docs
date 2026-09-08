# Hit Test Control
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=9430c77017ca73641537d932a3d7d8a4c99c078b translatedAt=2026-09-01T12:39:45.097Z -->

Sets the [hit testing](../../../ui/arkts-interaction-basic-principles.md#hit-testing) mode for the component. In the ArkUI framework, when processing touchscreen events and mouse events, a hit test is performed between the press point and the response hot zone of components before the event is triggered, to collect the components that need to respond to the event. Based on the test result, the framework dispatches the event to the components that pass the hit test. When components have touch response conflicts such as overlapping and penetration, you can set different hit test response modes through the hitTestBehavior attribute to affect the hit test collection result and subsequent event dispatch, avoiding unnecessary touch responses. For details about the impact, see the [HitTestMode](./ts-appendix-enums.md#hittestmode9) enum. This attribute affects the dispatch of [click events](./ts-universal-events-click.md), [touch events](./ts-universal-events-touch.md), [drag events](./ts-universal-events-drag-drop.md), [mouse events](./ts-universal-mouse-key.md), [axis events](./ts-universal-events-axis.md), [hover events](./ts-universal-events-hover.md), [accessibility hover events](./ts-universal-accessibility-hover-event.md), and [gesture events](./ts-gesture-settings.md).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - When multiple nodes in a Stack component have overlapping touch areas, if a child component of the topmost node is hit, only the node displayed at the top is subject to the hit test by default. In this case, only when hitTestBehavior of the node displayed at the top is set to HitTestMode.Transparent can the node displayed at the lower layer trigger the hit test.

## hitTestBehavior

hitTestBehavior(value: HitTestMode): T

Sets the hit test mode for a component. If **hitTestBehavior** is not set, the component defaults to **HitTestMode.Default**.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name           | Type    | Mandatory                            | Description                              |
| -------------------- | -------- | ---------------------------------------- | ---------------------------------------- |
| value | [HitTestMode](./ts-appendix-enums.md#hittestmode9) | required | Sets the hit test mode of the current component. |

**Return values**

| Type| Description|
| -------- | -------- |
| T | Returns the current component, used for chained calls. |

## Examples

### Example 1: Understanding the Hit Test Effect When the Hit Test Mode Is Block and Transparent

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
          console.info(`outer button touched type: ${(event as TouchEvent).type}`);
        })
      // inner stack
      Stack() {
        Button('inner button')
          .onTouch((event) => {
            console.info(`inner button touched type: ${(event as TouchEvent).type}`);
          })
      }
      .width('100%').height('100%')
      // Set the hit test type to Block. The node responds to the hit test but prevents sibling nodes from participating in the hit test.
      .hitTestBehavior(HitTestMode.Block)
      .onTouch((event) => {
        console.info(`stack touched type: ${(event as TouchEvent).type}`);
      })

      Text('Transparent')
        // Set the hit test type to Transparent. The node does not intercept the hit test and allows lower-layer nodes to respond to the hit test.
        .hitTestBehavior(HitTestMode.Transparent)
        .width('100%').height('100%')
        .onTouch((event) => {
          console.info(`text touched type: ${(event as TouchEvent).type}`);
        })
    }.width(300).height(300)
  }
}
```

### Example 2: Understanding the Hit Test Effect When the Hit Test Type is BLOCK_HIERARCHY

Starting from API version 20, this example demonstrates the hit test effect when the hit test mode is set to BLOCK_HIERARCHY.

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
            console.info(`HitTestMode outer button touched type: ${(event as TouchEvent).type}`);
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
              console.info(`HitTestMode button150 touched type: ${(event as TouchEvent).type}`);
            })
            .hitTestBehavior(HitTestMode.Transparent)
          Button()
            .id('button100')
            .backgroundColor('#707070')
            .width(100)
            .height(100)
            .onTouch((event) => {
              console.info(`HitTestMode button100 touched type: ${(event as TouchEvent).type}`);
            })
            .hitTestBehavior(HitTestMode.Transparent)
          Button()
            .id('button050')
            .backgroundColor('#D5D5D5')
            .width(50)
            .height(50)
            .onTouch((event) => {
              console.info(`HitTestMode button050 touched type: ${(event as TouchEvent).type}`);
            })
            .hitTestBehavior(HitTestMode.Transparent)
        }
        .width('100%').height('100%')
        // Set the hit test mode: The node itself and its child nodes respond to the hit test, preventing all sibling nodes and parent nodes with lower priority from participating in the hit test.
        .hitTestBehavior(HitTestMode.BLOCK_HIERARCHY)
        .onTouch((event) => {
          console.info(`HitTestMode stack touched type: ${(event as TouchEvent).type}`);
        })

        Text('Transparent')
          .hitTestBehavior(HitTestMode.Transparent)
          .width('100%').height('100%')
          .onTouch((event) => {
            console.info(`HitTestMode text touched type: ${(event as TouchEvent).type}`);
          })
      }.width(300).height(300)
      .borderWidth(2)
      .onTouch((event) => {
        console.info(`HitTestMode father stack touched type: ${(event as TouchEvent).type}`);
      })
    }.width(500).height(500)
    .borderWidth(2)
    .onTouch((event) => {
      console.info(`HitTestMode grandfather stack touched type: ${(event as TouchEvent).type}`);
    })
  }
}
```

### Example 3: Understanding the Hit Test Effect When the Hit Test Type is BLOCK_DESCENDANTS

Starting from API version 20, this example demonstrates the hit test effect when the hit test mode is set to BLOCK_DESCENDANTS.

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
            console.info(`HitTestMode outer button touched type: ${(event as TouchEvent).type}`);
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
              console.info(`HitTestMode inner button touched type: ${(event as TouchEvent).type}`);
            })
        }
        .width('100%').height('100%')
        // Set the hit test mode so that the node itself does not respond to the hit test, and all its descendants (children, grandchildren, and so on) do not respond to the hit test either, without affecting the hit test of ancestor nodes.
        .hitTestBehavior(HitTestMode.BLOCK_DESCENDANTS)
        .onTouch((event) => {
          console.info(`HitTestMode stack touched type: ${(event as TouchEvent).type}`);
        })

        Text('Transparent')
          .hitTestBehavior(HitTestMode.Transparent)
          .width('100%').height('100%')
          .onTouch((event) => {
            console.info(`HitTestMode text touched type: ${(event as TouchEvent).type}`);
          })
      }.width(300).height(300)
      .borderWidth(2)
      .onTouch((event) => {
        console.info(`HitTestMode father stack touched type: ${(event as TouchEvent).type}`);
      })
    }.width(500).height(500)
    .borderWidth(2)
    .onTouch((event) => {
      console.info(`HitTestMode grandfather stack touched type: ${(event as TouchEvent).type}`);
    })
  }
}
```

### Example 4: Understanding the Hit Test Effect When Multiple Nodes Overlap in the Stack Component

This example demonstrates the hit testing effect when multiple nodes have overlapping touch areas within a **Stack** component. If [HitTestMode](./ts-appendix-enums.md#hittestmode9) is set to **None**, the overlapping background area cannot respond to hit testing. The background area responds to hit testing only when the attribute is set to **Transparent**.

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
          console.info('background hit test!');
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