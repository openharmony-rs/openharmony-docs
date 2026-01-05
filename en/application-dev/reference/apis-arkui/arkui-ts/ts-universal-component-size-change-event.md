# Component Size Change Event
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiangtao92-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

The size change event is triggered whenever the component's size changes.

>  **NOTE**
>
>  The initial APIs of this module are supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.
>  
>  The width and height returned by this event are the width and height of the component after drawing, which may be different from the width and height set for the component.

## onSizeChange

onSizeChange(event: SizeChangeCallback): T

Triggered when the component size changes due to layout updates.

>**NOTE**
>
> 1. This API is triggered when the layout changes. Due to the calculation precision, the return value may be slightly different from the actual physical size.
>
> 2. onSizeChange is a synchronous callback triggered during the layout process. If the state variable is directly changed in onSizeChange, it may be included in the animation closure. Specifically, the animation compares the layout before the animation with the layout after the animation closure. If the onSizeChange callback is triggered synchronously in the layout before the animation, the changes made in the onSizeChange callback are included in the animation process together with the changes in the animation closure. To avoid this problem, you can use [setTimeOut](../../../reference/common/js-apis-timer.md#settimeout) or [postFrameCallback](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#postframecallback12) with a delay of 0 in onSizeChange to delay the UI processing logic to asynchronous execution.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                     | Mandatory| Description                                                        |
| -------- | ------------------------- | ---- | ------------------------------------------------------------ |
| event | [SizeChangeCallback](#sizechangecallback) | Yes  | Size of the component before and after the change.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

## SizeChangeCallback

type SizeChangeCallback = (oldValue: SizeOptions, newValue: SizeOptions) => void

Invoked when the component size changes.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                     | Mandatory| Description                                                        |
| -------- | ------------------------- | ---- | ------------------------------------------------------------ |
| oldValue | [SizeOptions](ts-types.md#sizeoptions) | Yes  | Width and height of the component before the change.|
| newValue | [SizeOptions](ts-types.md#sizeoptions) | Yes  | Width and height of the component after the change.|


## Example

This example demonstrates how to set a size change event for a **Text** component. When the size of the **Text** component changes, the **onSizeChange** event is triggered, allowing you to obtain relevant parameters.

```ts
// xxx.ets
@Entry
@Component
struct AreaExample {
  @State value: string = 'Text'
  @State sizeValue: string = ''

  build() {
    Column() {
      Text(this.value)
        .backgroundColor(Color.Green)
        .margin(30)
        .fontSize(20)
        .onClick(() => {
          this.value = this.value + 'Text'
        })
        .onSizeChange((oldValue: SizeOptions, newValue: SizeOptions) => {
          console.info(`Ace: on size change, oldValue is ${JSON.stringify(oldValue)} value is ${JSON.stringify(newValue)}`)
          this.sizeValue = JSON.stringify(newValue)
        })
      Text('new area is: \n' + this.sizeValue).margin({ right: 30, left: 30 })
    }
    .width('100%').height('100%').margin({ top: 30 })
  }
}
```
![onSizeChange](figures/onSizeChange.gif)
