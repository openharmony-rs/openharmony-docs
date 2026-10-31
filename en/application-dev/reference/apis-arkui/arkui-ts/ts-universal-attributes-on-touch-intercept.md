# Custom Event Interception
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=828befee530895124aaf1637c9402999a598c883 translatedAt=2026-09-02T11:56:49.873Z -->

Provides components with a custom event interception capability. It is applicable to scenarios where the **HitTestMode** attribute of a component needs to be dynamically determined based on event information such as the position where the event is pressed on the component and the input source, so as to control the hit testing and event response behavior of the component.

>  **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.


## onTouchIntercept

onTouchIntercept(callback: Callback\<TouchEvent, HitTestMode\>): T

Binds a custom event interception callback to a component.

> **NOTE**
>
> This API can be called in [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 20.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name       | Type                   | Mandatory | Description                        |
| ---------- | -------------------------- | ------- | ----------------------------- |
| callback | Callback\<[TouchEvent](ts-universal-events-touch.md#touchevent), [HitTestMode](ts-appendix-enums.md#hittestmode9)\> | Yes | Custom event interception callback. This function is called back when a [hit testing](../../../ui/arkts-interaction-basic-principles.md#hit-testing) is performed. The [HitTestMode](ts-appendix-enums.md#hittestmode9) of the component is set through the return value. Before using the touches attribute in TouchEvent, verify that it is not empty. |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

## Example

This example demonstrates how to modify the **HitTestMode** attribute of a component using **onTouchIntercept**.

```ts
// xxx.ets
@Entry
@Component
struct Index {
  isPolygon(event: TouchEvent) {
    return true;
  }

  build() {
    Row() {
      Column() {
        Text('hello world')
          .backgroundColor(Color.Blue)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            console.info('Text click');
          })
      }
      .width(400)
      .height(300)
      .backgroundColor(Color.Pink)
      .onClick(() => {
        console.info('Column click');
      })
      // Call onTouchIntercept to modify the HitTestMode attribute of the component.
      .onTouchIntercept((event: TouchEvent) => {
        console.info('OnTouchIntercept + ' + JSON.stringify(event));
        // Check whether touches is empty before using it.
        if (event && event.touches) {
          let touches = event.touches;
          for (let i = 0; touches[i] != null; i++) {
            console.info('onTouchIntercept touches:', JSON.stringify(touches[i]));
          }
        }
        // Return HitTestMode.None to exclude the component from the hit testing when the custom interception condition is met.
        if (this.isPolygon(event)) {
          return HitTestMode.None;
        }
        return HitTestMode.Default;
      })
    }
    .width('100%')
  }
}
```
