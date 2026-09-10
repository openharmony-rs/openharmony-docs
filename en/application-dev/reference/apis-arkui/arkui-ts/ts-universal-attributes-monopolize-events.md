# Event Monopolization
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=828befee530895124aaf1637c9402999a598c883 translatedAt=2026-09-02T11:55:47.795Z -->

Sets whether a component monopolizes events, including built-in events and custom click, touch, and gesture events defined by developers.<br>
Within a window, if an event on a component with monopolization control responds first, only the events set on this component are allowed to respond in this interaction, and events on other components in the same window do not respond. This capability applies to scenarios where a component needs to respond first and then prevent other components in the same window from responding, reducing interaction conflicts caused by simultaneous responses of multiple components.

>  **NOTE**
>
> - The initial APIs of this module are supported since API version 11. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## monopolizeEvents

monopolizeEvents(monopolize: boolean): T

Sets whether the component exclusively handles events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type| Mandatory| Description                 |
| ----------- | -------- | ------------------------ | ------------------------ |
| monopolize | boolean | Yes | Whether the component monopolizes events. The value true means the component monopolizes events, and false means the opposite.<br>Default value: false<br>**NOTE**<br>1. If the first finger triggers event monopolization of the component, and another finger is pressed before the first finger is lifted, the interaction of the second finger remains in the component monopolization state, and so on.<br>2. If the developer binds a gesture that is triggered simultaneously with the child component through [parallelGesture](ts-gesture-settings.md#parallelgesture), such as [PanGesture](ts-basic-gestures-pangesture.md), and the child component has monopolization control enabled and responds to the event first, the gesture of the parent component will not respond.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component, used for chained calls. |

## Example

This example demonstrates how to set whether a component monopolizes events by configuring monopolizeEvents.

```ts
// xxx.ets
@Entry
@Component
struct Index {
  @State message: string = 'set monopolizeEvents false';
  @State messageOut: string = ' ';
  @State messageInner: string = ' ';
  @State monopolize: boolean = false;

  build() {
    Column() {
      Text(this.message)
        .fontSize(22)
        .margin(10)
      Text(this.messageOut)
        .fontSize(22)
        .margin(10)
      Text(this.messageInner)
        .fontSize(22)
        .margin(10)
      Button('clean')
        .fontSize(22)
        .margin(10)
        // Clear the touch event prompt information of the inner and outer columns through the button click event.
        .onClick(() => {
          this.messageOut = ' ';
          this.messageInner = ' ';
        })
      Button('change monopolizeEvents')
        .fontSize(22)
        .margin(10)
        // Toggle the monopolization control attribute of the inner column through the button click event.
        .onClick(() => {
          this.monopolize = !this.monopolize;
          if (!this.monopolize) {
            this.message = 'set monopolizeEvents false';
          } else {
            this.message = 'set monopolizeEvents true';
          }
        })
      Column() {
        Column() {
        }
        // When this.monopolize is true, tapping the inner column triggers only its own touch event, not the touch event of the outer column.
        // When this.monopolize is false, tapping the inner column triggers both its own touch event and the touch event of the outer column.
        .monopolizeEvents(this.monopolize)
        .width('100%')
        .height('40%')
        .backgroundColor(Color.Blue)
        // Bind the touch event to the inner column.
        .onTouch((event: TouchEvent) => {
          if (event.type == TouchType.Down) {
            console.info('inner column touch down');
            this.messageInner = 'inner column touch down';
          }
        })
      }
      .backgroundColor(Color.Gray)
      .height('100%')
      .width('100%')
      // Bind the touch event to the outer column.
      .onTouch((event) => {
        if (event.type == TouchType.Down) {
          console.info('outside column touch down');
          this.messageOut = 'outside column touch down';
        }
      })
    }
    .height('100%')
  }
}
```
![obscured](figures/monopolize-events.gif)