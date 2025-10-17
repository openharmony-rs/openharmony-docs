# Custom Event Interception
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiangtao92-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @HelloCrease-->

The custom event interception capability provided for components allows you to dynamically determine the **HitTestMode** attribute of a component based on the position where the event is triggered on the component, as well as other event information such as the input source.

>  **NOTE**
>
>  The initial APIs of this module are supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.


## onTouchIntercept

onTouchIntercept(callback: Callback<TouchEvent, HitTestMode>): T

Binds a custom event interception callback to a component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name       | Type                   | Mandatory | Description                        |
| ---------- | -------------------------- | ------- | ----------------------------- |
| callback      | Callback<[TouchEvent](ts-universal-events-touch.md#touchevent), [HitTestMode](ts-appendix-enums.md#hittestmode9)> | Yes    |  Custom event interception callback. Triggered during [hit testing](../../../ui/arkts-interaction-basic-principles.md#hit-testing). Returns a value to set the component's [hit test behavior](ts-universal-attributes-hit-test-behavior.md).|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

> **NOTE**
>- This API can be called in [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 20.

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
        Text("hello world")
          .backgroundColor(Color.Blue)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            console.info("Text click");
          })
      }
      .width(400)
      .height(300)
      .backgroundColor(Color.Pink)
      .onClick(() => {
        console.info("Column click");
      })
      // Call onTouchIntercept to modify the HitTestMode attribute of the component.
      .onTouchIntercept((event: TouchEvent) => {
        console.info("OnTouchIntercept + " + JSON.stringify(event));
        // Check whether touches is empty before using it.
        if (event && event.touches) {
          let touches = event.touches;
          for(let i = 0; touches[i] != null; i++) {
            console.info('onTouchIntercept touches:', JSON.stringify(touches[i]));
          }
        }
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
