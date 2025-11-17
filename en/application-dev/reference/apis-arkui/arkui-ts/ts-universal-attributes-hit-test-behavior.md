# Hit Test Control
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiangtao92-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @HelloCrease-->

You can configure the [hit test](../../../ui/arkts-interaction-basic-principles.md#hit-testing) behavior for components. In the ArkUI framework, before processing touchscreen events and mouse events, the system performs hit testing between the touch point and the component's response area to identify components that should respond to events. Then ArkUI dispatches the event based on the test result. The **hitTestBehavior** attribute sets different hit test response modes, which affects both the hit test results and subsequent event dispatch. For details about the impact, see [HitTestMode](./ts-appendix-enums.md#hittestmode9). This affects the dispatch of [click](ts-universal-events-click.md), [touch](ts-universal-events-touch.md), [drag](ts-universal-events-drag-drop.md), [mouse](ts-universal-mouse-key.md), [axis](ts-universal-events-axis.md), [hover](ts-universal-events-hover.md), [accessibility hover](ts-universal-accessibility-hover-event.md), and [gesture](ts-gesture-settings.md) events.

>  **NOTE**
>  - The APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>  - When the touch areas of nodes in the **Stack** component overlap, hit testing is performed only on the node displayed at the top layer by default. To perform hit testing on the node at the lower layer, set **hitTestBehavior** to **HitTestMode.Transparent** for the upper-layer node.

## hitTestBehavior

hitTestBehavior(value: HitTestMode): T

Sets how the component behaves during hit testing. If **hitTestBehavior** is not set, the component defaults to **HitTestMode.Default**.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name           | Type    | Mandatory                            | Description                              |
| -------------------- | -------- | ---------------------------------------- | ---------------------------------------- |
| value | [HitTestMode](./ts-appendix-enums.md#hittestmode9) | Yes| How the component behaves during hit testing.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

## Example

### Example 1: Understanding Hit Test Effects for Block and Transparent Modes

This example demonstrates the hit test effects of **Block** and **Transparent** hit test modes by setting different **HitTestMode** values.

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

This example demonstrates the hit test effect when the hit test type is set to **BLOCK_HIERARCHY**.

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

This example demonstrates the hit test effect when the hit test type is set to **BLOCK_DESCENDANTS**.

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
